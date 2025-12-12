---
---

**Blöcke suchen und einfügen** ist ein Addon, mit dem man schneller programmieren kann, indem Blöcke beim Eintippen ihrer Namen direkt beim Mauszeiger platziert werden, ohne dass in der Blockpalette nach ihnen gesucht werden muss. Das Popup kann mit einem Mittelklick auf den Codebereich oder durch Drücken von `Strg` + `Leertaste` geöffnet werden. Du kannst dann mit der Eingabe beginnen, um nach Blöcken zu suchen, und sie dann mit der Maus hinausziehen.

## Hintergrund

Die Originalversion wurde von Griffpatch für die Erweiterung "Developer Tools", die später Teil von Scratch Addons wurde, entwickelt. Als das _Entwicklertools_-Addon in mehrere kleinere Addons aufgeteilt wurde, wurde auch diese Funktion zu einem eigenständigen Addon.

## Features

- Die Suche unterstützt alle Blöcke des Codebereichs. Dies umfasst benutzerdefinierte Blöcke, Blöcke von Erweiterungen, Variablen / Listen usw.
- Für ein noch schnelleres Sucherlebnis kannst du mit den Pfeiltasten und der Entertaste in den Suchergebnissen navigieren.
- Wenn ein Ergebnis markiert ist, kannst du die Tabulator-Taste drücken, um deine Suche nach dem Block automatisch zu vervollständigen.
- Das Popup kann mehrere verschachtelte Blöcke gleichzeitig einfügen, indem man etwas wie "gehe meine Variable + 10 Schritte" eingibt.
- Bei mathematischen Blöcken gilt standardmäßig die Reihenfolge der Operationen, aber du kannst die Reihenfolge in eckigen Klammern ändern.
- Du kannst Text in doppelte Anführungszeichen umgeben, um den Sucher zu zwingen, deinen Text nicht in Blöcke zu verwandeln. Dies ist nützlich für Situationen wie den Versuch, den Text "x-Position" anstelle der Variablen `x-Position` zu sagen, wo du sage "x-Position" eingeben kannst.

## Einstellungen

### Popup Block-Größe

Steuert, wie groß die Blöcke im Menü erscheinen. Es ist die Höhe in Pixeln eines einzelnen Blocks.

### Popup-Breite

Steuert, wie breit das Popup ist. Dies ist ein Prozentsatz der Breite des gesamten Fensters.

### Maximale Höhe des Pop-Ups

Steuert, wie hoch das Popup sein kann, bevor eine Bildlaufleiste angezeigt wird. Dies ist ein Prozentsatz der Höhe des gesamten Fensters.

## Zukunftspläne

- Das Popup sollte durch Ziehen einer der Ecken im Editor geändert werden können, anstatt eine Einstellung ändern zu müssen.
- Das Hinzufügen von String-Interpolation für Zeichenfolgen in Anführungszeichen könnte wirklich bei Situationen helfen, in denen viele Verbindungsblöcke normalerweise mühsam angeordnet werden müssten.

## Bekannte Probleme

- Die Blöcke im Popup dieses Addons respektieren nicht die Einstellungen des Addons *Anpassbare Blockformen*.
- Der Algorithmus zum Sortieren der Suchergebnisse erfordert noch viel Arbeit, und manchmal ist das Ergebnis, nach dem du wahrscheinlich suchst, unter einem Berg schlechterer Ergebnisse versteckt.

## Danksagung

Tacodiva hat den größten Teil des Addons so gemacht, wie es heute aussieht. Darüber hinaus half Griffpatch sehr, indem er Feedback gab und Fehler in der überarbeiteten Version fand.

## Updates

{{< docs/outdated-section >}}

- **V1.30.0** Das Addon "Blöcke nach Namen einfügen" wurde erstellt.
- **V1.31.0** Das Addon wurde komplett überarbeitet und ermöglichte das Verschachteln von Blöcken, das Hinzufügen der automatischen Vervollständigung und das Ändern der Art und Weise, wie die Blöcke im Popup angezeigt wurden.
- **V1.31.1** Der Suchalgorithmus wurde geändert und mehrere Fehler wurden behoben.

## Unterschiedliches

- Dies war die erste Addon-Seite, die für die Addon Docs geschrieben wurde!
- Obwohl es erst vor kurzem zu einem eigenen Addon geworden ist, ist das mittlere Klick-Popup eine der ältesten Funktionen von Scratch Addons, die Teil der Entwicklertools sind.
- Der ursprüngliche Code für das Popup wurde erstellt, bevor es Scratch Addons von Griffpatch im Jahr 2019 überhaupt gab.
- Als Tacodiva das Addon für v1.31.0 überarbeitete, hatte der Code fast 2.800 Codezeilen hinzugefügt und 149 Commits!
- Der Name des Git-Zweigs für die Überholung war `idk-what-im-doing`.
- Tacodiva hatte so viel Mühe, ein Problem zu beheben, dass CST1229, obwohl er nur zwei Zeilen CSS zur Behebung des Problems beisteuerte, in den Credits des Addons steht!

## Galerie

{{< docs/stub-section >}}

## Verwandt

{{< docs/stub-section >}}
