---
title: Yükleme
---

## Eklenti mağazalarından

Scratch Eklentileri bu mağazalarda mevcuttur

| Mağaza | İndir | Desteklenen tarayıcılar | Sistem gereksinimleri |
| - | - | - | - |
| Chrome Web Mağazası | [![Chrome Web Mağazası için İndir](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 80+<br />Microsoft Edge 80+<br />Opera 67+<br />Brave 1.3+<br />Vivaldi 2.11+<br />*Chromium 80+* | Windows 7+<br />OS X / MacOS 10.11+<br />~6 yıldan yeni Chromebook'lar
| Firefox için eklentiler | [![Firefox Eklentileri için İndir](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 86+ | Windows 7+<br />OS X / MacOS 10.12+
| Microsoft Edge Eklentileri | [![Microsoft Edge Eklentileri için İndir](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 80+ | Windows 7+<br />OS X / MacOS 10.11+

## Kaynağından

### GitHub sürümleri hakkında

[Sürümler sayfası](https://github.com/ScratchAddons/ScratchAddons/releases) Scratch Eklentilerin tüm geliştirme yapıları için kod ve kurulum dosyalarının yanı sıra mağaza yapılarının aynasını içerir.

### Depoyu klonlama

Scratch Eklentilerini geliştirme amacıyla kurmanın önerilen yolu budur. Bu, Git'in hâlihazırda kurulu olduğunu varsayar.

Depoyu indirmek için `https://github.com/ScratchAddons/ScratchAddons.git` dosyasını klonlamanız yeterlidir.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Scratch Eklentilerini güncellemek için önce `cd` ile klasöre gidin, ve ardından aşağıdaki komutları çalıştırın.

```sh
$ git fetch
$ git pull
```

Bu, Scratch Eklentilerini güncelleyecek ve kodu düzenlemeye hazır hâle getirecektir. Google Chrome kullanıyorsanız, güncellemenin [burada](#install-on-google-chrome) görünmesi gerektiğini unutmayın.


### Zipball'u indirmek

Git yüklü değilse, bu yöntemi deneyebilirsiniz. Scratch Eklentilerini her güncellemek istediğinizde bu işlemi manuel olarak tekrarlamanız gerekeceğini unutmayın.

1. [Depoya](https://github.com/ScratchAddons/ScratchAddons) gidin ve kodu indir düğmesini bulun.

   ![Kodu indir düğmesinin ekran görüntüsü](/assets/img/docs/download-code-button.png)

2. Tıklayın ve "ZIP'i indir" seçeneğini seçin.

   ![ZIP'i indir düğmesinin ekran görüntüsü](/assets/img/docs/download-zipball-button.png)

3. Arşivi bir klasöre çıkarın.

### Google Chrome'a veya Microsoft Edge'ye yüklemek

1. Uzantı Yönetimi sayfasını açmak için adres çubuğunuza `chrome://extensions` yazın.

2. Geliştirici Modunu açmak için `Geliştirici modu`'nun yanındaki açma/kapama düğmesini açık hâle getirin. Bu, uzantıları bir klasörden veya dosyadan yüklemenize olanak tanır.

   ![Uzantı Yönetim çubuğunun ekran görüntüsü](/assets/img/docs/developer-mode-toggle.png)

3. `Sıkıştırılmamışı yükle` düğmesinin göründüğünü görmelisiniz. Tıkladığınızda, yükleyeceğiniz bir klasörü seçmenize izin verecektir.

   ![Sıkıştırılmamışı yükle düğmenin ekran görüntüsü](/assets/img/docs/load-unpacked-button.png)

4. Çıkarılan klasörü seçin.
5. Uzantı artık yüklenmiş olmalıdır.

Güncellemeyi bitirmek için ([buradaki](#cloning-the-repository) güncelleme adımlarını uyguladığınızı varsayarak), `Update` düğmesine tıklayın:

![Güncelle düğmesinin ekran görüntüsü](/assets/img/docs/update-button.png)


### Mozilla Firefox'da indirme

1. Hata ayıklama sayfasını açmak için adres çubuğunuza `about:debugging` yazın.

2. Soldaki menüden `Bu Firefox` butonuna tıklayın.

   ![Soldaki menünün ekran görüntüsü](/assets/img/docs/left-hand-menu.png)

4. `Geçici Eklenti Yükle...` seçeneğine tıklayın.

   ![Geçici Eklenti yükle düğmesinin ekran görüntüsü](/assets/img/docs/load-addon.png)

6. Çıkarılan klasörün içindeki manifest.json dosyasını seçin.
7. Uzantı artık yüklenmiş olmalıdır.

Not: Firefox geçici eklentileri aslında kalıcı değildir. Firefox'u yeniden başlatmak bunları kaldıracaktır, bu nedenle Scratch Eklentilerin geliştirme sürümünü kullanmak istiyorsanız, her zaman Google Chrome gibi Chromium tabanlı bir tarayıcı kullanmanız önerilir.

