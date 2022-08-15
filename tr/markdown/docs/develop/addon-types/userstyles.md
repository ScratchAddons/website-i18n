---
title: Userstyle'lar
description: Userstyle'lar, Scratch sitesine CSS eklemenize olanak tanır - userscript'ler ile eklediğiniz düğmeleri renkli hâle getirmek veya yerel Scratch ögesini özelleştirmek için kullanışlıdır.
---
## O da neyin nesi?
Userstyle'lar, Scratch sitesine CSS eklemenize olanak tanır - userscript'ler ile eklediğiniz düğmeleri renkli hâle getirmek veya yerel Scratch ögesini özelleştirmek için kullanışlıdır.

## Nasıl bir userstyle eklerim?
**Eklentinizde herhangi bir değişiklik yaptıktan sonra Scratch Eklentilerini `chrome://extensions` dan yenilemeyi unutmayın.**
Eklentinizin (addon.json) manifest dosyasına gidin ve `"userstyles"` adlı bir özellik ekleyin.
Bu özellik bir dizi olmalıdır.
Dizinin her bir öğesi şu özelliklere sahip olmalıdır: `"url"` ve `"matches"`.
`"url"`, bir CSS dosyasına göreli bir bağlantı olmalıdır.
`"matches"`, userstyle'ını eklenmesini istediğiniz bağlantıların bir dizisi olmalıdır. Yıldız işaretlerini kullanabilirsiniz.
Örnek manifest:
```json
{
  "name": "Scratch Mesajlaşma",
  "description": "Scratch mesajlarınızı kolayca okumanızı ve yanıtlamanızı sağlar.",
  "userstyles": [
    {
      "url": "userstyle.css",
      "matches": ["https://scratch.mit.edu/*"]
    },
    {
      "url": "second_userstyle.css",
      "matches": ["https://scratch.mit.edu/projects/*", "https://scratch.mit.edu/users/*"]
    }
  ],
  "tags": ["community"],
  "enabledByDefault": false
}
```

## Userstyle'larda hata ayıklama
**Eklentinizde herhangi bir değişiklik yaptıktan sonra Scratch Eklentilerini `chrome://extensions`dan yenilemeyi unutmayın.**
Userstyle'ınızın çalıştığını görmüyorsanız, eklentinizin etkin olduğundan emin olun.
Hâlâ sorun yaşıyorsanız, lütfen bu depoda bir sorun oluşturun.
