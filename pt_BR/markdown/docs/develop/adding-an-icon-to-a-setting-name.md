---
title: Adicionando um Ícone a uma Opção
---
Para adicionar um ícone ao nome de uma opção sem [causar](https://github.com/ScratchAddons/ScratchAddons/pull/1529) [crashes](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54),

- Verifique se o nome do arquivo do ícone não contém hifens
- Digite `@ARQUIVODOICONE.svg nome da opção` em `addon.json`
- Adicione o arquivo `ARQUIVODOICONE.svg` à pasta `/images/icons/` se ele já não estiver lá
- Edite `/background/load-addon-manifests.js` e adicione `iconfilenameIcon: "@ARQUIVODOICONE.svg",`
- Edite `/addons/scratch-notifier/background.js` para mudar as opções do Notificador do Scratch (Scratch Notifier)