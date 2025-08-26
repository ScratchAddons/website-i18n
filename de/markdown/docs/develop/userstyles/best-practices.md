---
title: Empfohlene Vorgehensweisen
description: Befolge diese bewährten Praktiken beim Schreiben oder Überprüfen von Benutzerstilen.
---

Befolge diese bewährten Praktiken beim Schreiben oder Überprüfen von Benutzerstilen.


<!-- TODO: ## Unterstützung des dunklen Modus --> <!-- Beispiele zur Referenzierung von CSS-Variablen von editor-dark-mode, dark-www und scratchr2 -->


## Internationalisierung

### Sprachen mit längeren Wörtern berücksichtigen

Denke daran, dass in einigen Sprachen UI-Elemente wie Schaltflächen schmaler oder breiter sein können.

<!-- TODO: ### Unterstützung von Rechts-nach-Links-Sprachen (RTL) -->


## Styling der bestehenden Scratch UI


### Vermeide die Verwendung von Hash-Klassennamen

Der Scratch-Projekteditor enthält normalerweise Klassennamen, die dem Format `class_name_{hash}` folgen. Zum Beispiel: `green-flag_green-flag_1kiAo`.

Da sich die Hashes in der Zukunft ändern und sich zwischen den Scratch-Forks unterscheiden können, solltest du es vermeiden, sie in Benutzerstyles zu verwenden.

{{< admonition error >}}
```css /* Tu dies nicht: */ .green-flag_green-flag_1kiAo { visibility: hidden; } ```
{{< /admonition >}}

{{< admonition success >}}
```css /* Mache stattdessen dies: */ [class*="green-flag_green-flag_"] { visibility: hidden; } ```
{{< /admonition >}}

### Vermeide `!wichtig`, es sei denn, es ist unbedingt erforderlich

Wenn möglich, verwende [CSS specificity](https://web.dev/learn/css/specificity/), um deine Selektoren spezifischer zu machen, anstatt `!important` zu verwenden. <!-- Dies könnte noch detaillierter sein -->


## Gestaltung der UI-Elemente des Addons


### Beginne addondefinierte Klassennamen mit `sa-`.

{{< admonition info >}} Bei der Definition eigener Klassennamen verwenden wir immer den `kebab-case`. {{< /admonition >}}

Wir empfehlen, dass die Namen der von Addons definierten Klassen mit `sa-` beginnen, um mögliche Namenskollisionen mit Scratch oder anderen Erweiterungen zu vermeiden.

Es wird auch empfohlen, die Addon-ID (oder einen Teil davon) in den Klassennamen aufzunehmen.

<!-- TODO: ### Verwendung von z-index im Scratch-Editor und verwandte Konzepte erklären -->
