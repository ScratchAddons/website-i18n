---
title: 설치
---

## 스토어에서 확장 프로그램 설치하기

스크래치 애드온은 이 스토어들에서 설치할 수 있습니다.

[![Chrome Web Store](https://raw.githubusercontent.com/ScratchAddons/ScratchAddons/master/.github/readme-images/cws-badge.png)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco)
[![Firefox Add-ons](https://raw.githubusercontent.com/ScratchAddons/ScratchAddons/master/.github/readme-images/ff-addon-badge.png)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/)

| 스토어 | 설치 | 지원되는 브라우저 | 시스템 사양 |
| - | - | - | - |
| 크롬 웹 스토어 | [![크롬 웹 스토어에서 설치](https://img.shields.io/chrome-web-store/v/fbeffbjdlemaoicjdapfpikkikjoneco?style=flat-square&logo=google-chrome&logoColor=white&label=install&color=4285F4)](https://chrome.google.com/webstore/detail/fbeffbjdlemaoicjdapfpikkikjoneco) | Google Chrome 96+<br />Microsoft Edge 96+<br />Opera 82+<br />Brave 1.33+<br />Vivaldi 5.0+<br />*Chromium 96+* | 윈도우 7+<br />OS X / 맥 OS 10.11+
| 파이어폭스 애드온 | [![파이어폭스 애드온에서 설치](https://img.shields.io/amo/v/scratch-messaging-extension?style=flat-square&logo=firefox-browser&logoColor=white&label=install&color=FF7139)](https://addons.mozilla.org/firefox/addon/scratch-messaging-extension/) | Mozilla Firefox 109+ | 윈도우 7+<br />OS X / 맥 OS 10.12+
| 마이크로소프트 엣지 애드온 | [![마이크로소프트 애드온에서 설치](https://img.shields.io/badge/dynamic/json?style=flat-square&logo=microsoftedge&logoColor=white&label=install&color=0078D7&prefix=v&query=%24.version&url=https%3A%2F%2Fmicrosoftedge.microsoft.com%2Faddons%2Fgetproductdetailsbycrxid%2Filiepgjnemckemgnledoipfiilhajdjj)](https://microsoftedge.microsoft.com/addons/detail/iliepgjnemckemgnledoipfiilhajdjj) | Microsoft Edge 96+ | 윈도우 7+<br />OS X / 맥 OS 10.11+

## 소스로부터

{{< admonition info >}}
Unlike the store releases, installing from source requires a browser based on Chromium 121+ or Firefox 121+.
{{< /admonition >}}

### 깃허브 릴리즈에 대해

[릴리즈 페이지](https://github.com/ScratchAddons/ScratchAddons/releases)는 코드와 설치 파일을 포함한 스토어 빌드의 복사본인 스크래치 애드온 개발 빌드를 포함하고 있습니다.

### 레포지토리 복사하기

This is the recommended way to install Scratch Addons for development purposes, assuming you have Git installed.

If you plan on contributing, fork the repository on GitHub first and then clone the fork, replacing `<username>` with your Github username.

```sh
$ git clone https://github.com/<username>/ScratchAddons.git
```
스크래치 애드온을 업데이트하려면, 폴더 안으로 `cd`를 하고, 다음의 명령어를 실행하세요.

```sh
$ git fetch
$ git pull
```

Remember to also update Scratch Addons from the browser.


### Downloading the Zip

{{< admonition warning >}}
  This method is not recommended for development unless Git cannot be installed on the system since it will need to be manually repeated every time you update Scratch Addons.
{{< /admonition >}}

If you don not have Git installed, use this method instead.

1. Go to the [repository](https://github.com/ScratchAddons/ScratchAddons) and find the download code button.

1. Click it and select "Download ZIP".

1. Extract the archive into a folder.

### Installing on Google Chrome or Microsoft Edge

To load the extension into Google Chrome and most Chromium-based browsers such as Microsoft Edge, Opera, Brave or Vivaldi:

1. Go to [chrome://extensions](chrome://extensions)

1. Turn on "Developer mode" in the top-right corner

1. Click "Load unpacked" and select the `ScratchAddons` folder.

To update the extension when testing, click the refresh icon on the extension's card.

{{< admonition info >}}
  The "Unrecognized manifest key" warnings may safely be ignored, since they are required by Firefox.
{{< /admonition >}}


### 모질라 파이어폭스에 설치하기

To load the extension into Mozilla Firefox:

{{< admonition info >}}
  Extensions loaded into Firefox this way are temporary and must be reloaded every time the browser is restarted. Because of this Chrome is recommended for development, but everything is still expected to work on Firefox.
{{< /admonition >}}

1. Type `about:debugging` into the address bar.

1. Click "This Firefox" on the sidebar

1. Click "Load Temporary Add-on..."

1. Select the `manifest.json` file in the `ScratchAddons` folder.

To reload the extension when testing, click the "Reload" button on the extension's card.

{{< admonition info >}}
  The unexpected WebExtension manifest property warnings may safely be ignored, since they are required by Chrome.
{{< /admonition >}}


### Installing on Firefox for Android

{{< admonition info >}}
  This is only recommended if there is a mobile specific issue that cannot be easily replicated with the browser's developer tools since extensions loaded this way are temporary and must be reinstalled over USB every time the app is restarted.
{{< /admonition >}}

#### One time setup

##### Desktop

1. Download and extract the Android SDK Platform Tools ([Windows](https://dl.google.com/android/repository/platform-tools-latest-windows.zip), [MacOS](https://dl.google.com/android/repository/platform-tools-latest-darwin.zip), [Linux](https://dl.google.com/android/repository/platform-tools-latest-linux.zip)).
1. Add the folder to the PATH environment variable.
1. Install web-ext with NPM by running `npm install --global web-ext`.

##### Android

1. In the Android settings app, open the about page and tap the build number 7 times.
1. Navigate to the "Developer options" page and enable "USB debugging".
1. Install the standard Firefox app from the [Google Play store](https://play.google.com/store/apps/details?id=org.mozilla.firefox).
1. Open the Firefox app and enable "Remote debugging via USB" in its settings.

#### Loading the extension

1. Plug in the Android device and tap allow on it.
2. Navigate to the `ScratchAddons` folder.
3. Run `adb devices` to get the device's serial number and ensure ADB is working.
4. Run the following command replacing `[serial number]` with the one from `adb devices`:
```
web-ext run -t firefox-android --adb-device [serial number] --firefox-apk org.mozilla.firefox
```

The extension should install and automatically reload when changes are made, otherwise close the Firefox app and re-run the command.

#### Inspecting

Desktop Firefox can inspect extensions and active tabs running in the Firefox app over USB:

1. On desktop Firefox type `about:debugging` into the address bar.
1. Click "Enable USB Devices".
1. Click connect on the device in the sidebar. If none appear, restart desktop Firefox.
1. Click on the device again.
