---
title: インストール
---

## 拡張機能ストアから

Scratch Addons は次のストアで入手できます。

| ストア | インストール | 対応ブラウザー | システム要件 |
| - | - | - | - |
| Chrome Web Store | [![Chrome Web Storeでインストール](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 96+<br />Microsoft Edge 96+<br />Opera 82+<br />Brave 1.33+<br />Vivaldi 5.0+<br />*Chromium 96+* | Windows 7+<br />OS X / MacOS 10.11+
| Add-ons for Firefox | [![Add-ons for Firefoxでインストール](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 109+ | Windows 7+<br />OS X / MacOS 10.12+
| Microsoft Edge Add-ons | [![Microsoft Edge Addonsでインストール](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 96+ | Windows 7+<br />OS X / MacOS 10.11+

## ソースコードから

{{< admonition info >}}
Unlike the store releases, installing from source requires a browser based on Chromium 121+ or Firefox 121+.
{{< /admonition >}}

### GitHubリリースについて

[リリースページ](https://github.com/ScratchAddons/ScratchAddons/releases) には、ストア版のミラーに加え、Scratch Addonsの開発版のコードとインストールファイルがあります。

### リポジトリのクローン

This is the recommended way to install Scratch Addons for development purposes, assuming you have Git installed.

If you plan on contributing, fork the repository on GitHub first and then clone the fork, replacing `<username>` with your Github username.

```sh
$ git clone https://github.com/<username>/ScratchAddons.git
```
Scratch Addonsを更新するには、フォルダー内に `cd` し、次のコマンドを実行してください:

```sh
$ git fetch
$ git pull
```

Remember to also update Scratch Addons from the browser.


### Downloading the Zip

{{< admonition warning >}}
  This method is not recommended for development unless Git cannot be installed on the system since it will need to be manually repeated every time you update Scratch Addons.
{{< /admonition >}}

If you don not have Git installed, use this method instead.

1. [リポジトリ](https://github.com/ScratchAddons/ScratchAddons) にて、ダウンロードボタンを押します。

1. クリックし、「Download ZIP」を選択します。

1. アーカイブをフォルダーに解凍します。

### Google ChromeやMicrosoft Edge上でのインストール

To load the extension into Google Chrome and most Chromium-based browsers such as Microsoft Edge, Opera, Brave or Vivaldi:

1. Go to [chrome://extensions](chrome://extensions)

1. Turn on "Developer mode" in the top-right corner

1. Click "Load unpacked" and select the `ScratchAddons` folder.

To update the extension when testing, click the refresh icon on the extension's card.

{{< admonition info >}}
  The "Unrecognized manifest key" warnings may safely be ignored, since they are required by Firefox.
{{< /admonition >}}


### Mozilla Firefox上でのインストール

To load the extension into Mozilla Firefox:

{{< admonition info >}}
  Addons loaded into Firefox this way are temporary and must be reloaded every time the browser is restarted. Because of this Chrome is recommended for development, but everything is still expected to work on Firefox.
{{< /admonition >}}

1. Go to [about:debugging](about:debugging)

1. Click "This Firefox" on the sidebar

1. Click "Load Temporary Add-on..."

1. Select the `manifest.json` file in the `ScratchAddons` folder.

1. If a permission tab opens, click the "Enable" button.

To reload the extension when testing, click the "Reload" button on the extension's card.

{{< admonition info >}}
  The unexpected WebExtension manifest property warnings may safely be ignored, since they are required by Chrome.
{{< /admonition >}}

