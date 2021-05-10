---
title: Test Page 3
description: Test Page 3
weight: 2
---

```js
let darkTheme = false
let extensionStyledTheme = false
let toggle

const updateExtensionStyledTheme = () => {
    document.body.classList.toggle("extension-styled")
    extensionStyledTheme = !extensionStyledTheme
    localStorage.setItem("extensionStyledTheme", extensionStyledTheme)
}

const updateDarkTheme = (shiftPressed = false) => {
    document.body.classList.toggle("no-animation")

    if (shiftPressed || [...document.body.classList].indexOf(".extension-styled") + 1) {
        updateExtensionStyledTheme()
    } 

    document.body.classList.toggle("dark")
    setTimeout(() => document.body.classList.toggle("no-animation"), 200)
    darkTheme = !darkTheme
    localStorage.setItem("darkTheme", darkTheme)
}
    
if (localStorage.getItem("extensionStyledTheme") === "true") {
    updateExtensionStyledTheme()
} else {
    localStorage.setItem("extensionStyledTheme", false)
}

if (localStorage.getItem("darkTheme") === "true") {
    updateDarkTheme()
} else {
    localStorage.setItem("darkTheme", false)
}

document.body.dataset.themeLoaded = true
    
waitForElement("#dark-toggle").then(() => {

    toggle = document.querySelector("#dark-toggle")
    
    if (darkTheme) {
        toggle.innerHTML = '<span class="iconify" data-icon="fa-solid:sun" data-inline="false"></span>'
    } else {
        toggle.innerHTML = '<span class="iconify" data-icon="fa-solid:moon" data-inline="false"></span>'
    }

    toggle.addEventListener("click", event => {
        if (event && event.shiftKey) updateExtensionStyledTheme()
        updateDarkTheme()
            if (darkTheme) {
                toggle.innerHTML = '<span class="iconify" data-icon="fa-solid:sun" data-inline="false"></span>'
            } else {
                toggle.innerHTML = '<span class="iconify" data-icon="fa-solid:moon" data-inline="false"></span>'
            }
    })
        
})
```

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.0",
  "author": {
    "name": "USER",
    "id": "ID"
  },
  "contributors": [{
    "name": "USER",
    "id": "ID"
  }],
  "service": "SERVICE",
  "altnames": ["SERVICE"],
  "description": {
    "en": "DESCRIPTION"
  },
  "url": "URL",
  "version": "VERSION",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#HEX000",
  "tags": ["TAG1", "TAG2"],
  "category": "CATEGORY",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "iframe": false,
  "settings": [
        {
            "id": "ID",
            "title": "DISPLAY TITLE",
            "icon": "FONTAWESOME FREE ICON",
            "value": true
        },
        {
            "id": "ID",
            "if": {
                "ID": true
            },
            "title": "DISPLAY TITLE",
            "icon": "FONTAWESOME FREE ICON",
            "value": "\"%song%\" by %artist%",
            "placeholder": "use %song% or %artist%"
        },
        {
            "id": "ID",
            "title": "DISPLAY TITLE",
            "icon": "FONTAWESOME FREE ICON",
            "value": 0,
            "values": ["1", "2", "etc."]
        }
    ]
}
```

```md
# Heading 1

Hello world!

## Explanation

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque ut vehicula ipsum. Suspendisse ultricies enim ut lorem pharetra, sed faucibus leo porttitor. Phasellus vel enim non orci vulputate mattis. Aenean diam nisi, fringilla et purus sed, ornare feugiat orci. Integer aliquet interdum nibh sit amet euismod. Donec ornare, nibh ut viverra fringilla, elit massa malesuada quam, sed scelerisque erat ante vitae lacus. Curabitur iaculis hendrerit sem, lobortis posuere enim feugiat rutrum. Sed vel augue faucibus, luctus mauris id, molestie tellus. 
```

```py
import random
min = 1
max = 6

roll_again = "yes"

while roll_again == "yes" or roll_again == "y":
    print "Rolling the dices..."
    print "The values are...."
    print random.randint(min, max)
    print random.randint(min, max)

    roll_again = raw_input("Roll the dices again?")
```