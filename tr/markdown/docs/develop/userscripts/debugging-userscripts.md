---
title: Hata Ayıklama İpuçları
description: Userscript'lerinde kolayca hata ayıklamanız için ipuçları ve dikkate alınması gereken püf noktalar.
---

Userscript'lerinde kolayca hata ayıklamanız için ipuçları ve dikkate alınması gereken püf noktalar.

## İpuçları

### Eklentiyi yeniden yüklemeniz her zaman gerekli değildir

Halihazırda var olan bir JavaScript veya CSS dosyasının kaynağını değiştirirken `chrome://extensions` adresine giderek uzantıyı yeniden yüklemek gerekli değildir. Bu gibi durumlarda, sayfayı yeniden yüklemeniz yeterlidir.

### Konsoldan addon.* API'yi kullanın

The `addon` object is accessible within the browser console through the `__addon` global variable when at least one addon is running.

### "debugger" anahtar kelimesini kullanarak kesme noktaları oluşturabilirsiniz

Geliştirici araçları açıksa JavaScript'teki `debugger;` anahtar kelimesi çalıştırıldığında sayfa dondurulur. Kesme noktalarını ayarlama ve yürütme sırasında yerel değişkenlerin değerini incelemek için kullanışlıdır.

### Konsol mesajlarını eklenti ID'sine göre filtreleyin

Yalnızca günlükleri, uyarıları ve ayrıca `console.error()` ile günlüğe kaydedilen hataları görüntülemek için "filtre" konsolu arama çubuğuna addon ID'sini girin. Açıkça kodunuza kaydetmediğiniz sürece bunun tüm diğer istisnaları gizleyeceğini unutmayın.


## Püf noktalar


### Scratch proje sayfası ve düzenleyicisi


#### Düzenleyicinin içine girildikten veya dışına çıkıldıktan sonra DOM yok edilir

Scratch, kullanıcı "içine bak" veya "proje sayfasını gör"e her tıkladığında tüm HTML ögelerini tekrar oluşturur ve eskilerini yok eder.
Bu genellikle `addon.tab.waitForElement` veya `urlChange` olayı kullanılarak düzeltilebilir.

#### Scratch düzenleyicisinin dili, yeniden yükleme yapılmadan değiştirilebilir

Scratch sitesinin aksine Scratch düzenleyicisinin dili değiştirirken yeniden yüklenmeyecektir. Farklı bir dil seçerken, Scratch bazı HTML ögelerini yok edebilir ve yeniden oluşturabilir.

#### Dikkate alınması gereken diğer durumlar

- Proje düzenleyicisi, tanımlı bir proje ID'si olmadan kullanılabilir (örneğin oturum kapatıldığında).
- Düzenleyici, sayfanın yeniden yüklenmesini gerektirmeden LTR'den RTL'ye (veya tam tersi) geçebilir.


### Scratch sitesi

#### scratch-www sayfaları giriş yapıldıktan sonra yeniden yüklenmez

Scratchr2 sayfalarının aksine scratch-www sayfaları, oturum açtıktan sonra bir sayfayı yeniden yüklenmesi için zorlamaz. Örneğin, oturumu kapatmışken bir proje sayfasına giderseniz ve ardından oturum açarsanız, sayfa yeniden yüklenmez. Bu, aynı zamanda stüdyolar, mesajlar sayfası vb. için de geçerlidir.
Buna karşılık, tüm Scratch sayfaları oturum kapatıldıktan sonra yeniden yüklenir.

#### Proje sayfaları asla 404s hatası döndürmez

Proje paylaşılmamış veya mevcut olmasa bile, Scratch, 200 HTTP durum kodunu döndürür. "Sunucumuz kafasını kaşıyor" mesajı Scratch tarafından sayfaya dinamik olarak eklenir.

#### Dikkate alınması gereken diğer durumlar

- Stüdyoların içindeki 4 sekmenin her biri farklı URL'lere sahiptir ancak bir tarayıcı hareketini tetiklemez. Baş URL ne olursa olsun, 4 sayfadan herhangi birini tetikleyen eklentiler çalışmalıdır.
