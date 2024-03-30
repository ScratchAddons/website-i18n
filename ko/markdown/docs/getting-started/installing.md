---
title: 설치
---

## 스토어에서 확장 프로그램 설치하기

스크래치 애드온은 이 스토어들에서 설치할 수 있습니다.

| 스토어 | 설치 | 지원되는 브라우저 | 시스템 사양 |
| - | - | - | - |
| 크롬 웹 스토어 | [![크롬 웹 스토어에서 설치](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 96+<br />Microsoft Edge 96+<br />Opera 82+<br />Brave 1.33+<br />Vivaldi 5.0+<br />*Chromium 96+* | 윈도우 7+<br />OS X / 맥 OS 10.11+
| 파이어폭스 애드온 | [![파이어폭스 애드온에서 설치](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 109+ | 윈도우 7+<br />OS X / 맥 OS 10.12+
| 마이크로소프트 엣지 애드온 | [![마이크로소프트 애드온에서 설치](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 96+ | 윈도우 7+<br />OS X / 맥 OS 10.11+

## 소스로부터

### 깃허브 릴리즈에 대해

[릴리즈 페이지](https://github.com/ScratchAddons/ScratchAddons/releases)는 코드와 설치 파일을 포함한 스토어 빌드의 복사본인 스크래치 애드온 개발 빌드를 포함하고 있습니다.

### 레포지토리 복사하기

스크래치 애드온을 개발적인 목적으로 사용한다면 권장되는 방법입니다. 깃이 설치되어있음을 가정합니다.

저장소를 다운로드 받으려면, 단순히 `https://github.com/ScratchAddons/ScratchAddons.git` 를 복사하세요.

```sh
$ git clone https://github.com/ScratchAddons/ScratchAddons.git
```
스크래치 애드온을 업데이트하려면, 폴더 안으로 `cd`를 하고, 다음의 명령어를 실행하세요.

```sh
$ git fetch
$ git pull
```

This will update Scratch Addons and get it ready for code editing. Note that you will need to see the finish updating section [here](#install-on-google-chrome) if you are using Google Chrome.


### Downloading the zipball

If you don't have Git installed, you can try this method instead. Note that you will need to manually repeat this process every time you want to update Scratch Addons.

1. Go to the [repository](https://github.com/ScratchAddons/ScratchAddons) and find the download code button.

   ![Download code button screenshot](/assets/img/docs/download-code-button.png)

2. Click it and select "Download ZIP".

   ![Download ZIP button screenshot](/assets/img/docs/download-zipball-button.png)

3. Extract the archive into a folder.

### Installing on Google Chrome or Microsoft Edge

1. Type `chrome://extensions` into your address bar to open the Extension Management page.

2. Click the toggle next to `Developer mode` to turn on the Developer Mode. This allows you to install extensions from a folder or file.

   ![Extension Management top bar screenshot](/assets/img/docs/developer-mode-toggle.png)

3. You should see the `Load unpacked` button appear. Clicking it will allow you to select a folder to upload.

   ![Load unpacked button screenshot](/assets/img/docs/load-unpacked-button.png)

4. Select the extracted folder.
5. 확장 프로그램은 이제 실행될 겁니다.

To finish updating (assuming you followed the updating steps [here](#cloning-the-repository)), click the `Update` button:

![Update button screenshot](/assets/img/docs/update-button.png)


### 모질라 파이어폭스에 설치하기

1. Type `about:debugging` into your address bar to open the debugging page.

2. Click `This Firefox` on the left-hand menu.

   ![Left-hand menu screenshot](/assets/img/docs/left-hand-menu.png)

4. Click `Load Temporary Add-on...`.

   ![Load Temporary Add-on button screenshot](/assets/img/docs/load-addon.png)

6. Select the manifest.json file inside the extracted folder.
7. 확장 프로그램은 이제 실행될 겁니다.

Note: Firefox temporary add-ons are actually temporary. Restarting Firefox will remove them, so if you want to use the development version of Scratch Addons all the time, it is recommended that you use a Chromium-based browser like Google Chrome.

