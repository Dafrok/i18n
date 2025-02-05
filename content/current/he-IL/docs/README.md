# Official Guides

אנא שים לב שאתה משתמש בתיעוד שמתאים לגרסאת Electron שלך. The version number should be a part of the page URL. אם מספר הגירסה אינו נמצא בכתובת העמוד, אתה כנראה צופה בתיעוד של גרסה בפיתוח אשר עשויה להכיל שינויי ממשק שאינם מתאימים לגרסת האלקטרון שברשותך. לצפייה בגרסאות ישנות יותר של התיעוד, אתה יוכל [ לחפש לפי גירסה](https://github.com/electron/electron/tree/v1.4.0) ב-Github ולבחור בתג שמתאים לגירסה שלך בתפריט "Switch branches/tags".

## שאלות נפוצות

There are questions that are asked quite often. Check this out before creating an issue:

* [Electron שאלות נפוצות](faq.md)

## מדריכים וערכות לימוד

### Quickstart

* [Quick Start Guide](tutorial/quick-start.md)
  * [Prerequisites](tutorial/quick-start.md#prerequisites)
  * [Create a basic application](tutorial/quick-start.md#create-a-basic-application)
  * [Run your application](tutorial/quick-start.md#run-your-application)
  * [Package and distribute the application](tutorial/quick-start.md#package-and-distribute-the-application)

### Learning the basics

* [Electron's Process Model](tutorial/quick-start.md#application-architecture)
  * [התהליך הראשי ותהליך הייצוג](tutorial/quick-start.md#main-and-renderer-processes)
  * [Electron API](tutorial/quick-start.md#electron-api)
  * [Node.js API](tutorial/quick-start.md#nodejs-api)
* הוספת תכונות לאפליקציה שלך
  * [Notifications](tutorial/notifications.md)
  * [מסמכים אחרונים](tutorial/recent-documents.md)
  * [התקדמות התרגום](tutorial/progress-bar.md)
  * [תפריט עגינה מותאם אישית](tutorial/macos-dock.md)
  * [שורת משימות מותאמת אישית של Windows](tutorial/windows-taskbar.md)
  * [פעולות מותאמות אישית בסביבת לינוק לשולחן עבודה](tutorial/linux-desktop-actions.md)
  * [קיצורי מקלדת](tutorial/keyboard-shortcuts.md)
  * [זיהוי מקוון/לא מקוון](tutorial/online-offline-events.md)
  * [Represented File for macOS BrowserWindows](tutorial/represented-file.md)
  * [Native File Drag & Drop](tutorial/native-file-drag-drop.md)
  * [Offscreen Rendering](tutorial/offscreen-rendering.md)
  * [Dark Mode](tutorial/dark-mode.md)
  * [Web embeds in Electron](tutorial/web-embeds.md)
* [תבניות וממשקי שורת הפקודות (CLI)](tutorial/boilerplates-and-clis.md)
  * [השוואה בין תבניות ובין ממשקי שורת הפקודות](tutorial/boilerplates-and-clis.md#boilerplate-vs-cli)
  * [electron-forge](tutorial/boilerplates-and-clis.md#electron-forge)
  * [electron-builder](tutorial/boilerplates-and-clis.md#electron-builder)
  * [electron-react-boilerplate](tutorial/boilerplates-and-clis.md#electron-react-boilerplate)
  * [כלים ותבניות נוספים](tutorial/boilerplates-and-clis.md#other-tools-and-boilerplates)

### Advanced steps

* ארכיטקטורת יישום
  * [שימוש במודולים טבעיים של Node.js](tutorial/using-native-node-modules.md)
  * [אסטרטגיות ביצועים](tutorial/performance.md)
  * [Security Strategies](tutorial/security.md)
* [Accessibility](tutorial/accessibility.md)
  * [Manually Enabling Accessibility Features](tutorial/accessibility.md#manually-enabling-accessibility-features)
* [בדיקה ואיתור באגים](tutorial/application-debugging.md)
  * [Debugging the Main Process](tutorial/debugging-main-process.md)
  * [Debugging with Visual Studio Code](tutorial/debugging-vscode.md)
  * [שימוש ב-Selenium ו-WebDriver](tutorial/using-selenium-and-webdriver.md)
  * [Testing on Headless CI Systems (Travis, Jenkins)](tutorial/testing-on-headless-ci.md)
  * [DevTools Extension](tutorial/devtools-extension.md)
  * [בדיקות אוטומטיות עם Driver מותאם אישית](tutorial/automated-testing-with-a-custom-driver.md)
* [הפצה](tutorial/application-distribution.md)
  * [Supported Platforms](tutorial/support.md#supported-platforms)
  * [חתימה על קוד](tutorial/code-signing.md)
  * [חנות היישומים של Mac](tutorial/mac-app-store-submission-guide.md)
  * [חנות Windows](tutorial/windows-store-guide.md)
  * [Snapcraft](tutorial/snapcraft.md)
* [עדכונים](tutorial/updates.md)
  * [הטמעת שרת עדכונים](tutorial/updates.md#deploying-an-update-server)
  * [הטמעת עדכונים ביישום שלך](tutorial/updates.md#implementing-updates-in-your-app)
  * [החלת עדכונים](tutorial/updates.md#applying-updates)
* [קבלת תמיכה](tutorial/support.md)

## מדריכים מפורטים

אלו מדריכים פרטניים שנועדים לפרט על נושאים שנדונו בקווים המנחים שלהלן.

* [התקנת Electron](tutorial/installation.md)
  * [מתווכים](tutorial/installation.md#proxies)
  * [Custom Mirrors and Caches](tutorial/installation.md#custom-mirrors-and-caches)
  * [פתרון בעיות](tutorial/installation.md#troubleshooting)
* גרסאות של Electron & משוב מפתחים
  * [מדיניות גרסאות](tutorial/electron-versioning.md)
  * [ציר זמן הוצאות לאור](tutorial/electron-timelines.md)
* [Testing Widevine CDM](tutorial/testing-widevine-cdm.md)

---

* [מילון מונחים](glossary.md)

## הפניה לממשק

* [Synopsis](api/synopsis.md)
* [Process Object](api/process.md)
* [Supported Command Line Switches](api/command-line-switches.md)
* [משתני סביבה](api/environment-variables.md)
* [Chrome Extensions Support](api/extensions.md)
* [שינויים השוברים את ה־API](breaking-changes.md)

### אלמנטי DOM מותאמים אישית:

* [`File` Object](api/file-object.md)
* [`<webview>` תג](api/webview-tag.md)
* [`window.open` Function](api/window-open.md)
* [`BrowserWindowProxy` Object](api/browser-window-proxy.md)

### מודלים עבור ה־Main Process:

* [יישומים](api/app.md)
* [autoUpdater](api/auto-updater.md)
* [BrowserView](api/browser-view.md)
* [BrowserWindow](api/browser-window.md)
* [contentTracing](api/content-tracing.md)
* [דיאלוג](api/dialog.md)
* [globalShortcut](api/global-shortcut.md)
* [inAppPurchase](api/in-app-purchase.md)
* [ipcMain](api/ipc-main.md)
* [תפריט](api/menu.md)
* [MenuItem](api/menu-item.md)
* [net](api/net.md)
* [netLog](api/net-log.md)
* [nativeTheme](api/native-theme.md)
* [Notification](api/notification.md)
* [powerMonitor](api/power-monitor.md)
* [powerSaveBlocker](api/power-save-blocker.md)
* [protocol](api/protocol.md)
* [screen](api/screen.md)
* [session](api/session.md)
* [systemPreferences](api/system-preferences.md)
* [TouchBar](api/touch-bar.md)
* [Tray](api/tray.md)
* [webContents](api/web-contents.md)
* [webFrameMain](api/web-frame-main.md)

### Modules for the Renderer Process (Web Page):

* [desktopCapturer](api/desktop-capturer.md)
* [ipcRenderer](api/ipc-renderer.md)
* [remote](api/remote.md)
* [webFrame](api/web-frame.md)

### Modules for Both Processes:

* [clipboard](api/clipboard.md)
* [crashReporter](api/crash-reporter.md)
* [nativeImage](api/native-image.md)
* [shell](api/shell.md)

## פיתוח

See [development/README.md](development/README.md)
