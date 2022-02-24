---
title: Często Zadawane Pytania
description: Ta strona zawiera listę najczęściej zadawanych pytań odnoszących się do dodatku Scratch Addons
---

Ta strona zawiera listę najczęściej zadawanych pytań odnoszących się do dodatku Scratch Addons

### Co to Scratch Addons?

Dodatki Scratch to rozszerzenie przeglądarki „wszystko w jednym” dla strony internetowej Scratch i edytora projektów. Zapewnia funkcje i motywy (nazywane wewnętrznie dodatkami), zarówno dla strony internetowej Scratch, jak i edytora projektu. Misją Scratch Addons jest połączenie wszystkich istniejących rozszerzeń Scratch, skryptów użytkownika i stylów użytkownika, opracowanych przez kilku członków społeczności Scratch, w jedno, i stworzyć łatwo dostępne miejsce, jednocześnie pozwalając użytkownikom wybrać, które z nich włączyć. 

### Co to "dodatek" dokładniej?

Dodatek jest podobny do rozszerzenia lub do kodu użytkownika, ale używa specjalnego API , który jest dostarczany przez rozszerzenie. API znacznie ułatwia pisanie skryptów (kody użytkownika) oraz zmienianie stylów strony (style użytkownika).

Skrypty użytkownika używają API do Java Scripta `addon.*` , pozwalający im dostać informacje o użytkowniku (nick) oraz pozwala prościej wywoływać funkcje jak (wysyłanie powiadomień).

### Jeśli wszystko to dodatek, więc co robi Scratch Addons?

W gruncie rzeczy Scratch Addons to tylko program ładujący dodatki, jego zadaniami są:

- Pozwalać użytkownikom włączać, wyłączać oraz ustawiać dodatki
- Sterować dodatkami i dawać im API.
- Dodawanie możliwości edytowania nadrzędnych funkcji (np. addon.auth API).
- Naprawiać błędy strony Scratch.
- Zapewniać sposoby uzyskiwania dostępu do stanu Redux i modyfikowania go. 
- Zapobiega nakładaniu się kodu dodatków na siebie.
- Importuje biblioteki, które są wykorzystywane przez wiele dodatków jednocześnie.

### Czy Scratch Addons jest bezpieczne?

Tak. Dodatki Scratch nie powinny mieć żadnych problemów z bezpieczeństwem w swojej najnowszej wersji. Scratch Addons to projekt typu open source, więc kod jest stale weryfikowany przez współtwórców Scratch Addons, a także recenzentów z Chrome Web Store i Add-ons dla Firefoksa. 

### Jak mogę zgłosić lukę w zabezpieczeniach? 

Jeśli tak się stanie, prosimy o skontaktowanie się prywatnie z @World_Languages wysyłając email na adres `worldxlanguages (at) gmail.com`. Jeśli nie otrzymasz odpowiedzi w ciągu 48 godzin, proszę stworzyć zgłoszenie [tutaj](https://github.com/ScratchAddons/ScratchAddons/issues/).

Możesz [przeczytać naszą politykę bezpieczeństwa](https://github.com/ScratchAddons/ScratchAddons/security/policy) lub [sprawdzić opublikowane przez nas porady](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published). 

### Czy moje konto będzie bezpieczne podczas korzystania z Scratch Addons? 

Scratch Addons nie musi znać danych o Twoim koncie. Możesz nawet być wylogowany/a ze Scratch, a nasz dodatek nadal będzie działać. Scratch Addons jedynie wysyła informacje oparte na Cookies, które zawierają informacje jak dodatek działa na Twoim komputerze. Dodatki wymagające zalogowania to m.in. Wiadomości Scratch.

Dodatki w naszym rozszerzeniu są sprawdzane przez wiele współtwórców, więc nikt nie wgra złego oprogramowania do Scratch Addons!

Nigdy nie wysyłamy informacji o Twoim koncie Scratch po za Twoją przeglądarkę. Przeczytaj [politykę prywatności dla naszego dodatku](/docs/privacy/policies/extension) po więcej informacji.

### Czy mogę mówić osobom o Scratch Addons na stronie Scratch?

Nie możesz, i proszę tego nie robić. Scratch ma politykę zabraniającą promowania dodatków/rozszerzeń, opis przeczytasz [tutaj](https://scratch.mit.edu/discuss/post/2907564/). Możesz użyć innych możliwości kontaktu, aby powiedzieć przyjaciołom o Scratch Addons.

### Jak mogę coś dodać do Scratch Addons?

Najpierw, dziękujemy Ci za zainteresowaniem się tym tematem. Doceniamy Twoje zainteresowanie i Twoje przyszłe zmiany.

Jako projekt z Otwartym Źródłem jesteśmy otwarci na wszystkie zmiany. Nie musisz pytać żeby coś zmienić! Każdy może na pomóc!

Możesz rozwijać nasz projekt w wiele sposobów, a niektóre są na prawdę proste!

- **Polepszanie projektu**

  Jeśli potrafisz programować w JavaScript, HTML5 i CSS, możesz rozwijać nasz projekt za pomocą programowania. Możesz naprawiać błędy i dodawać nowe funkcjonalności!

  Jak już napiszesz kod możesz stworzyć pull request. Aby to zrobić musisz sklonować nasze [repozytorium](https://github.com/ScratchAddons/ScratchAddons/). Jeśli zgłoszenie będzie odpowiednie, dodamy to do naszego rozszerzenia!

  Jesteśmy otwarci na nowych współtwórców, nie tylko w budowie rozszerzenia! Możesz zobaczyć nasze repozytoria na  [stronie naszej organizacji na GitHub](https://github.com/ScratchAddons) i pomóc nam je budować.

- **Zaproponuj pomysł**

  Masz jakiś pomysł co moglibyśmy dodać do Scratch Addons? [Powiedz nam!](#i-think-you-missed-a-feature-what-can-i-do)

- **Zgłoś błąd**

  Jeśli znalazłeś błąd w jednym z naszych dodatków, stronie ustawień, lub w naszym rozszerzeniu? [Wyślij nam zgłoszenie](#what-can-i-do-if-i-find-a-problem).

- **Tłumaczenie Scratch Addons**

  Jeśli płynie mówisz w innym języku niż Angielsku, możesz nam pomóc tłumaczyć Scratch Addons na Twój język. Możesz zacząć to robić  [tutaj](/docs/localization/joining-the-localization-team).

- **Pisanie dokumentacji**

  Znasz dobrze nasze rozszerzenie? Jeśli tak, możesz pomóc nam pisać dokumentację. W dokumentacji powinieneś zawrzeć informacje jak działa i jak używać daną funkcję. Porozmawiaj z nami na [dyskusji znajdującej się na GIthub](https://github.com/ScratchAddons/ScratchAddons/discussions), aby poznać więcej informacji.

- **Wyślij opinię**

  Jeśli chcesz nam podać opinię, możesz to zrobić [tutaj](https://scratchaddons.com/feedback). Twoja opinia może nam pomóc w rozwijaniu i polepszaniu naszego rozszerzenia!

- **Daj opinię na Stronach Rozszerzeń**

  Możesz wysłać opinię o Scratch Addons na [stronie dodatków Chrome](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) lub [na stronie rozszerzeń Firefox](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/).

- **Daj gwiazdkę naszemu projektowi**

  Gwiazdki GIthub, są podobne do ustawiania projektów jako ulubionych na Scratch. Możesz to zrobić w [naszym repozytorium](https://github.com/ScratchAddons/ScratchAddons) klikając w ikonkę w prawym górnym rogu ekranu.

- **Promuj nas**

  Możesz powiedzieć wszystkim o Scratch Addons, jak np. przyjaciele, członkowie rodziny, lub nawet nauczyciel informatyki. Prosimy Ciebie o [nie promowanie Nas na Stronie Scratch](#can-i-tell-people-about-scratch-addons-on-scratch).

### Jak mogę stworzyć własny dodatek?

Przeczytaj więcej o tworzeniu dodatków [tutaj](/docs/develop/getting-started).

### Jak moje imię może znaleźć się na liście [współtwórców](/contributors)?

Proszę przeczytaj instrukcję w [tym zgłoszeniu](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) jeśli chcesz, aby to imię znalazło się na tej liście.

### Jak mogę usunąć swoje imię z [listy współtwórców](/contributors)?

Jeśli nie chcesz mieć swojego imienia na tej liście, powiedz nam  [w naszym repozytorium](https://github.com/ScratchAddons/contributors/issues/), albo w innych sposobach kontaktu. Przepraszamy, za nasz błąd.

### Co mam zrobić jeśli znalazłem/am problem?

Jeśli chcesz nam zgłosić problem, skorzystaj z tych metod.

- Wyślij opis błędu w [karcie na opinie](https://scratchaddons.com/feedback).
- Stwórz błąd w naszym [repozytorium](https://github.com/ScratchAddons/ScratchAddons/issues).
- Wyślij wiadomość w [zakładce Dyskusji](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Powiedz nam na naszym [serwerze discord](https://discord.gg/R5NBqwMjNc).

### Masz pomysł na nową funkcjonalność?

Jeśli sądzisz że brakuje jakiejś funkcjonalności, lub masz pomysł na dodatek, zgłoś nam [za pomocą jednego z tych sposobów](#what-can-i-do-if-i-find-a-problem).

### Gdzie mogę rozmawiać o Scratch Addons?

Możesz zrobić to w [zakładce Dyskusji](https://github.com/ScratchAddons/ScratchAddons/discussions) lub [na naszym serwerze Discord](https://discord.gg/R5NBqwMjNc). Tam możesz dyskutować o naszym rozszerzeniu i pytać o różne rzeczy.

### Jeśli Scratch Addons zwalnia Scratch to co mam zrobić?

Spróbuj wyłączyć dodatki których nie używasz. W dodatku sprawdź opisy dodatków, aby przeczytać, które ustawienia/dodatki mogą zwalniać Twój komputer.

### Jak mogę włączyć Ukryte Dodatki?

Aby pokazać ukryte dodatki należy w menu ustawień, wpisać Konami Code  (↑↑↓↓←→←→BA). Gdy to zrobisz, w tym miejscu pojawią się Easter Eggi, które możesz wtedy włączyć.

Niektóre z Dodatków Niespodzianek to "Zamień litery na drukowanie" i "Błąd przecinka". Zobacz [listę dodatków](/addons), aby poznać ich listę.

### Mam więcej pytań!

Jeśli masz więcej pytań na które szukasz odpowiedzi, stwórz zgłoszenie [na Karcie Dyskusj](https://github.com/ScratchAddons/ScratchAddons/discussions)  lub wyślij wiadomość na naszym [serwerze Discord](https://discord.gg/R5NBqwMjNc). Na pewno ktoś Ci odpowie!
