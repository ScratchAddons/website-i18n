---
title: ユーザースタイル
description: ユーザースタイルは、ScratchウェブサイトにCSSを挿入するのに利用できます。たとえば、ユーザースクリプトで追加したボタンのスタイルを変更したり、Scratchそのものをカスタマイズするのに使えます。
---

ユーザースタイルは、ScratchウェブサイトにCSSを挿入するのに利用できます。たとえば、ユーザースクリプトで追加したボタンのスタイルを変更したり、Scratchそのものをカスタマイズするのに使えます。

## ユーザースタイルの追加方法
**アドオンへの変更後はScratch Addonsを `chrome://extensions` から再読み込みしてください。**
アドオン・マニフェスト(addon.json)にて `userstyles` プロパティを追加してください。
これは配列でないといけません。
各項目には `url` と `matches` プロパティが必要です。
`url` はCSSファイルへの相対URLです。
`matches` はユーザースタイルを挿入するURLの配列です。アスタリスクが使用できます。
例:
```json
{
"name": "Scratch Messaging",
"description": "Provides easy reading and replying to your Scratch messages.",
"userstyles": [
{
"url": "userstyle.css",
"matches": ["https://scratch.mit.edu/*"]
},
{
"url": "second_userstyle.css",
"matches": ["https://scratch.mit.edu/projects/*", "https://scratch.mit.edu/users/*"]
}
],
"tags": ["community"],
"enabledByDefault": false
}
```

## ユーザースタイルのデバッグ
**アドオンへの変更後はScratch Addonsを `chrome://extensions` から再読み込みしてください。**
ユーザースタイルが動かない場合は、アドオンが有効化されているかまず確認し、それでも問題があるならこのリポジトリにて報告してください。
