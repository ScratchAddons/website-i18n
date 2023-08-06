---
title: En İyi Yöntemler
description: Userstyle yazarken veya incelerken bu en iyi yöntemleri takip edin.
---

Userstyle yazarken veya incelerken bu en iyi yöntemleri takip edin.


<!-- YAPILACAK: ## Eklenti karanlık modu desteği -->
<!-- Editor-dark-mode, dark-www ve scrapr2'den CSS değişkenlerine atıfta bulunma örnekleri -->


## Uluslararasılaştırma

### Daha uzun sözcükleri olan dilleri göz önünde bulundur

Bazı dillerde düğmeler gibi UI ögelerinin daha dar veya daha geniş olabileceğini unutmayın.

<!-- YAPILACAK: ### Sağdan sola yazılan dilleri destekleme (RTL) -->


## Scratch'in var olan UI'ını şekillendirme


### Karma işlevi uygulanmış sınıf adlarını hedeflemekten kaçının

Scratch proje düzenleyicisi genellikle `class_name_{hash}` biçimini izleyen sınıf adları içerir. Örneğin, `green-flag_green-flag_1kiAo`.

As the hashes might change in the future and may differ between Scratch forks, you should avoid using them in userstyles.

{{< admonition error >}}
```css
/* Bunu yapmayın: */
.green-flag_green-flag_1kiAo {
  visibility: hidden;
}
```
{{< /admonition >}}

{{< admonition success >}}
```css
/* Onun yerine bunu yapın: */
[class*="green-flag_green-flag_"] {
  visibility: hidden;
}
```
{{< /admonition >}}

### Kesinlikle gerekli olmadıkça `!important`tan kaçının

If possible, use [CSS specificity](https://web.dev/learn/css/specificity/) features to make your selectors more specific, instead of using `!important`.
<!-- This could be more detailed -->


## Eklentinin UI ögelerini şekillendirme


### Begin addon-defined class names with `sa-`

{{< admonition info >}}
We always use `kebab-case` when defining our own class names.
{{< /admonition >}}

We recommend that addon-defined class names begin with `sa-` to avoid potential name collisions with Scratch or other extensions.

It is also recommended to include the addon ID (or part of it) in the class name.

<!-- TODO: ### explain usage of z-index in the Scratch editor and related concepts -->
