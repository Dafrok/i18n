# Aselerador

> Ipaliwanag ang mga shortcut ng keyboard.

Accelerators are Strings that can contain multiple modifiers and a single key code, combined by the `+` character, and are used to define keyboard shortcuts throughout your application.

Mga Halimbawa:

* `CommandOrControl+A`
* `CommandOrControl+Shift+Z`

Ang mga shortcut ay irehistro kasabay ang modyul ng [`globalShortcut`](global-shortcut.md) na gamit ang paraan ng [`register`](global-shortcut.md#globalshortcutregisteraccelerator-callback), i.e.

```javascript
const { app, globalShortcut } = require('electron')

app.whenReady().then(() => {
  // Register a 'CommandOrControl+Y' shortcut listener.
  globalShortcut.register('CommandOrControl+Y', () => {
    // Gumawa ng bagay-bagay kapag ang Y at alinman sa Command/Control ay napindot na.
  })
})
```

## Paunawa sa Platform

Sa Linux at Windows, ang key na `Command` ay walang anumang epekto kaya dapat gamitin ang `CommandOrControl` na kumakatawan sa mga `Command` sa macOS at `Control` sa Linux at Windows upang bigyang kahulugan ang ilang mga aselerador.

Use `Alt` instead of `Option`. The `Option` key only exists on macOS, whereas the `Alt` key is available on all platforms.

Ang key ng `Super` ay naka-balangkas sa key ng `Windows` sa Windows at Linux at `Cmd` naman sa macOS.

## Ang magagamit na mga modifier

* `Command` (o `Cmd` kapag pinaikli)
* `Control` (o `Ctrl` kapag pinaikli)
* `CommandOrControl` (o `CmdOrCtrl` kapag pinaikli)
* `Alt`
* `Option`
* `AltGr`
* `Shift`
* `Super`

## Ang mga key code na magagamit

* Mula `0` hanggang `9`
* Mula `A` hanggang `Z`
* Mula `F1` hanggang `F24`
* Punctuation like `~`, `!`, `@`, `#`, `$`, etc.
* `Plus`
* `Space`
* `Tab`
* `Capslock`
* `Numlock`
* `Scrolllock`
* `Backspace`
* `Delete`
* `Insert`
* `Return` (o `Enter` bilang alyas)
* `Up`, `Down`, `Left`, at `Right`
* `Home` at `End`
* `PageUp` at `PageDown`
* `Escape` (o `Esc` kapag pinaikli)
* `VolumeUp`, `VolumeDown` at `VolumeMute`
* `MediaNextTrack`, `MediaPreviousTrack`, `MediaStop` at `MediaPlayPause`
* `PrintScreen`
* NumPad Keys
  * `num0` - `num9`
  * `numdec` - decimal key
  * `numadd` - numpad `+` key
  * `numsub` - numpad `-` key
  * `nummult` - numpad `*` key
  * `numdiv` - numpad `÷` key
