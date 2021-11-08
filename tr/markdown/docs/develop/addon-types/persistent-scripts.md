---
title: Kalıcı Komut Dosyaları
description: Kalıcı komut dosyaları, JavaScript'i arka planda çalıştırmanıza izin verir! Kullanıcıyı bir şeyler hakkında bilgilendirmek veya kullanıcı ihtiyaç duyduğunda hazır olması için verileri önceden yüklemek harikadır.
---

> ** Mümkün olduğunda kalıcı komut dosyalarından kaçınmanız önerilir. [Manifest V3] (https://developer.chrome.com/docs/extensions/mv3/intro/mv3-migration/#background-service-workers)'e gelecekteki bir geçiş, arka plan sayfaları yerine hizmet çalışanlarını kullanmamızı gerektirecektir. kalıcı komut dosyalarını bir meydan okuma yapmak. Geçiş yaptığımızda ne kadar az kalıcı komut dosyası olursa o kadar iyi. **

## Onlar nelerdir?
Kalıcı komut dosyaları, JavaScript'i arka planda çalıştırmanıza izin verir! Kullanıcıyı bir şeyler hakkında bilgilendirmek veya kullanıcı ihtiyaç duyduğunda hazır olması için verileri önceden yüklemek harikadır.

## Kalıcı bir komut dosyasını nasıl ekleyebilirim?
**Eklentinizde herhangi bir değişiklik yaptıktan sonra Scratch Eklentilerini `chrome://extensions`dan yenilemeyi unutmayın.**
Eklentinizin manifest dosyasına (addon.json) gidin ve `"persistent_scripts"` adlı bir özellik ekleyin.
Eklentiniz yalnızca bir kalıcı komut dosyası kullanacak olsa bile bu özellik bir dizi olmalıdır.
Dizinin her öğesi, bir JS dosyasına işaret eden göreli bir URL olmalıdır.
Örnek manifest:
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
  "persistent_scripts": ["background.js"],
  "tags": ["community"],
  "enabled_by_default": false
}
```

## JavaScript dosyası nasıl görünüyor?
Kalıcı komut dosyalarının yanı sıra kullanıcı komut dosyası, çalışması için belirli bir yapı gerektirir.
Kalıcı komut dosyaları için, tüm kodunuzu şuna benzeyen bir işlevin içine sarmanız **zorunludur**:
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  console.log("Hello, " + addon.auth.username);
}
```
Daha temiz bir koda sahip olmak için kendi fonksiyonlarınızı yazmak istiyorsanız, bunları ana fonksiyonların içine dahil etmelisiniz:
**Bu çalışacak:**
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  // This works!
  sayHello();
  function sayHello() {
    console.log("Hello, " + addon.auth.username);
  }
}
```
**Bu işe YARAMAYACAK:**
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  // This WON'T work!
  sayHello();
}
function sayHello() {
  console.log("Hello, " + addon.auth.username);
  // Error: addon is not defined!
}
```

## [`addon.*` API'leri](/docs/developing/addon-apis-reference)
Çoğu `addon.*` API'sine kalıcı komut dosyalarından erişebilirsiniz. Daha fazla bilgi için belgelere bakın.

## Kalıcı komut dosyalarının teknik yönleri
Teknik olarak konuşursak, her kalıcı komut dosyası, bir işlevi dışa aktaran bir JavaScript modülüdür. JavaScript modülleri her zaman "katı modda" çalışır.
Bu, aynı eklentinin kalıcı komut dosyalarının değişkenleri ve işlevleri PAYLAŞMADIĞI anlamına gelir! Bunu yapmak istiyorsanız, `global` nesneyi kullanmalısınız (daha fazla bilgi aşağıda).
Scratch Eklentiler daha sonra dışa aktarılan bu işlev modüllerini çağırır ve özel sarmalayıcıların yanı sıra `addon.*` API'lerine erişmesini sağlar:
- `addon`: [`addon.*` API'lerine](/docs/developing/addon-apis-reference) kalıcı komut dosyasına erişimi sağlar.
- `global`: bu, aynı eklentinin tüm kalıcı komut dosyaları arasında paylaşılan bir nesnedir. **Örnek kullanım:**
```js
// background-1.js
varsayılan zaman uyumsuz işlevini dışa aktar ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  global.sayHello = () => console.log("Hello, " + addon.auth.username);
}

// background-2.js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  global.sayHello();
  // This works, as long as in the addon manifest, background-1.js is before background-2.js in the persistent_scripts array.
}
```
- `console`: Bu, gördüğünüz günlüğü hangi eklentinin tetiklediğini kolayca görmenizi sağlayan bir sarmalayıcıdır.
- `setTimeout` ve `setInterval`: eklentiniz çalışırken devre dışı bırakılırsa, Scratch Addons' un bekleyen zaman aşımlarını ve aralıkları durdurmak için beklemesi gerekir. Bunu başarılı bir şekilde yapabilmek için, eklentilerin `window.setTimeout` ve `window.setInterval` yerine bu sarmalayıcıları kullanması gerekir.
- `clearTimeout` ve `clearInterval`: bellek sızıntılarını önlemek için bunların da sarılması gerekir - Scratch Addons, bir zaman aşımını veya aralığı temizlediğinizi bilmez ve zaman aşımı/aralık kimliğini sebepsiz yere depolar. `window.clearTimeout` veya `window.clearInterval` kullanmamalısınız.

## Kalıcı komut dosyalarında hata ayıklama
**Eklentinizde herhangi bir değişiklik yaptıktan sonra Scratch Eklentilerini `chrome://extensions` dan yenilemeyi unutmayın.**
Kalıcı komut dosyalarında hata ayıklamak için öncelikle eklentinizin etkin olduğundan emin olun.
Ardından, `chrome://extensions` a gidin, geliştirici modunun açık olduğundan emin olun ve Scratch Addons'u bulun.
"Görünümleri inceleyin: background/background.html" yazan yere tıklayın.
İşte bu kadar - eklentinizdeki tüm konsol günlükleri orada olacak ve bir devtools uzmanıysanız, kodunuzda kesme noktaları ayarlamakta herhangi bir sorun yaşamayacaksınız.
İpucu: Dosyanızı her seferinde değiştirmeden `addon.*` API'sini test etmek istiyorsanız, eklentinizi `window.addon = addon;` yapın (ana işlevin içinde) ve eklentinizin ` konsoldan addon` nesnesi. Bu depoya katkıda bulunmadan önce bu satırı kaldırdığınızdan emin olun! Kalıcı komut dosyaları genel nesneyi kirletmemelidir.