---
title: Eklenti Temelleri
---

## Eklenti nedir, gerçekten?
Aslında bir eklenti, bir userscript ile bir userstyle ya da ikisinin de birleşiminden fazlası değildir. Bunlardan herhangi biri varsa, onları tek bir ad altında aynı eklentinin parçası yaparız. Örneğin, "Scratch 3 Geliştirici Araçları" eklentisinde, düzenleyiciye bir arama çubuğu eklemekten sorumlu bir userscript ve bu kutuya CSS ekleyen bir userstyle vardır.

## Userscript nedir?
Bir userscript, bir Scratch sekmesiyle birlikte çalışan bir JavaScript kodu parçasıdır. Bu userscript'in nerede çalışacağını seçebilirsiniz, örneğin yalnızca proje sayfalarını belirtebilirsiniz. Userscript'ler, tarayıcı uzantılarındaki içerik komut dosyalarına benzer ve daha önce bir userscript yöneticisi kullandıysanız, bunların temelde aynı olduğunu göreceksiniz.
Userscript'ler, örneğin gezinme çubuğuna düğmeler eklemek veya kaldırmak gibi, Scratch sitesinin davranışını değiştirmek için yararlıdır.

## Bir userstyle nedir?
Bir userstyle, userscript'e benzer; onlar için bağlantı kalıpları da belirtebilirsiniz. Ancak, userstyle'lar JavaScript yerine CSS'i kullanır. Bunlar genellikle userscript'lerde kendileri tarafından eklenen ögelere stil vermek için kullanılırlar, ancak yerel Scratch ögelerine stil vermek için de kullanılabilirler. Durum böyle olduğundan, genellikle onlara "temalar" deriz.

## Kavramsal olarak, bir eklenti ne olmalıdır?
Yeni bir eklenti oluşturmanın veya mevcut bir eklentiyi değiştirmenin daha iyi bir fikir olup olmadığını merak edebilirsiniz.
2 eklenti bu özelliklerin bazılarını paylaşıyorsa, muhtemelen birleştirilmelidirler.
- Her ikisi de, kullanıcı etkileşimi gerektiren izinlere (bildirimler gibi) ihtiyaç duyar veya ihtiyaç duymaz.
- Bir sürü kod paylaşıyorlar.
- Kullanıcı, eklentinin her iki özelliği de sunmasını bekler.
- Ayrılırlarsa, birbirlerine müdahale edebilirler.

Eklentilerin kullanıcı tarafından özelleştirilebileceğini unutmayın - yeni işlevler eklemek, özellikle yapmadığımız sürece eklentinin eski kullanıcılarını etkilemez.