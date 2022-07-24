---
title: Style użytkownika
description: Style użytkownika pozwalają dać kod CSS na stronę Scratch - użyteczne, żeby zmienić wygląd elementu na stronie.
---
## Po co one są?
Style użytkownika pozwalają dać kod CSS na stronę Scratch - użyteczne, żeby zmienić wygląd elementu na stronie.

## Jak dodać styl użytkownika?
**Upewnij się żeby odświeżyć rozszerzenie ze strony `chrome://extensions` po zrobieniu zmian do dodatku.**
Przejdź do ustawień Twojego dodatku (addon.json) i dodaj wartość `"userstyles"`. Ta wartość musi być deklaracją listy.
Każdy obiekt w liście musi mieć dwie wartości `"url"` i `"matches"`
`"url"` musi być linkiem do pliku CSS
`"matches"` must be warunkiem na jakich stronach styl ma być włączony
Przykładowa deklaracja:
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

## Naprawianie stylów użytkownika
**Upewnij się żeby odświeżyć dodatek ze strony `chrome://extensions` po zrobieniu zmian** 
Jeśli nie widzisz zmian, upewnij się że dodatek jest odblokowany 
Jeśli nadal natrafiasz na problem, skontaktuj się z nami na GitHub!
