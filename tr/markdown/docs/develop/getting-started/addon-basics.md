---
title: Eklenti Temelleri
---

## Eklenti nedir, gerçekten?
Aslında bir eklenti, şunlardan en az birinin birleşiminden çok daha fazlası değildir: persistent scripts, userscripts  ve userstyles. Bunlardan herhangi biri ilgiliyse, onları tek bir ad altında aynı eklenti' nin parçası yaparız. Örneğin, "Scratch 3 Geliştirici Araçları" eklentisinde, düzenleyiciye bir bulma kutusu eklemekten sorumlu bir kullanıcı yazısı ve bu kutuya CSS ekleyen bir userstyle vardır.

## persistent script nedir?
Kalıcı komut dosyası / persistent script, kullanıcının açık Scratch sekmesi olmasa bile her zaman arka planda çalışan bir JavaScript kodu parçasıdır. Örneğin, Scratch'te bir güncelleme olup olmadığını kullanıcıya bildirmek için kullanışlıdırlar. Kalıcı komut dosyaları, tarayıcı uzantılarındaki arka plan komut dosyalarına benzer.

## Userscript nedir?
Userscript, bir Scratch sekmesiyle birlikte çalışan bir JavaScript kodu parçasıdır. Kalıcı komut dosyalarından farklı olarak, bu kullanıcı kodunun ne zaman çalışacağını, örneğin yalnızca proje sayfalarını belirtebilirsiniz. Kullanıcı komut dosyaları, tarayıcı uzantılarındaki içerik komut dosyalarına benzer ve daha önce bir kullanıcı komut dosyası yöneticisi kullandıysanız, bunların temelde aynı olduğunu fark edeceksiniz.
Userscripts, örneğin gezinme çubuğuna düğmeler eklemek veya kaldırmak gibi, Scratch web sitesinin davranışını değiştirmek için yararlıdır.

## Userstyle nedir?
Bir userstyle, bir userscript' e benzer; onlar için URL kalıpları da belirtebilirsiniz. Ancak, kullanıcı stilleri JavaScript yerine CSS'yi enjekte eder. Bunlar genellikle userscripts kendileri tarafından eklenen öğelere stil vermek için kullanılırlar, ancak yerel Scratch öğelerine stil vermek için de kullanılabilirler. Durum böyle olduğunda, genellikle onlara "temalar" deriz.

## Kavramsal olarak, bir eklenti ne olmalıdır?
Yeni bir eklenti oluşturmanın veya mevcut bir eklentiyi değiştirmenin daha iyi bir fikir olup olmadığını merak edebilirsiniz.
2 eklenti bunlardan bazılarını paylaşıyorsa, muhtemelen birleştirilmelidirler.
- Her ikisi de kullanıcı etkileşimi (bildirimler gibi) gerektiren izinlere ihtiyaç duyar veya gerek duymaz.
- Bir sürü kod paylaşıyorlar.
- Kullanıcı, bu eklentinin her iki özelliği de sunmasını bekler.
- Ayrılsalardı, birbirlerine müdahale ederlerdi.

Eklentilerin kullanıcı tarafından özelleştirilebileceğini unutmayın - yeni işlevler eklemek, kasıtlı olarak yapmadığımız sürece eklentinin eski kullanıcılarını etkilemez.