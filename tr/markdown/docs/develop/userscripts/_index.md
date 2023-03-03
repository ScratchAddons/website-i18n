---
title: Userscript'ler
description: Userscript'ler, kullanıcı bir Scratch sayfasını her yüklediğinde yürütülen JavaScript dosyalarıdır. Belgenin HTML'sini değiştirebilir, yeni düğmeler ekleyebilir, Scratch düzenleyicisinin davranışlarını özelleştirebilir ve çok daha fazlasını yapabilirler.
---

Userscript'ler, kullanıcı bir Scratch sayfasını her yüklediğinde yürütülen JavaScript dosyalarıdır. Belgenin HTML'sini değiştirebilir, yeni düğmeler ekleyebilir, Scratch düzenleyicisinin davranışlarını özelleştirebilir ve çok daha fazlasını yapabilirler.

Tampermonkey ve Greasemonkey gibi userscript yöneticileri için indirebileceğiniz userscript'lere benzer şekilde, Scratch Eklentileri userscript'leri, Scratch'in kendisinden gelen JavaScript koduyla aynı çalıştırma bağlamında yürütülen JavaScript parçalarından oluşur. Tarayıcı uzantısı sözlüğünde bu çalıştırma bağlamı, genellikle "ana dünya" ya da "main world" olarak adlandırılır.

Scratch Eklentileri userscript'leri bir tarayıcı uzantısının parçası olsa da, herhangi bir `chrome.*` veya `browser.*` API'sine erişemezler. Bunun yerine Scratch Eklentileri bir [`addon.*` API](/docs/reference/addon-api/) sunar.


## Eklenti manifest'inde userscript'leri çağırma

{{< admonition warning >}}
Eklenti manifest dosyasının güncellenmesi gibi **bazı değişikliklerin etkili olması için uzantının `chrome://extensions` adresinden yeniden yüklenmesi gerekir**.

Halihazırda var olan bir userscript JavaScript dosyasının kaynağını değiştirirken uzantıyı yeniden yüklemek gerekli değildir. Bu gibi durumlarda, sayfayı yeniden yüklemek yeterlidir.
{{< /admonition >}}

Userscript'ler, bir "userscripts" dizisi içinde çağırılır.

Dizinin her ögesi aşağıdaki özelliklere sahip olmalıdır:
- `"url"`: bir JavaScript dosyasına ilişkin URL.
- `"matches"`: userscript'in çalışacağı Scratch sayfalarının listesi. Daha fazla bilgi için [matches](/docs/reference/addon-manifest/#matches) sayfasına bakın.

Örnek manifest:
```json
{
  "name": "Scratch Mesajlaşma",
  "description": "Scratch mesajlarınızı kolayca okumanızı ve yanıtlamanızı sağlar.",
  "userscripts": [
    {
      "url": "userscript.js",
      "matches": ["projects", "https://scratch.mit.edu/", "profiles"]
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```

## İlk userscript'ini oluşturma

Uzantı içerik kodlarından ve Tampermonkey userscript'lerinden farklı olarak, tüm kodunuzu bir varsayılan dışa aktarma modülü içine yazmanız gerekir:
```js
// Example userscript
export default async function ({ addon, console }) {
  console.log("Selam, " + await addon.auth.fetchUsername());
  console.log("Bugün nasılsın?");
}
```

JavaScript'in, işlevlerin diğer işlevlerin içinde çağırılmasına izin verdiğini unutmayın, örneğin:
```js
export default async function ({ addon, console }) {
  async function kullaniciyaSelamVer() {
    console.log("Selam, " + await addon.auth.fetchUsername());
  }

  await kullaniciyaSelamVer();
  console.log("Bugün nasılsın?");
}
```

{{< admonition info >}}
Birçok `addon.*` API yardımcısına userscript'lerden erişebilirsiniz. Örneğin, geçerli kullanıcı adını alabilir, sayfada bir öge bulunana kadar bekleyebilir veya Scratch VM nesnesine bir başvuru alabilirsiniz.

Daha fazla bilgi için [API referansı](/docs/reference/addon-api/)na göz atın.
{{< /admonition >}}


## Belge HTML'sini düzenlemek

Sayfanın HTML'sini düzenlemek için [tarayıcı DOM API'leri](https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API)ni kullanın.

İşte bir örnek:
```js
const myButton = document.createElement("button");
myButton.textContent = "Tıkla bana!";
myButton.classList.add("button");
myButton.setAttribute("title", "Bir düğmenin üzerinde duruyorsun");

const myContainer = document.querySelector(".container");
myContainer.append(myButton);
```

## Userscript'lerin yerelleştirilmesi

Eklenti userscript'lerinin bazen İngilizce kelimelere veya cümlelere başvurması gerekir. Çeviri sürecinin bir parçası olabilmeleri için bunları sabit olarak kodlamadığınızdan emin olun.

{{< admonition error >}}
```js
// Bunu yapma:
document.querySelector(".sa-find-bar").placeholder = "Blok ara";
```
{{< /admonition >}}

Çevrilebilir bir dizi oluşturmak için, şu adımları takip edin:
1. `/addon-l10n/en` klasörü içerisine `eklenti-kimligi.json` adında bir dosya ekle.
2. Her dizi için bir ID tanımlayın:
```json
{
  "addon-id/find": "Find blocks"
}
```
3. Userscript'te `msg()` işlevini içe aktardığınızdan emin olun. Userscript'inizin ilk satırı şöyle görünmelidir:
```js
export default async function ({ addon, console, msg  }) {
                                              // ^^^
```
4. Kodunuzda sabit kodlanmış bir dizi yapmak yerine `msg()` işlevini kullanın:
```js
document.querySelector(".sa-find-bar").placeholder = msg("find");
```

{{< admonition info >}}
Userscript'lerin yerelleştirilmesi hakkında daha fazla bilgi için [bu sayfa](/docs/localization/localizing-addons/)ya bak.
{{</admonition >}}


## Teknik detaylar

Her userscript dosyası, bir işlevi dışa aktaran bir JavaScript modülüdür. Scratch Eklentileri, modülü yalnızca gerekirse içe aktarır ve sayfa tamamen yüklendikten sonra çalıştırır.

Userscript'ler özünde JavaScript modülleridir, dolayısıyla her zaman ["strict mode"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)da çalışırlar. Bu, ayrıca userscript'lerin diğer JavaScript dosyalarını içe aktarmak için [top-level imports](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) kullanabileceği anlamına gelir.

The order in which userscripts run may vary on each page load. After page load, the user might dynamically enable some addons in a custom order, so order of execution is never guaranteed. Some APIs like [`addon.tab.appendToSharedSpace`](addon.tab.appendtosharedspace) attempt to fix any potential race conditions and unexpected behavior when dynamically enabling addons.

### runAtComplete

Userscripts may opt-in into being executed before the page has fully loaded by specifying `"runAtComplete": false` in the addon manifest, once for each userscript.

As of now, only `document.head` is guaranteed to exist when running a userscript early. In the future, `document.body` will also be guaranteed to exist, so no userscripts will ever run before the HTML document loaded enough to reach `</head> <body>`.
