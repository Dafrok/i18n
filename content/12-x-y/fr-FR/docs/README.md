# Guide officiel

Veuillez vous assurer d'utiliser la documentation qui correspond à votre version d'Electron. Le numéro de version doit être une partie de l'URL de la page. Si ce n'est pas le cas, vous utilisez probablement la documentation d'une branche de développement pouvant contenir des modifications de l'API qui ne sont pas compatibles avec votre version d'Electron. Pour consulter les anciennes versions de la documentation, vous pouvez [Parcourir par tag](https://github.com/electron/electron/tree/v1.4.0) sur GitHub en ouvrant la liste déroulante « Switch branches/tags » et sélectionnez le tag qui correspond à votre version.

## FAQ

Certaines questions sont souvent posées. Vérifiez ceci avant de créer un problème :

* [FAQ Electron](faq.md)

## Guides et tutoriels

### Démarrage rapide

* [Guide de démarrage rapide](tutorial/quick-start.md)
  * [Prerequisites](tutorial/quick-start.md#prerequisites)
  * [Créer une application élémentaire](tutorial/quick-start.md#create-a-basic-application)
  * [Exécuter votre application](tutorial/quick-start.md#run-your-application)
  * [Préparer l'application pour la distribuer](tutorial/quick-start.md#package-and-distribute-the-application)

### Apprendre les bases

* [Modèle des processus d'Electron](tutorial/quick-start.md#application-architecture)
  * [فرآیندهای اصلی و رندرینگparsian](tutorial/quick-start.md#main-and-renderer-processes)
  * [Electron API](tutorial/quick-start.md#electron-api)
  * [Node.js API](tutorial/quick-start.md#nodejs-api)
* Ajouter des fonctionnalités à votre App
  * [Notifications](tutorial/notifications.md)
  * [Documents récents](tutorial/recent-documents.md)
  * [Progression de l'Application](tutorial/progress-bar.md)
  * [Menu Dock personnalisé](tutorial/macos-dock.md)
  * [Barre des tâches Windows personnalisée](tutorial/windows-taskbar.md)
  * [Actions de bureau Linux personnalisées](tutorial/linux-desktop-actions.md)
  * [Raccourcis clavier](tutorial/keyboard-shortcuts.md)
  * [Détection en ligne/hors ligne](tutorial/online-offline-events.md)
  * [Fichier représenté pour BrowserWindows sur macOS](tutorial/represented-file.md)
  * [Fichier natif Drag & Drop](tutorial/native-file-drag-drop.md)
  * [Rendu Offscreen](tutorial/offscreen-rendering.md)
  * [Dark Mode](tutorial/dark-mode.md)
  * [Intégrer le Web dans Electron](tutorial/web-embeds.md)
* [Les Boilerplates et CLIs](tutorial/boilerplates-and-clis.md)
  * [Boilerplate vs CLI](tutorial/boilerplates-and-clis.md#boilerplate-vs-cli)
  * [electron-forge](tutorial/boilerplates-and-clis.md#electron-forge)
  * [electron-builder](tutorial/boilerplates-and-clis.md#electron-builder)
  * [electron-react-boilerplate](tutorial/boilerplates-and-clis.md#electron-react-boilerplate)
  * [Autres outils et boilerplates](tutorial/boilerplates-and-clis.md#other-tools-and-boilerplates)

### Sujets Avancés

* Architecture d'une application
  * [Utilisation des Modules Natifs de Node.js](tutorial/using-native-node-modules.md)
  * [Stratégies de performance](tutorial/performance.md)
  * [Stratégies de sécurité](tutorial/security.md)
* [Accessibilité](tutorial/accessibility.md)
  * [Activation manuelle des fonctionnalités d’accessibilité](tutorial/accessibility.md#manually-enabling-accessibility-features)
* [Test et débogage](tutorial/application-debugging.md)
  * [Débogguer le Processus Principal](tutorial/debugging-main-process.md)
  * [Débogage avec Visual Studio Code](tutorial/debugging-vscode.md)
  * [Utilisation de Selenium et WebDriver](tutorial/using-selenium-and-webdriver.md)
  * [Tests sur les systèmes CI (Travis, Jenkins)](tutorial/testing-on-headless-ci.md)
  * [Extension DevTools](tutorial/devtools-extension.md)
  * [Test automatisé avec un driver personnalisé](tutorial/automated-testing-with-a-custom-driver.md)
* [Distribution](tutorial/application-distribution.md)
  * [Plateformes supportées](tutorial/support.md#supported-platforms)
  * [Signature de code](tutorial/code-signing.md)
  * [Mac App Store](tutorial/mac-app-store-submission-guide.md)
  * [Windows Store](tutorial/windows-store-guide.md)
  * [Snapcraft](tutorial/snapcraft.md)
* [Mises à jour](tutorial/updates.md)
  * [Déploiement d’un serveur de mise à jour](tutorial/updates.md#deploying-an-update-server)
  * [Implémentation des mises à jour dans votre application](tutorial/updates.md#implementing-updates-in-your-app)
  * [Application des mises à jour](tutorial/updates.md#applying-updates)
* [Obtenir de l'aide](tutorial/support.md)

## Tutoriels détaillés

Ces tutoriels individuels développent les sujets abordés dans le guide ci-dessus.

* [Installer Electron](tutorial/installation.md)
  * [Les proxys](tutorial/installation.md#proxies)
  * [Mirroirs et Caches personnalisés](tutorial/installation.md#custom-mirrors-and-caches)
  * [Résolution de problème](tutorial/installation.md#troubleshooting)
* Releases d'Electron & Feedback
  * [Versioning Policy](tutorial/electron-versioning.md)
  * [Calendrier de release99](tutorial/electron-timelines.md)
* [Packaging du code source de l'App avec asar](tutorial/application-packaging.md)
  * [Créer une archive asar](tutorial/application-packaging.md#generating-asar-archives)
  * [Lire une archive asar](tutorial/application-packaging.md#using-asar-archives)
  * [Limitations](tutorial/application-packaging.md#limitations-of-the-node-api)
  * [Ajouter des fichiers non empaquetés dans une archive asar](tutorial/application-packaging.md#adding-unpacked-files-to-asar-archives)
* [Tester le CDM Widevine](tutorial/testing-widevine-cdm.md)

---

* [Glossaire des termes](glossary.md)

## Références de l'API

* [Synopsis](api/synopsis.md)
* [Process Object](api/process.md)
* [Commandes Supportées](api/command-line-switches.md)
* [Variables d'environnement](api/environment-variables.md)
* [Chrome Extensions Support](api/extensions.md)
* [Modifications importantes de l'API](breaking-changes.md)

### Éléments DOM Personnalisé :

* [`File` Object](api/file-object.md)
* [`<webview>` Tag](api/webview-tag.md)
* [`window.open` Function](api/window-open.md)
* [`BrowserWindowProxy` Object](api/browser-window-proxy.md)

### Modules pour le processus principal :

* [app](api/app.md)
* [autoUpdater](api/auto-updater.md)
* [BrowserView](api/browser-view.md)
* [BrowserWindow](api/browser-window.md)
* [contentTracing](api/content-tracing.md)
* [dialog](api/dialog.md)
* [globalShortcut](api/global-shortcut.md)
* [Achat inApp](api/in-app-purchase.md)
* [ipcMain](api/ipc-main.md)
* [Menu](api/menu.md)
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

### Modules pour le processus de rendu (Page Web) :

* [desktopCapturer](api/desktop-capturer.md)
* [ipcRenderer](api/ipc-renderer.md)
* [remote](api/remote.md)
* [webFrame](api/web-frame.md)

### Modules pour les deux processus :

* [clipboard](api/clipboard.md)
* [crashReporter](api/crash-reporter.md)
* [nativeImage](api/native-image.md)
* [shell](api/shell.md)

## Développement

Voir [development/README.md](development/README.md)
