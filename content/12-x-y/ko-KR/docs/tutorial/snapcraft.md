# Snapcraft Guide (우분투 소프트웨어 센터 및 기타)

이 가이드는 Ubuntu Software Center를 포함한, 모든 Snapcraft 환경에서 Electron 애플리케이션을 패키징하는 방법에 대한 정보를 제공합니다.

## 배경 및 요구 사항

Canonical은 보다 광범위한 Linux 커뮤니티와 함께 [`snapcraft`](https://snapcraft.io/) 프로젝트의 다양한 일반적인 소프트웨어 설치 문제의 해결을 목적으로 하고 있습니다. 스냅은 필요한 종속성, 자동 업데이트를 포함하는 컨테이너화된 소프트웨어 패키지이며, 시스템 수정 없이 모든 주요 Linux 배포판에서 작동합니다.

`.snap</0 파일을 생성하는 3가지 방법을 소개합니다.</p>

<p spaces-before="0">1) <code>snap`과 함께 사용되는 [`electron-forge`][electron-forge] 또는 [`electron-builder`][electron-builder] 두가지 툴 모두 즉시 지원합니다. 이것이 가장 쉬운 방법입니다. 2) `electron-packager`의 결과물을 가지고, `electron-installer-snap`을 사용합니다. 3) 이미 생성된 `.deb` 패키지를 사용합니다.

In some cases, you will need to have the `snapcraft` tool installed. Instructions to install `snapcraft` for your particular distribution are available [here](https://snapcraft.io/docs/installing-snapcraft).

## `electron-installer-snap` 사용

이 모듈은 [`electron-winstaller`][electron-winstaller] 및 이와 유사한 모듈과 같이 동작하며 스냅 패키지를 만드는 것으로 제한됩니다. 다음과 같이 설치할 수 있습니다:

```sh
npm install --save-dev electron-installer-snap
```

### Step 1: Electron 애플리케이션 패키지.

패키지 애플리케이션은 [electron-packager][electron-packager] (혹은 유사한 도구) 를 사용합니다. 실제로 필요하지 않은 모듈은 애플리케이션의 크기를 증가시킬 것이므로, 최종 애플리케이션에서 필요없는 `node_modules`을 제거하십시오.

결과물은 대략 아래와 같이 보일것 입니다:

```plaintext
.
└── dist
    └── app-linux-x64
        ├── LICENSE
        ├── LICENSES.chromium.html
        ├── content_shell.pak
        ├── app
        ├── icudtl.dat
        ├── libgcrypt.so.11
        ├── libnode.so
        ├── locales
        ├── resources
        ├── v8_context_snapshot.bin
        └── version
```

### Step 2: `electron-installer-snap` 실행

`snapcraft`의 경로가 `PATH`에 설정되 있는 터미널을 열고, 첫번째 단계에서 생성된 Electron 애플리케이션 패키지의 경로에서 유일한 필요 옵션`--src`을 사용해 `electron-installer-snap`을 실행합니다.

```sh
npx electron-installer-snap --src=out/myappname-linux-x64
```

만약 기존 빌드 파이프 라인이 있는 경우 라면, 프로그래밍 방식으로 `electron-installer-snap`을 사용할 수 있습니다. 더 자세한 정보를 보고싶다면, [Snapcraft API docs][snapcraft-syntax]을 참고하세요.

```js
const snap = require('electron-installer-snap')

snap(options)
  .then(snapPath => console.log(`Created snap at ${snapPath}!`))
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

## 기존 데비안 패키지 사용하기

Snapcraft는 기존 `.deb` 파일을 가져 와서`.snap` 파일로 변환 할 수 있습니다. 스냅 생성은 소스, 종속성, 설명 및 기타 핵심 구성 요소를 설명하는 `snapcraft.yaml` 파일을 사용하여 구성됩니다.

### Step 1: 데비안 패키지 생성

만약 `.deb` 패키지가 아직 없는 경우, `electron-installer-snap`을 사용하는것이 스냅 패키지를 만드는 쉬운 길이 될 수 있습니다. 그러나, [`electron-forge`][electron-forge], [`electron-builder`][electron-builder] 또는 [`electron-installer-debian`][electron-installer-debian]을 포함한 데비안 패키지를 만드는 여러 솔루션이 존재합니다

### Step 2: snapcraft.yaml 생성

For more information on the available configuration options, see the [documentation on the snapcraft syntax][snapcraft-syntax]. Let's look at an example:

```yaml
name: myApp
version: '2.0.0'
summary: A little description for the app.
description: |
 You know what? This app is amazing! It does all the things
 for you. Some say it keeps you young, maybe even happy.

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

`엄격한` 제한으로 `snap`을 작성하는 경우, `desktop-launch` 명령을 사용할 수 있습니다:

```yaml
apps:
  myApp:
    # Chromium Framework / Electron의 안전을 위한 TMPDIR 경로 수정
    # libappindicator에는 읽기 가능한 리소스들이 있습니다.
    command: env TMPDIR=$XDG_RUNTIME_DIR PATH=/usr/local/bin:${PATH} ${SNAP}/bin/desktop-launch $SNAP/myApp/desktop
    desktop: usr/share/applications/desktop.desktop
```

[snapcraft-syntax]: https://docs.snapcraft.io/build-snaps/syntax
[snapcraft-syntax]: https://docs.snapcraft.io/build-snaps/syntax
[electron-packager]: https://github.com/electron/electron-packager
[electron-forge]: https://github.com/electron-userland/electron-forge
[electron-builder]: https://github.com/electron-userland/electron-builder
[electron-installer-debian]: https://github.com/unindented/electron-installer-debian
[electron-winstaller]: https://github.com/electron/windows-installer
