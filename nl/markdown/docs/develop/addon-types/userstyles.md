---
title: Userstyles
description: Userstyles laten je CSS injecteren op de Scratch-website - handig om je knoppen uit userscripts kleurrijk te maken, of om natieve Scratch-elementen aan te passen.
---
## Wat zijn ze?
Userstyles laten je CSS injecteren op de Scratch-website - handig om je knoppen uit userscripts kleurrijk te maken, of om natieve Scratch-elementen aan te passen.

## Hoe voeg ik een userstyle toe?
**Make sure to refresh Scratch Addons from `chrome://extensions` after doing any changes to your addon.**  
Go to the manifest of your addon (addon.json) and add a property called `"userstyles"`.  
This property must be an array.  
Each item of the array must have the following properties: `"url"` and `"matches"`.  
`"url"` must be a relative URL to a CSS file.  
`"matches"` must be an array of URLs where you want the userstyle to be injected. You can use asterisks.
Example manifest:
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
      "url": "second_userstyles.css",
      "matches": ["https://scratch.mit.edu/projects/*", "https://scratch.mit.edu/users/*"]
    }
  ],
  "tags": ["community"],
  "enabled_by_default": false
}
```

## Debugging userstyles
**Make sure to refresh Scratch Addons from `chrome://extensions` after doing any changes to your addon.**  
If you don't see your userstyle working, make sure your addon is enabled.  
If you're still having trouble, please create an issue in this repo.
