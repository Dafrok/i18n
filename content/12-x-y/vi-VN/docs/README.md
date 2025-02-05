# Hướng dẫn sử dụng chính thức

Hãy chắc chắn rằng bạn đang sử dụng các tài liệu phù hợp với phiên bản Electron của bạn. Các đánh số của phiên bản là một phần của URL. If it's not, you are probably using the documentation of a development branch which may contain API changes that are not compatible with your Electron version. Để xem các tài liệu của phiên bản cũ hơn, bạn có thể [duyệt theo thẻ](https://github.com/electron/electron/tree/v1.4.0) trên GitHub mở trình đơn thả xuống "Swich branches/tags" và chọn từ khóa phù hợp với phiên bản của bạn.

## FAQ (câu hỏi thường gặp)

There are questions that are asked quite often. Check this out before creating an issue:

* [Electron FAQ (các câu hỏi thường gặp)](faq.md)

## Hướng dẫn

### Quickstart

* [Quick Start Guide](tutorial/quick-start.md)
  * [Điều kiện tiên quyết](tutorial/quick-start.md#prerequisites)
  * [Create a basic application](tutorial/quick-start.md#create-a-basic-application)
  * [Run your application](tutorial/quick-start.md#run-your-application)
  * [Package and distribute the application](tutorial/quick-start.md#package-and-distribute-the-application)

### Learning the basics

* [Electron's Process Model](tutorial/quick-start.md#application-architecture)
  * [Tiến trình chính và tiến trình kết xuất](tutorial/quick-start.md#main-and-renderer-processes)
  * [Electron API](tutorial/quick-start.md#electron-api)
  * [Node.js API](tutorial/quick-start.md#nodejs-api)
* Thêm các tính năng vào app của bạn
  * [Notifications](tutorial/notifications.md)
  * [Recent Documents](tutorial/recent-documents.md)
  * [Tiến độ ứng dụng](tutorial/progress-bar.md)
  * [Custom Dock Menu](tutorial/macos-dock.md)
  * [Cửa sổ tùy chỉnh thanh taskbar](tutorial/windows-taskbar.md)
  * [Custom Linux Desktop Actions](tutorial/linux-desktop-actions.md)
  * [Các phím tắt](tutorial/keyboard-shortcuts.md)
  * [Offline/Online Detection](tutorial/online-offline-events.md)
  * [Represented File for macOS BrowserWindows](tutorial/represented-file.md)
  * [Native File Drag & Drop](tutorial/native-file-drag-drop.md)
  * [Offscreen Rendering](tutorial/offscreen-rendering.md)
  * [Dark Mode](tutorial/dark-mode.md)
  * [Web embeds in Electron](tutorial/web-embeds.md)
* [Các bản mẫu và Giao diện dòng lệnh](tutorial/boilerplates-and-clis.md)
  * [So sánh bảng mẫu và giao diện dòng lệnh](tutorial/boilerplates-and-clis.md#boilerplate-vs-cli)
  * [electron-forge](tutorial/boilerplates-and-clis.md#electron-forge)
  * [electron-builder](tutorial/boilerplates-and-clis.md#electron-builder)
  * [electron-react-boilerplate](tutorial/boilerplates-and-clis.md#electron-react-boilerplate)
  * [Các công cụ khác và Boilerplates](tutorial/boilerplates-and-clis.md#other-tools-and-boilerplates)

### Advanced steps

* Cấu trúc ứng dụng
  * [Sử dụng các Module Native của Node](tutorial/using-native-node-modules.md)
  * [Performance Strategies](tutorial/performance.md)
  * [Security Strategies](tutorial/security.md)
* [Accessibility](tutorial/accessibility.md)
  * [Manually Enabling Accessibility Features](tutorial/accessibility.md#manually-enabling-accessibility-features)
* [اختبار وتصحيح](tutorial/application-debugging.md)
  * [Debugging the Main Process](tutorial/debugging-main-process.md)
  * [Debugging with Visual Studio Code](tutorial/debugging-vscode.md)
  * [Sử dụng Selenium và WebDriver](tutorial/using-selenium-and-webdriver.md)
  * [Testing on Headless CI Systems (Travis, Jenkins)](tutorial/testing-on-headless-ci.md)
  * [Phần mở rộng DevTools](tutorial/devtools-extension.md)
  * [Kiểm lỗi tự động với driver tùy chỉnh](tutorial/automated-testing-with-a-custom-driver.md)
* [Phân phối](tutorial/application-distribution.md)
  * [Nền tảng hỗ trợ](tutorial/support.md#supported-platforms)
  * [Code Signing](tutorial/code-signing.md)
  * [Mở App store](tutorial/mac-app-store-submission-guide.md)
  * [Kho ứng dụng Windows](tutorial/windows-store-guide.md)
  * [Snapcraft](tutorial/snapcraft.md)
* [Cập Nhật](tutorial/updates.md)
  * [Triển khai một Update Server](tutorial/updates.md#deploying-an-update-server)
  * [Thực hiện cập nhật trong ứng dụng của bạn](tutorial/updates.md#implementing-updates-in-your-app)
  * [Áp dụng cập nhật](tutorial/updates.md#applying-updates)
* [Hỗ trợ](tutorial/support.md)

## Hướng dẫn cụ thể

Những hướng dẫn sau đây là mở rộng của các chủ đề đã được thảo luận trong các tài liệu trên.

* [Cài đặt Electron](tutorial/installation.md)
  * [Proxies](tutorial/installation.md#proxies)
  * [Tuỳ chỉnh Mirrors và Caches](tutorial/installation.md#custom-mirrors-and-caches)
  * [Xử lý sự cố](tutorial/installation.md#troubleshooting)
* Phát hành Electron & phản hồi của nhà phát triển
  * [Chính sách phiên bản](tutorial/electron-versioning.md)
  * [Lịch phát hành](tutorial/electron-timelines.md)
* [Chi tiết: Đóng gói mã nguồn của ứng dụng với asar](tutorial/application-packaging.md)
  * [Tạo ra một file asar Archives](tutorial/application-packaging.md#generating-asar-archives)
  * [Sử dụng các file đóng gói asar](tutorial/application-packaging.md#using-asar-archives)
  * [Hạn chế](tutorial/application-packaging.md#limitations-of-the-node-api)
  * [Huan](tutorial/application-packaging.md#adding-unpacked-files-to-asar-archives)
* [Thử nghiệm Widevine CDM](tutorial/testing-widevine-cdm.md)

---

* [Từ điển thuật ngữ](glossary.md)

## Tài liệu tham khảo về API

* [Tóm tắt](api/synopsis.md)
* [Process Object](api/process.md)
* [Dòng lệnh chuyển được hỗ trợ](api/command-line-switches.md)
* [Các biến môi trường (Environment Variables)](api/environment-variables.md)
* [Tiện ích Chrome được hỗ trợ](api/extensions.md)
* [Những thay đổi API](breaking-changes.md)

### Tùy chỉnh các DOM Element:

* [`File` Object](api/file-object.md)
* [`<webview>` Tag](api/webview-tag.md)
* [`window.open` Function](api/window-open.md)
* [`BrowserWindowProxy` Object](api/browser-window-proxy.md)

### Các Module của Main Process:

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
* [Thông báo](api/notification.md)
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

### Các Module của Renderer Process (trên Web Page):

* [desktopCapturer](api/desktop-capturer.md)
* [ipcRenderer](api/ipc-renderer.md)
* [remote](api/remote.md)
* [webFrame](api/web-frame.md)

### Các Module của cả hai Process trên:

* [clipboard](api/clipboard.md)
* [crashReporter](api/crash-reporter.md)
* [nativeImage](api/native-image.md)
* [shell](api/shell.md)

## Development

</a>
