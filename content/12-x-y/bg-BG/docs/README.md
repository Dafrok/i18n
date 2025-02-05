# Официални ръководства

Моля, уверете се, че използвате документите, които съответстват на вашата версия на Електрон. Номерът на версията трябва да е част от URL адреса на страницата. Ако не успявате да идентифицирате версията, то най-вероятно четете настоящият документ касаещ версия на продукта която се разработва в момента. Бъдете внимателни защото информацията, която получавате в момента може да не е съвместима с версията на Electron, с която работите в момента. Ако се интересувате от по-стара версия на продукта, ви съветваме да използвате функцията [browse by tag](https://github.com/electron/electron/tree/v1.4.0) в GitHub като отворите менюто "Switch branches/tags" и изберете версията, която ви интересува.

## Често задавани въпроси

There are questions that are asked quite often. Check this out before creating an issue:

* [често задавани въпроси за Electron](faq.md)

## Ръководства и уроци

### Quickstart

* [Quick Start Guide](tutorial/quick-start.md)
  * [Prerequisites](tutorial/quick-start.md#prerequisites)
  * [Create a basic application](tutorial/quick-start.md#create-a-basic-application)
  * [Run your application](tutorial/quick-start.md#run-your-application)
  * [Package and distribute the application](tutorial/quick-start.md#package-and-distribute-the-application)

### Learning the basics

* [Electron's Process Model](tutorial/quick-start.md#application-architecture)
  * [Основен и Рендериращ процес](tutorial/quick-start.md#main-and-renderer-processes)
  * [Electron API](tutorial/quick-start.md#electron-api)
  * [Node.js API](tutorial/quick-start.md#nodejs-api)
* Добавяне на функции към вашето приложение
  * [Notifications](tutorial/notifications.md)
  * [Последни документи](tutorial/recent-documents.md)
  * [Прогрес на приложението](tutorial/progress-bar.md)
  * [Потребителско док меню](tutorial/macos-dock.md)
  * [Потребителска Windows лентата на задачите](tutorial/windows-taskbar.md)
  * [Потребителски настолни действия при Linux](tutorial/linux-desktop-actions.md)
  * [Клавишни комбинации](tutorial/keyboard-shortcuts.md)
  * [Offline/Online откриване](tutorial/online-offline-events.md)
  * [Represented File for macOS BrowserWindows](tutorial/represented-file.md)
  * [Native File Drag & Drop](tutorial/native-file-drag-drop.md)
  * [Рендиране извън екрана](tutorial/offscreen-rendering.md)
  * [Dark Mode](tutorial/dark-mode.md)
  * [Web embeds in Electron](tutorial/web-embeds.md)
* [Шаблони и CLI](tutorial/boilerplates-and-clis.md)
  * [Шаблон срещу CLI](tutorial/boilerplates-and-clis.md#boilerplate-vs-cli)
  * [electron-forge](tutorial/boilerplates-and-clis.md#electron-forge)
  * [electron-builder](tutorial/boilerplates-and-clis.md#electron-builder)
  * [electron-react-boilerplate](tutorial/boilerplates-and-clis.md#electron-react-boilerplate)
  * [Други инструменти и шаблони](tutorial/boilerplates-and-clis.md#other-tools-and-boilerplates)

### Advanced steps

* Архитектура на приложението
  * [Използване на родни Node.js модули](tutorial/using-native-node-modules.md)
  * [Performance Strategies](tutorial/performance.md)
  * [Security Strategies](tutorial/security.md)
* [Accessibility](tutorial/accessibility.md)
  * [Manually Enabling Accessibility Features](tutorial/accessibility.md#manually-enabling-accessibility-features)
* [5256783105227699](tutorial/application-debugging.md)
  * [Debugging the Main Process](tutorial/debugging-main-process.md)
  * [Debugging with Visual Studio Code](tutorial/debugging-vscode.md)
  * [Работа със Selenium Web Driver](tutorial/using-selenium-and-webdriver.md)
  * [Тестване и употреба на Системи за непрекъсната интеграция (Travis, Jenkins)](tutorial/testing-on-headless-ci.md)
  * [Разширения за работа с инструменти за писане на програмен код](tutorial/devtools-extension.md)
  * [5256783105227699](tutorial/automated-testing-with-a-custom-driver.md)
* [Разпределения](tutorial/application-distribution.md)
  * [Поддържани платформи](tutorial/support.md#supported-platforms)
  * [5256783105227699](tutorial/code-signing.md)
  * [Mac App Store](tutorial/mac-app-store-submission-guide.md)
  * [Windows Store](tutorial/windows-store-guide.md)
  * [Snapcraft](tutorial/snapcraft.md)
* [5256783105227699](tutorial/updates.md)
  * [Дистрибуция на обновен сървър](tutorial/updates.md#deploying-an-update-server)
  * [Добавяне на новости във вашето приложение](tutorial/updates.md#implementing-updates-in-your-app)
  * [Прилагане на новости](tutorial/updates.md#applying-updates)
* [Getting Support](tutorial/support.md)

## รายละเอียดบทความสอน

บทความสอนแต่ละบทจะขยายความจากหัวข้อคำแนะนำข้างบน.

* [Инсталиране на Електрон](tutorial/installation.md)
  * [Proxies](tutorial/installation.md#proxies)
  * [Потребителски mirrors и кеширане](tutorial/installation.md#custom-mirrors-and-caches)
  * [Отстраняване на неизправности](tutorial/installation.md#troubleshooting)
* Versiones Electron & Comentarios de desarrollador
  * [Versiebeleidid](tutorial/electron-versioning.md)
  * [Calendrier de release9996](tutorial/electron-timelines.md)
* [5256783105227699](tutorial/application-packaging.md)
  * [การสร้างคลังเก็บอาซาร์](tutorial/application-packaging.md#generating-asar-archives)
  * [การใช้ asar Archives](tutorial/application-packaging.md#using-asar-archives)
  * [Ограничения](tutorial/application-packaging.md#limitations-of-the-node-api)
  * [การเพิ่มไฟล์ที่คลายการบีบอัดไปยัง asar Archives](tutorial/application-packaging.md#adding-unpacked-files-to-asar-archives)
* [Testing Widevine CDM](tutorial/testing-widevine-cdm.md)

---

* [Речник на термините](glossary.md)

## Функционална документация

* [Обзор](api/synopsis.md)
* [กระบวนการของวัตถุ](api/process.md)
* [Supported Command Line Switches](api/command-line-switches.md)
* [Променливи на средата](api/environment-variables.md)
* [Chrome Extensions Support](api/extensions.md)
* [5256783105227699](breaking-changes.md)

### Персонални DOM елементи:

* [Обект `File`](api/file-object.md)
* [`<webview>`Етикет](api/webview-tag.md)
* [Функция `window.open`](api/window-open.md)
* [5256783105227699](api/browser-window-proxy.md)

### Модули за основния процес:

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
* [5256783105227699](api/net-log.md)
* [nativeTheme](api/native-theme.md)
* [5256783105227699](api/notification.md)
* [powerMonitor](api/power-monitor.md)
* [powerSaveBlocker](api/power-save-blocker.md)
* [protocol](api/protocol.md)
* [screen](api/screen.md)
* [session](api/session.md)
* [systemPreferences](api/system-preferences.md)
* [5256783105227699](api/touch-bar.md)
* [Tray](api/tray.md)
* [webContents](api/web-contents.md)
* [webFrameMain](api/web-frame-main.md)

### Модули за визуализиращи процеси (Web страници):

* [desktopCapturer](api/desktop-capturer.md)
* [ipcRenderer](api/ipc-renderer.md)
* [remote](api/remote.md)
* [webFrame](api/web-frame.md)

### Общи модули:

* [clipboard](api/clipboard.md)
* [crashReporter](api/crash-reporter.md)
* [nativeImage](api/native-image.md)
* [shell](api/shell.md)

## Разработка

See [development/README.md](development/README.md)
