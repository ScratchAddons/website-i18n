---
title: Kalıcı Komut Dosyaları
description: Kalıcı komut dosyaları, JavaScript' i arka planda çalıştırmanıza izin verir! Kullanıcıyı bir şeyler hakkında bilgilendirmek veya kullanıcı ihtiyaç duyduğunda hazır olması için verileri önceden yüklemek harikadır.
---

> **Mümkün olduğunca kalıcı komut dosyalarından kaçınmanızı öneririz. Eğer [Manifest V3](https://developer.chrome.com/docs/extensions/mv3/intro/mv3-migration/#background-service-workers)' e geçiş yapılırsa, arka plan sayfaları yerine hizmet çalışanlarını kullanmamızı ve kalıcı komut dosyalarını bir meydan okuma yapmak gerektirecektir. Geçiş yaptığımızda ne kadar az kalıcı komut dosyası olursa o kadar iyi olur.**

## O da neyin nesi?
Kalıcı komut dosyaları, JavaScript'i arka planda çalıştırmanıza izin verir! Kullanıcıyı bir şeyler hakkında bilgilendirmek veya kullanıcı ihtiyaç duyduğunda hazır olması için verileri önceden yüklemek harikadır.

## Kalıcı bir komut dosyasını nasıl ekleyebilirim?
**Eklentinizde herhangi bir değişiklik yaptıktan sonra Scratch Eklentilerini `chrome://extensions` dan yenilemeyi unutmayın.**
Eklentinizin manifest dosyasına (addon.json' a) gidin ve `"persistent_scripts"` adlı bir özellik ekleyin.
Eklentiniz yalnızca bir kalıcı komut dosyası kullanacak olsa bile bu özellik bir dizi olmalıdır.
Dizinin her öğesi, bir JS dosyasını gösteren ilgili bir URL bulundurmalı.
Örnek manifest:
```json
{
  "name": "Scratch Mesajlaşma",
  "description": "Scratch mesajlarınızı kolayca okumanızı ve yanıtlamanızı sağlar.",
  "persistent_scripts": ["background.js"],
  "tags": ["community"],
  "enabled_by_default": false
}
```

## JavaScript dosyası nasıl görünüyor?
Kalıcı komut dosyalarının yanı sıra kullanıcı komut dosyası, çalışması için belirli bir yapı gerektirir.
Kalıcı komut dosyaları için, tüm kodunuzu şuna benzeyen bir işlevin içine yazmanız **zorunludur**:
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  console.log("Merhaba, " + addon.auth.username);
}
```
Daha temiz bir koda sahip olmak için kendi fonksiyonlarınızı yazmak istiyorsanız, bunları ana fonksiyonların içine dahil etmelisiniz:
**Bu çalışmalı:**
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  // Bu çalışıyor!
  sayHello();
  function sayHello() {
    console.log("Merhaba, " + addon.auth.username);
  }
}
```
**Bu işe YARAMAYACAK:**
```js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  // Bu işe YARAMAZ!
  sayMerhaba();
}
function sayMerhaba() {
  console.log("Merhaba, " + addon.auth.username);
  // Hata: eklenti tanımlı değil!
}
```

## [`eklenti.*` API'leri](/docs/developing/addon-apis-reference)
Çoğu `eklenti.*` API' sine kalıcı komut dosyalarından erişebilirsiniz. Daha fazla bilgi için belgelere bakın.

## Kalıcı komut dosyalarının teknik yönleri
Teknik olarak konuşursak, her kalıcı kod dosyası, bir fonksiyonu dışa aktaran bir JavaScript modülüdür. JavaScript modülleri her zaman "katı mod"' da çalışır.
Bu, aynı eklentinin kalıcı komut dosyalarının değişkenleri ve işlevleri PAYLAŞMADIĞI anlamına gelir! Bunu yapmak istiyorsanız, `global` nesneyi kullanmalısınız (daha fazla bilgi aşağıda).
Scratch Eklentileri daha sonra dışa aktarılan bu işlev modüllerini çağırır ve özel sarmalayıcıların yanı sıra `eklenti.*` API' lerine erişmesini sağlar:
- `addon`: [`addon.*` API' lerine](/docs/developing/addon-apis-reference) kalıcı komut dosyası erişimi verir.
- `global`: bu, aynı eklentinin tüm kalıcı komut dosyaları arasında paylaşılan bir nesnesidir. **Örnek kullanım:**
```js
// background-1.js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  global.sayMerhaba = () => console.log("Merhaba, " + addon.auth.username);
}

// background-2.js
export default async function ({ addon, global, console, setTimeout, setInterval, clearTimeout, clearInterval }) {
  global.sayMerhaba();
  // Bu, eklenti bildiriminde olduğu sürece, background-1.js, persistan_scripts dizisindeki background-2.js'den önce olduğu sürece çalışır.
}
```
- `console`: Bu, gördüğünüz günlüğü hangi eklentinin tetiklediğini kolayca görmenizi sağlayan bir sarmalayıcıdır.
- `setTimeout` ve `setInterval`: eklentiniz çalışırken devre dışı bırakılırsa, Scratch Eklentilerin bekleyen zaman aşımlarını ve aralıkları durdurmak için beklemesi gerekir. Bunu başarılı bir şekilde yapabilmek için, eklentilerin `window.setTimeout` ve `window.setInterval` yerine bu sarmalayıcıları kullanması gerekir.
- `clearTimeout` ve `clearInterval`: bellek sızıntılarını önlemek için bunların da sarılması gerekir - Scratch Eklentileri, bir zaman aşımını veya aralığı temizlediğinizi bilmez ve zaman aşımı/aralık kimliğini sebepsiz yere depolar. `window.clearTimeout` veya `window.clearInterval` kullanmamalısınız.

## Kalıcı komut dosyalarında hata ayıklama
**Eklentinizde herhangi bir değişiklik yaptıktan sonra Scratch Eklentilerini `chrome://extensions`' dan yenilemeyi unutmayın.**
Kalıcı komut dosyalarında hata ayıklamak için öncelikle eklentinizin etkin olduğundan emin olun.
Ardından, `chrome://extensions`' a gidin, geliştirici modunun açık olduğundan emin olun ve Scratch Eklentilerini bulun.
"Görünümleri inceleyin: background/background.html" yazan yere tıklayın.
İşte bu kadar - eklentinizdeki tüm konsol günlükleri orada olacak ve bir devtools uzmanıysanız, kodunuzdaki kesme işaretlerini ayarlamakta herhangi bir sorun yaşamayacaksınız.
Profesyonel ipucu: Dosyanızı her seferinde değiştirmeden `addon.*` API' sini test etmek istiyorsanız, eklentinizi (ana işlevin içinde iken) `window.addon = addon;` yapın ve eklentinizin konsolundan `addon` nesnesini kaldırın. Bu depoya katkıda bulunmadan önce bu satırı kaldırdığınızdan emin olun! Kalıcı komut dosyaları genel nesneyi kirletmemelidir.