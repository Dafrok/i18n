# 任务栏的进度条 (Windows, macOS, Unity)

## 概览

A progress bar enables a window to provide progress information to the user without the need of switching to the window itself.

On Windows, you can use a taskbar button to display a progress bar.

![Windows Progress Bar](https://cloud.githubusercontent.com/assets/639601/5081682/16691fda-6f0e-11e4-9676-49b6418f1264.png)

On macOS, the progress bar will be displayed as a part of the dock icon.

![macOS Progress Bar](../images/macos-progress-bar.png)

On Linux, the Unity graphical interface also has a similar feature that allows you to specify the progress bar in the launcher.

![Linux Progress Bar](../images/linux-progress-bar.png)

> NOTE: on Windows, each window can have its own progress bar, whereas on macOS and Linux (Unity) there can be only one progress bar for the application.

----

All three cases are covered by the same API - the [`setProgressBar()`](../api/browser-window.md#winsetprogressbarprogress-options) method available on an instance of `BrowserWindow`. To indicate your progress, call this method with a number between `0` and `1`. For example, if you have a long-running task that is currently at 63% towards completion, you would call it as `setProgressBar(0.63)`.

Setting the parameter to negative values (e.g. `-1`) will remove the progress bar, whereas setting it to values greater than `1` (e.g. `2`) will switch the progress bar to indeterminate mode (Windows-only -- it will clamp to 100% otherwise). In this mode, a progress bar remains active but does not show an actual percentage. Use this mode for situations when you do not know how long an operation will take to complete.

参见 [API documentation for more options and modes](../api/browser-window.md#winsetprogressbarprogress-options)。

## 示例

从 起从[快速启动指南](quick-start.md)开始运行，将以下行添加到 `main.js` 文件：

```javascript fiddle='docs/fiddles/features/progress-bar'
const { BrowserWindow } = require('electron')
const win = new BrowserWindow()

win.setProgressBar(0.5)
```

After launching the Electron application, you should see the bar in the dock (macOS) or taskbar (Windows, Unity), indicating the progress percentage you just defined.

![macOS dock progress bar](../images/dock-progress-bar.png)

For macOS, the progress bar will also be indicated for your application when using [Mission Control](https://support.apple.com/en-us/HT204100):

![Mission Control Progress Bar](../images/mission-control-progress-bar.png)
