---
title: Perguntas Frequentes
description: Essa página contém perguntas frequentes relacionadas à extensão e projeto do Scratch Addons.
---

Essa página contém perguntas frequentes relacionadas à extensão e projeto do Scratch Addons.

### O que é o Scratch Addons?

O Scratch Addons é uma extensão de navegador "tudo-em-um" para o site e editor de projeto do Scratch. Ele adiciona funções e temas (chamados de addons) ambos para o site do Scratch e para o editor de projeto. A missão do Scratch Addons é combinar todas as extensões, userscripts e userstyles existentes para o Scratch, desenvolvidos por diversos membros da comunidade, em um único lugar de fácil acesso, e ainda deixar os usuários escolherem quais funções querem usar.

### O que exatamente é um "addon"?

Um addon é parecido com uma extensão ou userscript, mas usa APIs especiais da extensão do Scratch Addons. Essas APIs permitem que addons rodem scripts em uma página do Scratch (userscripts) ou mudem a aparência do site do Scratch (userstyles).

Userscripts podem utilizar as APIs JavaScript `addon.*`, que lhes permitem obter informações relacionadas ao Scratch (por exemplo, obter o usuário atual logado) e também utilizar APIs de extensão (como o envio de notificações).

### Se tudo é um addon, então o que o Scratch Addons faz?

Sozinho, o Scratch Addons é apenas um carregador de addons. Suas principais tarefas são:

- Permitir aos usuários ativar, desativar e configurar addons.
- Executar addons e fornecer APIs.
- Fornecer um estado global para addons (por exemplo, a API addon.auth).
- Fornecer protótipos que os addons userscript podem usar.
- Fornecer maneiras de acessar e modificar o estado Redux.
- Não deixar que addons interfiram uns com os outros.
- Evitar que addons diferentes façam o mesmo trabalho.

### O Scratch Addons é seguro?

Sim. A versão mais recente do Scratch Addons não deve ter nenhum problema de segurança. Scratch Addons é um projeto de código aberto, portanto o código está sendo constantemente verificado por colaboradores do Scratch Addons, bem como por revisores da Chrome Web Store e Add-ons for Firefox.

### Como posso reportar uma vulnerabilidade de segurança?

Se você encontrar uma vulnerabilidade de segurança, por favor, entre em contato com World_Languages em particular, enviando um e-mail para `worldxlanguages (arroba) gmail.com`. Se você não receber uma resposta dentro de 48 horas, por favor, crie um issue [aqui](https://github.com/ScratchAddons/ScratchAddons/issues/) mencionando que você enviou um e-mail.

Você pode [ler nossa política de segurança](https://github.com/ScratchAddons/ScratchAddons/security/policy), ou [verificar os conselhos que publicamos](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published).

### Minha conta estará segura se eu usar o Scratch Addons?

O Scratch Addons não usa as credenciais de sua conta para funcionar. Na verdade, você pode nem estar logado no Scratch, e o Scratch Addons ainda funcionará. O Scratch Addons só envia pedidos baseados nos cookies que você tem, que são fornecidos pelo navegador para cada pedido, portanto alguns addons como Mensagens do Scratch não funcionarão quando você estiver logando, mas não afetarão outras partes da extensão.

Addons do Scratch Addons também foram revisados por vários colaboradores no repositório, de modo que ninguém pode simplesmente passar código malicioso sem a gente perceber.

Nunca enviamos informações de contas do Scratch ou configurações da extensão para fora de seu navegador. Consulte [a política de privacidade da extensão](/docs/privacy/policies/extension) para mais informações.

### Posso falar do Scratch Addons no Scratch?

Você não pode, e por favor não fale. Existe uma política no Scratch que proíbe usuários de propagarem extensões/userscripts [aqui](https://scratch.mit.edu/discuss/post/2907564/). Você pode, porém, usar outros métodos para contar sobre o Scratch Addons pros seus amigos.

### Como posso contribuir com o Scratch Addons?

Primeiramente, obrigado por se interessar em contribuir com o Scratch Addons. Agradecemos seu interesse e suas próximas contribuições.

Como um projeto de código aberto, acolhemos qualquer tipo de contribuição. Você nem precisa nos pedir ou ser conhecido. Qualquer um é bem-vindo. Há até mesmo uma chance de que você nem perceba que contribuiu para o projeto!

Voltando ao ponto. Você pode contribuir de muitas maneiras, e algumas delas são super fáceis.

- **Contribuir com código**

  Se você sabe programar em JavaScript, HTML5 e CSS, você pode contribuir programando. Você pode corrigir bugs, resolver alguns pedidos, ou criar seu próprio addon.

  Depois disso, você precisa criar um pull request. Você pode fazer isso criando um fork do [repositório](https://github.com/ScratchAddons/ScratchAddons/), fazendo suas mudanças necessárias e criando um pull request. Se for viável, faremos o merge.

  Também estamos abertos para contribuições de outros aspectos que não a extensão. Você pode ver nossos repositórios na [nossa página de organização no GitHub] (https://github.com/ScratchAddons) e ajudar a desenvolvê-los.

- **Sugerir uma ideia**

  Tem alguma ideia que você acha que seria uma boa adição ao Scratch Addons? [Conte-nos!](#i-think-you-missed-a-feature-what-can-i-do)

- **Reportar um bug**

  Encontrou um bug em um de nossos addons, na página de configurações, ou qualquer outra coisa em nossa extensão? [Envie-nos um relatório de bug](#what-can-i-do-if-i-find-a-problem).

- **Traduzir o Scratch Addons**

  Se você fala inglês e outro idioma fluentemente, você pode ajudar a traduzir/localizar o Scratch Addons para seu idioma. Você pode começar [aqui](/docs/localization/joining-the-localization-team).

- **Escrever a documentação**

  Está familiarizado com o Scratch Addons? Se sim, você pode escrever a documentação. A documentação pode incluir informações sobre como usar a extensão, ou como ela funciona. Entre em contato conosco pela [nossa aba Discussão] (https://github.com/ScratchAddons/ScratchAddons/discussions) para mais informações.

- **Mandar feedback**

  Você pode enviar feedback em nosso formulário, que está na [página de feedback] (https://scratchaddons.com/feedback). Seu feedback pode nos dar uma perspectiva diferente no desenvolvimento da extensão e nos ajudar a saber que coisas precisam de atenção e que bugs corrigir.

- **Deixar uma resenha nas lojas**

  Você pode nos deixar uma resenha sobre o Scratch Addons na [página da extensão no Chrome](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) ou na [página do addon no Firefox](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/).

- **Deixar uma estrela no nosso repositório**

  Basicamente, o botão de estrela de GitHub é semelhante ao botão de estrela/favorito no Scratch. Você pode fazer isso indo até o [nosso repositório](https://github.com/ScratchAddons/ScratchAddons) e clicando no botão "Star" no canto superior direito.

- **Divulgar**

  Você pode falar sobre o Scratch Addons pra qualquer pessoa, como seus amigos, seus parentes, seus familiares ou até mesmo seu professor, se quiser. Só pedimos que você [não faça isso no site Scratch](#can-i-tell-people-about-scratch-addons-on-scratch).

### Como posso criar meu próprio addon?

Leia mais sobre como criar um addon no Scratch Addons [aqui](/docs/develop/getting-started).

### Como posso colocar o meu nome na [página de contribuidores](/contributors)?

Por favor leia e siga as instruções [nesse issue](https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}) para incluir seu nome na página.

### Como posso remover meu nome da [página de contribuidores](/contributors)?

Se você não quiser que seu nome esteja na página, por favor, nos diga criando um issue no [nosso repositório de colaboradores](https://github.com/ScratchAddons/contributors/issues/), ou por outros meios de contato. Pedimos desculpas pelo inconveniente.

### O que posso fazer se encontrar um problema?

Você pode nos contar usando um desses meios:

- Envie através de [nosso formulário de feedback](https://scratchaddons.com/feedback).
- Crie um issue no [repositório](https://github.com/ScratchAddons/ScratchAddons/issues).
- Crie uma postagem na [nossa aba Discussão](https://github.com/ScratchAddons/ScratchAddons/discussions).
- Conte-nos no [nosso servidor do Discord](https://discord.gg/R5NBqwMjNc).

### Acho que falta uma função na extensão. O que posso fazer?

Se você acha que falta uma função, ou se quiser sugerir uma adição à extensão, ou se tiver uma boa ideia, nos diga [através de um dos métodos mencionados acima](#what-can-i-do-if-i-find-a-problem).

### Onde posso falar sobre o Scratch Addons?

Você pode discutir na [nossa aba Discussão](https://github.com/ScratchAddons/ScratchAddons/discussions) ou no [nosso servidor do Discord](https://discord.gg/R5NBqwMjNc). Lá, você pode discutir e fazer perguntas se estiver tendo problemas.

### Acho que o Scratch Addons está deixando o Scratch mais lento. O que posso fazer?

Tente desligar os addons que você não precisa. Além disso, verifique os avisos de cada addon para decidir quais devem ser desligados para um melhor desempenho.

### Como ativo os addons secretos?

Para mostrar os easter eggs, faça o Konami Code (↑↑↓↓←→←→BA) no seu teclado na página de configurações. Assim, os addons secretos aparecerão, e você poderá ativá-los.

Alguns de nossos addons secretos são "Corrigir capitalização de Configurações de Conta" e "Glitch do ponto e vírgula". Confira [a aba de addons](/addons) para uma lista completa.

### Tenho mais perguntas!

Se você tiver mais perguntas que precisam de respostas, você pode criar uma postagem na [nossa aba Discussão](https://github.com/ScratchAddons/ScratchAddons/discussions) ou enviar uma mensagem no [nosso servidor do Discord](https://discord.gg/R5NBqwMjNc). Alguém tentará respondê-lo para você.
