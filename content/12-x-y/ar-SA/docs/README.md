# الوثائق الرسمية

الرجاء التأكد من استخدام المستندات التي تتطابق مع إصدار الالكترون الخاص بك. ينبغي أن يكون رقم الإصدار جزءا من عنوان الصفحة URL. اذا كان إصدارك لا يطابق الظاهر في رابط الصفحة، هذا يعني انك تستعرض دليل لا يتوافق مع اصدار الكترون الخاص بك وهناك احتمال بأن لا تتوافق التعليمات و API مع اصدار الكترون الذي لديك. لعرض الإصدارات القديمة من الوثائق، يمكنك [تصفح بواسطة العلامة](https://github.com/electron/electron/tree/v1.4.0) على كيت هاب بفتح قائمة "تبديل branch" واختيار التي تطابق الإصدار الخاص بك.

## الأسئلة الشائعة

وهناك أسئلة تُطرح في كثير من الأحيان. تحقق من هذا قبل إنشاء مشكلة:

* [Electron  - الاسئلة الشائعة](faq.md)

## الإرشادات و الشروحات

### البداية السريعة

* [دليل البدء السريع](tutorial/quick-start.md)
  * [المتطلبات الأساسية](tutorial/quick-start.md#prerequisites)
  * [إنشاء تطبيق أساسي](tutorial/quick-start.md#create-a-basic-application)
  * [تشغيل التطبيق الخاص بك](tutorial/quick-start.md#run-your-application)
  * [حزمة الطلب وتوزيعه](tutorial/quick-start.md#package-and-distribute-the-application)

### تعلم الأساسيات

* [Electron's Process Model](tutorial/quick-start.md#application-architecture)
  * [العمليات الرئيسية والرابط](tutorial/quick-start.md#main-and-renderer-processes)
  * [Electron API](tutorial/quick-start.md#electron-api)
  * [Node.js API](tutorial/quick-start.md#nodejs-api)
* إضافة ميزات إلى تطبيقك
  * [الإشعارات](tutorial/notifications.md)
  * [المستندات الأخيرة](tutorial/recent-documents.md)
  * [سير الترجمة](tutorial/progress-bar.md)
  * [خصص شريط المهام](tutorial/macos-dock.md)
  * [خصص شريط مهام الويندوز](tutorial/windows-taskbar.md)
  * [خصص إجراءات سطح المكتب المخصص لـ Linux](tutorial/linux-desktop-actions.md)
  * [Keyboard Shortcuts](tutorial/keyboard-shortcuts.md)
  * [إكتشاف المتصل/ غير المتصل](tutorial/online-offline-events.md)
  * [Represented File for macOS BrowserWindows](tutorial/represented-file.md)
  * [سحب الملف الأصلي & إسقاط](tutorial/native-file-drag-drop.md)
  * [Offscreen Rendering](tutorial/offscreen-rendering.md)
  * [Dark Mode](tutorial/dark-mode.md)
  * [تضمين الويب في إلكترون](tutorial/web-embeds.md)
* [Boilerplates and CLIs](tutorial/boilerplates-and-clis.md)
  * [Boilerplate مقابل CLI](tutorial/boilerplates-and-clis.md#boilerplate-vs-cli)
  * [electron-forge](tutorial/boilerplates-and-clis.md#electron-forge)
  * [electron-builder](tutorial/boilerplates-and-clis.md#electron-builder)
  * [electron-react-boilerplate](tutorial/boilerplates-and-clis.md#electron-react-boilerplate)
  * [أدوات أخرى و Boilerplates](tutorial/boilerplates-and-clis.md#other-tools-and-boilerplates)

### Advanced steps

* معمارية التطبيق
  * [باستخدام Native Node.js Modules](tutorial/using-native-node-modules.md)
  * [Performance Strategies](tutorial/performance.md)
  * [Security Strategies](tutorial/security.md)
* [إمكانية الوصول](tutorial/accessibility.md)
  * [تمكين ميزات إمكانية الوصول يدويا](tutorial/accessibility.md#manually-enabling-accessibility-features)
* [اختبار وتصحيح](tutorial/application-debugging.md)
  * [تنقيح عملية الرئيسية](tutorial/debugging-main-process.md)
  * [Debugging with Visual Studio Code](tutorial/debugging-vscode.md)
  * [Using Selenium and WebDriver](tutorial/using-selenium-and-webdriver.md)
  * [Testing on Headless CI Systems (Travis, Jenkins)](tutorial/testing-on-headless-ci.md)
  * [DevTools Extension](tutorial/devtools-extension.md)
  * [الاختبار الآلي مع برنامج تشغيل مخصص](tutorial/automated-testing-with-a-custom-driver.md)
* [التوزيع](tutorial/application-distribution.md)
  * [Supported Platforms](tutorial/support.md#supported-platforms)
  * [توقيع الكود](tutorial/code-signing.md)
  * [Mac App ore](tutorial/mac-app-store-submission-guide.md)
  * [متجر تطبيقات Windows](tutorial/windows-store-guide.md)
  * [Snapcraft](tutorial/snapcraft.md)
* [التحديثات](tutorial/updates.md)
  * [نشر خادم التحديث](tutorial/updates.md#deploying-an-update-server)
  * [تنفيذ التحديثات في تطبيقك](tutorial/updates.md#implementing-updates-in-your-app)
  * [تطبيق التحديثات](tutorial/updates.md#applying-updates)
* [Getting Support](tutorial/support.md)

## دروس مفصلة

هذه دروس مفصلة للمواضيع التي تمت مناقشتها في الدليل بالأعلى.

* [تنصيب إلكترون (Electron)](tutorial/installation.md)
  * [بروكسيات](tutorial/installation.md#proxies)
  * [مرايا مخصصة ومخابئ](tutorial/installation.md#custom-mirrors-and-caches)
  * [اكتشاف الأخطاء وإصلاحها](tutorial/installation.md#troubleshooting)
*
  * [Versioning Policy](tutorial/electron-versioning.md)
  * [Release Timelines](tutorial/electron-timelines.md)
* [Packaging App Source Code with asar](tutorial/application-packaging.md)
  * [توليد ملفات asar](tutorial/application-packaging.md#generating-asar-archives)
  * [استخدام أرشيفات asar](tutorial/application-packaging.md#using-asar-archives)
  * [القيود](tutorial/application-packaging.md#limitations-of-the-node-api)
  * [إضافة ملفات غير مخزنة إلى أرشيفات asar](tutorial/application-packaging.md#adding-unpacked-files-to-asar-archives)
* [اختبار Widevine CDM](tutorial/testing-widevine-cdm.md)

---

* [قاموس المصطلحات](glossary.md)

## مراجع API

* [Synopsis](api/synopsis.md)
* [Process Object](api/process.md)
* [Supported Command Line Switches](api/command-line-switches.md)
* [Environment Variables](api/environment-variables.md)
* [دعم إضافات Chrome](api/extensions.md)
* [كسر تغييرات API](breaking-changes.md)

### عناصر DOM مخصصة:

* [`File` Object](api/file-object.md)
* [`<webview>` Tag](api/webview-tag.md)
* [`window.open` Function](api/window-open.md)
* [`BrowserWindowProxy` Object](api/browser-window-proxy.md)

### وحدات للـ Main Process:

* [التطبيقات](api/app.md)
* [تحديث تلقائي](api/auto-updater.md)
* [BrowserView (عرض المتصفح)](api/browser-view.md)
* [نافذة المتصفح](api/browser-window.md)
* [تتبع المحتوى](api/content-tracing.md)
* [نافذة الحوار](api/dialog.md)
* [اختصار عالمي](api/global-shortcut.md)
* [inAppPurchase (مشتريات داخل التطبيق)](api/in-app-purchase.md)
* [ipcMain](api/ipc-main.md)
* [Menu (القائمة)](api/menu.md)
* [MenuItem (عنصر في القائمة)](api/menu-item.md)
* [net](api/net.md)
* [netLog](api/net-log.md)
* [nativeTheme](api/native-theme.md)
* [Notification (الإشعارات)](api/notification.md)
* [powerMonitor](api/power-monitor.md)
* [powerSaveBlocker](api/power-save-blocker.md)
* [protocol](api/protocol.md)
* [شاشة](api/screen.md)
* [session](api/session.md)
* [systemPreferences](api/system-preferences.md)
* [شريط اللمس](api/touch-bar.md)
* [Tray](api/tray.md)
* [webContents](api/web-contents.md)
* [webFrameMain](api/web-frame-main.md)

### الوحدات النمطية لعملية التقديم (صفحة ويب):

* [desktopCapturer](api/desktop-capturer.md)
* [ipcRenderer](api/ipc-renderer.md)
* [منصة_شليلة](api/remote.md)
* [webFrame](api/web-frame.md)

### الوحدات لكلا العمليتين:

* [لوحة القُصاصات](api/clipboard.md)
* [crashReporter](api/crash-reporter.md)
* [nativeImage](api/native-image.md)
* [صدفة](api/shell.md)

## التطوير

See [development/README.md](development/README.md)
