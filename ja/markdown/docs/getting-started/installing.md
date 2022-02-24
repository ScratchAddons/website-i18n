---
title: インストール
---

## 拡張機能ストアから

Scratch Addonsは、Chrome Web StoreとAdd-ons for Firefoxの両方で入手可能です。

- Chrome Web Store (Google Chrome、Opera、Brave、Vivaldi、Microsoft Edge (>79)、その他のChromiumベースのブラウザー)
  https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco
- Add-ons for Firefox (Mozilla Firefox)
  https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/


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

### Google Chrome上でのインストール

1. アドレスバーに `chrome://extensions` と入力し、拡張機能管理ページを開きます。

2. `開発者モード` をトグルし、開発者モードを有効にします。有効にすると、フォルダーやファイルから拡張機能をインストールできるようになります。

   ![Extension Managment top bar screenshot](/assets/img/docs/developer-mode-toggle.png)

3. You should see the `Load unpacked` button appear. Clicking it will allow you to select a folder to upload.

   ![Load unpacked button screenshot](/assets/img/docs/load-unpacked-button.png)

4. Select the extracted folder.
5. The extension should now be loaded.

To finish updating (assuming you followed the updating steps [here](#cloning-the-repository)), click the `Update` button:

![Update button screenshot](/assets/img/docs/update-button.png)


### Installing on Mozilla Firefox

1. Type `about:debugging` into your address bar to open the debugging page.

2. Click `This Firefox` on the left-hand menu.

   ![Left-hand menu screenshot](/assets/img/docs/left-hand-menu.png)

4. Click `Load Temporary Add-on...`.

   ![Load Temporary Add-on button screenshot](/assets/img/docs/load-addon.png)

6. Select the manifest.json file inside the extracted folder.
7. The extension should now be loaded.

Note: Firefox temporary add-ons are actually temporary. Restarting Firefox will remove them, so if you want to use the development version of Scratch Addons all the time, it is recommended that you use a Chromium-based browser like Google Chrome.

