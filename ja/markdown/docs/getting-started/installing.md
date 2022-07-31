---
title: インストール
---

## 拡張機能ストアから

Scratch Addons は次のストアで入手できます。

| ストア | インストール | 対応ブラウザー | システム要件 |
| - | - | - | - |
| Chrome Web Store | [![Chrome Web Storeでインストール](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 80+<br />Microsoft Edge 80+<br />Opera 67+<br />Brave 1.3+<br />Vivaldi 2.11+<br />*Chromium 80+* | Windows 7+<br />OS X / MacOS 10.11+<br /> ~6年以内に販売されたChromebook
| Add-ons for Firefox | [![Add-ons for Firefoxでインストール](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 86+ | Windows 7+<br />OS X / MacOS 10.12+
| Microsoft Edge Addons | [![Microsoft Edge Addonsでインストール](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 80+ | Windows 7+<br />OS X / MacOS 10.11+

## ソースコードから

### GitHubリリースについて

[リリースページ](https://github.com/ScratchAddons/ScratchAddons/releases) には、ストア版のミラーに加え、Scratch Addonsの開発版のコードとインストールファイルがあります。

### リポジトリのクローン

開発用にScratch Addonsをインストールするためには、この方法がおすすめです。Gitをインストールして、以下の手順に従ってください:

リポジトリをダウンロードするには、 `https://github.com/ScratchAddons/ScratchAddons.git` をクローンしてください。

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
Scratch Addonsを更新するには、フォルダー内に `cd` し、次のコマンドを実行してください:

```sh
$ git fetch
$ git pull
```

Scratch Addonsが更新され、コードの編集に適した状態になります。Google Chromeを使用している場合は、 [アップデートを完了させる](#install-on-google-chrome) ために追加の手順が必要です。


### Zip 形式でダウンロード

Gitをインストールしていない場合は、この方法が利用できます。この場合は、Scratch Addonsをアップデートする場合に手動で同じ作業を繰り返さないといけません。

1. [リポジトリ](https://github.com/ScratchAddons/ScratchAddons) にて、ダウンロードボタンを押します。

   ![ダウンロードボタンのスクリーンショット](/assets/img/docs/download-code-button.png)

2. クリックし、「Download ZIP」を選択します。

   ![Download ZIP ボタンのスクリーンショット](/assets/img/docs/download-zipball-button.png)

3. アーカイブをフォルダーに解凍します。

### Installing on Google Chrome or Microsoft Edge

1. アドレスバーに `chrome://extensions` と入力し、拡張機能管理ページを開きます。

2. `開発者モード` をトグルし、開発者モードを有効にします。有効にすると、フォルダーやファイルから拡張機能をインストールできるようになります。

   ![拡張機能管理ページのスクリーンショット](/assets/img/docs/developer-mode-toggle.png)

3. `Load unpacked` ボタンが表示されるので、クリックしてフォルダーを選択してください。

   ![Load unpacked ボタンのスクリーンショット](/assets/img/docs/load-unpacked-button.png)

4. 解凍したフォルダーを選択してください。
5. 拡張機能が読み込まれたはずです。

[クローンの更新後](#cloning-the-repository) アップデートを完了させるには、 `更新` ボタンを押してください。

![更新ボタンスクリーンショット](/assets/img/docs/update-button.png)


### Mozilla Firefox上でのインストール

1. アドレスバーに `about:debugging` と入力し、デバッグページを開きます。

2. 画面左の `This Firefox` を選択します。

   ![画面左のスクリーンショット](/assets/img/docs/left-hand-menu.png)

4. `Load Temporary Add-on...` をクリックします。

   ![Load Temporary Add-on ボタンのスクリーンショット](/assets/img/docs/load-addon.png)

6. 解凍したフォルダー内のmanifest.jsonファイルを選択します。
7. 拡張機能が読み込まれたはずです。

注意: Firefoxのアドオンは一時的に読み込まれただけなので、ブラウザー再起動後に削除されます。開発版のバージョンを常時使用する場合は、Google ChomeなどのChromiumベースのブラウザーの使用をおすすめします。

