---
title: Eklentileri Yerelleştirme
description: Eklentileri yerelleştirmek kolaydır.
---
Eklentileri yerelleştirmek kolaydır.

## Mesaj ekleme
`addons-l10n/en/` altında, `ADDONID.json` adında bir dosya oluşturun; burada ADDONID, eklentinin kimliğidir (klasör adı). Çevirmek istediğiniz mesajlarınızı buraya yazın:

```json
{
  "ADDONID/meow": "Meow",
  "ADDONID/cats": "{number, plural, one {1 cat} other {# cats}}",
  "ADDONID/eat": "I want to eat {food}!",
  "ADDONID/salmon": "salmon",
  "ADDONID/sardine": "sardine"
}
```

### Yer tutucu
Bazen mesajların dinamik olarak oluşturulmuş şeylere sahip olması gerekir. Örneğin, kedi sayısı veya giriş. Bunu halletmek için `{placeholderName}` gibi yer tutucular kullanabilirsiniz. Yer tutucu adı yalnızca harflerden oluşmalıdır (sayı içermemelidir).

### Çoğul
Ya yer tutucu bir sayıysa? `{placeholderName, plural, one {ne zaman bir şey} diğer {ne zaman # şey}}` gibi çoğullar kullanabiliriz. Yer tutucu 1 ise, "bir şey olduğunda" gösterilir, aksi takdirde "(yer tutucu) şeyler olduğunda" yazar.

## Çevirileri kullanma
Userscript' i ilk satırını aşağıdaki gibi değiştirin:
```
export default async function ({ addon, console }) {
```

ile:
```
export default async function ({ addon, console, msg }) {
```

Eklenen `msg`, çevirileri almak için kullandığınız işlevdir. Örneğin, `text = "Meow"` artık `metin = msg("meow")` olabilir. Eklenti kimliği ve eğik çizgi atlanır.

### Yer tutucular
Yer tutucu değerleri sağlayabilirsiniz:
```js
cat = msg("cats", {number: 1}) // shows "1 cat"
cats = msg("cats", {number: 3}) // shows "3 cats"
hungry = msg("eat", {food: "cod"}) // shows "I want to eat cod!"
```

Ayrıca mesajları "iç içe" yerleştirebilirsiniz:
```js
hungry2 = msg("eat", {food: msg("salmon")}) // shows "I want to eat salmon!"
```

### Emniyet
Ham HTML yazıyorsanız, `msg`, `safeMsg` nin daha güvenli sürümüyle değiştirilmelidir. Lütfen `safeMsg` nin kalıcı persistent script' leri bulunmadığını unutmayın.
