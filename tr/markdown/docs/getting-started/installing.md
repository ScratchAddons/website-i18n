---
title: Yükleme
---

## Eklenti mağazalarından

Scratch Eklentileri hem Chrome Web Mağazası' nda hem de Firefox Eklentilerinde mevcuttur.

- Chrome Web Mağazası (Google Chrome, Opera, Brave, Vivaldi, Microsoft Edge (>79) ve diğer Chromium tabanlı tarayıcılar için)
  https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco 
- Firefox için Eklentiler (Mozilla Firefox için)
  https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/ 


## Kaynağından

### GitHub sürümleri hakkında

[Sürümler sayfası](https://github.com/ScratchAddons/ScratchAddons/releases) Scratch Eklentiler' in tüm geliştirme yapıları için kod ve kurulum dosyalarının yanı sıra mağaza yapılarının aynasını içerir.

### Depoyu klonla

Geliştirme amacıyla Scratch Eklentilerini kurmanın önerilen yol budur. Bu, Git' in kurulu olduğunu varsayar.

Depoyu indirmek için `https://github.com/ScratchAddons/ScratchAddons.git` dosyasını klonlamanız yeterlidir.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Scratch Eklentiler' i güncellemek için önce `cd` klasörüne atın ve ardından aşağıdaki komutları çalıştırın.

```sh
$ git fetch
$ git pull
```

Bu, Scratch Eklentilerini güncelleyecek ve kodu düzenlemeye hazır hale getirecektir. Google Chrome kullanıyorsanız, güncellemenin [burada](#install-on-google-chrome) görünmesi gerektiğini unutmayın.


### Zipball'u indir

Git yüklü değilse, bu yöntemi deneyebilirsiniz. Scratch Eklentileri' ni her güncellemek istediğinizde bu işlemi manuel olarak tekrarlamanız gerekeceğini unutmayın.

1. [Depoya](https://github.com/ScratchAddons/ScratchAddons) gidin ve kodu indir düğmesini bulun.

   ![Kod düğmesinin ekran görüntüsünü indir](/assets/img/docs/download-code-button.png)

2. Tıklayın ve "ZIP' i indir" i seçin.

   ![ZIP düğmesi ekran görüntüsünü indir](/assets/img/docs/download-zipball-button.png)

3. Arşivi bir klasöre çıkarın.

### Google Chrome' da yükleme

1. Uzantı Yönetimi sayfasını açmak için adres çubuğunuza `chrome://extensions` yazın.

2. Geliştirici Modunu açmak için `Geliştirici modu` nun yanındaki geçiş düğmesini tıklayın. Bu, bir klasörden veya dosyadan uzantılar yüklemenize olanak tanır.

   ![Uzantı Yönetim çubuğu ekran görüntüsü](/assets/img/docs/developer-mode-toggle.png)

3. `Paketlenmemişi yükle` düğmesinin göründüğünü görmelisiniz. Tıklamak, yüklenecek bir klasörü seçmenize izin verecektir.

   ![Paketlenmemiş düğmenin ekran görüntüsünü yükle](/assets/img/docs/load-unpacked-button.png)

4. Çıkarılan klasörü seçin.
5. Uzantı şimdi yüklenmiş olmalıdır.

Güncellemeyi bitirmek için ([buradaki](#cloning-the-repository) güncelleme adımlarını uyguladığınızı varsayarak), `Güncelle` düğmesine tıklayın:

![Güncelleme düğmesinin ekran görüntüsü](/assets/img/docs/update-button.png)


### Mozilla Firefox' da Kurulum

1. Hata ayıklama sayfasını açmak için adres çubuğunuza `about:debugging` yazın.

2. Soldaki menüden `Bu Firefox` a tıklayın.

   ![Sol menünün ekran görüntüsü](/assets/img/docs/left-hand-menu.png)

4. `Geçici Eklenti Yükle` seçeneğine tıklayın.

   ![Geçici Eklenti düğmesinin ekran görüntüsünü yükle](/assets/img/docs/load-addon.png)

6. Çıkarılan klasörün içindeki manifest.json dosyasını seçin.
7. Uzantı şimdi yüklenmiş olmalıdır.

Not: Firefox geçici eklentileri aslında kalıcı değildir. Firefox' u yeniden başlatmak bunları kaldıracaktır, bu nedenle Scratch Addons' un geliştirme sürümünü kullanmak istiyorsanız, her zaman Google Chrome gibi Chromium tabanlı bir tarayıcı kullanmanız önerilir.

