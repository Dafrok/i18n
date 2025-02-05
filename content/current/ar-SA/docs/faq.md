# Electron FAQ

## لماذا أواجه مشكلة في تثبيت إلكترون؟

Wywołując polecenie `npm install electron`, niektórzy użytkownicy napotykają okazjonalne błędy instalacji.

في جميع الحالات تقريبا، هذه الأخطاء هي نتيجة لمشاكل الشبكة وليس القضايا الفعلية مع حزمة `npm الإلكترون.` أخطاء مثل `ELIFECYCLE`، `EAI_AGAIN`، `ECONNRESET`، `وETIMEDOUT` كلها مؤشرات على مثل هذه مشاكل الشبكة. أفضل دقة هي محاولة تبديل الشبكات، أو الانتظار قليلا وحاول تثبيت مرة أخرى.

يمكنك أيضا محاولة لتحميل الإلكترون مباشرة من [الإلكترون / الإلكترون / الإصدارات](https://github.com/electron/electron/releases) إذا كان التثبيت عبر `npm` يفشل.

## متى ستتم ترقية الإلكترون إلى Chrome الأحدث؟

عادة ما يتم صدم نسخة كروم من الإلكترون في غضون أسبوع أو أسبوعين بعد يتم إصدار إصدار Chrome مستقر جديد. هذا التقدير غير مضمون و يعتمد على مقدار العمل المعني بالترقية.

يتم استخدام قناة كروم المستقرة فقط. إذا كان إصلاح مهم في قناة بيتا أو ديف ، سنقوم بعودة المنبور.

لمزيد من المعلومات، يرجى الاطلاع على [مقدمة الأمان.](tutorial/security.md).

## When will Electron upgrade to latest Node.js?

When a new version of Node.js gets released, we usually wait for about a month before upgrading the one in Electron. So we can avoid getting affected by bugs introduced in new Node.js versions, which happens very often.

New features of Node.js are usually brought by V8 upgrades, since Electron is using the V8 shipped by Chrome browser, the shiny new JavaScript feature of a new Node.js version is usually already in Electron.

## How to share data between web pages?

To share data between web pages (the renderer processes) the simplest way is to use HTML5 APIs which are already available in browsers. Good candidates are [Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Storage), [`localStorage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage), [`sessionStorage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage), and [IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API).

بدلاً من ذلك، يمكنك استخدام البدائيات IPC التي توفرها إلكترون. ل مشاركة البيانات بين العمليات الرئيسية و عمليات العرض. يمكنك استخدام وحدات [`ipcMain`](api/ipc-main.md) و [`ipcRenderer`](api/ipc-renderer.md) للتواصل مباشرة بين صفحات الويب، يمكنك إرسال [`منفذ الرسائل`](https://developer.mozilla.org/en-US/docs/Web/API/MessagePort) من واحد إلى الآخر، ربما عن طريق العملية الرئيسية باستخدام [`ipcRenderer. ostMessage()`](api/ipc-renderer.md#ipcrendererpostmessagechannel-message-transfer). الاتصال اللاحق عبر منافذ الرسائل هو اتصال مباشر ولا يغادر خلال العملية الرئيسية.

## اختفت صالة تطبيقي بعد بضع دقائق.

يحدث هذا عندما يتم جمع المتغير الذي يستخدم لتخزين العلامة القمامة.

If you encounter this problem, the following articles may prove helpful:

* [Memory Management](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Memory_Management)
* [Variable Scope](https://msdn.microsoft.com/library/bzt2dkta(v=vs.94).aspx)

If you want a quick fix, you can make the variables global by changing your code from this:

```javascript
const { app, Tray } = require('electron')
app.whenReady{()) => {
  علبة const = علبة جديدة('/path/to/icon.png')
  tray.setTitle ('مرحبا العالم')
})
```

to this:

```javascript
const { app, Tray } = مطلوب('electron')
اسمح باللعبة = null
app.whenReady().then(() => {
  tray = Tray('/path/to/icon.png')
  tray.setTitle('hello world')
})
```

## I can not use jQuery/RequireJS/Meteor/AngularJS in Electron.

Due to the Node.js integration of Electron, there are some extra symbols inserted into the DOM like `module`, `exports`, `require`. This causes problems for some libraries since they want to insert the symbols with the same names.

To solve this, you can turn off node integration in Electron:

```javascript
// In the main process.
const { BrowserWindow } = مطلوبة ('electron')
الفوز = متصفح جديد Window({
  webPreferences: {
    nodeIntegration: false
  }
})
win.show()
```

But if you want to keep the abilities of using Node.js and Electron APIs, you have to rename the symbols in the page before including other libraries:

```html
<head>
<script>
window.nodeRequire = require;
delete window.require;
delete window.exports;
delete window.module;
</script>
<script type="text/javascript" src="jquery.js"></script>
</head>
```

## `require('electron').xxx` is undefined.

When using Electron's built-in module you might encounter an error like this:

```sh
> require('electron').webFrame.setZoomFactor(1.0)
Uncaught TypeError: Cannot read property 'setZoomLevel' of undefined
```

من المحتمل جدا أنك تستخدم الوحدة في العملية الخاطئة. يمكن استخدام ` electron.app </ 0> فقط في العملية الرئيسية ، بينما <>> electron.webFrame </ 0>
متاح فقط في renderer processes.</p>

<h2 spaces-before="0">يبدو الخط غير واضح، ما هو هذا وماذا يمكنني أن أفعل؟</h2>

<p spaces-before="0">If <a href="https://alienryderflex.com/sub_pixel/">sub-pixel anti-aliasing</a> is deactivated, then fonts on LCD screens can look blurry. مثال:</p>

<p spaces-before="0">!<a href="images/subpixel-rendering-screenshot.gif">subpixel يقدم المثال</a></p>

<p spaces-before="0">وتحتاج مكافحة التحرر من الباطن إلى خلفية غير شفافة للطبقة التي تحتوي على غليفات الخط. (انظر <a href="https://github.com/electron/electron/issues/6344#issuecomment-420371918">هذه المشكلة</a> لمزيد من المعلومات).</p>

<p spaces-before="0">لتحقيق هذا الهدف، اضبط الخلفية في البناء ل <a href="api/browser-window.md">نافذة المتصفح</a>:</p>

<pre><code class="javascript">const { BrowserWindow } = مطلوبة ('electron')
الفوز = متصفح جديد ({
  backgroundColor: '#fff'
})
`</pre>

التأثير مرئي فقط على (بعض؟) شاشات LCD. حتى لو كنت لا ترى فرقا، قد يرى بعض المستخدمين الخاص بك. ومن الأفضل أن نضع دائماً الخلفية بهذه الطريقة، ما لم تكن لديك أسباب لعدم القيام بذلك.

لاحظ أن إعداد الخلفية فقط في CSS ليس له التأثير المطلوب.
