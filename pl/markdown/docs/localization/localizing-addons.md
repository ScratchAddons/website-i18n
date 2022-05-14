---
title: Tłumaczenie Dodatków
description: Tłumaczenie dodatków jest proste.
---
Tłumaczenie dodatków jest proste.

## Dodawanie wiadomości
W pliku `addons-l10n/en/`, stwórz nowy plik `IDDODATKU.json`, gdzie IDDODATKU to nazwa folderu w którym znajduje się dodatek. Tam napisz swoje wiadomości:

```json
{
"IDDODATKU/meow": "Meow",
"IDDODATKU/cats": "{number, plural, one {1 cat} other {# cats}}",
"IDDODATKU/eat": "I want to eat {food}!",
"IDDODATKU/salmon": "salmon",
"IDDODATKU/sardine": "sardine"
}
```

### Słowa-wypełniacze
Czasami wiadomości muszą zawierać zawartość automatycznie generowaną. Na przykład liczbę kodów, lub tekst wpisany przez użytkownika. Aby to obsłużyć, musisz używać, możesz używać "słów-wypełniaczy" np `{słowoWypełniacz}`. Słowa-wypełniacze powinny zawierać tylko litery (nie liczby).

### Liczba mnoga
Co jeśli symbolem zastępczym jest liczba? Możemy użyć liczby mnogiej, takiej jak `{nazwa zastępcza, liczba mnoga, liczba pojedyncza {gdy jest jedna rzecz}, inna {gdy jest # rzeczy}}`. Jeśli symbol zastępczy ma wartość 1, pokaże się „Gdy jest jedna rzecz.”, w przeciwnym razie zostanie napisane „Gdy jest (symbol zastępczy) rzeczy”.

## Używanie tłumaczeń
Zmień pierwszą linię swojego kodu z czegoś takiego:
```
export default async function ({ addon, console }) {
```

na:
```
export default async function ({ addon, console, msg }) {
```

`msg` to jest funkcja, którą możesz użyć do tłumaczenia. Na przykład:  `text = "Meow"` możesz zamienić na `text = msg("meow")`. Podając id wiadomości, nie wpisuj slasha i id dodatku.

### Słowa-wypełniacze
Możesz podać słowa zastępujące w taki sposób:
```js
cat = msg("cats", {number: 1}) // pokazuje "1 kot"
cats = msg("cats", {number: 3}) // pokazuje "3 koty"
hungry = msg("eat", {food: "cod"}) // pokazuje "Chcę zjeść dorsza!"
```

Możesz także "zagnieździć" wiadomości:
```js
hungry2 = msg("eat", {food: msg("salmon")}) // pokazuje "Chcę zjeść łososia!"
```

### Bezpieczeństwo
Jeśli piszesz w samym HTML'u powinnieś używać `safeMsg` zamiast `msg`.
