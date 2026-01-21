---
---

**Режим повышенной частоты кадров проекта** — дополнение, которое позволяет настройку скорости воспроизведения проекта в быстрейшую сторону.

Обычно Scratch итерирует через циклы 30 раз в секунду, то есть с частотой в 30 Кадров в Секунду (FPS). Это дополнение может увеличить частоту итераций, в итоге изменяя частоту кадров. В результате имеем эффект более гладкого проекта, но ещё и более быстрого, по сравнению с выбранным значением FPS; следует, значение по умолчанию 60 FPS элементарно сделает проект дважды быстрым.

Некоторые проекты могут адаптироваться к изменениям в частоте кадров с помощью техник как [изменение времени](https://en.wikipedia.org/wiki/Delta_timing), для исправного воспроизведения с гладкими анимациями.

Возможность можно переключать с помощью зажатия клавиши `alt` и нажатия на зелёный флажок. Флажок должен стать синим и над ним должна появиться иконка перемотки, указывающая на повышенную скорость проекта.

## Особенности

- Функциональность дополнения только включена при её активации пользователем через зажатие клавиши `alt` и нажатии зелёного флажка. Эта возможность дополнения выключается при каждом открытии или обновлении страницы.
- Дополнение теперь работает и на странице проектов, и в редакторе.
- По умолчанию, дополнение (при активации) устанавливает частоту кадров проекта в 60 FPS. Это значение можно поменять в настройка дополнения на любое целое число от 31-ого до 240-ок.

## Настройки

### Пользовательская Частота Кадров

Устанавливает значение частоты кадров проекта при включённом дополнении.

## Планы о будущем

- Дополнение могут объявить опасным для ограничения проектов, которые требуют это дополнение на веб-сайте Scratch. [#6860](https://github.com/ScratchAddons/ScratchAddons/issues/6860)
- Так как включение дополнения требует зажимания клавиши `alt`, оно не совместимо с устройствами сенсорных экранов. Есть предложенное решение — добавить контекстное меню зелёному флажку для этого и многих других дополнений. [#7230](https://github.com/ScratchAddons/ScratchAddons/issues/7230)

## Титры

Jeffalo создал оригинальное дополнение, которое могло только увеличивать скорость проигрывателя проекта до значений 60 FPS. TheColaber добавил настройку FPS и много других исправлений. Удобный индикатор в зелёном флажке был создан JoanRiosiPla до того как он был подправлен WorldLanguages.

## Список изменений

- **v1.1.0** Дополнение **60FPS Режим Проигрывателя** было создано.
- **v1.3.0** Дополнение теперь включено по умолчанию для всех пользователей, и отмечено биркой Рекомендуемо.
- **v1.7.0** Добавлена настройка изменять конечные FPS, которые до этого были закреплены за 60.
- **v1.11.0** Дополнение переименовано в **Alt+ЗелёныйФлажок 60FPS режим проигрывателя** и краткая информационная подсказка была добавлена. Был установлен лимит пользовательских FPS, который теперь лежит от 31-го до 240-ка.
- **v1.13.0** Обнаружение нажатия `Alt` + Зелёного Флажка было улучшено. Дополнение теперь можно динамически включать и выключать.
- **v1.14.0** Дополнение получило бирку Проигрыватель Проекта.
- **v1.18.0** Дополнение переименовано в **60FPS режим проигрывателя проектов**. Оно теперь также может использоватеься во внедрениях проектов.
- **v1.24.0** Bug fix: The addon no longer loses track of state when changing from project page to editor.
- **v1.26.0** Bug fix: The addon no longer causes variables to not visually update in some cases.
- **v1.30.0** The addon is no longer enabled by default for all users.
- **v1.34.0** A more accessible yellow fast-forward icon was added to the green flag indicator whenever the addon is toggled on. Information box was rewritten to clarify that most projects will not behave properly when addon is enabled.
- **v1.36.0** The addon was renamed to **Higher project framerate mode**. The addon's description and information box was rewritten for clarity.
- **v1.37.0** A second information box was added that explains issues with user devices' power saving mode.

## Trivia

- Although TurboWarp Addons does not have this addon, Turbowarp's advanced project settings allows you to customize the project's framerate in a similar way.
- Despite the addon's setting for customizing the FPS is limited from 31 to 240, the Scratch project player is perfectly fine with values both lower and higher than these limits! There are several ways to bypass this limit, as only the setting's input field sets the limit.
- Jeffalo added the addon because "its hecking cool"[^1]
- There is a method that allows Scratch projects to roughly detect a custom FPS, which may indicate that the addon is enabled.[^2]

## Gallery

{{< docs/stub-section >}}

## Related

{{< docs/stub-section >}}

[^1]: https://github.com/ScratchAddons/ScratchAddons/pull/383#issue-714126835
[^2]: https://en.scratch-wiki.info/wiki/Making_an_FPS_Counter
