---
---

**Höherer Projekt-Framerate-Modus** ist ein Addon, das die Anpassung der Laufgeschwindigkeit des Projekts ermöglicht, um schneller zu werden.

Scratch iteriert normalerweise Schleifen 30 Mal pro Sekunde, was zu einer Bildschirmaktualisierungsrate von 30 Bildern pro Sekunde (FPS) führt. Dieses Addon kann die Iterationsrate erhöhen und dadurch die Bildrate ändern. Dies hat zur Folge, dass die Projektanimation im Vergleich zum benutzerdefinierten FPS-Wert reibungsloser, aber auch schneller läuft; daher wird der Standardwert von 60 FPS das Projekt im Wesentlichen doppelt so schnell ausführen.

Einige Projekte passen sich mit Techniken wie [Delta-Zeit](https://en.wikipedia.org/wiki/Delta_timing) an Framerate-Erhöhungen an, um ordnungsgemäß zu laufen und gleichzeitig die Animationen reibungslos zu erhalten.

Die Funktion kann ein- und ausgeschaltet werden, indem Sie `alt` gedrückt halten und auf die grüne Flagge klicken. Die Flagge wird blau und ein gelbes Schnellvorlaufsymbol wird darüber angezeigt, das anzeigt, dass das Projekt schneller läuft.

## Features

- Die Funktionalität des Addons wird nur aktiviert, wenn der Benutzer es aktiviert, indem er `alt` gedrückt hält und auf das grüne Flag klickt. Die Funktionalität des Addons wird jedes Mal deaktiviert, wenn die Seite geöffnet/aktualisiert wird.
- Das Addon funktioniert sowohl auf der Projektseite als auch im Editor.
- Standardmäßig setzt das Addon (wenn es aktiviert ist) die Bildrate des Projekts auf 60 FPS. Dieser Wert kann in den Einstellungen des Addons in eine ganze Zahl von 31 bis 240 geändert werden.

## Einstellungen

### Benutzerdefinierte FPS

Legt den Wert der Framerate des Projekts fest, wenn das Addon aktiviert ist.

## Zukunftspläne

- Das Addon kann als gefährlich markiert werden, um Projekte einzudämmen, die dieses Addon auf der Scratch-Website erfordern. [#6860](https://github.com/ScratchAddons/ScratchAddons/issues/6860)
- Da das Aktivieren des Addons das Halten der `alt` Taste fordert, ist es nicht mit Touchscreen-Geräten kompatibel. Eine vorgeschlagene Lösung besteht darin, dem grünen Flag für dieses Addon und mehrere andere ein Kontextmenü hinzuzufügen. [#7230](https://github.com/ScratchAddons/ScratchAddons/issues/7230)

## Danksagungen

Jeffalo hat das ursprüngliche Addon erstellt, das den Projektplayer nur auf 60 FPS eingestellt hat. TheColaber hat die benutzerdefinierte FPS-Einstellung und verschiedene andere Fehlerbehebungen hinzugefügt. Der zugängliche grüne Flaggenindikator wurde von JoanRiosiPla erstellt, bevor er von WorldLanguages optimiert wurde.

## Updates

- **V1.1.0** Das Addon **60FPS Player Mode** wurde erstellt.
- **V1.3.0** Das Addon ist jetzt standardmäßig für alle Benutzer aktiviert und hat das Recommended-Tag erhalten.
- **V1.7.0** Option hinzugefügt, um die Ziel-FPS anzupassen, die zuvor auf 60 gesperrt war.
- **V1.11.0** Das Addon wurde in **Alt+GreenFlag 60FPS-Spielermodus** umbenannt, und ein kurzes Informationsfeld wurde hinzugefügt. Für die benutzerdefinierten FPS wurde ein Limit festgelegt, das nun zwischen 31 und 240 liegt.
- **V1.13.0** `Alt` + grüne Flagge Klickerkennung wurde verbessert. Das Addon kann jetzt dynamisch aktiviert und deaktiviert werden.
- **V1.14.0** Das Addon erhielt das Project Player-Tag.
- **V1.18.0** Das Addon wurde in **60FPS Projektplayer-Modus** umbenannt. Das Addon kann jetzt in Projekteinbettungen ausgeführt werden.
- **V1.24.0** Fehlerbehebung: Das Addon verliert nicht mehr den Überblick über den Status, wenn es von der Projektseite zum Editor wechselt.
- **V1.26.0** Fehlerbehebung: Das Addon führt in einigen Fällen nicht mehr dazu, dass Variablen nicht visuell aktualisiert werden.
- **V1.30.0** Das Addon ist nicht mehr standardmäßig für alle Benutzer aktiviert.
- **V1.34.0** Ein besser zugängliches gelbes Schnellvorlauf-Symbol wurde dem grünen Flag-Indikator hinzugefügt, wenn das Addon umschaltet wird. Die Informationsbox wurde umgeschrieben, um klarzustellen, dass sich die meisten Projekte nicht richtig verhalten, wenn das Addon aktiviert ist.
- **V1.36.0** Das Addon wurde in **Höherer Projekt FPS-Modus** umbenannt. Das Beschreibungs- und Informationsfeld des Addons wurde der Klarheit halber umgeschrieben.
- **V1.37.0** Ein zweites Informationsfeld wurde hinzugefügt, das Probleme mit dem Energiesparmodus der Benutzergeräte erklärt.

## Verschiedenes

- Obwohl TurboWarp Addons dieses Addon nicht hat, können Sie mit den erweiterten Projekteinstellungen von Turbowarp die Bildrate des Projekts auf ähnliche Weise anpassen.
- Obwohl die Einstellung des Addons zum Anpassen der FPS von 31 auf 240 begrenzt ist, ist der Scratch-Projektplayer mit Werten sowohl niedriger als auch höher als diese Grenzen völlig in Ordnung! Es gibt mehrere Möglichkeiten, dieses Limit zu umgehen, da nur das Eingabefeld der Einstellung das Limit festlegt.
- Jeffalo fügte das Addon hinzu, weil "es verdammt cool ist"[^1]
- Es gibt eine Methode, die es Scratch-Projekten ermöglicht, einen benutzerdefinierten FPS grob zu erkennen, was darauf hinweisen kann, dass das Addon aktiviert ist.[ ^2]

## Galerie

{{< docs/stub-section >}}

## Verwandt

{{< docs/stub-section >}}

[^1]: https://github.com/ScratchAddons/ScratchAddons/pull/383#issue-714126835
[^2]: https://en.scratch-wiki.info/wiki/Making_an_FPS_Counter
