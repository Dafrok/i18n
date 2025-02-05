# تصحيح أخطاء التطبيق

كلما كان تطبيق إلكترون الخاص بك لا يتصرف بالطريقة التي تريدها، مجموعة من أدوات تصحيح الأخطاء قد تساعدك على العثور على أخطاء في البرمجة، اختناقات الأداء أو فرص التحسين.

## عملية العارض

الأداة الأكثر شمولاً لتصحيح عمليات العرض الفردية هي أداة مطور كروميوم. وهي متاحة لجميع عمليات العرض، بما في ذلك مثيلات `نافذة المتصفح`، `عرض المتصفح`، و `عرض الويب`. يمكنك فتحها برمجياً عن طريق الاتصال بـ `أدوات openDevDevols()` API على `webContents` من المثال:

```javascript
const { BrowserWindow } = require('electron')

const win = new BrowserWindow()
win.webContents.openDevTools()
```

تقدم جوجل [وثائق ممتازة لأدوات المطور](https://developer.chrome.com/devtools). ننصح بأن تكون على دراية بها - فهي عادة واحدة من أقوى المنافع في أي حزام أدوات مطور إلكترون.

## العملية الرئيسية

تصحيح أخطاء العملية الرئيسية أكثر صعوبة، لأنه لا يمكنك فتح أدوات المطور لهم. يمكن استخدام أدوات مطور كروميوم [ لتصحيح العملية الرئيسية لـ Electron's](https://nodejs.org/en/docs/inspector/) بفضل التعاون الأوثق بين Google / Chrome و العقدة. ، ولكن قد تواجه خلافات مثل `تتطلب` عدم وجود في وحدة التحكم.

للمزيد من المعلومات، انظر [تصحيح الأخطاء في وثائق العملية الرئيسية](./debugging-main-process.md).

## تحطم V8

إذا تعطل سياق V8، فستعرض أدوات DevTools هذه الرسالة.

`تم قطع اتصال الأدوات من الصفحة. بمجرد إعادة تحميل الصفحة، سيتم إعادة الاتصال تلقائيًا.`

يمكن تمكين سجلات الكروم عن طريق متغير البيئة `ELECTRON_ENABLE_LOGING`. For more information, see the [environment variables documentation](../api/environment-variables.md#electron_enable_logging).

بدلاً من ذلك، يمكن تمرير حجة سطر الأوامر `--تسجيل الأوامر` More information is available in the [command line switches documentation](../api/command-line-switches.md#--enable-logging).
