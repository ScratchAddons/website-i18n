---
title: Bir Eklenti Oluşturma
---
Gerekli yazılım: metin düzenleyici, Chrome.
Mümkünse, sorunları önlemek için devam etmeden önce mağazadan indirdiğiniz Scratch Eklentileri uzantısını devre dışı bırakın.

## 1. Adım: [Eklenti temelleri](addon-basics) hakkında bilgi edinin
Terminolojiye aşina olmak için bu makaleyi okuduğunuzdan emin olun.

## 2. Adım: Depoyu çatallayın/klonlayın
Veya isterseniz ZIP olarak indirin. Başka bir deyişle, kaynak kodunu yerel olarak indirmeniz yeterlidir.

## 3. Adım: Uzantıyı Chrome' a yükleyin
*Not: Eklentiler üzerinde çalışmak için Chrome önerilir. Yine de eklentilerin Firefox' da da çalışma ihtimali var.*
Artık dosya sisteminizde uzantıya sahip olduğunuza göre, `chrome://extensions`' a gidin ve "geliştirici modu"' nu etkinleştirin.
"Sıkıştırılmamış' ı yükle"' ye tıklayın, ardından Scratch Eklentilerin bulunduğu klasörü seçin. Bununla ilgili sorun yaşıyorsanız, `manifest.json` dosyasının bulunduğu klasörü seçtiğinizden emin olun.
İşte bu, uzantıyı yüklediniz! Şuna benzer görünmelidir:
![görsel](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)
Not: "hatalar" yazdığını güvenle görmezden gelebilirsiniz. Bu, Firefox' un tanınmayan bir "manifest anahtarı" için yalnızca bir uyarıdır.

## 4. Adım: Eklentiniz ne hakkında?
Şimdi eğlenceli kısım geliyor!
Eklentiniz ne yapacak? Kendini açıklayıcı bir eklenti kimliği düşünün (tireler dışında boşluk veya özel karakter koymayın).
Anladın mı?

## 5. Adım: Eklenti için bir klasör oluşturun
Bir dosya gezgini kullanarak Scratch Eklentilerin dosya sisteminizde bulunduğu klasöre gidin. `addons` klasörünü bulun.
Ardından, adı olarak epik eklenti kimliğinizle yeni bir klasör oluşturun.

## 6. Adım: Bir manifest eklentisi ekleyin
Eklenti manifesti, Scratch Eklentilerine eklentinizin nasıl çalıştığını söyler. Baş ağrısından kurtulmak için bunu yaptığınızdan emin olun.
Az önce oluşturduğunuz klasörün içinde bir `addon.json` dosyası oluşturun.
Bu, kodlamaya başlamak için kullanabileceğiniz bir temeldir, gelecekte değiştirdiğinizden emin olun:
```json
{
  "name": "Aaaaaaaaaa eklentim",
  "description": "Merhaba dünya!",
  "tags": ["community"],
  "enabledByDefault": false
}
```
Manifest' de ne beyan edebileceğiniz hakkında daha fazla bilgi için [bu makaleye](/docs/developing/the-addon-manifest-(addon.json)) bakın.


## 7. Adım: Scratch Eklentilere eklentinizin kimliğinin ne olduğunu söyleyin
Scratch Eklentileri kendi başına yeni klasörler bulamaz, bu nedenle adı özel bir dosyaya eklemeniz gerekir.
`scratchAddonsFolder/addons/addons.json` adresine gidin ve eklentinizin kimliğini diziye ekleyin.

## 8. Adım: Merhaba dünya
Eklentiniz şu anda hiçbir şey yapmıyor, bu nedenle daha önce yaptığımız her şeyin çalışıp çalışmadığını kontrol etmek için iyi bir zaman.
` chrome://extensions`' a gidin ve sayfayı yenileme sembolüne tıklayarak Scratch Eklentileri yeniden yükleyin.
Şimdi, Scratch Eklentiler simgesine sağ basın ve "seçenekler" e tıklayın.
Eklentinizi listede görmelisiniz! Eklentinizi bulduktan sonra etkinleştirin ve sahip olabileceğiniz tüm ayarları yapın.

## 9. Adım: Eğlenceli kısım, kod!
*Devam etmeden önce 1. adımda bağlantısı verilen wiki makalesini okuduğunuzdan emin olun.*

İşin eğlenceli kısmı geliyor: Kendi JS veya CSS dosyalarınızı oluşturun! Profesyonel İpucu: Eklentinizde herhangi bir değişiklik yaptıktan sonra, 8. adımda yaptığınız gibi Scratch Eklentiler uzantısını yenilediğinizden emin olun.

Eklentinizin ne yapmasını istediğinize bağlı olarak, şimdi şu wiki sayfalarını kontrol etmelisiniz:
- [Kalıcı komut dosyaları](/docs/develop/addon-types/persistent-scripts)
- [Kullanıcı Komut Dosyaları](/docs/develop/addon-types/userscripts)
- [Kullanıcı stilleri](/docs/develop/addon-types/userstyles)

## 10. Adım: Eklentinizi özelleştirilebilir yapın
İsterseniz eklentinizi özelleştirilebilir hale getirebilirsiniz!
Eklentinizin kullanıcıları ayarları değiştirebilir, sayı girebilir veya daha fazlasını yapabilir!
Başlamak için [manifest eklentisinde ayarların nasıl bildirileceğine](/docs/reference/addon-manifest/#settings-object) bakın.
Ardından, kullanıcı komut dosyalarından ve kalıcı komut dosyalarından kullanıcı seçimlerine nasıl erişileceğini öğrenmek için [addon.settings belgelerine](/docs/reference/addon-api/addon.settings) gidin.

## 11. Adım: Eklentinizi yayınlamadan önce
Artık eklentiniz çalıştığına göre, onu eklenti kitaplığına ekleyebileceğimizden emin olalım.
Eklentinizin manifest dosyasının uygun olduğundan emin olun, [daha fazla bilgi için buraya tıklayın](/docs/reference/addon-manifest). Eklentinizin adına, açıklamasına ve etiketlerine çok dikkat edin. `"enabledByDefault"`u `false` olarak ayarladığınızdan veya kaldırdığınızdan emin olun.
Eklentinizin diğer eklentileri bozmadığından emin olun.
Kodunuzun anlaşılır olduğundan emin olun; Gereksiz yorumlara sahip olmak, hiç yorum yapmamaktan iyidir.

## 12. Adım: Bir çekme isteği gönderin!
Henüz yapmadıysanız, depoyu çatallayın, yeni eklentinizi yapın ve bir çekme isteği gönderin!
Bazı değişiklikler yapmanızı isteyebileceğimizi unutmayın, ancak eklentinizi minimum düzeyde uygun olduğu sürece muhtemelen kabul edeceğiz.
