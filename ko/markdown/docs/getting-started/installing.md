---
title: 설치하기
---

## 확장 프로그램 스토어에서

스크래치 애드온은 크롬 웹 스토어와 파이어폭스 애드온에서 사용하실 수 있습니다.

- 크롬 웹 스토어 (구글 크롬, 오페라, 브레이브, 비발디, 마이크로소프트 엣지 (>79), 그 외 크로미움 기반 브라우저들 지원)
  https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco
- 파이어폭스 애드온 (모질라 파이어폭스 지원)
  https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/


## 소스로부터

### 깃허브 릴리즈에 대해

[릴리즈 페이지]
(https://github.com/ScratchAddons/ScratchAddons/releases)
코드와 설치 파일을 포함한 스토어 빌드의 복사본인 스크래치 애드온 개발 빌드입니다.

### 레포지토리 복사하기

스크래치 애드온을 개발적인 목적으로 사용한다면 권장되는 방법입니다. 깃이 설치되어있음을 가정합니다.

레포지토리를 다운받으려면, 단순히 `https://github.com/ScratchAddons/ScratchAddons.git`을 복사하세요.

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

### Installing on Google Chrome

1. Type `chrome://extensions` into your address bar to open the Extension Management page.

2. Click the toggle next to `Developer mode` to turn on the Developer Mode. This allows you to install extensions from a folder or file.

   ![Extension Managment top bar screenshot](/assets/img/docs/developer-mode-toggle.png)

3. You should see the `Load unpacked` button appear. Clicking it will allow you to select a folder to upload.

   ![Load unpacked button screenshot](/assets/img/docs/load-unpacked-button.png)

4. Select the extracted folder.
5. The extension should now be loaded.

To finish updating (assuming you followed the updating steps [here](#cloning-the-repository)), click the `Update` button:

![Update button screenshot](/assets/img/docs/update-button.png)


### Installing on Mozilla Firefox

1. Type `about:debugging` into your address bar to open the debugging page.

2. Click `This Firefox` on the left-hand menu.

   ![Left-hand menu screenshot](/assets/img/docs/left-hand-menu.png)

4. Click `Load Temporary Add-on...`.

   ![Load Temporary Add-on button screenshot](/assets/img/docs/load-addon.png)

6. Select the manifest.json file inside the extracted folder.
7. The extension should now be loaded.

Note: Firefox temporary add-ons are actually temporary. Restarting Firefox will remove them, so if you want to use the development version of Scratch Addons all the time, it is recommended that you use a Chromium-based browser like Google Chrome.

