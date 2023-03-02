---
title: Uporabniški slogi
description: Uporabniški slogi omogočajo dodajanje kode CSS Scratchevi spletni strani - z njimi lahko naredite gumbe, ki jih dodajo uporabniške skripte, barvite, ali pa spremenite videz Scratchevih elementov.
---

Uporabniški slogi omogočajo dodajanje kode CSS Scratchevi spletni strani - z njimi lahko naredite gumbe, ki jih dodajo uporabniške skripte, barvite, ali pa spremenite videz Scratchevih elementov.

## Kako dodam uporabniški slog?
**Vedno znova naložite Scratch Addons na strani `chrome://extensions`, potem ko spremenite vaš dodatek.**  
Odprite datoteko addon.json in dodajte lastnost `"userstyles"`.  
Ta lastnost mora biti seznam.  
Vsak element seznama mora imeti naslednji lastnosti: `"url"` in `"matches"`.  
`"url"` mora biti relativen URL datoteke CSS.  
`"matches"` mora biti seznam URL-jev, na katerih naj bo dodan uporabniški slog. Lahko uporabite zvezdice.
Primer datoteke addon.json:
```json
{
  "name": "Scratch Messaging",
  "description": "Provides easy reading and replying to your Scratch messages.",
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

## Razhroščevanje uporabniških slogov
**Vedno znova naložite Scratch Addons na strani `chrome://extensions`, potem ko spremenite vaš dodatek.**  
Če uporabniški slog ne deluje, preverite, če je dodatek vključen.  
Če imate še vedno težave, prosimo, da jih prijavite na GitHub.
