---
title: Kullanıcı Stilleri
description: Kullanıcı stilleri, Scratch web sitesine CSS eklemenize olanak tanır - kullanıcı komut dosyaları ile eklediğiniz düğmeleri renkli hale getirmek veya yerel Scratch öğesini özelleştirmek için kullanışlıdır.
---
## O da neyin nesi?
Kullanıcı stilleri, Scratch web sitesine CSS eklemenize olanak tanır - kullanıcı komut dosyaları ile eklediğiniz düğmeleri renkli hale getirmek veya yerel bir Scratch öğesini özelleştirmek için kullanışlıdır.

## Nasıl bir kullanıcı stili eklerim?
**Eklentinizde herhangi bir değişiklik yaptıktan sonra Scratch Eklentilerini `chrome://extensions`' dan yenilemeyi unutmayın.**
Eklentinizin (addon.json) manifest dosyasına gidin ve `"userstyles"` adlı bir özellik ekleyin.
Bu özellik bir dizi olmalıdır.
Dizinin her bir öğesi şu özelliklere sahip olmalıdır: `"url"` ve `"matches"`.
`"url"`, bir CSS dosyasına göreli bir URL olmalıdır.
`"matches"`, userstyle' ını eklenmesini istediğiniz URL' lerin bir dizisi olmalıdır. Yıldız işaretlerini kullanabilirsiniz.
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
      "url": "second_userstyles.css",
      "matches": ["https://scratch.mit.edu/projects/*", "https://scratch.mit.edu/users/*"]
    }
  ],
  "tags": ["community"],
  "enabled_by_default": false
}
```

## Kullanıcı stilleri' nde hata ayıklama
**Eklentinizde herhangi bir değişiklik yaptıktan sonra Scratch Eklentilerini `chrome://extensions`' dan yenilemeyi unutmayın.**
Kullanıcı stilinizin çalıştığını görmüyorsanız, eklentinizin etkin olduğundan emin olun.
Hala sorun yaşıyorsanız, lütfen bu depoda bir sorun oluşturun.
