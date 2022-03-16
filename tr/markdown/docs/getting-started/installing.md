---
title: Yükleme
---

## Eklenti mağazalarından

Scratch Eklentileri hem Chrome Web Mağazası'nda hem de Firefox Eklentilerinde mevcuttur.

- Chrome Web Mağazası (Google Chrome, Opera, Brave, Vivaldi, Microsoft Edge >79 ve diğer Chromium tabanlı tarayıcılar için)
  https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco

- Firefox için Eklentiler (Mozilla Firefox için)
  https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/

- Microsoft Edge Eklentileri (Microsoft Edge >79 için)
  https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj

## Kaynağından

### GitHub sürümleri hakkında

[Sürümler sayfası](https://github.com/ScratchAddons/ScratchAddons/releases) Scratch Eklentilerin tüm geliştirme yapıları için kod ve kurulum dosyalarının yanı sıra mağaza yapılarının aynasını içerir.

### Depoyu klonla

Scratch Eklentilerini geliştirme amacıyla kurmanın önerilen yolu budur. Bu, Git'in halihazırda kurulu olduğunu varsayar.

Depoyu indirmek için `https://github.com/ScratchAddons/ScratchAddons.git` dosyasını klonlamanız yeterlidir.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Scratch Eklentilerini güncellemek için önce `cd` ile klasöre gidin, ve ardından aşağıdaki komutları çalıştırın.

```sh
$ git fetch
$ git pull
```

Bu, Scratch Eklentilerini güncelleyecek ve kodu düzenlemeye hazır hale getirecektir. Google Chrome kullanıyorsanız, güncellemenin [burada](#install-on-google-chrome) görünmesi gerektiğini unutmayın.


### Zipball'u indirmek

Git yüklü değilse, bu yöntemi deneyebilirsiniz. Scratch Eklentilerini her güncellemek istediğinizde bu işlemi manuel olarak tekrarlamanız gerekeceğini unutmayın.

1. [Depoya](https://github.com/ScratchAddons/ScratchAddons) gidin ve kodu indir düğmesini bulun.

   ![Kodu indir düğmesinin ekran görüntüsü](/assets/img/docs/download-code-button.png)

2. Tıklayın ve "ZIP'i indir" seçeneğini seçin.

   ![ZIP'i indir düğmesinin ekran görüntüsü](/assets/img/docs/download-zipball-button.png)

3. Arşivi bir klasöre çıkarın.

### Google Chrome'da yükleme

1. Uzantı Yönetimi sayfasını açmak için adres çubuğunuza `chrome://extensions` yazın.

2. Geliştirici Modunu açmak için `Geliştirici modu`'nun yanındaki geçiş düğmesine tıklayın. Bu, bir klasörden veya dosyadan uzantılar yüklemenize olanak tanır.

   ![Uzantı Yönetim çubuğunun ekran görüntüsü](/assets/img/docs/developer-mode-toggle.png)

3. `Sıkıştırılmamış'ı yükle` düğmesinin göründüğünü görmelisiniz. Tıkladığınızda, yükleyeceğiniz bir klasörü seçmenize izin verecektir.

   ![Paketlenmemiş'i yükle düğmenin ekran görüntüsü](/assets/img/docs/load-unpacked-button.png)

4. Çıkarılan klasörü seçin.
5. Uzantı artık yüklenmiş olmalıdır.

Güncellemeyi bitirmek için ([buradaki](#cloning-the-repository) güncelleme adımlarını uyguladığınızı varsayarak), `Update` düğmesine tıklayın:

![Güncelle düğmesinin ekran görüntüsü](/assets/img/docs/update-button.png)


### Mozilla Firefox'da indirme

1. Hata ayıklama sayfasını açmak için adres çubuğunuza `about:debugging` yazın.

2. Soldaki menüden `Bu Firefox` butonuna tıklayın.

   ![Sol-el menüsünün ekran görüntüsü](/assets/img/docs/left-hand-menu.png)

4. `Geçici Eklenti Yükle...` seçeneğine tıklayın.

   ![Geçici Eklenti yükle düğmesinin ekran görüntüsü](/assets/img/docs/load-addon.png)

6. Çıkarılan klasörün içindeki manifest.json dosyasını seçin.
7. Uzantı artık yüklenmiş olmalıdır.

Not: Firefox geçici eklentileri aslında kalıcı değildir. Firefox'u yeniden başlatmak bunları kaldıracaktır, bu nedenle Scratch Eklentilerin geliştirme sürümünü kullanmak istiyorsanız, her zaman Google Chrome gibi Chromium tabanlı bir tarayıcı kullanmanız önerilir.

