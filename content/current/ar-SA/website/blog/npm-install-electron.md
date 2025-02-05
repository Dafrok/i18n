---
title: npm install electron
author: zeke
date: '2016-08-16'
---

منذ إصدار إلكترون 1.3.1، يمكنك `npm تثبيت إلكترون --save-dev` إلى تثبيت أحدث نسخة مسبقة التجميع من إلكترون في التطبيق الخاص بك.

---

![npm install electron](https://cloud.githubusercontent.com/assets/378023/17259327/3e3196be-55cb-11e6-8156-525e9c45e66e.png)

## ثنائي إلكترون مبني مسبقاً

إذا كنت قد عملت على تطبيق إلكترون من قبل، فمن المرجح أن تأتي إلى حزمة `التي تم بناؤها مسبقاً إلكترونيا` npm . هذه الحزمة جزء لا غنى عنه من حوالي كل مشروع إلكترون. عند التثبيت، فإنه يكتشف نظام التشغيل الخاص بك ويقوم بتنزيل ثنائي مبني مسبقاً يتم تجميعه للعمل على معماري النظام الخاص بك.

## الاسم الجديد

كانت عملية تثبيت إلكترون في كثير من الأحيان حجر عثرة أمام المطورين الجدد. حاول العديد من الناس الشجعان البدء في تطوير إلكترون بواسطة التطبيق عن طريق تشغيل `npm تثبيت إلكترون` بدلاً من `npm تثبيت إلكترون - تم بناؤه مسبقاً`، فقط لاكتشاف (غالباً بعد الكثير من الارتباك) أنه ليس إلكترون `` هم يبحثون عنه.

كان ذلك بسبب وجود مشروع `إلكترون` موجود على npm، تم إنشاؤه قبل وجود مشروع إلكترون GitHub. للمساعدة في جعل تطوير إلكترون أسهل وأكثر بديهيا للمطورين الجدد، لقد وصلنا إلى مالك حزمة `إلكترون الحالي` npm لسؤاله عما إذا كان على استعداد للسماح لنا باستخدام الاسم. لحسن الحظ كان معجباً بمشروعنا، ووافق على مساعدتنا في إعادة إستخدام الاسم.

## الحياة المبنية مسبقاً على

بدءاً من الإصدار 1.3.1، بدأنا في نشر [`إلكترون`](https://www.npmjs.com/package/electron) و `إلكترون - تم بناؤه مسبقاً` حزم إلى npm بالترادف. والحزمتان متطابقتان. لقد اخترنا الاستمرار في نشر الحزمة تحت كلا الاسمين لبعض الوقت حتى لا نزعج الآلاف من المطورين الذين يستخدمون حاليا `التي تم بناؤها سلفا` في مشاريعهم. نوصي بتحديث حزمة `الخاصة بك. ابن` ملفات لاستخدام `إلكترون الجديد` التبعية، لكننا سنستمر في إصدار إصدارات جديدة من `الإلكترون الذي تم بناؤه مسبقاً` حتى نهاية عام 2016.

The [electron-userland/electron-prebuilt](https://github.com/electron-userland/electron-prebuilt) repository will remain the canonical home of the `electron` npm package.

## شكراً جزيلاً

نحن مدينون بشكر خاص ل [@mafintosh](https://github.com/mafintosh)، [@maxogden](https://github.com/maxogden)، والعديد من [المساهمين](https://github.com/electron-userland/electron-prebuilt/graphs/contributors) لإنشاء وصيانة `الإلكترون الذي تم بناؤه مسبقاً`، ولخدمتهم الدؤوبة إلى JavaScript، العقدة. ، ومجتمعات إلكترون.

وبفضل [@logicalparadox](https://github.com/logicalparadox) لسماحه لنا بتولي حزمة البريد `` على npm.

## تحديث مشاريعك

لقد عملنا مع المجتمع لتحديث الحزم الشعبية التي تتأثر بهذا التغيير. حزم مثل [حزمة إلكترون-حزمة](https://github.com/electron-userland/electron-packager)، [إلكترون - إعادة بناء](https://github.com/electron/electron-rebuild)، و [وحدة الإنشاء الإلكتروني](https://github.com/electron-userland/electron-builder) تم تحديثها بالفعل للعمل مع الاسم الجديد مع الاستمرار في دعم الاسم القديم.

إذا واجهت أي مشاكل في تثبيت هذه الحزمة الجديدة، الرجاء إبلاغنا عن طريق فتح مشكلة في [مستودع إلكترون-مستخدم/إلكترون-تم بناؤه مسبقاً](https://github.com/electron-userland/electron-prebuilt/issues) .

لأي مشاكل أخرى مع إلكترون، الرجاء استخدام [electron/electron](https://github.com/electron/electron/issues) مستودع.

