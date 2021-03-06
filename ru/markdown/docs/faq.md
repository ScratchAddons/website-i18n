---
title: Часто задаваемые вопросы
description: На этой странице перечислены часто задаваемые вопросы о расширении Scratch Addons и проекте.
---

На этой странице перечислены часто задаваемые вопросы о расширении Scratch Addons и проекте.

### Что такое Scratch Addons?

Scratch Addons — браузерное расширение «всё в одном» для веб сайта Scratch и его редактора проектов. Он даёт новые функции и темы (которые называются аддонами), для веб сайта Scratch и редактора проектов. Миссия Scratch Addons — соединить все существующие Scratch расширения, юзерскрипты и юзерстили, которые разработаны некоторыми участниками сообщества Scratch, в одно место с лёгким доступом, давая пользователям выбирать, какие нужно включить.

### Что такое «аддон»?

Аддон похож на расширение или юзерскрипт, но они используют специальные API, которые предоставлены расширением Scratch Addons. Эти API позволяют аддонам выполнять скрипты на странице Scratch (юзерскрипты) или применять стили к веб-сайту Scratch (юзерстили).

Юзерскрипты могут использовать JavaScript API `addon.*`, которые позволяют им получать соответствующую информацию о Scratch (например, получать пользователя, который вошёл в систему) и также использовать API расширения (по типу отправления уведомлений).

### Если всё — это аддон, то что делает Scratch Addons?

В двух словах, Scratch Addons — загрузчик аддонов. Его основные задачи:

- Позволять пользователям включать, выключать и настраивать аддоны.
- Запускать аддоны и давать им различные API.
- Предоставлять глобальное состояние аддонам (например, API addon.auth).
- Создавать прототипы для испольщования с помощью юзерскриптов для аддонов.
- Предоставлять способы, чтобы получить доступ к состоянию Redux и доступ к модифицированию состояния.
- Избегайте тех случаев, когда аддоны мешают друг другу.
- Избегайте скопированную работу из других аддонов.

### Scratch Addons безопасен?

Да. Scratch Addons не должен иметь любые проблемы с безопасностью в его самой новой версии. Scratch Addons — проект с открытым исходным кодом, поэтому код постоянно подтверждается внесёнными вклад в Scratch Addons, а также теми, кто пишет отзывы в магазине расширений Chrome и в дополнения для Firefox.

### Как я могу сказать о проблеме с безопасностью?

Если Вы как-то нашли проблему с безопасностью, пожалуйста, свяжитесь с World_Languages лично через электронную почту: `worldxlanguages@gmail.com`. Если Вы не получите ответ в течении 48 часов, пожалуйста, создайте проблему [здесь](https://github.com/ScratchAddons/ScratchAddons/issues/), с упоминанием того, что Вы отправили имейл.

Вы можете [прочитать нашу политику безопасности](https://github.com/ScratchAddons/ScratchAddons/security/policy) или [ознакомиться с нашими рекомендациями, которые мы опубликовали](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Будет ли мой аккаунт безопасен во время использования Scratch Addons?

Scratch Addons не использует учётные данные Вашего Scratch аккаунта, чтобы работать. На самом деле, если Вы выйдите из своего Scratch аккаунта, Scratch Addons будет всё равно работать. Scratch Addons будет только отправлять запросы на основах куки которые у Вас есть, который предоставляется браузером для каждого запроса, поэтому некоторые аддоны по типу Scratch Messaging не будут работать пока Вы входите, но это не затронет другие части расширения.

Аддоны на Scratch Addons также были редактированы некоторыми тех, кто внёс вклад на репозитории, так что никто не может просто засунуть вредоносный код под нашими глазами.

Мы никогда не отправляем информацию о аккаунте Scratch или настройки расширения вне Вашего браузера. См. [политику конфиденциальности расширения](/docs/privacy/policies/extension) для большей информации.

### Могу ли я говорить людям о Scratch Addons на Scratch?

Вы не можете, и, пожалуйста, не надо. Есть правило, которое запрещает рекламу браузерных расширений/юзерскриптов [здесь](https://scratch.mit.edu/discuss/post/2907564/). Правда, Вы можете использовать другие способы чтобы рассказать Вашим друзьям о Scratch Addons.

### Как я могу внести вклад в Scratch Addons?

Во-первых, спасибо за Ваш проявленный интерес. Мы ценим Ваш интерес и Ваши последующие вклады.

Как проект с открытым исходным кодом, мы приветствуем любых внёсшие вклад. Вам даже не надо спрашивать нас или иметь какой-либо ранг. Приветствуется любой желающий. Есть даже шанс, что Вы не осознаете, что помогли проекту!

Итак, вернёмся к делу. Вы можете помочь проекту разными способами, и некоторые из них очень лёгкие.

- **Помочь с кодом**

  Если Вы умеете программировать на JavaScript, HTML5 и CSS, то Вы можете внести вклад программированием. Вы можете исправить баги, заняться некоторыми запросами или сделать свой аддон.

  После этого, Вам нужно сделать pull запрос. Нужно раздвоить (fork) [репозиторию](https://github.com/ScratchAddons/ScratchAddons/), сделать нужные Ваши изменения и сделать pull запрос. Если Ваши изменения будут возможным, мы объединим их.

  Вы также можете внести вклад не только в расширение. Вы можете посмотреть наши репозитории в [странице нашей организации GitHub](https://github.com/ScratchAddons) и помочь нам их разрабатывать.

- **Предложить идею**  

  Есть что-то, что будет хорошим дополнением к Scratch Addons? [Скажите нам!](#i-think-you-missed-a-feature-what-can-i-do)

- **Пожаловаться на баг**

  Нашли баг в одном из наших аддонов, странице настроек или любое другое в нашем расширении? [Отправьте нам жалобу о баге](#what-can-i-do-if-i-find-a-problem).

- **Перевести Scratch Addons**  

  Если Вы можете разговаривать на другом языке, который не английский, Вы можете помочь с переводом Scratch Addons на Ваш язык. Вы можете начать [отсюда](/docs/localization/joining-the-localization-team).

- **Написать документацию**

  Вы знакомы с Scratch Addons? Если да, то Вы можете написать документацию для него. Документация может содержать как использовать это или как это работает. Пожалуйста, свяжитесь с нами в [вкладке обсуждений](https://github.com/ScratchAddons/ScratchAddons/discussions) для большей информации.

- **Отправить отзыв**

  Вы можете отправить отзыв на нашей форме, которая находиться в [странице обратной связи](https://scratchaddons.com/feedback). Ваши отзывы могут дать нам другой взгляд на разработку расширения и помочь нам понять, на что необходимо обратить внимание, и исправить ошибки.

- **Написать отзыв на магазинах расширений**

  Вы можете написать нам отзыв о Scratch Addons в [магазине расширений Chrome](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) или в [расширениях Firefox](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/).

- **Поставить звезду на нашей репозитории**

  В двух словах, звёздочка в GitHub похожа на звёздочку в Scratch. Вы можете это сделать, зайдя на [нашу репозиторию](https://github.com/ScratchAddons/ScratchAddons) и кликая кнопку «Star» в правом-верхнем углу.

- **Рассказать о Scratch Addons**

  Вы можете рассказать любым о Scratch Addons, например, Вашим друзьям, родственникам, членам семьи или даже Вашему учителю, если хотите. Только пожалуйста, [не делайте это на сайте Scratch](#can-i-tell-people-about-scratch-addons-on-scratch).

### Как я могу сделать свой аддон?

Прочитайте, как сделать аддон в Scratch Addons [здесь](/docs/develop/getting-started).

### Как я могу попасть в [странице тех, кто внёс вклад](/contributors)?

Пожалуйста, прочитайте и следуйте инструкции [этой проблемы (issue)](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}), чтобы попасть на ту страницу.

### Как я могу удалить своё имя с [страницы тех, кто внёс вклад](/contributors)?

Если Вы не хотите быть на той странице, скажите нам, создав проблему (issue) на [нашей репозитории внёсших вклад](https://github.com/ScratchAddons/contributors/issues/) или другими способами связи. Приносим извинения за причиненные неудобства.

### Что я могу сделать, если я найду проблему?

Вы можете сказать нам, используя одних из этих способов.

- Отправить его через [нашу форму обратной связи](https://scratchaddons.com/feedback).
- Создать проблему (issue) в [репозитории](https://github.com/ScratchAddons/ScratchAddons/issues).
- Создать пост в [нашей вкладке дискуссирования](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Сказать нам на [нашем Discord сервере](https://discord.gg/R5NBqwMjNc).

### Мне кажется, Вы пропустили особенность. Что я могу сделать?

Если Вы считаете, что какая-либо фича отсутствует, Вы хотите предложить аддон для расширения или у Вас есть хорошая идея, скажите нам [с помощью одних из этих способов](#what-can-i-do-if-i-find-a-problem).

### Где я могу обсуждать о Scratch Addons?

Вы можете это сделать на [нашей вкладке «Discussion»](https://github.com/ScratchAddons/ScratchAddons/discussions) или на [нашем Discord сервере](https://discord.gg/R5NBqwMjNc). Там Вы можете обсуждать это и спрашивать вопросы, если у Вас есть проблемы.

### Мне кажется, Scratch Addons замедляет Scratch. Что я могу сделать?

Попробуйте отключить аддоны, которые Вам не нужны. А также проверьте уведомления и предупреждения аддонов чтобы решить, какие аддоны должны быть выключены для повышения производительности.

### Как можно активировать пасхальные аддоны?

Чтобы показать пасхальные аддоны, введите код Конами (↑↑↓↓←→←→BA) клавиатурой на странице настроек. Затем пасхальные аддоны будут показаны, позволяя Вам активировать их.

Некоторые из наших пасхальных аддонов — «Аддон, который ничего не делает» («Исправить капитализацию слов "Настройки Учётной Записи"») и «Глюк точки с запятой». Вгляните на [вкладку аддонов](/addons) для полного списка.

### У меня есть ещё вопросы!

Если у Вас есть больше вопросов, Вы можете создать пост на [нашей вкладке «Disscusion»](https://github.com/ScratchAddons/ScratchAddons/discussions) или отправить сообщение [на нашем Discord сервере](https://discord.gg/R5NBqwMjNc). Кто-то попробует ответить на Ваш вопрос.
