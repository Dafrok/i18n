# Підтримка Electron

## Підтримка

Якщо у вас виникли проблеми з безпекою, будь ласка, подивіться [документ безпеки](https://github.com/electron/electron/tree/master/SECURITY.md).

Якщо ви шукаєте допомогу програмування, для відповідей на питання, або приєднатися до дискусії з іншими розробниками, які використовують Electron, ви можете взаємодіяти з спільнотою в таких умовах:

- [`Electron's Discord`](https://discord.com/invite/electron) has channels for:
  - Getting help
  - Ecosystem apps like [Electron Forge](https://github.com/electron-userland/electron-forge) and [Electron Fiddle](https://github.com/electron/fiddle)
  - Sharing ideas with other Electron app developers
  - And more!
- [`electron`](https://discuss.atom.io/c/electron) category on the Atom forums
- `#atom-shell` канал на Freenode
- `#electron` канал [Atom's Slack](https://discuss.atom.io/t/join-us-on-slack/16638?source_topic_id=25406)
- [`electron-ru`](https://telegram.me/electron_ru) *(Російська)*
- [`electron-br`](https://electron-br.slack.com) *(бразильська португальська)*
- [`electron-kr`](https://electron-kr.github.io/electron-kr) *(корейська)*
- [`electron-jp`](https://electron-jp.slack.com) *(японська)*
- [`electron-tr`](https://electron-tr.herokuapp.com) *(Турецька)*
- [`electron-id`](https://electron-id.slack.com) *(Індонезія)*
- [`electron-pl`](https://electronpl.github.io) *(Польща)*

Якщо ви хочете зробити внесок на Electron, дивись [сторінку з учасником](https://github.com/electron/electron/blob/master/CONTRIBUTING.md).

Якщо ви знайшли помилку у [підтримуваній версії](#supported-versions) Electron, , повідомте про це за допомогою [трекера питань](../development/issues.md).

[шановний електрон](https://github.com/sindresorhus/awesome-electron) - список підтримуваних спільнотою додатків, інструментів і ресурсів.

## Підтримувані версії

Підтримуються найновішими *стабільними* основними версіями команди Electron. Наприклад, якщо останній випуск рівний 6.1.x, так само як і 5.0.x, так і як підтримуються серії 4.2.x.  Ми підтримуємо тільки останній незначний випуск для кожної стабільної випускової серії.  Це означає, що у випадку безпечного виправлення 6.1. отримає фікс, але ми не випустимо нову версію 6.0.x.

Останній стабільний випуск в односторонньому порядку отримує всі фікси від `майстра`, і версія до цього отримує переважну більшість виправлень як ордер на час і пропускну здатність. Найстаріша підтримувана реліз буде надана тільки безпечні виправлення безпосередньо.

Всі підтримувані випуски релізу будуть приймати запити на зовнішній pull в backport виправляти раніше об'єднані з `головним аркером`, хоча це може бути за кожного випадку основу для деяких старих підтримуваних ліній. Всі оспорювані рішення навколо релізу звіт по лінії будуть вирішені [Робочою групою релізів](https://github.com/electron/governance/tree/master/wg-releases) як елементом порядку денного на їх щотижневому засіданні згідно з рейтингом зворотного зв'язку.

Коли API змінюється або видаляється таким чином, що порушує існуючу функцію, попередній функціонал буде підтримуватися як мінімум дві основні версії перед видаленням. Наприклад, якщо функція приймає три аргументи, і ця кількість скорочена до двох у великій версії 10, версія з трьох аргументів продовжуватиме працювати доти, як мінімум, мажорна версія 12. Минуло мінімальну двоверсію поріг, ми будемо намагатися підтримувати зворотну сумісність поза двома версіями , поки супроводжуючі вважають, що навантаження на обслуговування буде занадто високим, щоб продовжувати це робити.

### Встановлені версії

- 11.x.y
- 10.x.y
- 9.x.y

### Кінець життя

Коли гілка випуску досягає кінця циклу підтримки, серія буде застаріла в NPM і остання версія підтримки буде створена . Цей реліз додасть попередження, щоб повідомити про непідтримувану версію Electron вже використовується.

Ці кроки полягають в тому, щоб допомогти розробникам програми, коли гілка використовується не підтримується, але не завдяки надмірній нав'язливості для кінцевих користувачів.

Якщо програма має виняткові обставини і повинна залишатися на непідтримуваних серіях Electron, розробникам можна приглушити попередження про кінець підтримки, пропустивши остаточний випуск з пакету `. син` `devDependencies`. Наприклад, оскільки серія 1-6-х закінчилася кінцевою підтримкою 1.6. 8 релізу, розробники могли б вибирати , щоб залишатись на початковій серії без попереджень із `відданістю` із `"електрона": 1. .0 - 1.6.17`.

## Підтримувані Платформи

Наступні платформи підтримуються Electron:

### macOS

Only 64bit binaries are provided for macOS, and the minimum macOS version supported is macOS 10.10 (Yosemite).

### Windows

Windows 7 і пізніше підтримуються, старі операційні системи не підтримуються (і не працюють).

Обидві `ia32` (`x86`) та `x64` (`amd64`) виконувані файли надаються для Windows. [Electron 6.0.8 та старше додайте власну підтримку для Windows на Arm (`arm64`) пристроїв](windows-arm.md). Запуск додатків, пов'язаних з попередніми версіями можливий використання двійкового файла ia32.

### Linux

The prebuilt binaries of Electron are built on Ubuntu 18.04.

Whether the prebuilt binary can run on a distribution depends on whether the distribution includes the libraries that Electron is linked to on the building platform, so only Ubuntu 18.04 is guaranteed to work, but following platforms are also verified to be able to run the prebuilt binaries of Electron:

* Ubuntu 14.04 and newer
* Fedora 24 and newer
* Debian 8 and newer
