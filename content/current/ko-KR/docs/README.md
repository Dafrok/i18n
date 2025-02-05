# 공식 가이드

Electron 버전과 일치하는 문서를 보고있는지 확인하세요. 페이지 URL은 버전 번호를 포함하고 있어야 합니다. URL에 버전 번호가 포함되지 않았다면, development 브랜치 문서를 사용하고 있는 것이며 여기에는 여러분의 Electron 버전과 호환되지 않는 API 변경 사항을 담고 있을지도 모릅니다. GitHub 에서 "Switch branches/tags" 드롭다운 메뉴의 [태그 찾기](https://github.com/electron/electron/tree/v1.4.0)를 활용해 여러분의 Electron 버전과 일치하는 태그를 선택하면 구 버전 문서들을 볼 수 있습니다.

## 자주 묻는 질문

자주 묻는 질문이 있습니다. 이슈를 제기하기 전에 확인하세요.

* [Electron 자주 묻는 질문](faq.md)

## 가이드와 튜토리얼

### Quickstart

* [Quick Start Guide](tutorial/quick-start.md)
  * [빌드전 요구 사양](tutorial/quick-start.md#prerequisites)
  * [Create a basic application](tutorial/quick-start.md#create-a-basic-application)
  * [Run your application](tutorial/quick-start.md#run-your-application)
  * [Package and distribute the application](tutorial/quick-start.md#package-and-distribute-the-application)

### Learning the basics

* [Electron's Process Model](tutorial/quick-start.md#application-architecture)
  * [메인과 렌더러 프로세스](tutorial/quick-start.md#main-and-renderer-processes)
  * [Electron API](tutorial/quick-start.md#electron-api)
  * [Node.js API](tutorial/quick-start.md#nodejs-api)
* 여러분의 앱에 기능 추가하기
  * [알림(Notifications)](tutorial/notifications.md)
  * [최근 문서들(Recent Documents)](tutorial/recent-documents.md)
  * [애플리케이션 진행 상황](tutorial/progress-bar.md)
  * [커스텀 Dock 메뉴](tutorial/macos-dock.md)
  * [커스텀 Windows 작업 표시줄](tutorial/windows-taskbar.md)
  * [커스텀 Linux 데스크톱 동작](tutorial/linux-desktop-actions.md)
  * [키보드 단축키](tutorial/keyboard-shortcuts.md)
  * [오프라인/온라인 감지](tutorial/online-offline-events.md)
  * [macOS BrowserWindows에 대한 파일 표현](tutorial/represented-file.md)
  * [네이티브 파일 Drag & Drop](tutorial/native-file-drag-drop.md)
  * [오프 스크린 렌더링](tutorial/offscreen-rendering.md)
  * [Dark Mode](tutorial/dark-mode.md)
  * [Web embeds in Electron](tutorial/web-embeds.md)
* [Boilerplates와 CLI](tutorial/boilerplates-and-clis.md)
  * [Boilerplate vs CLI](tutorial/boilerplates-and-clis.md#boilerplate-vs-cli)
  * [electron-forge](tutorial/boilerplates-and-clis.md#electron-forge)
  * [electron-builder](tutorial/boilerplates-and-clis.md#electron-builder)
  * [electron-react-boilerplate](tutorial/boilerplates-and-clis.md#electron-react-boilerplate)
  * [기타 도구와 Boilerplates](tutorial/boilerplates-and-clis.md#other-tools-and-boilerplates)

### Advanced steps

* 애플리케이션 아키텍처
  * [기본 Node.js 모듈 사용하기](tutorial/using-native-node-modules.md)
  * [성능 전략](tutorial/performance.md)
  * [Security Strategies](tutorial/security.md)
* [접근성](tutorial/accessibility.md)
  * [Manually Enabling Accessibility Features](tutorial/accessibility.md#manually-enabling-accessibility-features)
* [테스팅과 디버깅](tutorial/application-debugging.md)
  * [메인 프로세스 디버깅하기](tutorial/debugging-main-process.md)
  * [Debugging with Visual Studio Code](tutorial/debugging-vscode.md)
  * [Selenium 과 WebDriver 사용하기](tutorial/using-selenium-and-webdriver.md)
  * [헤드리스 CI 시스템 (트래비스, 젠킨스) 테스트](tutorial/testing-on-headless-ci.md)
  * [DevTools 확장](tutorial/devtools-extension.md)
  * [커스텀 드라이버를 이용한 자동화된 테스팅](tutorial/automated-testing-with-a-custom-driver.md)
* [배포](tutorial/application-distribution.md)
  * [지원되는 플랫폼](tutorial/support.md#supported-platforms)
  * [코드 서명(Code Signing)](tutorial/code-signing.md)
  * [Mac App Store](tutorial/mac-app-store-submission-guide.md)
  * [Windows 스토어](tutorial/windows-store-guide.md)
  * [Snapcraft](tutorial/snapcraft.md)
* [업데이트](tutorial/updates.md)
  * [서버에 업데이트 배포](tutorial/updates.md#deploying-an-update-server)
  * [앱에 업데이트 구현하기](tutorial/updates.md#implementing-updates-in-your-app)
  * [업데이트 적용](tutorial/updates.md#applying-updates)
* [지원받기](tutorial/support.md)

## 자세한 튜토리얼

이 가이드는 위에서 설명된 주제의 확장입니다.

* [Electron 설치하기](tutorial/installation.md)
  * [프록시](tutorial/installation.md#proxies)
  * [커스텀 미러와 캐시](tutorial/installation.md#custom-mirrors-and-caches)
  * [문제 해결](tutorial/installation.md#troubleshooting)
* Electron 릴리즈 & 개발자 피드백
  * [버저닝 정책](tutorial/electron-versioning.md)
  * [버전 출시 일정](tutorial/electron-timelines.md)
* [Widevine CDM 테스트](tutorial/testing-widevine-cdm.md)

---

* [용어집](glossary.md)

## API 참조 문서

* [개요](api/synopsis.md)
* [프로세스 개체](api/process.md)
* [지원되는 명령행 스위치](api/command-line-switches.md)
* [환경 변수](api/environment-variables.md)
* [Chrome 확장 지원](api/extensions.md)
* [중요한 API 변화](breaking-changes.md)

### 사용자 지정 DOM 요소:

* [`File` 객체](api/file-object.md)
* [`<webview>` 태그](api/webview-tag.md)
* [`window.open` 함수](api/window-open.md)
* [`BrowserWindowProxy` Object](api/browser-window-proxy.md)

### 주요 프로세스 모듈:

* [app](api/app.md)
* [autoUpdater](api/auto-updater.md)
* [BrowserView](api/browser-view.md)
* [BrowserWindow](api/browser-window.md)
* [contentTracing](api/content-tracing.md)
* [dialog](api/dialog.md)
* [globalShortcut](api/global-shortcut.md)
* [inAppPurchase](api/in-app-purchase.md)
* [ipcMain](api/ipc-main.md)
* [Menu](api/menu.md)
* [MenuItem](api/menu-item.md)
* [net](api/net.md)
* [netLog](api/net-log.md)
* [nativeTheme](api/native-theme.md)
* [알림](api/notification.md)
* [powerMonitor](api/power-monitor.md)
* [powerSaveBlocker](api/power-save-blocker.md)
* [protocol](api/protocol.md)
* [screen](api/screen.md)
* [세션](api/session.md)
* [systemPreferences](api/system-preferences.md)
* [TouchBar](api/touch-bar.md)
* [Tray](api/tray.md)
* [webContents](api/web-contents.md)
* [webFrameMain](api/web-frame-main.md)

### 렌더러 프로세스 (웹 페이지) 에 대한 모듈:

* [desktopCapturer](api/desktop-capturer.md)
* [ipcRenderer](api/ipc-renderer.md)
* [remote](api/remote.md)
* [webFrame](api/web-frame.md)

### 두 프로세스에 대한 모듈:

* [clipboard](api/clipboard.md)
* [crashReporter](api/crash-reporter.md)
* [기본이미지](api/native-image.md)
* [shell](api/shell.md)

## 개발

[Electron 개발하기](development/README.md) 문서를 확인하세요.
