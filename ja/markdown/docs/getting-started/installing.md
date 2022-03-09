---
title: インストール
---

## 拡張機能ストアから

Scratch Addonsは、Chrome Web StoreとAdd-ons for Firefoxの両方で入手可能です。

- Chrome Web Store (Google Chrome、Opera、Brave、Vivaldi、Microsoft Edge >79、その他のChromiumベースのブラウザー)
  https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco

- Add-ons for Firefox (Mozilla Firefox)
  https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/

- Microsoft Edge Add-ons (Microsoft Edge >79用)
  https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj

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

