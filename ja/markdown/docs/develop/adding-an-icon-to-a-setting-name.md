---
title: 設定名にアイコンを加える
---
[クラッシュを](https://github.com/ScratchAddons/ScratchAddons/pull/1529)[引き起こさずに](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54)設定名にアイコンを加えるには、

- ファイル名にハイフンは利用できない。
- `@アイコンファイル名.svg 設定名`と`addon.json`に書く。
- 存在しない場合は、`/images/icons/`に`アイコンファイル名.svg`を追加する。
- `/background/load-addon-manifests.js`を編集し、`アイコンファイル名Icon: "@アイコンファイル名.svg",`を追加する。
- Scratch 通知の設定では、`/addons/scratch-notifier/notifier.js`を編集する。