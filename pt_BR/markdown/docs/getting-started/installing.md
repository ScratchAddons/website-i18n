---
title: Como instalar
---

## Usando lojas de extensão

Scratch Addons is available in these stores.

| Store | Instalar | Supported browsers | Requisitos do sistema |
| - | - | - | - |
| Chrome Web Store | [![Install for Chrome Web Store](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 96+<br />Microsoft Edge 96+<br />Opera 82+<br />Brave 1.33+<br />Vivaldi 5.0+<br />*Chromium 96+* | Windows 7+<br />OS X / MacOS 10.11+
| Add-ons for Firefox | [![Install for Add-ons for Firefox](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 109+ | Windows 7+<br />OS X / MacOS 10.12+
| Microsoft Edge Add-ons | [![Install for Microsoft Edge Addons](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 96+ | Windows 7+<br />OS X / MacOS 10.11+

## Usando o código fonte

### Sobre releases do GitHub

[A página de releases](https://github.com/ScratchAddons/ScratchAddons/releases) contém o código e arquivos de instalação para todas as versões em desenvolvimento do Scratch Addons, além de uma cópia dos arquivos nas lojas de extensão.

### Clonando o repositório

Esse é o jeito recomendado de instalar o Scratch Addons para desenvolvimento. Você precisa ter o Git instalado.

Para baixar o repositório, apenas clone `https://github.com/ScratchAddons/ScratchAddons.git`.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Para atualizar o Scratch Addons, primeiro entre em sua pasta usando `cd` e rode os comandos a seguir.

```sh
$ git fetch
$ git pull
```

Isso atualizará o Scratch Addons e ele estará pronto para edição. Se você estiver usando o Google Chrome, você precisará ver [esta seção](#install-on-google-chrome) para terminar a atualização.


### Baixando o zipball

Se você não tem Git instalado, você pode tentar desse jeito. Note que você precisará repetir esse processo manualmente toda vez que quiser atualizar o Scratch Addons.

1. Vá para o [repositório](https://github.com/ScratchAddons/ScratchAddons) e procure pelo botão de baixar o código.

   ![Print do botão de baixar o código](/assets/img/docs/download-code-button.png)

2. Clique nele e selecione "Download ZIP".

   ![Print do botão download ZIP](/assets/img/docs/download-zipball-button.png)

3. Extraia os arquivos.

### Installing on Google Chrome or Microsoft Edge

1. Digite `chrome://extensions` na barra de endereço para abrir a página de Extensões.

2. Clique no botão `Modo do desenvolvedor` para ligar o Modo de Desenvolvedor. Isso te deixa instalar extensões a partir de uma pasta ou arquivo.

   ![Extension Management top bar screenshot](/assets/img/docs/developer-mode-toggle.png)

3. Vai aparecer um botão escrito `Carregar sem compactação`. Clique nele para selecionar uma pasta para carregar.

   ![Print do botão de carregar sem compactação](/assets/img/docs/load-unpacked-button.png)

4. Selecione a pasta extraída.
5. A extensão será carregada.

Para terminar de atualizar (se você já tiver seguido os passos [aqui](#cloning-the-repository)), clique no botão de `Atualizar`:

![Print do botão de atualizar](/assets/img/docs/update-button.png)


### Instalando no Mozilla Firefox

1. Digite `about:debugging` na barra de endereço para abrir a página de debug.

2. Clique em `Este Firefox` no menu da esquerda.

   ![Print do menu da esquerda](/assets/img/docs/left-hand-menu.png)

4. Clique em `Carregar Add-on Temporário...`.

   ![Print do botão Carregar Add-on Temporário](/assets/img/docs/load-addon.png)

6. Selecione o arquivo manifest.json dentro da pasta extraída.
7. A extensão será carregada.

Nota: Add-ons temporários no Firefox são temporários mesmo. Se você reiniciar o Firefox eles serão removidos, então se você quiser usar uma versão de desenvolvimento do Scratch Addons o tempo todo, é recomendado que você use um navegador baseado em Chromium como o Google Chrome.

