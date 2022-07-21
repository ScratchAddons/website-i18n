---
title: Felhasználói stílusok
description: A felhasználói stílusok megengedik, hogy CSS-t injektálj a Scratch weboldalba - hasznos arra, hogy a felhasználói szkriptekkel hozzáadott gombokat színezhesd, vagy személyre szabhass egy helyi Scratch elemet.
---
## Mik is ezek?
A felhasználói stílusok megengedik, hogy CSS-t injektálj a Scratch weboldalba - hasznos arra, hogy a felhasználói szkriptekkel hozzáadott gombokat színezhesd, vagy személyre szabhass egy helyi Scratch elemet.

## Hogy adhatok hozzá felhasználói stílust?
**Frissítsd le a Scratch Addons-t a `chrome://extensions` -ben miután bármit változtattál a bővítményeden.**
Menj a bővítményed manifest-jébe (addon.json) és adj hozzá egy `"userstyles"` nevű tulajdonságot.
Ennek egy array-nek kell lennie.
Az array minden elemének birtokolnia kell a következő tulajdonságokat: `"url"` és `"matches"`.
Az `"url"` egy relatív URL kell legyen egy CSS fájlhoz.
A `"matches"` egy URL array, ami azt tartalmazza hova akarod a userstyle-t alkalmazni. Használhatsz csillagokat.
Példa manifest:
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

## Felhasználói stílusok debugolása
**Frissítsd le a Scratch Addons-t a `chrome://extensions` -ben miután bármit változtattál a bővítményeden.**
Ha nem látod, hogy a beállításaid működnének, bizonyosodj meg arról, hogy a bővítmény engedélyezve van.
Ha még mindig gondjaid akadnak, írj egy megjegyzést itt.
