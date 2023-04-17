---
title: 翻譯插件
description: 翻譯插件很簡單。
---
翻譯插件很簡單

## 增加訊息
在 `addons-l10n/en/` 下，創建一個名為 `ADDONID.json` 的文件，其中 ADDONID 是插件的 ID（文件夾名稱）。在那裡寫下你想翻譯的信息：

```json
{
  "ADDONID/meow": "Meow",
  "ADDONID/cats": "{number, plural, one {1 cat} other {# cats}}",
  "ADDONID/eat": "I want to eat {food}!",
  "ADDONID/salmon": "salmon",
  "ADDONID/sardine": "sardine",
  "ADDONID/move-steps": {
    "string": "move {number} steps",
    "developer_comment": "Please translate this to match Scratch's official translation for the block."
  }
}
```

### 占位符
有時消息需要有動態產生的東西。例如，貓的數量或輸入。為了處理這個問題，你可以使用像 `{placeholderName}` 這樣的佔位符。佔位符名稱只能包含字母（無數字）。

### 複數
如果占位符是數字怎麼辦？ 我們可以使用複數形式，例如`{placeholderName,plural, one {when there is one thing} other {when there are # things}}`。 如果占位符為1，則顯示“當有一件事時”，否則顯示“當有（佔位符）事物時”。

### Developer comments

Transifex will display the developer comment when a translator has selected the specified string. These comments are usually used to ask for a particular translation of the string or to provide additional information for languages that do not differentiate between uppercase and lowercase characters.

## 使用翻譯
從以下內容更改用戶腳本的第一行：
```
導出缺少和不同步的函數 ({ 插件，控制台 }) {
```

至：
```
導出缺少和不同步的函數 ({ 插件，控制台，msg }) {
```

添加的 `msg` 是您用來獲取翻譯的功能。例如， `text = "Meow"` can now be `text = msg("meow")`. 省略插件 ID 和斜線省略。

### 占位符
您可以提供佔位符數值：
```函式積木
cat = msg("cats", {number: 1}) // shows "1 cat"
cats = msg("cats", {number: 3}) // shows "3 cats"
hungry = msg("eat", {food: "cod"}) // shows "I want to eat cod!"
```

您還可以“嵌入”消息：
```函式積木
hungry2 = msg("eat", {food: msg("salmon")}) // shows "I want to eat salmon!"
```

### 安全
如果您正在編寫原始 HTML，則應將 `msg` 替換為更安全的 `safeMsg` 版本。
