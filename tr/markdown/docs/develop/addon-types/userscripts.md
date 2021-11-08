---
title: Kullanıcı komut dosyaları
description: Kullanıcı komut dosyaları, Scratch sayfaları boyunca kod çalıştırmanıza izin verir - düğme ekleme, Scratch düzenleyiciyi geliştirme veya hayal edebileceğiniz herhangi bir şey gibi şeyler yapabilirsiniz.
---
## Onlar neler?
Kullanıcı komut dosyaları, Scratch sayfaları boyunca kod çalıştırmanıza izin verir - düğme ekleme, Scratch düzenleyiciyi geliştirme veya hayal edebileceğiniz herhangi bir şey gibi şeyler yapabilirsiniz.

## Nasıl userscript eklerim?
**Eklentinizde herhangi bir değişiklik yaptıktan sonra Scratch Eklentilerini `chrome://extensions`dan yenilemeyi unutmayın.**
Eklentinizin (addon.json) manifest dosyasına gidin ve `userscripts"` adında bir özellik ekleyin.
Bu özellik bir dizi olmalıdır.
Dizinin her bir öğesi şu özelliklere sahip olmalıdır: `"url"` ve `"eşleşir"`.
`"url"`, bir JavaScript dosyasına göreli bir URL olmalıdır.
`"matches"`, kullanıcı kodunu çalıştırmak istediğiniz URL'lerin bir dizisi olmalıdır. Yıldız işaretlerini kullanabilirsiniz.
Örnek manifest:
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
  "userscripts": [
    {
      "url": "userscript.js",
      "matches": ["https://scratch.mit.edu/*"]
    },
    {
      "url": "second_userscript.js",
      "matches": ["https://scratch.mit.edu/projects/*", "https://scratch.mit.edu/users/*"]
    }
  ],
  "tags": ["community"],
  "enabled_by_default": false
}
```

## JavaScript dosyası nasıl görünüyor?
Userscripts JS dosyalarının çalışması için belirli bir yapı gerekir.
Kullanıcı komut dosyaları için, tüm kodunuzu şuna benzeyen bir işlevin içine sarmanız **zorunludur**:
```js
export default async function ({ addon, global, console }) {
  console.log("Hello, " + addon.auth.username);
}
```
Daha temiz bir koda sahip olmak için kendi fonksiyonlarınızı yazmak istiyorsanız, bunları ana fonksiyonların içine dahil etmelisiniz:
**Bu çalışacak:**
```js
export default async function ({ addon, global, console }) {
  // This works!
  sayHello();
  function sayHello() {
    console.log("Hello, " + addon.auth.username);
  }
}
```
**Bu işe YARAMAYACAK:**
```js
export default async function ({ addon, global, console }) {
  // Bu işe yaramaz!
  sayHello();
}
function sayHello() {
  console.log("Hello, " + addon.auth.username);
  // Hata: eklenti tanımlı değil!
}
```

## [`addon.*` API'leri](/docs/developing/addon-apis-reference)
Bazı `addon.*` API'lerine userscript' lerden erişebilirsiniz. Daha fazla bilgi için belgelere bakın.

## Kullanıcı komut dosyalarının teknik yönleri
Kullanıcı komut dosyaları, Scratch sayfası tamamen yüklendikten sonra çalışır - başka bir deyişle, `erteleme` modunda çalışırlar.
Teknik olarak konuşursak, her kullanıcı yazısı, bir işlevi dışa aktaran bir JavaScript modülüdür. JavaScript modülleri her zaman "katı modda" çalışır.
Bu, aynı eklentinin kullanıcı komut dosyalarının değişkenleri ve işlevleri PAYLAŞMADIĞI anlamına gelir! Bunu yapmak istiyorsanız, `global` nesnesini kullanmalısınız (daha fazla bilgi aşağıda).
Scratch Addons daha sonra dışa aktarılan bu işlev modüllerini çağırır ve özel sarmalayıcıların yanı sıra `addon.*` API'lerine erişmesini sağlar:
- `addon`: Kullanıcı komut dosyalarına [`addon.*` API'lerine](/docs/developing/addon-apis-reference) erişim sağlar.
- `global`: bu, aynı eklentinin tüm kullanıcı komut dosyaları arasında paylaşılan bir nesnedir. **Örnek kullanım:**
```js
// userscript-1.js
varsayılan zaman uyumsuz işlevini dışa aktar ({ addon, global, konsol }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.username);
}

// userscript-2.js
export default async function ({ addon, global, console }) {
  global.sayHello();
  // Bu, eklenti bildiriminde olduğu sürece çalışır, userscript-1.js, userscripts dizisindeki userscript-2.js'den öncedir.
}
```
- `console`: Bu, gördüğünüz günlüğü hangi eklentinin tetiklediğini kolayca görmenizi sağlayan bir sarmalayıcıdır.

## Kullanıcı komut dosyalarında hata ayıklama
**Eklentinizde herhangi bir değişiklik yaptıktan sonra Scratch Eklentilerini `chrome://extensions`dan yenilemeyi unutmayın.**
Kullanıcı komut dosyalarında hata ayıklamak için öncelikle eklentinizin etkin olduğundan emin olun.
Ardından, kullanıcı komut dosyanızın çalışması gerektiğini belirttiğiniz bir URL'ye gidin.
Ctrl+Shift+J tuşlarına basarak konsolu açın.
Sizinki de dahil olmak üzere eklentilere göre konsol günlüklerini görmelisiniz. Bir devtools uzmanıysanız, kodunuzda kesme noktaları ayarlamakta herhangi bir sorun yaşamayacaksınız.
İpucu: Dosyanızı her seferinde değiştirmeden `addon.*` API'sini test etmek istiyorsanız, eklentinizi `window.addon = addon;` yapın (ana işlevin içinde) ve eklentinizin `konsoldan addon` nesnesi. Bu depoya katkıda bulunmadan önce bu satırı kaldırdığınızdan emin olun! Kullanıcı betikleri global nesneyi kirletmemelidir.