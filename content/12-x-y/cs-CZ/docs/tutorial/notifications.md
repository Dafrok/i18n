# Oznámení (Windows, Linux, macOS)

## Přehled

Všechny tři operační systémy poskytují prostředky pro zasílání oznámení uživateli. Technika zobrazování oznámení se liší v hlavních procesech a procesech Renderer.

Pro proces Renderer Electron pohodlně umožňuje vývojářům odesílat oznámení pomocí [HTML5 Notification API](https://notifications.spec.whatwg.org/). pomocí nativního oznámení aktuálně spuštěného operačního systému k jeho zobrazení.

Chcete-li zobrazit oznámení v hlavním procesu, musíte použít modul [Oznámení](../api/notification.md).

## Ukázka

### Zobrazit oznámení v procesu vykreslování

Předpokládejme, že máte fungující Electron aplikaci z [Rychlého startu](quick-start.md), přidejte následující řádek do indexu `. tml` soubor před uzavřením značky `</body>`:

```html
<script src="renderer.js"></script>
```

a přidejte soubor `render.js`:

```js
const myNotification = nové oznámení ('Title', {
  body: 'Notification from the Renderer process'
})

myNotification.onclick = () => {
  console.log('Kliknutí na oznámení')
}
```

Po spuštění Electron aplikace byste měli vidět oznámení:

![Oznámení v procesu vykreslování](../images/notification-renderer.png)

Pokud otevřete konzoli a pak klikněte na oznámení, uvidíte zprávu, která byla vygenerována po spuštění události `na kliknutí`:

![Onclick zpráva pro oznámení](../images/message-notification-renderer.png)

### Zobrazit oznámení v hlavním procesu

Začíná fungující aplikací z [Rychlý startovací průvodce](quick-start.md), aktualizujte soubor `main.js` o následující řádky:

```js
const { Notification } = require('electron')

funkce showNotification () {
  const notification = {
    title: 'Basic Notification',
    body: 'Notification from the Main process'
  }
  new Notification(notifikace).show()
}

app.whenReady().then(createWindow).then(showNotification)
```

Po spuštění Electron aplikace byste měli vidět oznámení:

![Oznámení v hlavním procesu](../images/notification-main.png)

## Další informace

Přestože jsou kódy a uživatelská zkušenost mezi operačními systémy podobná, existují jemné rozdíly.

### Windows

* On Windows 10, a shortcut to your app with an [Application User Model ID][app-user-model-id] must be installed to the Start Menu. Toto může být přepsáno během vývoje, takže přidejte `node_modules\electron\dist\electron.exe` do tvého Start Menu také trik. Přejděte do souboru v Průzkumníku, klepněte pravým tlačítkem myši a "Připnout pro spuštění menu". Potom budete muset přidat řádek `app.setAppUserModelId(process.execPath)` do vašeho hlavního procesu pro zobrazení oznámení.
* On Windows 8.1 and Windows 8, a shortcut to your app with an [Application User Model ID][app-user-model-id] must be installed to the Start screen. Všimněte si však, že nemusí být připnut na úvodní obrazovku.
* V systému Windows 7 fungují notifikace prostřednictvím vlastní implementace, která vizuálně připomíná nativní na novějších systémech.

Electron se pokouší automatizovat práci kolem ID uživatelského modelu aplikace. When Electron is used together with the installation and update framework Squirrel, [shortcuts will automatically be set correctly][squirrel-events]. Kromě toho Electron zjistí, že byla použita veverka a automaticky zavolá `app.setAppModelId()` se správnou hodnotou. During development, you may have to call [`app.setAppUserModelId()`][set-app-user-model-id] yourself.

V systému Windows 8 je navíc maximální délka těla oznámení 250 znaků, s týmem Windows, který doporučuje, aby oznámení byla uchovávána až 200 znaků. Toto omezení bylo odstraněno v systému Windows 10 a tým Windows požádal vývojáře, aby byli rozumní. Pokus o zaslání obrovského množství textu API (tisíce znaků) může vést k nestabilitě.

#### Rozšířená oznámení

Pozdější verze systému Windows umožňují pokročilé oznámení, s vlastními šablonami, obrázky a další flexibilní prvky. Chcete-li odeslat tato oznámení (buď z hlavního procesu, nebo z procesu renderování), použijte uživatelský modul [elektronická oznámení](https://github.com/felixrieseberg/electron-windows-notifications). který používá doplňky nativního uzlu k odesílání `ToastNotification` a `objektů TileNotification`.

Zatímco oznámení včetně tlačítek fungují s `elektronickými okny`, zpracování odpovědí vyžaduje použití [`elektronických oken - interaktivních oznámení`](https://github.com/felixrieseberg/electron-windows-interactive-notifications) která pomáhá s registrací požadovaných komponent COM a voláním do vaší Electron aplikace se zadanými uživatelskými daty.

#### Režim Tichých hodin / prezentace

Chcete-li zjistit, zda máte povoleno posílat oznámení, použijte uživatelský modul [elektronický stav oznámení](https://github.com/felixrieseberg/electron-notification-state).

To vám umožní určit, zda Windows bude či nebude tiše vyhodit oznámení pryč.

### macOS

Notifications are straight-forward on macOS, but you should be aware of [Apple's Human Interface guidelines regarding notifications][apple-notification-guidelines].

Upozorňujeme, že oznámení mají velikost 256 bajtů a pokud překročíte tento limit, budou zkrácena .

#### Rozšířená oznámení

Pozdější verze macOS umožňují oznámení se vstupním polem, což uživateli umožňuje rychle odpovědět na oznámení. In order to send notifications with an input field, use the userland module [node-mac-notifier][node-mac-notifier].

#### Nerušit / Stav relace

To detect whether or not you're allowed to send a notification, use the userland module [electron-notification-state][electron-notification-state].

To vám umožní zjistit dopředu, zda budou či nebudou oznámení zobrazena.

### Linux

Notifications are sent using `libnotify` which can show notifications on any desktop environment that follows [Desktop Notifications Specification][notification-spec], including Cinnamon, Enlightenment, Unity, GNOME, KDE.

[apple-notification-guidelines]: https://developer.apple.com/macos/human-interface-guidelines/system-capabilities/notifications/

[node-mac-notifier]: https://github.com/CharlieHess/node-mac-notifier

[electron-notification-state]: https://github.com/felixrieseberg/electron-notification-state

[notification-spec]: https://developer.gnome.org/notification-spec/
[app-user-model-id]: https://msdn.microsoft.com/en-us/library/windows/desktop/dd378459(v=vs.85).aspx
[set-app-user-model-id]: ../api/app.md#appsetappusermodelidid-windows
[squirrel-events]: https://github.com/electron/windows-installer/blob/master/README.md#handling-squirrel-events
