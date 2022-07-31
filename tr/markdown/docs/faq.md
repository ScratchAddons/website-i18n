---
title: Sık Sorulan Sorular
description: Bu sayfa, Scratch Eklentiler uzantısı ve projesiyle ilgili sık sorulan soruları listeler.
---

Bu sayfa, Scratch Eklentileri uzantısı ve projesiyle ilgili sık sorulan soruları listeler.

### Scratch Eklentileri Nedir?

Scratch Eklentileri, Scratch sitesi ve proje düzenleyicisi için "hepsi bir arada" bir tarayıcı uzantısıdır. Hem Scratch sitesi hem de proje düzenleyicisi için özellikler ve temalar (dahili olarak eklentiler olarak adlandırılır) sağlar. Scratch Eklentilerinin misyonu, Scratch topluluğunun birkaç üyesi tarafından geliştirilen mevcut tüm Scratch uzantılarını, kullanıcı komut dosyalarını ve kullanıcı stillerini, erişimi kolay tek bir yerde birleştirirken, kullanıcıların hangilerini etkinleştireceklerini seçmelerine izin vermektir.

### "Eklenti" tam olarak nedir?

Bir eklenti, bir uzantıya veya bir userscript'e benzer, ancak Scratch Eklentileri uzantısı tarafından sağlanan özel API'leri kullanırlar. Bu API'ler, eklentilerin bir Scratch sayfasında komut dosyaları çalıştırmasına (userscript'lere) veya Scratch sitesine stiller uygulamasına (userstyle'lerine) izin verir.

Userscript'ler, Scratch ile ilgili bilgileri almalarına (örneğin, oturum açmış mevcut kullanıcıyı alma) ve ayrıca uzantı API'lerini (bildirim gönderme gibi) kullanmalarına olanak tanıyan `addon.*` JavaScript API'lerini kullanabilir.

### Her şey bir eklenti ise, Scratch Eklentileri ne yapıyor o halde?

Kendi başına, Scratch Eklentileri sadece bir eklenti yükleyicidir. Başlıca görevleri şunlardır:

- Kullanıcıların eklentileri etkinleştirmesine, devre dışı bırakmasına ve yapılandırmasına izin verir.
- Eklentileri çalıştırın ve onlara API'ler sağlayın.
- Eklentilere genel durum sağlar (örneğin, addon.auth API).
- Eklenti, userscript'ler tarafından kullanılmak üzere prototipleri kirletin.
- Redux durumuna erişmenin ve değiştirmenin yollarını sağlayın.
- Eklentilerin birbirine müdahale etmesini önler.
- Farklı eklentilerde tekrarlanan, gereksiz özelliklerden kaçınır.

### Scratch Eklentileri güvenli mi?

Evet. Scratch Eklentilerinin en son sürümünde herhangi bir güvenlik sorunu bulunmamalıdır. Scratch Eklentileri, açık kaynaklı bir projedir, bu nedenle kod, Scratch Eklentileri katkıda bulunanların yanı sıra Chrome Web Mağazası, Firefox Eklentileri ve Microsoft Edge Eklentileri'nde eklentileri gözden geçiren insanlar tarafından sürekli olarak doğrulanır.

### Bir güvenlik açığını nasıl bildirebilirim?

Bir güvenlik açığı bulursanız, lütfen `worldxlanguages (et) gmail.com` adresine e-posta göndererek World_Languages ile özel olarak iletişime geçin. 48 saat içinde yanıt alamazsanız, lütfen [buradan](https://github.com/ScratchAddons/ScratchAddons/issues/) bir e-posta gönderdiğinizden bahsederek bir sorun başlığı oluşturun.

[Güvenlik politikamızı okuyabilirsiniz](https://github.com/ScratchAddons/ScratchAddons/security/policy) veya [yayınladığımız tavsiyelerimizi kontrol edebilirsiniz](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Scratch Eklentilerini kullanırken hesabım güvende olacak mı?

Scratch Eklentileri, esasen çalışmak için hesap bilgilerinizi kullanmaz. Aslında, Scratch'den çıkış yapabilirsiniz ve Scratch Eklentileri çalışmaya devam eder. Scratch Eklentileri, yalnızca sahip olduğunuz ve her istek için tarayıcı tarafından sağlanan çerezlere dayalı olarak istek gönderir, bu nedenle, Scratch Mesajlaşma gibi bazı eklentiler, sadece oturum açtığınızda çalışır, ancak diğer bölümleri etkilemez.

Scratch Eklentilerindeki Eklentiler, depodaki birden fazla katkıda bulunan kişi tarafından da kontrol edilir. Bu nedenle hiç kimse kötü niyetli kodlarını bizden saklayamaz.

Scratch hesap bilgilerini veya uzantı ayarlarını asla tarayıcınızın dışına göndermeyiz. Daha fazla bilgi için [uzantı gizlilik politikasına](/docs/privacy/policies/extension) bakın.

### Scratch'teki insanlara Scratch Eklentileri'nden bahsedebilir miyim?

Yapamazsınız ve lütfen yapmayınız. [burada](https://scratch.mit.edu/discuss/post/2907564/) tarayıcı uzantılarının/kullanıcı komut dosyalarının reklamını yasaklayan bir politika vardır. Bununla birlikte, arkadaşlarınıza Scratch Eklentileri hakkında bilgi vermek için farklı yöntemler kullanabilirsiniz.

### Scratch Eklentilerine nasıl katkıda bulunabilirim?

Öncelikle, Scratch Eklentilere katkıda bulunmaya gösterdiğiniz ilgi için teşekkür ederiz. İlginiz ve sonraki katkılarınız için de teşekkür ederiz.

Açık kaynak kodlu bir proje olarak her türlü katkıya açığız. Bizden izin almanıza veya belirli bir rütbeye sahip olmanıza bile gerek yok. Herkese açığız. Projeye katkıda bulunduğunuzun farkında olmama ihtimaliniz bile var!

Her neyse, konuya dönelim. Birçok yönden katkıda bulunabilirsiniz ve bazıları gerçekten çok kolay.

- **Biraz kod ekleyin**

  JavaScript, HTML5 ve CSS ile kod yazabiliyorsanız, biraz kodlama/programlama yaparak katkıda bulunabilirsiniz. Hataları düzeltebilir, bazı istekleri yerine getirebilir veya kendi eklentinizi oluşturabilirsiniz.

  Bundan sonra, bir pull request oluşturmanız gerekir. Bunu [depoyu](https://github.com/ScratchAddons/ScratchAddons/) çatallayarak yapabilir, gerekli değişiklikleri yapabilir ve bir pull request oluşturabilirsiniz. Eğer her şeyin uygun olduğu görülürse ana proje ile sizin projenizi birleştireceğiz.

  Uzantı dışındaki diğer yönlerin katkılarına da açığız. Depolarımızı [GitHub organizasyon sayfamızda](https://github.com/ScratchAddons) görüntüleyebilir ve bunları oluşturmamıza yardımcı olabilirsiniz.

- **Bir fikir önerin**

  Scratch Eklentiler'e iyi bir katkı olacağını düşündüğünüz bir şey mi var? [Bize anlatın!](#i-think-you-missed-a-feature-what-can-i-do)

- **Bir hata bildirin**

  Eklentimizden birinde, ayarlar sayfamızda veya uzantımızdaki başka herhangi bir şeyde bir hata mı buldunuz? [Bize bir hata raporu gönderin](#what-can-i-do-if-i-find-a-problem).

- **Scratch Eklentilerini Çevirin**

  İngilizce'den başka bir dili akıcı bir şekilde konuşabiliyorsanız, Scratch Eklentilerini kendi dilinize çevirmeye/yerelleştirmeye yardımcı olabilirsiniz. [Buradan](/docs/localization/joining-the-localization-team) başlayabilirsiniz.

- **Belgelerinizi yazın**

  Scratch Eklentilerine aşina mısınız? Eğer öyleyse, bunun için kılavuzlar yazabilirsiniz. Kılavuzlar, eklentileri nasıl kullanılacağınızı veya nasıl çalıştığınızı anlatır. Daha fazla bilgi için lütfen [Tartışma sekmemizden](https://github.com/ScratchAddons/ScratchAddons/discussions) bizimle iletişime geçin.

- **Geri bildirim gönderin**

  [Geri bildirim sayfasında](https://scratchaddons.com/feedback) bulunan formumuza geri bildirim gönderebilirsiniz. Geri bildiriminiz, uzantı geliştirmede bize farklı bir bakış açısı verebilir ve dikkat edilmesi gereken şeyleri bilmemize ve hataları düzeltmemize yardımcı olabilir.

- **Mağazalarda Scratch Eklentileri hakkında yorum bırakın**

  [Chrome uzantı sayfası](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco)nda, [Firefox eklenti sayfası](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/)nda veya [Microsoft Edge eklenti sayfası](https://microsoftedge.microsoft.com/addons/detail/scratch-addons/iliepgjnemckemgnledoipfiilhajdjj)nda Scratch Eklentileri hakkında bize bir inceleme bırakabilirsiniz.

- **Depomuza yıldız ekleyin**

  Temel olarak GitHub yıldızı, Scratch yıldızına/favorisine benzer. Bunu [depomuza](https://github.com/ScratchAddons/ScratchAddons) giderek ve sağ üst köşedeki "Yıldız" düğmesine tıklayarak yapabilirsiniz.

- **Bunu dünyaya yayın**

  Arkadaşlarınız, akrabalarınız, aile üyeleriniz ve hatta isterseniz öğretmeniniz gibi herkese Scratch Eklentileri hakkında bilgi verebilirsiniz. Sizden sadece [Bunu Scratch sitesinde yapmamanızı](#can-i-tell-people-about-scratch-addons-on-scratch) rica ediyoruz.

### Kendi eklentimi nasıl oluşturabilirim?

Scratch Eklentilerinde nasıl eklenti oluşturulacağı hakkında daha fazla bilgiyi [buradan](/docs/develop/getting-started) edinebilirsiniz.

### Adımı [katkıda bulunanlar sayfasına](/contributors) nasıl koyabilirim?

Adınızın söz konusu sayfada yer alması için lütfen [bu sorunun](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) talimatlarını okuyun ve uygulayın.

### Adımı [katkıda bulunanlar sayfasından](/contributors) nasıl kaldırabilirim?

Adınızın sayfada görünmesini istemiyorsanız, lütfen [katkıda bulunanlar depomuzdan](https://github.com/ScratchAddons/contributors/issues/) veya diğer iletişim araçlarını kullanarak bir sorun oluşturarak bize bildirin. Rahatsızlık için özür dileriz.

### Bir sorun bulursam ne yapabilirim?

Bu yöntemlerden birini kullanarak bize söyleyebilirsiniz.

- [Geri bildirim formumuz](https://scratchaddons.com/feedback) aracılığıyla bize bildirin.
- [Depoda](https://github.com/ScratchAddons/ScratchAddons/issues) bir sorun oluşturun.
- [Tartışma sekmemizde](https://github.com/ScratchAddons/ScratchAddons/discussions) bir gönderi oluşturun.
- [Discord sunucumuzdan](https://discord.gg/R5NBqwMjNc) bize bildirin.

### Sanırım bir özelliği atlamışsınız. Ne yapabilirim?

Bir özelliğin eksik olduğunu düşünüyorsanız, uzantıya bir eklenti önermek istiyorsanız veya iyi bir fikriniz varsa [yukarıda belirtilen yöntemlerden birini uygulayarak](#what-can-i-do-if-i-find-a-problem) bize bildirin.

### Scratch Eklentileri hakkında nerede tartışabilirim?

Bunu [Tartışma sekmemizde](https://github.com/ScratchAddons/ScratchAddons/discussions) veya [Discord sunucumuzda](https://discord.gg/R5NBqwMjNc) yapabilirsiniz. Orada, bunun hakkında tartışabilir ve sorun yaşıyorsanız destek bulabilirsiniz.

### Scratch Eklentilerinin, Scratch'i yavaşlattığını düşünüyorum. Ne yapabilirim?

İhtiyacınız olmayan eklentileri kapatmayı deneyin. Ayrıca, daha iyi performans için hangi eklentilerin kapatılması gerektiğine karar vermek için eklenti bildirimlerine ve uyarılarına dikkat edin.

### Easter egg eklentilerini nasıl etkinleştirebilirim?

Easter egg eklentilerini ortaya çıkarmak için, ayarlar sayfasında klavyenizle Konami Kodunu (↑↑↓↓←→←→BA) yazın. Bundan sonra, easter egg eklentileri gösterilecek ve onları etkinleştirmenize izin verilecektir.

Easter egg eklentilerimizden bazıları "Büyük Harfli Hesap Ayarları" ve "Noktalı virgül hatası"dır. Tam bir liste için [eklentiler sekmesine](/addons) göz atın.

### Daha fazla sorum var!

Yanıtlanması gereken başka sorularınız varsa [Tartışma sekmemizde](https://github.com/ScratchAddons/ScratchAddons/discussions) bir gönderi oluşturabilir veya [discord sunucumuza](https://discord.gg/R5NBqwMjNc) bir mesaj gönderebilirsiniz. Birisi sizin için cevaplamaya çalışacaktır.
