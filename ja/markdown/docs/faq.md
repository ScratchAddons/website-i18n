---
title: よくある質問
description: Scratch Addonsに関するよくある質問を掲載します。
---

Scratch Addonsに関するよくある質問を掲載します。

### Scratch Addonsとは?

Scratch Addonsは、Scratchウェブサイトとプロジェクトエディターの新機能やテーマを提供するブラウザー拡張機能です。Scratchコミュニティーのメンバーにて開発されたユーザースクリプトやユーザースタイルを収集し、アドオンとして利用できるようにしています。アドオンは各自に有効化できます。

### アドオンとは?

アドオンは拡張機能のようなものですが、Scratch AddonsのAPIを利用できます。このAPIによって、Scratchページ上でスクリプトを実行したり、Scratchウェブサイトの外観を変えることができます。

こうしたスクリプトは`addon.*`JavaScript APIを使って、Scratchに関連する情報(たとえば、現在ログイン中のユーザー名)を入手したり、通知の送信など拡張機能のAPIを利用できます。

### もしすべてがアドオンなら、Scratch Addonsの役目は何ですか?

Scratch Addonsはアドオンを読み込みます。たとえば:

- アドオンを個別に有効化したり、設定を変更したりする。
- アドオンにAPIを提供し、実行する。
- addon.auth APIなど、データを提供する。
- スクリプトの実行用にコードを挿入する。
- Reduxへのアクセスを提供する。
- アドオン間の干渉を防ぐ。
- アドオン間でのコードの重複を防ぐ。

### Scratch Addonsは安全ですか?

Yes. Scratch Addons should not have any security issues in its most recent version. Scratch Addons is an open source project, so the code is constantly being verified by Scratch Addons contributors, as well as by reviewers from the Chrome Web Store, Add-ons for Firefox and Microsoft Edge Add-ons.

### どうやって脆弱性を報告できますか?

脆弱性情報は、World_Languages氏に直接連絡してください。メールアドレスは`worldxlanguages (at) gmail.com`です。48時間以内に回答がない場合は、[ここ](https://github.com/ScratchAddons/ScratchAddons/issues/)にてIssueを作成してください。そのときは、メールを送信したことを述べてください。

[セキュリティー方針](https://github.com/ScratchAddons/ScratchAddons/security/policy)と[過去に発見された脆弱性情報](https://github.com/ScratchAddons/ScratchAddons/security/advisories?state=published)は各ウェブサイトで確認できます。

### Scratch Addonsを使っても、アカウントは安全ですか?

Scratch Addonsの基礎は、アカウントの認証情報を必要しません。そのため、多くの機能は、ログアウト時でも動作します。Scratch Addonsは、ブラウザーから提供されるクッキーを用いて認証します。Scratchメッセージのようなアドオンはログアウト時は動作しませんが、それ以外の部分は問題ありません。

Scratch Addonsのコードはすべて複数の貢献者によりチェックされているため、ウイルスなどを隠すことはできません。

Scratchのアカウント情報や拡張機能設定は、ブラウザー内にとどまります。詳細は[プライバシーポリシー](/docs/privacy/policies/extension)を参照してください。

### Scratch Addonsについて、Scratch上で言及していいですか?

できません - しないでください。[方針](https://scratch.mit.edu/discuss/post/2907564/)により、拡張機能等の宣伝は禁止されています。ただし、Scratch外であれば、問題はありません。

### どうやってScratch Addonsに貢献できますか?

Scratch Addonsへの貢献を考えてくれて、ありがとございます。

オープンソースプロジェクトとして、どのような貢献も歓迎します。特別な役職は必要ありません。だれでも参加できます。

以下のような方法があります:

- **コードを貢献する**

  JavaScript、HTML5、CSSの知識がある場合は、コーディングで貢献できます。バグを修正したり、機能追加の要請にこたえたり、自分のアドオンを作れます。

  [リポジトリ](https://github.com/ScratchAddons/ScratchAddons/)をフォークした後は、変更をし、プルリクエストを送信できます。その後開発者たちがマージします。

  拡張機能以外への貢献も大歓迎です。[GitHub ページ](https://github.com/ScratchAddons)でリポジトリの一覧を確認できます。

- **提案する**

  Scratch Addonsにほしい機能がありますか? [提案してみましょう!](#i-think-you-missed-a-feature-what-can-i-do)

- **バグを報告する**

  アドオンや設定ページなど、拡張機能に問題がある場合は、[バグレポートを送信できます](#what-can-i-do-if-i-find-a-problem)。

- **翻訳する**

  英語以外の言語を話す場合は、Scratch Addonの翻訳に協力できます。なお、日本語の翻訳者は受け付けていません。[詳細](/docs/localization/joining-the-localization-team)を確認できます。

- **説明文書を書く**

  Scratch Addonsに詳しい場合は、使用方法、動作などを含む説明文書を書くこともできます。詳細について気になる場合は、[Discussion ページ](https://github.com/ScratchAddons/ScratchAddons/discussions)にて連絡してください。

- **感想を送る**

  [フィードバックフォーム](https://scratchaddons.com/feedback)から、感想や意見を送れます。これらの意見は、拡張機能の開発に役立ちます。

- **ストアでレビューする**

  You can leave us a review about Scratch Addons on [the Chrome extension page](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco), [the Firefox addon page](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) or the [Microsoft Edge addon page](https://microsoftedge.microsoft.com/addons/detail/scratch-addons/iliepgjnemckemgnledoipfiilhajdjj).

- **リポジトリにスターをつける**

  [リポジトリ](https://github.com/ScratchAddons/ScratchAddons)にて、Starボタンを押してスターをつけられます。

- **拡散する**

  Scratch Addonsを友人などに広めてください。ただし、[Scratch ウェブサイト上ではしないでください](#can-i-tell-people-about-scratch-addons-on-scratch)。

### どうやってアドオンを作れますか?

[アドオンの作り方](/docs/develop/getting-started)に関しては、別のページにて記載されています。

### どうやって[貢献者ページ](/contributors)に名前を掲載できますか?

[このIssue]((https://github.com/ScratchAddons/contributors/issues/{{< specifics/contributors-issue >}}))を読んで、説明に従ってください。

### どうやって[貢献者ページ](/contributors)から名前を削除できますか?

貢献者ページに名前を掲載されたくない場合は、[貢献者ページのリポジトリ](https://github.com/ScratchAddons/contributors/issues/)にIssueを作成するか、その他の方法で連絡してください。

### 問題を見つけた場合はどうすればいいですか?

以下の方法で連絡できます:

- [フィードバックフォーム](https://scratchaddons.com/feedback)から送る。
- [リポジトリ](https://github.com/ScratchAddons/ScratchAddons/issues)にてIssueを作成する。
- [Discussion ページ](https://github.com/ScratchAddons/ScratchAddons/discussions)にて投稿する。
- [Discord サーバー](https://discord.gg/R5NBqwMjNc)にて投稿する。

### 機能を追加してほしいです。どうすればいいですか?

機能を提案したい場合は、[上に挙げた方法で連絡できます](#what-can-i-do-if-i-find-a-problem)。

### Scratch Addonsに関して議論できる場所はありますか?

[Discussion ページ](https://github.com/ScratchAddons/ScratchAddons/discussions)や[Discord サーバー](https://discord.gg/R5NBqwMjNc)にて行えます。Scratch Addonsに関して話したり、質問ができます。

### Scratch Addonsが重いです。どうすればいいですか?

不要なアドオンを無効にしてみてください。また、アドオン設定の注意書きにて、パフォーマンスに影響を及ぼすアドオンを確認できます。

### イースターエッグはありますか?

はい。イースターエッグを表示するには、設定ページにて「コナミコマンド」(↑↑↓↓←→←→BA)を入力してください。その後、イースターエッグのアドオンが表示されます。

イースターエッグのアドオンには「何もしないアドオン」や「セミコロンのバグ」があります。詳細は[アドオンページ](/addons)を確認してください。

### 他にも質問があります!

質問がある場合は、[Discussion ページ](https://github.com/ScratchAddons/ScratchAddons/discussions)や[Discord サーバー](https://discord.gg/R5NBqwMjNc)にて投稿できます。
