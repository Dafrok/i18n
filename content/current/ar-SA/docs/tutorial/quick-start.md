# دليل البدء السريع

## البداية السريعة

إلكترون هو إطار يمكّنك من إنشاء تطبيقات سطح المكتب باستخدام جافا سكريبت و HTML و CSS. يمكن بعد ذلك تعبئة هذه التطبيقات لتشغيلها مباشرة على macOS أو Windows أو Linux أو توزيعها عبر Mac App Store أو متجر Microsoft Store.

عادة ، تقوم بإنشاء تطبيق سطح المكتب لنظام تشغيل (OS) باستخدام أطر التطبيق الأصلية الخاصة بكل نظام تشغيل. يتيح إلكترون كتابة التطبيق الخاص بك بمجرد استخدام التقنيات التي تعرفها مسبقاً.

### المتطلبات الأساسية

قبل المضي قدما مع Electron تحتاج إلى تثبيت [Node.js](https://nodejs.org/en/download/). نوصي بتثبيت أحدث `LTS` أو `الإصدار الحالي` المتاح.

> الرجاء تثبيت Node.js باستخدام المثبتات المبنية مسبقاً للمنصة الخاصة بك. قد تواجه مشاكل عدم التوافق مع أدوات التطوير المختلفة لولا ذلك.

للتحقق من أن Node.js تم تثبيته بشكل صحيح، اكتب الأوامر التالية في العميل الطرفي الخاص بك:

```sh
العقدة -v
npm -v
```

وينبغي للأوامر أن تطبع نسختي Node.js و npm تبعا لذلك. إذا نجح الأمرين، فإنك على استعداد لتثبيت إلكترون.

### إنشاء تطبيق أساسي

من منظور التنمية، يعتبر تطبيق إلكترون أساسا تطبيقا من تطبيقات Node.js. هذا يعني أن نقطة البداية في تطبيق Electron الخاص بك ستكون ملف `package.json` مثل أي تطبيق Node.js آخر. التطبيق الإلكترون الأدنى له البنية التالية:

```plaintext
my-electron-app/
<unk> <unk> <unk> <unk> <unk> ', package.json
<unk> <unk> <unk> ', main.js
<unk> <unk> ', index.html
```

دعونا ننشئ تطبيقا أساسيا بناء على الهيكل أعلاه.

#### Install Electron

إنشاء مجلد لمشروعك وتثبيت إلكترون هناك:

```sh
mkdir my-electron-app && cd my-electron-app
npm init -y
npm i --save-dev electron
```

#### إنشاء ملف البرنامج النصي الرئيسي

يحدد البرنامج النصي الرئيسي نقطة الدخول في تطبيق إلكترون (في حالتنا الملف `main.js` ) الذي سيقوم بتشغيل العملية الرئيسية. عادة ، البرنامج النصي الذي يعمل في العملية الرئيسية يتحكم في دورة حياة التطبيق ، يعرض واجهة المستخدم الرسم البياني وعناصره، يقوم بأداء تفاعلات نظام التشغيل الأصلي، وينشئ عمليات Renderer داخل صفحات الويب. طلب إلكترون من الممكن أن يحتوي على عملية رئيسية واحدة فقط.

قد يبدو النص الرئيسي كما يلي:

```javascript fiddle='docs/fiddles/quick-start'
const { app, BrowserWindow } = require('electron')

function createWindow () {
  const win = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      nodeIntegration: true
    }
  })

  win.loadFile('index.html')
}

app.whenReady().then(createWindow)

app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') {
    app.quit()
  }
})

app.on('activate', () => {
  if (BrowserWindow.getAllWindows().length === 0) {
    createWindow()
  }
})
```

##### ماذا يحدث أعلاه؟

1. السطر 1: أولا، تستورد `التطبيق` و `نافذة المتصفح` وحدات `إلكترون` لحزمة لتتمكن من إدارة أحداث دورة حياة التطبيق الخاص بك، بالإضافة إلى إنشاء نوافذ المتصفح والتحكم فيها.
2. Line 3: After that, you define a function that creates a [new browser window](../api/browser-window.md#new-browserwindowoptions) with node integration enabled, loads `index.html` file into this window (line 12, we will discuss the file later).
3. Line 15: You create a new browser window by invoking the `createWindow` function once the Electron application [is initialized](../api/app.md#appwhenready).
4. Line 17: You add a new listener that tries to quit the application when it no longer has any open windows. هذا المستمع غير موجود على macOS بسبب سلوك إدارة النافذة [لنظام التشغيل](https://support.apple.com/en-ca/guide/mac-help/mchlp2469/mac).
5. Line 23: You add a new listener that creates a new browser window only if when the application has no visible windows after being activated. على سبيل المثال بعد إطلاق التطبيق لأول مرة أو إعادة تشغيل التطبيق قيد التشغيل بالفعل.

#### إنشاء صفحة ويب

هذه هي صفحة الويب التي تريد عرضها بمجرد تهيئة التطبيق. هذه الصفحة تمثل عملية المعرض. يمكنك إنشاء نوافذ متصفح متعددة، حيث كل نافذة تستخدم عارض مستقل خاص بها. يمكن منح كل نافذة اختياريا مع الوصول الكامل إلى واجهة برمجة التطبيقات Node.js من خلال تفضيلات `nodeIntegr`.

صفحة `index.html` تبدو كما يلي:

```html fiddle='docs/fiddles/quick-start'
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Hello World!</title>
    <meta http-equiv="Content-Security-Policy" content="script-src 'self' 'unsafe-inline';" />
</head>
<body style="background: white;">
    <h1>Hello World!</h1>
    <p>
        We are using node <script>document.write(process.versions.node)</script>,
        Chrome <script>document.write(process.versions.chrome)</script>,
        and Electron <script>document.write(process.versions.electron)</script>.
    </p>
</body>
</html>
```

#### تعديل ملف package.json

يستخدم تطبيق Electron الخاص بك ملف `package.json` كنقطة دخول رئيسية (كما في أي تطبيق Node.js آخر). البرنامج النصي الرئيسي لتطبيقك هو `main.js`، لذا قم بتعديل ملف `package.json` تبعاً لذلك:

```json
{
    "name": "my-electron-app",
    "version": "0.1.0",
    "author": "your name",
    "description": "My Electron app",
    "main": "main.js"
}
```

> ملاحظة: إذا تم حذف الحقل الرئيسي `` ، فسيحاول إلكترون تحميل فهرس `. s` ملف من الدليل الذي يحتوي على `package.json`.

> NOTE: The `author` and `description` fields are required for packaging, otherwise error will occur when running `npm run make`.

بشكل افتراضي، سيقوم أمر `npm star` بتشغيل البرنامج النصي الرئيسي باستخدام Node.js. لتشغيل البرنامج النصي باستخدام إلكترون، تحتاج إلى تغييره على هذا النحو:

```json
{
    "name": "my-electron-app",
    "version": "0.1.0",
    "author": "your name",
    "description": "My Electron app",
    "main": "main.js",
    "scripts": {
        "start": "electron ."
    }
}
```

#### تشغيل التطبيق الخاص بك

```sh
npm بداية
```

يجب أن يكون تطبيق إلكترون قيد التشغيل كما يلي:

![تطبيق إلكترون بسيط](../images/simplest-electron-app.png)

### حزمة الطلب وتوزيعه

أبسط وأسرع طريقة لتوزيع تطبيقك الذي تم إنشاؤه حديثا هي استخدام [إلكترون فورج](https://www.electronforge.io).

1. استيراد تصنيع إلكترون إلى مجلد التطبيق الخاص بك:

    ```sh
    npx @electron-forge/cli استيراد

    ✔ التحقق من نظامك
    ✔ التمهيد لمستودع Git
    ✔ كتابة الحزمة المعدلة. ملف سون
    ✔ تثبيت الإعتمادات
    ✔ كتابة الحزمة المعدلة. ملف ابن
    ✔ إصلاح قم بتحريك

    لدينا تيميميد لتحويل التطبيق الخاص بك إلى صيغة يفهمها تصنيع الإلكترون.

    شكرا لاستخدام "النسيج الإلكتروني"!!!
    ```

1. إنشاء قابل للتوزيع:

    ```sh
    npm تشغيل يجعل

    > my-gsod-electron-app@1.0. اجعل /my-electron-app
    > electron-forge صنع

    ✔ التحقق من نظامك
    ✔ إصلاح تشكيل التكوين
    نحن بحاجة إلى حزم تطبيقك قبل أن نتمكن من جعله
    ✔ التحضير لتطبيق الحزمة لـ ter: x64
    ✔ إعداد الإعتمادات الأصلية
    ✔ تطبيق الحزم
    لتحقيق الأهداف التالية: zip
    ✔ جعل الهدف : zip - على المنصة: لأرخ: 64
    ```

    ينشئ تصنيع إلكترون مجلد `خارج` حيث ستوضع الحزمة الخاصة بك:

    ```plain
    // مثال ل MacOS
    خارج/
    <unk> <unk> <unk> <unk> )-out/make/zip/darwin/x64/my-electron-app-darwin-x64-1.0.zip
    <unk> <unk> <unk> م....
    <unk> <unk> - خارج/my-electron-app-darwin-x64/my-electron-app.app/Contents/MacOS/my-electron-app
    ```

## تعلم الأساسيات

هذا القسم يوجهك من خلال أساسيات كيفية عمل إلكترون تحت القاعة. وهو يهدف إلى تعزيز المعرفة بشأن إلكترون والتطبيق الذي أنشئ في وقت سابق في قسم التدخل السريع.

### بنية التطبيق

يتكون إلكترون من ثلاث ركائز رئيسية:

* **Chromium** لعرض محتوى الويب.
* **Node.js** للعمل مع نظام الملفات المحلي ونظام التشغيل.
* **واجهات برمجة التطبيقات المخصصة** للعمل مع الدوال الأصلية المطلوبة في كثير من الأحيان.

تطوير تطبيق باستخدام Electron هو مثل بناء تطبيق Node.js مع واجهة ويب أو بناء صفحات ويب مع تكامل سلسلة Node.js.

#### العمليات الرئيسية والرابط

وكما ذُكر من قبل، فإن لشركة إلكترون نوعان من العمليات: الرئيسية وشركة Renderer.

* العملية الرئيسية **تنشئ** صفحات ويب عن طريق إنشاء `مثيلات نافذة المتصفح`. كل مثيل `نافذة المتصفح` يدير صفحة الويب في عملية العارض الخاصة به. عندما يتم تدمير نموذج `نافذة المتصفح` ، يتم إنهاء عملية العارض المقابلة كذلك.
* العملية الرئيسية **تدير** جميع صفحات الويب وعمليات العارض المقابلة لها.

----

* عملية المعرض **تدير** صفحة الويب المقابلة فقط. الانهيار في عملية عارض واحدة لا يؤثر على عمليات عارض أخرى.
* عملية المعرض **تتواصل** مع العملية الرئيسية عبر IPC لأداء عمليات واجهة المستخدم في صفحة ويب. أما استدعاء واجهة برمجة تطبيقات واجهة المستخدم المحلية من عملية العارض فهو محدود مباشرة بسبب الشواغل الأمنية واحتمال تسرب الموارد.

----

الاتصال بين العمليات ممكن من خلال وحدات الاتصال بين العمليات: [`ipcMain`](../api/ipc-main.md) و [`ipcRenderer`](../api/ipc-renderer.md).

#### APIs

##### Electron API

تم تعيين واجهة برمجة تطبيقات إلكترون استنادًا إلى نوع العملية، يعني أنه يمكن استخدام بعض الوحدات النمطية من عملية الرئيسية أو Renderer، وبعضها من كليهما. تشير وثائق واجهة برمجة تطبيقات Electron's إلى العملية التي يمكن استخدام كل وحدة منها.

على سبيل المثال، للوصول إلى واجهة برمجة تطبيقات إلكترون في كلتا العمليتين، يتطلب وحدة الإدراج:

```js
إلكترون = مطلوبة ('electron')
```

لإنشاء نافذة، اتصل بفصل `مستعرض النافذة` ، والذي هو متاح فقط في العملية الرئيسية:

```js
const { BrowserWindow } = مطلوبة ('electron')
الفوز = متصفح ويندوز جديد()
```

لتسمية العملية الرئيسية من المعرض، استخدم الوحدة النمطية للجنة IPC:

```js
// في العملية الرئيسية
const { ipcMain } = require('electron')

ipcMain.handle('perform-action', (event, ...args) => {
  // ... القيام بإجراءات نيابة عن المعرض
})
```

```js
// في عملية العارض
خلال { ipcRenderer } = المطلوب('electron')

ipcRenderer.invoke('perform-action', ...args)
```

> ملاحظة: لأن عمليات العارض قد تعمل برمز غير موثوق به (خاصة من أطراف ثالثة)، ومن المهم التحقق بعناية من صحة الطلبات التي تأتي إلى العملية الرئيسية.

##### Node.js API

> ملاحظة: للوصول إلى واجهة برمجة التطبيقات Node.js من عملية Renderer، تحتاج إلى تعيين تفضيل `nodeintegration` إلى `true`.

ويكشف إلكترون إمكانية الوصول الكامل إلى واجهة برمجة تطبيقات Node.js ووحداته في كل من عمليتي الرئيسية و Renderer. على سبيل المثال، يمكنك قراءة جميع الملفات من الدليل الجذر :

```js
const fs = مطلوب('fs')

الجذر = fs.readdirSync('/')

console.log(root)
```

لاستخدام وحدة Node.js ، تحتاج أولاً إلى تثبيته كاعتماد :

```sh
npm تثبيت --حفظ aws-sdk
```

ثم في تطبيق إلكترون الخاص بك، يتطلب الوحدة:

```js
S3 = مطلوبة ('aws-sdk/clients/s3')
```
