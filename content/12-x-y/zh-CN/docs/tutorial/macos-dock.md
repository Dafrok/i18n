# macOS Dock

## 概览

Electron有API来配置macOS Dock中的应用程序图标。 A macOS-only API exists to create a custom dock menu, but Electron also uses the app dock icon as the entry point for cross-platform features like [recent documents][recent-documents] and [application progress][progress-bar].

一个自定义的Dock项也普遍用于为那些用户不愿意为之打开整个应用窗口的任务添加快捷方式。

__Terminal.app 的 Dock 菜单:__

![基座菜单][3]

要设置您的自定义基座菜单，您需要使用 [`app.dock.setmenu`](../api/dock.md#docksetmenumenu-macos) API， 它仅在 macOS 上可用。

## 示例

Starting with a working application from the [Quick Start Guide](quick-start.md), update the `main.js` file with the following lines:

```javascript
const { app, Menu } = require('electron')

const dockMenu = Menu.buildFromTemplate([
  {
    label: 'New Window',
    click () { console.log('New Window') }
  }, {
    label: 'New Window with Settings',
    submenu: [
      { label: 'Basic' },
      { label: 'Pro' }
    ]
  },
  { label: 'New Command...' }
])

app.whenReady().then(() => {
  app.dock.setMenu(dockMenu)
})
```

启动 Electron 应用程序后，右键点击应用程序图标。 您应该看到您刚刚定义的自定义菜单：

![macOS 停靠菜单](../images/macos-dock-menu.png)

[3]: https://cloud.githubusercontent.com/assets/639601/5069962/6032658a-6e9c-11e4-9953-aa84006bdfff.png
[recent-documents]: ./recent-documents.md
[progress-bar]: ./progress-bar.md
