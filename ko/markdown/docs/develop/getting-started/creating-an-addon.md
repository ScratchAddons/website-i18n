---
title: 애드온 만들기
---
Required software: text editor, Chrome.  
If possible, disable the Scratch Addons extension you downloaded from the store before proceeding to avoid issues.


{{< admonition info >}}
If you plan to submit the addon you are developing as a pull request to our GitHub repository, please read our [contributing guidelines](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md) first. 

In case there is no existing GitHub issue in that repository related to your new addon idea, please [create one](https://github.com/ScratchAddons/ScratchAddons/issues/new/choose). However, if there is already an issue related to your feature idea, we suggest that you leave a comment on it stating your intention to develop the addon. This will enable other contributors to provide feedback on whether the addon could be accepted, or if further discussion is required.

However, if you are creating an addon for personal use, you may proceed with this guide.
{{< /admonition >}}

## 1 단계: [애드온 기초](/docs/develop/getting-started/addon-basics/)를 읽으세요.
Make sure to read that article to be familiar with the terminology.

## Step 2: Fork/clone the [repo](https://github.com/ScratchAddons/ScratchAddons)
Follow [these instructions](/docs/getting-started/installing/#from-source) to download the source code locally.

## 3 단계: 스크래치 애드온을 크롬에서 여세요.
*Note: Chrome is recommended for working on addons. Nevertheless, addons are expected to work on Firefox and Edge.*  
Now that you have the extension in your filesystem, go to `chrome://extensions` and toggle "developer mode".  
Click "load unpacked", then select the folder where Scratch Addons is located. If you're having issues with this, make sure to be selecting the folder where `manifest.json` is located.  
That's it, you loaded the extension! It should look similar to this:  
![image](https://user-images.githubusercontent.com/17484114/91502527-accfd580-e89e-11ea-9e16-7daa2b808379.png)  
Note: you can safely ignore it says "errors". That's just a warning for an unrecognized manifest key that's required by Firefox.

## 4 단계: 애드온은 무엇에 관한 건가요?
Now comes the fun part!  
What will your addon do? Think of a self descriptive addon ID (no spaces or special characters, except hyphens).  
Got it?

## 5 단계: 애드온을 위한 폴더를 만드세요.
Using a file explorer, go to the folder where Scratch Addons resides in your filesystem. Locate the `addons` folder.  
Then, create a new folder with your epic addon ID as its name.

## 6 단계: 애드온 설명을 추가하세요.
The addon manifest tells Scratch Addons how your addon works. Make sure to get this right to avoid headaches.  
Inside the folder you just created, create an `addon.json` file.  
This is a base you can use to start coding, make sure to change it in the future:
```json
{
  "name": "Epic placeholder text in place of addon name",
  "description": "Hello World! It would be really smart to replace this placeholder text with a description.",
  "tags": ["community"],
  "enabledByDefault": false
}
```
For more information on what you can declare in the manifest, check [this article](/docs/reference/addon-manifest/).


## 7 단계: 스크래치 애드온에 애드온 ID를 넣으세요.
Scratch Addons can't find new folders by itself, so you have to add the name to a special file.  
Go to `scratchAddonsFolder/addons/addons.json` and add the ID of your addon to the array.

## 8 단계: Hello World
Your addon does nothing at the moment, so it's a good time to check if everything we made previously worked.  
Go to `chrome://extensions` and reload Scratch Addons by clicking the refresh symbol on its card.  
Now, right-click the Scratch Addons icon, and click "options".  
You should see your addon on the list! Once you find it, enable it, and set any settings that you may have.

## 9 단계: 재밌는 부분, 코딩!
*Before proceeding, make sure you read the wiki article linked in step 1.*  

Here comes the fun part: create your own JS or CSS files!  
Protip: after making any change to your addon, make sure to refresh the Scratch Addons extension like you did in step 8.  

Depending on what you want your addon to do, you should now check these wiki pages:
- [Userscripts](/docs/develop/userscripts)
- [Userstyles](/docs/develop/userstyles)

## 10 단계: 애드온을 커스터마이즈 가능하게 만드세요.
If you want, you can make your addon customizable!  
Users of your addon will be able to toggle settings, enter numbers, and more!  
To get started, see [how to declare settings in the addon manifest](/docs/reference/addon-manifest/#settings-object).  
Then, head to the [addon.settings documentation](/docs/reference/addon-api/addon.settings) to learn how to access user choices from userscripts.

## 11 단계: 애드온을 출시하기 전.
Now that your addon works, let's make sure we can add it to the addon library.  
Make sure your addon's manifest is suitable, [more info here](/docs/reference/addon-manifest). Keep close attention to the name, description and tags of your addon. Make sure to set `"enabledByDefault"` to `false` or remove it.  
Make sure your addon doesn't break other addons.  
Make sure your code is understandable; having unnecessary comments is better than no comments.

## 12 단계: Pull Request를 보내세요!
Follow the steps on our [contributing guidelines](https://github.com/ScratchAddons/ScratchAddons/blob/master/.github/CONTRIBUTING.md). Simply put, fork the repo if you haven't already, commit your new addon and send a PR!  
Keep in mind we might request you to make some changes, however, we will probably accept your addon as long as it's minimally suitable.
