---
title: En İyi Yöntemler
description: Userstyle yazarken veya incelerken bu en iyi yöntemleri takip edin.
---

Userstyle yazarken veya incelerken bu en iyi yöntemleri takip edin.


<!-- YAPILACAK: ## Eklenti karanlık modu desteği -->
<!-- Editor-dark-mode, dark-www ve scrapr2'den CSS değişkenlerine atıfta bulunma örnekleri -->


## Uluslararasılaştırma

### Daha uzun sözcükleri olan dilleri göz önünde bulundur

Remember that in some languages, UI elements such as buttons may be narrower or wider.

<!-- YAPILACAK: ### Sağdan sola yazılan dilleri destekleme (RTL) -->


## Scratch'in var olan UI'ını şekillendirme


### Karma işlevi uygulanmış sınıf adlarını hedeflemekten kaçının

Scratch proje düzenleyicisi genellikle `class_name_{hash}` biçimini izleyen sınıf adları içerir. Örneğin, `green-flag_green-flag_1kiAo`.

Karmalar gelecekte değişebileceğinden ve Scratch fork'ları arasında farklılık gösterebileceğinden bunları userstyle'larda kullanmaktan kaçınmalısınız.

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

Mümkünse seçimlerinizi daha spesifik yapmak adına `!important` yerine [CSS specificity](https://web.dev/learn/css/specificity/) özelliklerini kullanın.
<!-- Bu daha detaylandırılabilir -->


## Eklentinin UI ögelerini şekillendirme


### Eklenti tanımlı sınıf adlarını `sa-` ile başlatın

{{< admonition info >}}
Kendi sınıf isimlerimizi tanımlarken her zaman `kebab-case` kullanırız.
{{< /admonition >}}

Scratch veya diğer uzantılarıyla muhtemel isim çakışmalarını engellemek için eklenti tanımlı sınıf isimlerini `sa-` ile başlatmanızı öneriyoruz.

Ayrıca sınıf ismine eklenti kimliğini (ya da bir kısmını) eklemeniz de önerilir.

<!-- YAPILACAK: ### Scratch düzenleyicide z-endeksi kullanımını ve ilgili kavramları açıkla -->
