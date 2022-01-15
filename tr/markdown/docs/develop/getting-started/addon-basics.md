---
title: Eklenti Temelleri
---

## Eklenti nedir, gerçekten?
Aslında bir eklenti, şunlardan en az birinin birleşiminden çok daha fazlası değildir: Kalıcı Komut Dosyaları, Kullanıcı Komut Dosyaları ve Kullanıcı Stilleri. Bunlardan herhangi biri ilgiliyse, onları tek bir ad altında aynı eklentinin parçası yaparız. Örneğin, "Scratch 3 Geliştirici Araçları" eklentisinde, düzenleyiciye bir bulma kutusu eklemekten sorumlu bir kullanıcı komut dosyası ve bu kutuya CSS ekleyen bir kullanıcı komut dosyası vardır.

## Kalıcı Kod Dosyası nedir?
Kalıcı komut dosyası, kullanıcının açık Scratch sekmesi olmasa bile her zaman arka planda çalışan bir JavaScript kodu parçasıdır. Örneğin, Scratch' te bir güncelleme olup olmadığını kullanıcıya bildirmek için kullanışlıdırlar. Kalıcı komut dosyaları, tarayıcı uzantılarındaki arka plan komut dosyalarına benzer.

## Kullanıcı Komut Dosyası nedir?
Bir kullanıcı komut dosyası, Scratch sekmesiyle birlikte çalışan bir JavaScript kodu parçasıdır. Kalıcı komut dosyalarından farklı olarak, bu kullanıcı kodunun ne zaman çalışacağını özel olarak belirtebilirsiniz. Örneğin yalnızca proje sayfalarını belirtebilirsiniz. Kullanıcı komut dosyaları, tarayıcı uzantılarındaki içerik komut dosyalarına benzer ve daha önce bir kullanıcı komut dosyası yöneticisi kullandıysanız, bunların temelde aynı olduğunu fark edeceksinizdir.
Kullanıcı komut dosyaları, örneğin gezinme çubuğuna düğmeler eklemek veya kaldırmak gibi, Scratch web sitesinin davranışını değiştirmek için yararlıdır.

## Kullanıcı Stili nedir?
Bir kullanıcı stili, bir kullanıcı stiline benzer; onlar için URL kalıpları da belirtebilirsiniz. Ancak, kullanıcı stilleri JavaScript yerine CSS' yi kullanır. Bunlar genellikle kullanıcı komut dosyalarında kendileri tarafından eklenen öğelere stil vermek için kullanılır, ancak yerel Scratch öğelerine stil vermek için de kullanılabilirler. Durum böyle olduğundan, genellikle onlara "temalar" deriz.

## Tam olarak, bir eklenti ne olmalıdır?
Yeni bir eklenti oluşturmanın veya mevcut bir eklentiyi değiştirmenin daha iyi bir fikir olup olmadığını merak edebilirsiniz.
2 eklenti de aklınızdakinden bazılarını karşılıyorsa, muhtemelen birleştirilmelerilerdir.
- Her ikisi de kullanıcı etkileşimi (bildirimler gibi) gerektiren izinlere ihtiyaç duyar veya gerek duymaz.
- Bir sürü kod paylaşıyorlar.
- Kullanıcı, eklentinin her iki özelliği de sunmasını bekler.
- Ayrı olarak çalışsalardı, birbirlerine karışırlardı.

Eklentilerin kullanıcı tarafından özelleştirilebileceğini unutmayın - yeni işlevler eklemek, kasıtlı olarak yapmadığımız sürece eklentinin eski kullanıcılarını etkilemez.