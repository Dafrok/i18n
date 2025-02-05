---
title: "استخدام GN لبناء إلكترون"
author: nornagon
date: '2018-09-05'
---

يستخدم إلكترون الآن GN لبناء نفسه. إليك مناقشة لماذا.

---

# GYP و GN

عندما تم اصدار إلكترون لأول مرة في عام 2013، تم كتابة اعدادات بناء كروميوم مع [GYP](https://gyp.gsrc.io/)، قصير لـ "إنشاء مشاريعك".

في عام 2014، قدم مشروع Chromium أداة تكوين جديدة تسمى [GN](https://gn.googlesource.com/gn/) (قصير لـ "إنشاء [نينجا](https://ninja-build.org/)") تم ترحيل ملفات بناء Chromium إلى GN وتم إزالة GYP من رمز المصدر.

لقد حافظ إلكترون تاريخياً على فصل بين [رمز إلكترون الرئيسي](https://github.com/electron/electron) و [ليبكروم المحتوى](https://github.com/electron/libchromiumcontent)، الجزء من إلكترون الذي يغلف وحدة 'المحتوى' الخاصة بـ Chromium. إلكترون استمر باستخدام GYP، بينما ليبكروم المحتوى -- كمجموعة فرعية من كروميوم -- انتقل إلى GN عندما فعل كروموم.

مثل أدوات التجهيز التي لا تتشابك تماما، كان هناك احتكاك بين استخدام نظامي البناء. الحفاظ على التوافق كان عرضة للأخطاء، من أعلام المترجم، و `#ID` التي تحتاج إلى الحفاظ عليها بدقة في المزامنة بين Chromium و Node, V8, و Electron.

لمعالجة هذا الأمر، يعمل فريق إلكترون على نقل كل شيء إلى GN. اليوم، [إلتزام](https://github.com/electron/electron/pull/14097) بإزالة آخر رمز GYP من إلكترون تم هبوطه في ماجستير.

# ماذا يعني هذا بالنسبة لك

إذا كنت تساهم في إلكترون نفسه، عملية التحقق وبناء إلكترون من `سيد` أو 4. .0 يختلف كثيرا عما كان عليه في 3.0.0 وما قبلها. راجع [تعليمات إنشاء GN](https://github.com/electron/electron/blob/master/docs/development/build-instructions-gn.md) للحصول على التفاصيل.

إذا كنت تقوم بتطوير تطبيق باستخدام إلكترون، هناك بعض التغييرات الطفيفة التي قد تلاحظ في إلكترون 4 الجديد. .0-ليلاً؛ ولكن من المرجح أن تغيير شركة Electron's في نظام البناء سيكون شفافاً تماماً بالنسبة لك.

# ما يعنيه هذا بالنسبة للإلكترون

GN هو [أسرع](https://chromium.googlesource.com/chromium/src/tools/gn/+/48062805e19b4697c5fbd926dc649c78b6aaa138/README.md) من GYP وملفاته أكثر قابلية للقراءة والصيانة. علاوة على ذلك، نأمل أن يؤدي استخدام نظام تكوين بناء واحد إلى تقليل العمل المطلوب لترقية إلكترون إلى إصدارات جديدة من كروميوم.

 * لقد ساعد بالفعل في التطوير على إلكترون 4.0.0 بشكل كبير لأن كروميوم 67 أزال الدعم لMSVC وتحول إلى بناء مع Clang على ويندوز. مع بناء GN ، نورث كل أوامر المجمّع من Chromium مباشرة، لذلك حصلنا على بناء العصابة على Windows مجاناً!

 * كما أنه جعل من الأسهل على إلكترون استخدام [BoringSSL](https://boringssl.googlesource.com/boringssl/) في بناء موحد عبر إلكترون، الكروميوم و العقدة -- شيء كان [إشكالية قبل](https://electronjs.org/blog/electron-internals-using-node-as-a-library#shared-library-or-static-library).
