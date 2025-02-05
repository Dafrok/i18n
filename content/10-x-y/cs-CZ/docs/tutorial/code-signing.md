# Podepsání kódu

Podpis kódu je bezpečnostní technologie, kterou používáte k potvrzení, že jste vytvořili aplikaci .

Na macOS systém umí detekovat jakékoliv změny aplikace, ať už je změna spuštěna omylem nebo škodlivým kódem.

V systému Windows systém přiřadí úroveň důvěry vašemu kódu k podepisování certifikátu , který pokud nemáte, nebo pokud je vaše důvěryhodnost nízká, způsobí bezpečnostní dialogová okna, která se budou zobrazovat při používání vaší aplikace.  Trust level buduje v průběhu času, takže je lepší začít podepisovat kód co nejdříve.

I když je možné distribuovat nepodepsané aplikace, není to doporučeno. Windows i macOS ve výchozím nastavení zabrání stahování nebo spuštění nepodepsaných aplikací. Počínaje macOS Catalina (verze 10.15), musí uživatelé procházet několika manuálními kroky k otevření nepodepsaných aplikací.

![macOS Catalina Gatekeeper varování: Aplikaci nelze otevřít, protože
vývojář nelze ověřit](../images/gatekeeper.png)

Jak vidíte, uživatelé dostávají dvě možnosti: přesuňte aplikaci přímo do koše nebo zrušte její spuštění. Nechcete, aby uživatelé viděli tento dialog.

Pokud budujete Electron aplikaci, kterou hodláte balit a distribuovat, měla by být označena kódem.

# Podepisuji & notarizuji macOS sestavení

Správná příprava macOS aplikací pro vydání vyžaduje dva kroky: Zaprvé, aplikace musí být označena kódem. Pak musí být aplikace nahrána do Apple pro proces nazvaný "notarizace", kde automatizované systémy dále ověří, že vaše aplikace nedělá nic, aby ohrozila její uživatele.

Chcete-li spustit proces, ujistěte se, že splníte požadavky pro podepsání a notarizaci vaší aplikace:

1. Enroll in the [Apple Developer Program][] (requires an annual fee)
2. Stáhnout a nainstalovat [Xcode][] - to vyžaduje počítač s macOS
3. Generate, download, and install [signing certificates][]

Electronův ekosystém upřednostňuje konfiguraci a svobodu, takže existuje více způsobů, jak podepsat vaši aplikaci a notarizovat.

## `elektronická forge`

Pokud používáte Electronův oblíbený nástroj pro sestavení, vyžaduje vaše aplikace podpis a notarizaci několik doplňků k vaší konfiguraci. [Forge](https://electronforge.io) je kolekce oficiálních nástrojů Electronu pomocí [`elektronického balíku`][], [`elektronická osx-značka`][]a [`elektronická notarizace`][] pod hákem.

Podívejme se na příklad konfigurace se všemi požadovanými poli. Ne všechny z nich jsou povinné: nástroje budou dostatečně chytré, aby automaticky našly vhodnou `identitu`, Například doporučujeme, abyste byli explicitní.

```json
{
  "name": "my-app",
  "version": "0.0. ",
  "config": {
    "forge": {
      "packagerConfig": {
        "osxSign": {
          "identity": "Export ID Application: Felix Rieseberg (LT94ZKYDCJ)",
          "ztížené runtime": true,
          "nároky": "nároky. list",
          "entitlements-inherit": "entitlements. list,
          "signature-flags": "library"
        },
        "osxNotarize": {
          "appleId": "felix@felix. un",
          "appleIdPassword": "my-apple-id-heslo",
        }
      }
    }
  }
}
```

`plist` soubor, na který se zde odkazuje, potřebuje následující oprávnění pro macOS, pro zajištění bezpečnostních mechanismů Apple, že vaše aplikace dělá tyto věci bez ohledu na újmu:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www. pple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>com.apple.security.cs. llow-jit</key>
    <true/>
    <key>com.apple.security.cs. llow-unsigned-executable-memory</key>
    <true/>
    <key>com. pple.security.cs.debugger</key>
    <true/>
  </dict>
</plist>
```

Chcete-li vše vidět v akci, podívejte se na zdrojový kód Electron Fiddle, [zejména jeho `elektronická forge` konfigurace soubor](https://github.com/electron/fiddle/blob/master/forge.config.js).


## `elektronický stavitel`

Electron Builder přichází s vlastním řešením pro podepsání vaší žádosti. naleznete [jeho dokumentaci zde](https://www.electron.build/code-signing).

## `elektronický balík`

Pokud nepoužíváte integrovaný vývojový plynovod jako Forge nebo Builder, pravděpodobně používáte [`elektronický balík`][], která obsahuje [`elektronický osx-znak`][] a [`elektronicko-notarize`][].

Pokud používáte API Packageru, můžete použít [v konfiguraci, že obě značky a notarizuje vaši aplikaci](https://electron.github.io/electron-packager/master/interfaces/electronpackager.options.html).

```js
const packager = require('electron-packager')

packager({
  dir: '/path/to/my/app',
  osxSign: {
    identita: 'Application of Developer ID: Felix Rieseberg (LT94ZKYDCJ)',
    'zestátněný pracovní čas': true,
    oprávnění: 'nároky. list,
    'entitlements-inherit': 'entitlements. list',
    'signature-flags': 'library'
  },
  osxNotarize: {
    appleId: 'felix@felix. un',
    appleIdPassword: 'my-apple-id-password'
  }
})
```

`plist` soubor, na který se zde odkazuje, potřebuje následující oprávnění pro macOS, pro zajištění bezpečnostních mechanismů Apple, že vaše aplikace dělá tyto věci bez ohledu na újmu:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www. pple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>com.apple.security.cs. llow-jit</key>
    <true/>
    <key>com.apple.security.cs. llow-unsigned-executable-memory</key>
    <true/>
    <key>com. pple.security.cs.debugger</key>
    <true/>
  </dict>
</plist>
```

## Mac App Store

See the [Mac App Store Guide][].

# Podepisování sestavení Windows

Před podpisem Windows sestavení musíte udělat následující:

1. Získejte podepsaný certifikát kódu Windows Authenticode (vyžaduje roční poplatek)
2. Nainstalujte Visual Studio pro získání podepisovacího nástroje (stačí bezplatná [komunita Edition](https://visualstudio.microsoft.com/vs/community/))

Můžete získat certifikát s podpisem kódu od mnoha prodejců. Ceny se liší, takže může mít cenu za váš čas nakupovat. Mezi populární prodejce patří:

* [digikert](https://www.digicert.com/code-signing/microsoft-authenticode.htm)
* [Comodo](https://www.comodo.com/landing/ssl-certificate/authenticode-signature/)
* [GoDaddy](https://au.godaddy.com/web-security/code-signing-certificate)
* Mimo jiné prosím nakupujte a najděte si, co vyhovuje vašim potřebám, Google je Váš přítel 😄

Existuje řada nástrojů pro podepsání vaší zabalené aplikace:

- [`elektronický instalátor`][] vygeneruje instalační program pro okna a podepíše ho pro
- [`elektronická forge`][] může podepisovat instalační programy, které generuje prostřednictvím Squirrel.Windows nebo MSI cílů.
- [`electron-builder`][] can sign some of its windows targets

## Windows Store

See the [Windows Store Guide][].

[Apple Developer Program]: https://developer.apple.com/programs/
[`electron-builder`]: https://github.com/electron-userland/electron-builder
[`elektronická forge`]: https://github.com/electron-userland/electron-forge
[`elektronická osx-značka`]: https://github.com/electron-userland/electron-osx-sign
[`elektronický osx-znak`]: https://github.com/electron-userland/electron-osx-sign
[`elektronického balíku`]: https://github.com/electron/electron-packager
[`elektronický balík`]: https://github.com/electron/electron-packager
[`elektronická notarizace`]: https://github.com/electron/electron-notarize
[`elektronicko-notarize`]: https://github.com/electron/electron-notarize
[`elektronický instalátor`]: https://github.com/electron/windows-installer
[Xcode]: https://developer.apple.com/xcode
[signing certificates]: https://github.com/electron/electron-osx-sign/wiki/1.-Getting-Started#certificates
[Mac App Store Guide]: mac-app-store-submission-guide.md
[Windows Store Guide]: windows-store-guide.md
