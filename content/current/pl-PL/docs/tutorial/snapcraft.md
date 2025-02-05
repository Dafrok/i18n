# Przewodnik Snapcrafta (Ubuntu Software Center & Więcej)

Ten przewodnik zawiera informacje o tym, jak spakować aplikację Electron dla każdego środowiska Snapcraft, w tym Centrum Oprogramowania Ubuntu

## Tło i wymagania

wraz z szerszą społecznością Linuksa, Canonical ma na celu rozwiązanie wielu z wspólnych problemów z instalacją oprogramowania z projektem [`snapcraft`](https://snapcraft.io/) . Snaps to pakiety oprogramowania konteneryzowanego, które zawierają wymagane zależności, automatyczną aktualizację i pracują na wszystkich głównych dystrybucjach Linuksa bez modyfikacji systemu.

Istnieją trzy sposoby na utworzenie pliku `.snap`:

1) Używanie [`electron-forge`](https://github.com/electron-userland/electron-forge) lub [`electron-builder`](https://github.com/electron-userland/electron-builder)oba narzędzia, które mają z `przyciągnij` wsparcie z pudełka. To najprostsza opcja. 2) Korzystanie z `electron-installer-snap`, który generuje `electron-packer`na wyjściu. 3) Korzystanie z już utworzonego pakietu `.deb`.

W niektórych przypadkach musisz mieć zainstalowane narzędzie `snapcraft`. Instrukcje instalacji `snapcraft` dla Twojej dystrybucji są dostępne [tutaj](https://snapcraft.io/docs/installing-snapcraft).

## Używanie `electron-installer-snap`

Moduł działa jak [`electron-winstaller`](https://github.com/electron/windows-installer) i podobne moduły, ponieważ jego zakres jest ograniczony do tworzenia pakietów przyciągających. Możesz zainstalować z:

```sh
npm install --save-dev electron-installer-snap
```

### Krok 1: Spakuj Twoją Aplikację Electron Upewnij się, że usuniesz `node_modules` , których nie potrzebujesz w swojej aplikacji końcowej, ponieważ jakikolwiek moduł, którego tak naprawdę nie potrzebujesz, zwiększy rozmiar aplikacji.</p> 

Wyjście powinno wyglądać mniej więcej tak:



```plaintext
.
Dźwignia
    † App linux-x64
        <unk> <unk> LICENSE
        <unk> <unk> LICENSES. hromium.html
        →content_shell. ak
        × aplikacja
        × × icudtl. na
        &gt; &gt; libgcrypt.so.11
        &gt; libnode. o
        <unk> <unk> locales
        <unk> resources
        <unk> <unk> <unk> v8_context_snapshot. w wersji

```




### Krok 2: Uruchamianie `electron-installer-snap`

Z terminalu, który `snapcraft` w swoim `PATH`, uruchom `electron-installer-snap` z jedynym wymaganym parametrem `--src`, która jest lokalizacją Twojego pakietu Aplikacja Electron utworzona w pierwszym kroku.



```sh
npx electron-installer-snap --src=out/myappname-linux-x64
```


Jeśli masz istniejący proces budowy, możesz użyć `electron-installer-snap` programowo. Aby uzyskać więcej informacji, zobacz [dokumentację API Snapcraft](https://docs.snapcraft.io/build-snaps/syntax).



```js
const snap = require('electron-installer-snap')

snap(opcje)
  .then(snapŚcieżka => console.log(`Utworzona snap w ${snapPath}!`))
```




## Using `snapcraft` with `electron-packager`



### Step 1: Create Sample Snapcraft Project

Create your project directory and add add the following to `snap/snapcraft.yaml`:



```yaml
name: electron-packager-hello-world
version: '0.1'
summary: Hello World Electron app
description: |
  Simple Hello World Electron app as an example
base: core18
confinement: strict
grade: stable

apps:
  electron-packager-hello-world:
    command: electron-quick-start/electron-quick-start --no-sandbox
    extensions: [gnome-3-34]
    plugs:
    - browser-support
    - network
    - network-bind
    environment:
      # Correct the TMPDIR path for Chromium Framework/Electron to ensure
      # libappindicator has readable resources.
      TMPDIR: $XDG_RUNTIME_DIR

parts:
  electron-quick-start:
    plugin: nil
    source: https://github.com/electron/electron-quick-start.git
    override-build: |
        npm install electron electron-packager
        npx electron-packager . --overwrite --platform=linux --output=release-build --prune=true
        cp -rv ./electron-quick-start-linux-* $SNAPCRAFT_PART_INSTALL/electron-quick-start
    build-snaps:
    - node/14/stable
    build-packages:
    - unzip
    stage-packages:
    - libnss3
    - libnspr4
```


If you want to apply this example to an existing project:

- Replace `source: https://github.com/electron/electron-quick-start.git` with `source: .`.
- Replace all instances of `electron-quick-start` with your project's name.



### Step 2: Build the snap



```sh
$ snapcraft

<output snipped>
Snapped electron-packager-hello-world_0.1_amd64.snap
```




### Step 3: Install the snap



```sh
sudo snap install electron-packager-hello-world_0.1_amd64.snap --dangerous
```




### Step 4: Run the snap



```sh
electron-packager-hello-world
```




## Używanie istniejącego pakietu Debian

Snapcraft jest w stanie pobrać istniejący plik `.deb` i zamienić go w plik `.snap`. Tworzenie snap jest skonfigurowane za pomocą `snapcraft. aml` plik opisujący źródła, zależności, opis i inne podstawowe bloki budowlane.



### Krok 1: Utwórz pakiet debiański

Jeśli nie masz jeszcze pakietu `.deb` , użycie `electron-installer-snap` może być prostszą ścieżką do tworzenia pakietów przyciągających. Jednak wiele rozwiązań do tworzenia pakietów Debian istnieje, w tym [`electron-forge`](https://github.com/electron-userland/electron-forge), [`electron-builder`](https://github.com/electron-userland/electron-builder) lub [`electron-installer-debian`](https://github.com/unindented/electron-installer-debian)



### Krok 2: Utwórz snapcraft.yaml

For more information on the available configuration options, see the [documentation on the snapcraft syntax](https://docs.snapcraft.io/build-snaps/syntax). Let's look at an example:



```yaml
nazwa: myApp
wersja: '2.0.0'
streszczenie: Mały opis aplikacji.
opis: |
 Wiesz co? Ta aplikacja jest niesamowita! To wszystko robi dla ciebie
. Niektórzy mówią, że jest to dla Ciebie młode, być może nawet szczęśliwe.

grade: stable
confinement: classic

parts:
  slack:
    plugin: dump
    source: my-deb.deb
    source-type: deb
    after:
      - desktop-gtk3
    stage-packages:
      - libasound2
      - libnotify4
      - libnspr4
      - libnss3
      - libpcre3
      - libpulse0
      - libxss1
      - libxtst6
  electron-launch:
    plugin: dump
    source: files/
    prepare: |
      chmod +x bin/electron-launch

apps:
  myApp:
    command: bin/electron-launch $SNAP/usr/lib/myApp/myApp
    desktop: usr/share/applications/myApp.desktop
    # Correct the TMPDIR path for Chromium Framework/Electron to ensure
    # libappindicator has readable resources.
    environment:
      TMPDIR: $XDG_RUNTIME_DIR
```


As you can see, the `snapcraft.yaml` instructs the system to launch a file called `electron-launch`. In this example, it passes information on to the app's binary:



```sh
#!/bin/sh

exec "$@" --executed-from="$(pwd)" --pid=$$ > /dev/null 2>&1 &
```


Alternatywnie, jeśli budujesz `przyciągnij` z `ścisłym` zamknięciem, możesz użyć polecenia `uruchamiania`:



```yaml
aplikacje:
  myApp:
    # Popraw ścieżkę TMPDIR dla Chromium Framework/Electron aby upewnić się, że
    # libappindicator ma czytelne zasoby.
    polecenie: plv TMPDIR=$XDG_RUNTIME_DIR PATH=/usr/local/bin:${PATH} ${SNAP}/bin/desktop-laun $SNAP/myApp/desktop
    desktop: usr/share/applications/desktop.desktop
```
