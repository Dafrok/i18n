# Pasek postępu w pasku zadań (Windows, macOS, Unity)

## Przegląd

A progress bar enables a window to provide progress information to the user without the need of switching to the window itself.

On Windows, you can use a taskbar button to display a progress bar.

![Windows Progress Bar][1]

On macOS, the progress bar will be displayed as a part of the dock icon.

![macOS Progress Bar][2]

On Linux, the Unity graphical interface also has a similar feature that allows you to specify the progress bar in the launcher.

![Linux Progress Bar][3]

> NOTE: on Windows, each window can have its own progress bar, whereas on macOS and Linux (Unity) there can be only one progress bar for the application.

----

All three cases are covered by the same API - the [`setProgressBar()`][setprogressbar] method available on an instance of `BrowserWindow`. To indicate your progress, call this method with a number between `0` and `1`. For example, if you have a long-running task that is currently at 63% towards completion, you would call it as `setProgressBar(0.63)`.

Setting the parameter to negative values (e.g. `-1`) will remove the progress bar, whereas setting it to values greater than `1` (e.g. `2`) will switch the progress bar to indeterminate mode (Windows-only -- it will clamp to 100% otherwise). In this mode, a progress bar remains active but does not show an actual percentage. Use this mode for situations when you do not know how long an operation will take to complete.

Zobacz [Dokumentacje API dla większej liczby opcji i trybów][setprogressbar].

## Przykład

Zaczynając od działającej aplikacji z [Poradnika szybkiego startu](quick-start.md), dodaj następujące linie do pliku `main.js`:

```javascript
const { BrowserWindow } = require('electron')
const win = new BrowserWindow()

win.setProgressBar(0.5)
```

After launching the Electron application, you should see the bar in the dock (macOS) or taskbar (Windows, Unity), indicating the progress percentage you just defined.

![macOS dock progress bar](../images/dock-progress-bar.png)

For macOS, the progress bar will also be indicated for your application when using [Mission Control](https://support.apple.com/en-us/HT204100):

![Mission Control Progress Bar](../images/mission-control-progress-bar.png)

[1]: https://cloud.githubusercontent.com/assets/639601/5081682/16691fda-6f0e-11e4-9676-49b6418f1264.png
[2]: ../images/macos-progress-bar.png
[3]: ../images/linux-progress-bar.png
[setprogressbar]: ../api/browser-window.md#winsetprogressbarprogress-options
[setprogressbar]: ../api/browser-window.md#winsetprogressbarprogress-options
