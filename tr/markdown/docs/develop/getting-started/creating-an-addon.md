---
title: Bir Eklenti Oluşturma
---
Gerekli yazılım: metin düzenleyici, Chrome.
Mümkünse, sorunları önlemek için devam etmeden önce mağazadan indirdiğiniz Scratch Eklentileri uzantısını devre dışı bırakın.

## 1. Adım: [Eklenti ile ilgili temel bilgiler](/docs/develop/getting-started/addon-basics/) hakkında bilgi edinin
Terminolojiye aşina olmak için bu makaleyi okuduğunuzdan emin olun.

## Adım 2: [Depoyu](https://github.com/ScratchAddons/ScratchAddons) çatalla/klonla
Kaynak kodunu yerel olarak indirmek için [bu yönergeleri](/docs/getting-started/installing/#from-source) takip edin.

## 3. Adım: Uzantıyı Chrome'a yükleyin
*Not: Eklentiler üzerinde çalışmak için Chrome önerilir. Yine de, eklentilerin Firefox ve Edge'de de çalışması bekleniyor.* 
Artık dosya sisteminizde uzantıya sahip olduğunuza göre, `chrome://extensions`a gidin ve "geliştirici modu"nu açın. 
"Paketlenmemiş yükle"ye tıklayın, ardından Scratch Eklentileri'nin bulunduğu klasörü seçin. Bununla ilgili sorun yaşıyorsanız, `manifest.json` dosyasının bulunduğu klasörü seçtiğinizden emin olun. 
İşte bu! Uzantıyı yüklediniz! Şuna benzer görünmelidir: 
![image](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)  
Not: "hatalar"ı güvenle görmezden gelebilirsiniz. Bu, Firefox tarafından gerekli görülen tanınmayan bir bildirim anahtarı için yalnızca bir uyarıdır.

## 4. Adım: Eklentiniz ne hakkında?
Şimdi eğlenceli kısım geliyor!
Eklentiniz ne yapacak? Kendini açıklayıcı bir eklenti kimliği düşünün (tireler dışında boşluk veya özel karakter koymayın).
Anladın mı?

## 5. Adım: Eklenti için bir klasör oluşturun
Bir dosya gezgini kullanarak Scratch Eklentileri'nin dosya sisteminizde bulunduğu klasöre gidin. `addons` klasörünü bulun.
Ardından, adı olarak epik eklenti kimliğinizle yeni bir klasör oluşturun.

## 6. Adım: Bir manifest eklentisi ekleyin
Eklenti manifesti, Scratch Eklentileri'ne eklentinizin nasıl çalıştığını söyler. Baş ağrısından kurtulmak için bunu yaptığınızdan emin olun.
Az önce oluşturduğunuz klasörün içinde bir `addon.json` dosyası oluşturun.
Bu, kodlamaya başlamak için kullanabileceğiniz bir temeldir, gelecekte değiştirdiğinizden emin olun:
``` json
{
  "name": "Eklenti adının olduğu yere destansı yer tutucu metni",
  "description": "Merhaba Dünya! Bu yer tutucu metnini bir açıklama ile değiştirmek gerçekten akıllıca olur.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
Manifest dosyasında neler bildirebileceğiniz hakkında daha fazla bilgi için [bu makaleye](/docs/reference/addon-manifest/) bakın.


## 7. Adım: Scratch Eklentileri'ne eklentinizin kimliğinin ne olduğunu söyleyin
Scratch Eklentileri kendi başına yeni klasörler bulamaz, bu nedenle adı özel bir dosyaya eklemeniz gerekir.
`scratchAddonsFolder/addons/addons.json` adresine gidin ve eklentinizin kimliğini diziye ekleyin.

## 8. Adım: Merhaba dünya
Eklentiniz şu anda hiçbir şey yapmıyor, bu nedenle daha önce yaptığımız her şeyin çalışıp çalışmadığını kontrol etmek için iyi bir zaman.
` chrome://extensions`a gidin ve sayfayı yenileme sembolüne tıklayarak Scratch Eklentileri'ni yeniden yükleyin.
Şimdi, Scratch Eklentileri simgesine sağ basın ve "seçenekler"e tıklayın.
Eklentinizi listede görmelisiniz! Eklentinizi bulduktan sonra etkinleştirin ve sahip olabileceğiniz tüm ayarları yapın.

## 9. Adım: Eğlenceli kısım, kod!
*Devam etmeden önce 1. adımda bağlantısı verilen wiki makalesini okuduğunuzdan emin olun.*

İşin eğlenceli kısmı geliyor: Kendi JS veya CSS dosyalarınızı oluşturun! Profesyonel İpucu: Eklentinizde herhangi bir değişiklik yaptıktan sonra, 8. adımda yaptığınız gibi Scratch Eklentileri uzantısını yenilediğinizden emin olun.

Eklentinizin ne yapmasını istediğinize bağlı olarak, şimdi şu wiki sayfalarını kontrol etmelisiniz:
- [Userscripts](/docs/develop/userscripts)
- [Userstyles](/docs/develop/userstyles)

## 10. Adım: Eklentinizi özelleştirilebilir yapın
İsterseniz eklentinizi özelleştirilebilir hâle getirebilirsiniz!
Eklentinizin kullanıcıları ayarları değiştirebilir, sayı girebilir ve çok daha fazlasını yapabilir!
Başlamak için [eklenti bildiriminde ayarların nasıl bildirileceğine](/docs/reference/addon-manifest/#settings-object) göz atın.
Ardından, userscript'lerden kullanıcı seçeneklerine nasıl erişileceğini öğrenmek için [addon.settings belgeleri](/docs/reference/addon-api/addon.settings)ne bakın.

## 11. Adım: Eklentinizi yayınlamadan önce
Artık eklentiniz çalıştığına göre, onu eklenti kitaplığına ekleyebileceğimizden emin olalım.  
Eklentinizin manifest dosyasının uygun olduğundan emin olun, [buradan](/docs/reference/addon-manifest) manifest dosyası hakkında daha fazla bilgi alabilirsiniz. Eklentinizin adına, açıklamasına ve etiketlerine çok dikkat edin. `"enabledByDefault"` değerini `false` olarak ayarladığınızdan veya satırı kaldırdığınızdan emin olun.
Eklentinizin diğer eklentilerin çalışmasını etkilemediğinden emin olun.
Kodunuzun anlaşılır olduğundan emin olun; Gereksiz yorumlara sahip olması, hiç yorum olmamasından daha iyidir.

## 12. Adım: Bir pull request gönderin!
[Katkı yapma kılavuzumuzdaki](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md) adımları takip edin. Basitçe söylemek gerekirse, eğer hâlihazırda yapmadıysanız depoyu çatallayın, yeni eklentinizi kaydedin ve bir PR gönderin!
Size bazı değişiklikler istediğimizi bildiren bir yanıt gönderebileceğimizi aklınızda bulundurun, ancak kabul edilebilir bir düzeyde olduğu sürece eklentinizi kabul edeceğiz.
