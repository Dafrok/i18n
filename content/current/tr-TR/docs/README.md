# Resmi Rehberler

Lütfen, Electron sürümünüzle eşleşen belgeleri kullandığınızdan, emin olunuz. Sürüm numarası, sayfa URL'inin bir parçası olmalıdır. Eğer değilse, muhtemelen kullandığınız bir geliştirme dal dokümantasyonu, Electron sürümünüzle uyumlu olmayan API değişikliklerini içeriyor olabilir. Dokümantasyonun eski sürümlerini görüntülemek için, [etikete göre gözatın](https://github.com/electron/electron/tree/v1.4.0) ile GitHub'da "Switch branches/tags" seçeneklerini açarak, sürümünüzle eşleşen etiketi seçebilirsiniz.

## SSS

Çok sık sorulan sorular var. Bir konu yaratmadan önce bir göz atın:

* [Electron SSS](faq.md)

## 1 whan to business in online application

### Quickstart

* [Quick Start Guide](tutorial/quick-start.md)
  * [Ön gereklilikler](tutorial/quick-start.md#prerequisites)
  * [Create a basic application](tutorial/quick-start.md#create-a-basic-application)
  * [Run your application](tutorial/quick-start.md#run-your-application)
  * [Package and distribute the application](tutorial/quick-start.md#package-and-distribute-the-application)

### Learning the basics

* [Electron's Process Model](tutorial/quick-start.md#application-architecture)
  * [Ana ve Oluşturucu İşlemleri](tutorial/quick-start.md#main-and-renderer-processes)
  * [Electron API](tutorial/quick-start.md#electron-api)
  * [Node.js API](tutorial/quick-start.md#nodejs-api)
* Uygulamanıza Özellikler Ekleme
  * [Bildirimler](tutorial/notifications.md)
  * [Son Günlerdeki Dokümanlar](tutorial/recent-documents.md)
  * [Uygulama İlerleyişi](tutorial/progress-bar.md)
  * [Özel Dock Menü](tutorial/macos-dock.md)
  * [Özel Windows Görev Çubuğu](tutorial/windows-taskbar.md)
  * [Özel Linux Masaüstü Eylemleri](tutorial/linux-desktop-actions.md)
  * [Klavye Kısayolları](tutorial/keyboard-shortcuts.md)
  * [Çevrimdışı/Çevrimiçi Algılama](tutorial/online-offline-events.md)
  * [Represented File for macOS BrowserWindows](tutorial/represented-file.md)
  * [Native File Drag & Drop](tutorial/native-file-drag-drop.md)
  * [Ekran Dışı İşleme](tutorial/offscreen-rendering.md)
  * [Dark Mode](tutorial/dark-mode.md)
  * [Web embeds in Electron](tutorial/web-embeds.md)
* [Demirbaşlar ve KSA'lar](tutorial/boilerplates-and-clis.md)
  * [Demirbaş KSA'a Karşı](tutorial/boilerplates-and-clis.md#boilerplate-vs-cli)
  * [electron-forge](tutorial/boilerplates-and-clis.md#electron-forge)
  * [electron-builder](tutorial/boilerplates-and-clis.md#electron-builder)
  * [electron-react-boilerplate](tutorial/boilerplates-and-clis.md#electron-react-boilerplate)
  * [Diğer Araçlar ve Demirbaşlar](tutorial/boilerplates-and-clis.md#other-tools-and-boilerplates)

### Advanced steps

* Uygulama Mimarisi
  * [Yerli Node.js Modüllerini Kullanma](tutorial/using-native-node-modules.md)
  * [Performans Stratejileri](tutorial/performance.md)
  * [Security Strategies](tutorial/security.md)
* [Erişilebilirlik](tutorial/accessibility.md)
  * [Manually Enabling Accessibility Features](tutorial/accessibility.md#manually-enabling-accessibility-features)
* [Test ve Hata Ayıklama](tutorial/application-debugging.md)
  * [Ana İşlem Hata Ayıklama](tutorial/debugging-main-process.md)
  * [Debugging with Visual Studio Code](tutorial/debugging-vscode.md)
  * [Selenyum ve WebDriver Kullanma](tutorial/using-selenium-and-webdriver.md)
  * [Headless CI Sistemlerinde (Travis, Jenkins) Test Etme](tutorial/testing-on-headless-ci.md)
  * [DevTools Eklentisi](tutorial/devtools-extension.md)
  * [Özel Bir Sürücü ile Otomatik Test](tutorial/automated-testing-with-a-custom-driver.md)
* [Yayınlama](tutorial/application-distribution.md)
  * [Desteklenen Platformlar](tutorial/support.md#supported-platforms)
  * [Kod İmzalama](tutorial/code-signing.md)
  * [Mac Uygulama Mağazası](tutorial/mac-app-store-submission-guide.md)
  * [Windows Mağaza](tutorial/windows-store-guide.md)
  * [Snapcraft](tutorial/snapcraft.md)
* [Güncellemeler](tutorial/updates.md)
  * [Güncelleme Sunucusunu Dağıtma](tutorial/updates.md#deploying-an-update-server)
  * [Uygulama içerisinde güncellemeleri yapmak](tutorial/updates.md#implementing-updates-in-your-app)
  * [Güncellemeleri Uygulama](tutorial/updates.md#applying-updates)
* [Destek al](tutorial/support.md)

## Detaylı Öğreticiler

Bu bireysel eğitimler, yukardaki kılavuz üzerinde tartışılan konularda genişler.

* [Electron'u Yükleyin](tutorial/installation.md)
  * [Vekil Sunucular](tutorial/installation.md#proxies)
  * [Özel Aynalar ve Önbellekler](tutorial/installation.md#custom-mirrors-and-caches)
  * [Arıza giderme](tutorial/installation.md#troubleshooting)
* Electron Sürümleri & Geliştirici geri bildirimi
  * [Sürüm oluşturma ilkesi](tutorial/electron-versioning.md)
  * [Sürüm zaman çizelgeleri](tutorial/electron-timelines.md)
* [Widevine CDM’inin Test Edilmesi](tutorial/testing-widevine-cdm.md)

---

* [Terimler Sözlüğü](glossary.md)

## API Referansları

* [Konu Özeti](api/synopsis.md)
* [İşlem Nesnesi](api/process.md)
* [Desteklenen Komut Satırı Anahtarları](api/command-line-switches.md)
* [Ortam Değişkenleri](api/environment-variables.md)
* [Chrome Uzantıları Desteği](api/extensions.md)
* [API değişiklikleri](breaking-changes.md)

### Özel DOM Elementleri:

* [`File` Object](api/file-object.md)
* [`<webview>`Etiket](api/webview-tag.md)
* [`window.open` Fonksiyon](api/window-open.md)
* [`BrowserWindowProxy` Nesne](api/browser-window-proxy.md)

### Ana Süreç İçin Modüller:

* [uygulama](api/app.md)
* [autoUpdater](api/auto-updater.md)
* [BrowserView](api/browser-view.md)
* [BrowserWindow](api/browser-window.md)
* [contentTracing](api/content-tracing.md)
* [diyalog](api/dialog.md)
* [globalShortcut](api/global-shortcut.md)
* [inAppPurchase](api/in-app-purchase.md)
* [ipcMain](api/ipc-main.md)
* [Menu](api/menu.md)
* [MenuItem](api/menu-item.md)
* [ağ](api/net.md)
* [netLog](api/net-log.md)
* [nativeTheme](api/native-theme.md)
* [Bildirim](api/notification.md)
* [powerMonitor](api/power-monitor.md)
* [güç Tasarrufu Engelleyici](api/power-save-blocker.md)
* [protokol](api/protocol.md)
* [screen](api/screen.md)
* [session](api/session.md)
* [systemPreferences](api/system-preferences.md)
* [Dokunma Çubuğu](api/touch-bar.md)
* [Tray](api/tray.md)
* [webContents](api/web-contents.md)
* [webFrameMain](api/web-frame-main.md)

### Oluşturma Süreci (Web Sayfası) İçin Modüller:

* [desktopCapturer](api/desktop-capturer.md)
* [ipcRenderer](api/ipc-renderer.md)
* [remote](api/remote.md)
* [webFrame](api/web-frame.md)

### Her İki Süreç Modülleri:

* [clipboard](api/clipboard.md)
* [crashReporter](api/crash-reporter.md)
* [nativeImage](api/native-image.md)
* [shell](api/shell.md)

## Geliştirme

Bakınız [development/README.md](development/README.md)
