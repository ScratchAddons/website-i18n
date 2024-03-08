---
title: En İyi Yöntemler
description: Userscript kodunu yazarken veya incelerken buradaki en iyi yöntemleri takip edin.
---

Userscript kodunu yazarken veya incelerken buradaki en iyi yöntemleri takip edin.


## DOM kullanımı


### "onevent" yerine addEventListener kullanın

`onclick` gibi HTML ögelerinde "onevent" değerleri kullanmaktan kaçının. Bunun yerine, `addEventListener` kullanın. Bu, çakışmadan birden çok eklentinin aynı olayı aynı ögeye kaydetmesine olanak tanır.
"onevent" kullanımı hâlâ geçerlidir, ancak yalnızca olayı kaydeden aynı eklenti tarafından oluşturulan ögeler için geçerlidir.
Her durumda, "onevent" HTML özelliklerini kullanmaktan kaçının, örneğin `element.setAttribute("onclick", "bunu yapma")`.

{{< admonition error >}}
```js
// Bunu yapma:
document.querySelector(".remix-button").onclick = () => {
  prompt("Katkı yapmak istediğinizden emin misiniz?");
};
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Onun yerine bunu yap:
document.querySelector(".remix-button").addEventListener("click", () => {
  prompt("Katkı yapmak istediğinizden emin misiniz?");
});
```
{{< /admonition >}}

### innerHTML kullanmaktan kaçının

`innerHTML` kullanmaktan kaçının. Bunun yerine `innerText` veya `textContent` kullanın.
Potansiyel olarak XSS güvenlik açıklarına yol açabilecek `insertAdjacentHTML`, `outerHTML` ve `document.write()` gibi diğer API'lerden de kaçınılmalıdır.

{{< admonition error >}}
```js
// Bunu yapma:
document.querySelector(".sa-remix-button").innerHTML = `<span>{projectTitle} Projesine Katkı Yap</span>`;
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Onun yerine bunu yap:
const span = document.createElement("span");
span.textContent = `${projectTitle} Projesine Katkı Yap`;
document.querySelector(".sa-remix-button").append(span);
```
{{< /admonition >}}

### Ögeleri kaldırmak yerine gizleyin

Aşırı durumlarda proje sayfasının çökmesine neden olabilecek HTML ögelerinde `.remove()` yöntemini çağırmaktan kaçının.
Eklentiler, yalnızca belirli durumlarda kendi oluşturdukları ögeler için kullanabilirler.

{{< admonition error >}}
```js
// Bunu yapma:
document.querySelector(".remix-button").remove();
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Onun yerine bunu yap:
document.querySelector(".remix-button").style.display = "none";

// Ya da bir userstyle'dan yardım alarak bunu yap:
document.querySelector(".remix-button").classList.add("sa-remix-button-hidden");
```
{{< /admonition >}}

### waitForElement'i yalnızca gerekli olduğunda kullanın

Ögenin var olduğu garanti ediliyorsa `addon.tab.waitForElement` API'sini kullanmaktan kaçının. Yine de düzgün çalışacak ve performansa büyük bir etkisi olmayacaktır, ancak kodu okuyan diğer geliştiricilerin kafasını karıştırabilir. waitForElement'in kullanımı genellikle ögenin o çalıştırma noktasında bulunmayan en az 1 senaryo olduğu anlamına gelmelidir.
Örneğin, userscript `"runAtComplete": false` ile bildirilmedikçe, forum gönderilerini ararken waitForElement kullanmak gerekli değildir. Bu gibi durumlarda, genelde `document.querySelectorAll()` işlevini kullanmanız yeterlidir.

### parentElement ögesini suistimal etmek yerine element.closest() ögesini kullanın

Bir ögenin atalarını çaprazlarken parentElement ögesini aşırı fazla kullanmaktan kaçının. Bunun yerine, `element.querySelector()` ile çok benzer şekilde çalışan `element.closest()` ögesini kullanın.

{{< admonition error >}}
```js
// Bunu yapma:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.parentElement.parentElement.parentElement.parentElement;
})
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Onun yerine bunu yap:
reportButton.addEventListener("click", (event) => {
  const commentElement = event.target.closest(".comment");
})
```
{{< /admonition >}}


## JavaScript en iyi yöntemler


### Modern JavaScript'i kullanın

- `XMLHttpRequest` yerine `fetch()` gibi daha yeni API'leri tercih edin.
- Karşılaştırma yapmak için asla `==` kullanmayın. Onun yerine `===` kullanın.
- When listening to keyboard events, accessing `event.key` is the preferred way to know which key was pressed. In general, you should avoid `event.code` and `event.keyCode`.
- Bir nesne bazen `null` olabiliyorsa isteğe bağlı zincirlemeyi kullanın.
Örneğin, `document.querySelector(".remix-button")?.textContent`.
- `for ... of` döngülerini veya `.forEach()`'i kullanın.
`for (let i = 0; i < arr.length; i++)` gibi C tarzı döngülerden kaçının.

### Değişken yeniden atanabilirse "const" yerine yalnızca "let" kullanın

{{< admonition info >}}
"let" veya "const" ile tanımlanmış olmalarına bakılmaksızın değişkenleri adlandırmak için genellikle `camelCase` kullanırız.
Sabit diziler veya sayılar içinse genellikle `SNAKE_CASE` kullanırız.

İşte bir örnek:
```js
let eylemSayaci = 0;
eylemSayaci++;

const katkiButonu = document.querySelector(".remix-button");

const VARSAYILAN_YAKINLASTIRMA = 1.20;
```
{{< /admonition >}}

Kodunuzu okuyan kişiler, "let" anahtar kelimesi aracılığıyla bildirilen bir değişkenin, kodun başka bir noktasında yeniden atanabileceğini varsayabilir. Aksi takdirde, bunun yerine "const" anahtar kelimesini kullanın.
JavaScript'te bir nesneyi veya diziyi "const" olarak bildirmenin, değerlerinin dondurulduğu anlamına gelmediğini unutmayın. Değişkenin kendisi yeniden atanamasa bile, nesnedeki değerler yine de değiştirilebilir.

### Evrensel değişkenleri değiştirmeyin

`fetch()` gibi genel bir işlevi kirletmediğiniz sürece, evrensel `window` nesnesindeki özellikleri değiştirmekten kaçının.
Birden çok eklentinin birbirleri arasında bilgi veya fonksiyon paylaşması gerekiyorsa, bir JS modül dosyası oluşturun ve onu her iki userscript'ten de içe aktarın.

{{< admonition error >}}
```js
// Bunu yapma:
window.isDarkMode = true;
```
{{< /admonition >}}

### Fonksiyonları varsayılan dışa aktarmanın dışında bildirmeyin

`export default async function(){}` fonksiyonu dışında fonksiyon bildirmek için hiçbir neden yoktur. JavaScript, fonksiyonların diğer fonksiyonların içinde çağırılmasına izin verir.

Uygunsa, fonksiyonları ayrı JS modül dosyalarına (eklenti manifest'inde userscript'leri olarak çağırılmayanlar) taşıyabilirsiniz ancak onu bağımsız değişken olarak kabul eden bir kurulum fonksiyonunu ortaya çıkarmadığınız ve fonksiyonu userscript giriş noktasında çağırmadığınız sürece, içe aktarılan bu dosyaların `addon` nesnesine erişimi olmayacağını unutmayın.

### Fonksiyonları temizlemeyin

`XMLHttpRequest`, `fetch()` veya `FileReader()` gibi Scratch VM yöntemleri, birden çok eklenti aynı fonksiyonu kirletmek isteyebilir.
Bu durumlarda, userscript'lerden biri gerçek fonksiyonu kirletirken, diğerleri zaten kendilerini kirletmiş olan fonksiyonları kirletecektir. Örneğin, kirleten ilk userscript kirletmeyi kaldırmaya karar verirse (örneğin, `window.fetch = realFetch` yaparak), "kirlilik zinciri"ndeki diğer tüm fonksiyonlar da kaybolur, ki bu beklenmeyen bir durumdur.
Bu nedenle fonksiyonlar temizlenmemiş olmamalıdır. Bunun yerine, bağımsız değişkenleri orijinal fonksiyona iletin.

{{< admonition error >}}
```js
const eskiKuklaSilme= vm.deleteSprite;
const yeniKuklaSilme = function (...args) {
  // ...
}

addon.self.addEventListener("disabled", () => {
  // Bunu yapma:
  vm.deleteSprite = eskiKuklaSilme;
});
```
{{< /admonition >}}

{{< admonition success >}}
```js
// Onun yerine bunu yap:
const eskiKuklaSilme = vm.deleteSprite;
const yeniKuklaSilme = function (...args) {
  if (addon.self.disabled) return eskiKuklaSilme.apply(this, args);
  // ...
};
```
{{< /admonition >}}
