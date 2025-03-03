---
---

**カスタマイズ可能なナビゲーションバー**は、ユーザーがScratchウェブサイトのナビゲーションバーのリンクを追加、変更、または削除できるようにするアドオンです。 また、ユーザーメニューを微調整し、ページスクロール時のナビゲーションバーの動作を変更できます。

## Background

Scratch removed the discuss button that linked to the forums in July 2017.[^1] The original addon was introduced to bring it back and included an option to remove the ideas link.

## 機能

- Add new links to Scratch pages or other websites.
- Re-order links and change their labels.
- Remove existing links.
- Prevent the navigation bar from scrolling with the page.
- Move the logged-in username out of the way.

## 設定

### Items

Controls the links displayed between the Scratch logo and search bar. Each item has the following inputs:

- Name: The link's label
- URL: The page to link to which can be relative to the home page (e.g. /mystuff) or absolute (e.g. https://example.com).

### コンパクトなユーザーメニュー

Moves the username of the logged-in user into the profile dropdown item.

### Stick to

- Top of screen: The navigation bar stays visible even when the page scrolls. This is Scratch's default behavior.
- Top of page: The navigation bar stays at the top of the page and scrolls away with it.

## クレジット

The original addon was written by WorldLanguages, and TheColaber was the author of the rewrite.

## 更新履歴

- **v1.0.0** The first version that added the discuss button and optionally removed ideas.
- **v1.24.0**: Made the links fully customizable.
- **v1.28.0**: Added the compact user dropdown setting.
- **v1.32.0**: Added the "stick to" setting.

## トリビア

- This is the first addon to modify the Scratch website.
- This is the first and only addon to use a table setting.
- This is one of the few addons to have no credits.

## Gallery

![コンパクトなユーザーメニュー](/assets/img/addons/docs/compact-nav-dropdown.png)

コンパクトなユーザーメニュー

## Related

- [Table setting pull request (#2875)](https://github.com/ScratchAddons/ScratchAddons/pull/2875)
- [カスタマイズ可能なエディターメニュー](https://scratch.mit.edu/scratch-addons-extension/settings#addon-custom-menu-bar)

[^1]: https://scratch.mit.edu/discuss/topic/269283/
