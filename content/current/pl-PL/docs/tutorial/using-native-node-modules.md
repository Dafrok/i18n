# Używanie Natywnych Modułów Node.JS

Native Node.js modules are supported by Electron, but since Electron has a different [application binary interface (ABI)](https://en.wikipedia.org/wiki/Application_binary_interface) from a given Node.js binary (due to differences such as using Chromium's BoringSSL instead of OpenSSL), the native modules you use will need to be recompiled for Electron. W przeciwnym razie otrzymasz następującą klasę błędu, gdy spróbujesz uruchomić aplikację:

```sh
Błąd: Moduł '/path/to/native/module.node'
został skompilowany z inną wersją Node.js za pomocą
NODE_MODULE_VERSION $XYZ. Ta wersja Node.js wymaga
NODE_MODULE_VERSION $ABC. Spróbuj ponownie skompilować lub ponownie zainstalować
moduł (na przykład używając `npm rebuild` lub `npm install`).
```

## Jak zainstalować natywne moduły

Istnieje kilka różnych sposobów instalacji natywnych modułów:

### Instalowanie modułów i odbudowa dla Electron

Możesz zainstalować moduły, takie jak inne projekty węzła, a następnie przebudować moduły dla Electrona z pakietem [`electron-rebuild`](https://github.com/electron/electron-rebuild). This module can automatically determine the version of Electron and handle the manual steps of downloading headers and rebuilding native modules for your app. If you are using [Electron Forge](https://electronforge.io/), this tool is used automatically in both development mode and when making distributables.

For example, to install the standalone `electron-rebuild` tool and then rebuild modules with it via the command line:

```sh
npm install --save-dev electron-rebuild

# Za każdym razem gdy uruchamiasz "npm install", uruchamiasz to:
./node_modules/.bin/electron-rebuild

# Jeśli masz problem na Windows, spróbuj:
.\node_modules\.bin\electron-rebuild.cmd
```

For more information on usage and integration with other tools such as [Electron Packager](https://github.com/electron/electron-packager), consult the project's README.

### Używając `npm`

Ustawiając kilka zmiennych środowiskowych, możesz użyć `npm` , aby zainstalować moduły bezpośrednio.

Na przykład, aby zainstalować wszystkie zależności dla Electron:

```sh
# Wersja Electrona.
eksport npm_config_target=1.2.3
# Architektura Electrona, zobacz https://electronjs.org/docs/tutorial/support#supported-platform
# dla obsługiwanych architektur.
export npm_config_arch=x64
export npm_config_target_arch=x64
# Pobierz nagłówki dla Electron.
eksportuj npm_config_disturl=https://electronjs.org/headers
# Opowiedz node-pregyp, który budujemy dla Electron.
eksportuj npm_config_runtime=electron
# Opowiedz node-pregyp aby zbudować moduł z kodu źródłowego.
eksportuj npm_config_build_from_source=true
# Zainstaluj wszystkie zależności i zapisz pamięć podręczną do ~/.electron-gyp.
HOME=~/.electron-gyp npm install
```

### Budowa ręczna dla Electrona

Jeśli jesteś deweloperem rozwijającym moduł natywny i chcesz przetestować go w Electron, możesz ręcznie odbudować moduł dla Electrona. Możesz użyć `node-gyp` bezpośrednio, aby zbudować Electron:

```sh
cd /path-to-module/
HOME=~/.electron-gyp przebuduj --target=1.2.3 --arch=x64 --dist-url=https://electronjs.org/headers
```

* `HOME=~/.electron-gyp` zmienia miejsce, gdzie znaleźć nagłówki programistyczne.
* `--target=1.2.3` jest wersją Electrona.
* `--dist-url=...` określa, gdzie pobrać nagłówki.
* `--arch=x64` mówi, że moduł jest zbudowany dla systemu 64-bitowego.

### Budowa ręczna dla niestandardowej budowy Electrona

To compile native Node modules against a custom build of Electron that doesn't match a public release, instruct `npm` to use the version of Node you have bundled with your custom build.

```sh
npm przebudowa --nodedir=/path/to/electron/vendor/node
```

## Rozwiązywanie problemów

Jeśli zainstalowałeś natywny moduł i znalazłeś że nie działa, musisz sprawdzić następujące rzeczy:

* Gdy masz wątpliwości, najpierw uruchom `electron-rebuild`.
* Upewnij się, że moduł natywny jest kompatybilny z docelową platformą i architekturą dla twojej aplikacji Electron.
* Upewnij się, że `win_delay_load_hook` nie jest ustawiony na `false` w `binding.gyp` modułu.
* Po ulepszeniu Electrona, zwykle musisz przebudować moduły.

### Notatka o `win_delay_load_hook`

W systemie Windows, domyślnie `node-gyp` łączy natywne moduły z `node.dll`. Jednak w Electron 4.x i wyższej symbole potrzebne przez natywne moduły są eksportowane przez `electron. xe`i nie ma `węzła.dll`. Aby załadować moduły natywne na Windows, `node-gyp` instaluje [opóźnienie hak](https://msdn.microsoft.com/en-us/library/z9h1h6ty.aspx) , który wyzwala po załadowaniu modułu natywnego, i przekierowuje węzeł `. ll` odwołanie do użycia pliku wykonywalnego zamiast szukać `węzła. lj` w ścieżce wyszukiwania w bibliotece (co nic nie powstał). W związku z tym, w Electron 4.x i wyższej, `'win_delay_load_hook': 'true'` jest wymagany do załadowania natywnych modułów.

Jeśli pojawi się błąd podobny do `Moduł nie zarejestrował się samowystarczalnie`, lub `Określona
procedura nie została znaleziona`, może to oznaczać, że moduł, który próbujesz użyć , nie zawierał prawidłowo zaczepu obciążenia opóźnień.  Jeśli moduł jest zbudowany z node-gyp, upewnij się, że zmienna `win_delay_load_hook` jest ustawiona na `true` w binding `. yp` plik i nigdzie go nie nadpisuje.  If the module is built with another system, you'll need to ensure that you build with a delay-load hook installed in the main `.node` file. Twoje `link.exe` wywołanie powinno wyglądać tak:

```plaintext
 link.exe /OUT:"foo.node" "...\node.lib" Delimp.lib /DELAYLOAD:node.exe /DLL
     "my_addon.obj" "win_delay_load_hook.obj"
```

W szczególności ważne jest, aby:

* łączysz się z `node.lib` z _Electron_ a nie Node. If you link against the wrong `node.lib` you will get load-time errors when you require the module in Electron.
* wliczasz flagę `/DELAYLOAD:node.exe`. Jeśli węzeł `. link xe` nie jest opóźniony, wtedy hak opóźnień nie będzie miał szansy na wystrzelenie i symbole węzła nie zostaną prawidłowo rozwiązane.
* `win_delay_load_hook.obj` jest połączony bezpośrednio z końcową DLL. Jeśli hak jest ustawiony w zależnej DLL, nie będzie strzelał we właściwym czasie.

Zobacz [`node-gyp`](https://github.com/nodejs/node-gyp/blob/e2401e1395bef1d3c8acec268b42dc5fb71c4a38/src/win_delay_load_hook.cc) dla przykładowego haka opóźnień, jeśli implementujesz własny.

## Moduły, które opierają się na `prebuild`

[`prebuild`](https://github.com/prebuild/prebuild) zapewnia sposób na opublikowanie natywnych modułów węzła z wstępnie wbudowanymi binarami dla wielu wersji węzła i Electron.

If the `prebuild`-powered module provide binaries for the usage in Electron, make sure to omit `--build-from-source` and the `npm_config_build_from_source` environment variable in order to take full advantage of the prebuilt binaries.

## Moduły, które opierają się na `node-pregyp`

Narzędzie [`node-pregyp`](https://github.com/mapbox/node-pre-gyp) zapewnia sposób na wdrożenie modułów natywnego węzła z wstępnie zbudowanymi binarami, i wiele popularnych modułów tego używa.

Sometimes those modules work fine under Electron, but when there are no Electron-specific binaries available, you'll need to build from source. Because of this, it is recommended to use `electron-rebuild` for these modules.

If you are following the `npm` way of installing modules, you'll need to pass `--build-from-source` to `npm`, or set the `npm_config_build_from_source` environment variable.
