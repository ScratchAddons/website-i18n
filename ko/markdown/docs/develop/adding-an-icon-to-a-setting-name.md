---
title: 설정 이름에 아이콘 추가하기
---
To add an icon to a setting name without [causing](https://github.com/ScratchAddons/ScratchAddons/pull/1529) [crashes](https://github.com/ScratchAddons/ScratchAddons/commit/ead64b9da1434e7ed593c141cba7b02addd70a54),

- 아이콘 파일 이름이 붙임표를 (-) 포함하지 않게 확인하세요.
- `addon.json`에 `@(아이콘 파일 이름).svg 설정 이름`을 작성하세요.
- Add `ICONFILENAME.svg` at `/images/icons/` if missing
- Edit `/background/load-addon-manifests.js` to add `iconfilenameIcon: "@ICONFILENAME.svg",`
- Edit `/addons/scratch-notifier/notifier.js` for Scratch Notifier settings