# Недавние документы (Windows & macOS)

## Обзор

Windows и macOS предоставляют легкий доступ к списку последних документов открытых приложением через JumpList или dock меню, соответственно.

__JumpList:__

![Список последних файлов][1]

__Dock меню приложения:__

![macOS панель меню][2]

To add a file to recent documents, you need to use the [app.addRecentDocument][addrecentdocument] API.

## Пример

### Добавить элемент в последние документы

Начиная с рабочего приложения из [Quick Start Guide](quick-start.md), добавьте следующие строки в файл `main.js`:

```javascript
const { app } = require('electron')

app.addRecentDocument('/Users/USERNAME/Desktop/work.type')
```

После запуска приложения Electron щелкните правой кнопкой мыши на значке приложения. Вы должны увидеть добавленный предмет. В этом руководстве элемент является файлом Markdown , находящимся в корне проекта:

![Недавний документ](../images/recent-documents.png)

### Очистить список последних документов

To clear the list of recent documents, you need to use [app.clearRecentDocuments][clearrecentdocuments] API in the `main.js` file:

```javascript
const { app } = require('electron')

app.clearRecentDocuments()
```

## Дополнительная информация

### Windows примечания

Чтобы использовать эту функцию в Windows, ваше приложение должно быть зарегистрировано как обработчик типа файла документа, иначе файл не будет отображаться в JumpList даже после его добавления. Вы можете найти все о регистрации вашего приложения в [Application Registration][app-registration].

Когда пользователь щелкает файл из JumpList, новый экземпляр приложения будет запущен с добавленного пути файла, как аргумент командной строки.

### macOS примечания

#### Добавить список последних документов в меню приложения

Вы можете добавить пункты меню для доступа к недавним документам и очистить их, добавив следующий код в шаблон меню:

```json
{
  "submenu":[
    {
      "label":"Open Recent",
      "role":"recentdocuments",
      "submenu":[
        {
          "label":"Clear Recent",
          "роль":"clearrecentdocuments"
        }
      ]
    }
  ]
}
```

![Элемент меню macOS последних документов][6]

Когда файл запрашивается из меню последних документов, будет эмулировано событие `open-file` из `приложения` для него.

[1]: https://cloud.githubusercontent.com/assets/2289/23446924/11a27b98-fdfc-11e6-8485-cc3b1e86b80a.png
[2]: https://cloud.githubusercontent.com/assets/639601/5069610/2aa80758-6e97-11e4-8cfb-c1a414a10774.png
[6]: https://user-images.githubusercontent.com/3168941/33003655-ea601c3a-cd70-11e7-97fa-7c062149cfb1.png
[addrecentdocument]: ../api/app.md#appaddrecentdocumentpath-macos-windows
[clearrecentdocuments]: ../api/app.md#appclearrecentdocuments-macos-windows
[app-registration]: https://msdn.microsoft.com/en-us/library/cc144104(VS.85).aspx
