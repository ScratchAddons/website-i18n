---
title: 將圖示添加到設置名稱
---
要將圖示添加到設置名稱而不  [導致]
(https://github.com/ScratchAddons/ScratchAddons/pull/1529)  [損壞]
(https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54)

- 確認圖示文件名不包含連字符號
- 在 `addon.json` 上輸入 `@ICONFILENAME.svg 設置名稱`
- 如果缺少，請在 `/images/icons/` 添加 `ICONFILENAME.svg`
- 編輯`/背景/下載插件清單.js`以添加`圖標文件名圖標：“@ICONFILENAME.svg”，`
- 為 Scratch Notifier 設置編輯`/插件/scratch通知/通知.js`