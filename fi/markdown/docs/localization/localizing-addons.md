---
title: Lisäosien lokalisointi
description: Lisäosien lokalisointi on helppoa.
---
Lisäosien lokalisointi on helppoa.

## Viestien lisääminen
Tee `ADDONID.json`-niminen tiedosto kohtaan `addons-l10n/en/`. ADDONID on lisäosan tunnus (kansion nimi). Kirjoita sinne viestit , jotka haluat kääntää:

```json
{
  "ADDONID/meow": "Meow",
  "ADDONID/cats": "{number, plural, one {1 cat} other {# cats}}",
  "ADDONID/eat": "I want to eat {food}!",
  "ADDONID/salmon": "salmon",
  "ADDONID/sardine": "sardine",
  "ADDONID/move-steps": {
    "string": "move {number} steps",
    "developer_comment": "Please translate this to match Scratch's official translation for the block."
  }
}
```

### Paikanvaraajat
Toisinaan viesteissä täytyy olla kohtia, jotka generoidaan dynaamisesti. Esimerkiksi kissojen lukumäärä tai syöte. Tätä varten voit käyttää paikanvaraajia, kuten `{paikanvaraajanNimi}`. Paikanvaraajan nimi saa sisältää ainoastaan kirjaimia (ei numeroita).

### Monikolliset muodot
Entä jos paikanvaraaja on numero? Tällöin voidaan käyttää monikollisia muotoja, kuten `{paikanvaraajanNimi, plural, one {kun on yksi asia} other {kun on # asiaa}}`. Jos paikanvaraaja on 1, näytetään kohta "kun on yksi asia". Muuten näytetään kohta "kun on (paikanvaraaja) asiaa".

### Kehittäjän kommentit

Transifex näyttää kehittäjän kommentin, kun kääntäjä on valinnut määritellyn merkkijonon. Kommenttien avulla yleensä kerrotaan yksityiskohtaisia tietoja merkkijonon käännöksestä tai tarjotaan lisätietoja kielille, jotka eivät erottele isoja ja pieniä kirjainmerkkejä.

## Käännösten käyttäminen
Muuta käyttäjäskriptisi ensimmäinen rivi jostakin tällaisesta:
```
export default async function ({ addon, console }) {
```

tällaiseen:
```
export default async function ({ addon, console, msg }) {
```

Skriptiin lisätty `msg` on funktio, jota käytetään käännösten saamiseksi. Esimerkiksi `text = "Meow"` voisi nyt olla `text = msg("meow")`. Lisäosatunnus ja kauttaviiva on jätetty pois.

### Paikanvaraajat
Voit käyttää paikanvaraajien arvoja:
```js
cat = msg("cats", {number: 1}) // shows "1 cat"
cats = msg("cats", {number: 3}) // shows "3 cats"
hungry = msg("eat", {food: "cod"}) // shows "I want to eat cod!"
```

Voit myös laittaa viestejä "sisäkkäin":
```js
hungry2 = msg("eat", {food: msg("salmon")}) // shows "I want to eat salmon!"
```

### Turvallisuus
Jos kirjoitat raakaa HTML-koodia, `msg` tulee korvata turvallisemmalla versiolla `safeMsg`.
