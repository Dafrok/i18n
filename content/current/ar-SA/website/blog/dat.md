---
title: 'مشروع الأسبوع: الأب'
author:
  - karissa
  - yoshuawuyts
  - maxogden
  - zeke
date: '2017-02-21'
---

المشروع المميز هذا الأسبوع هو [Dat](https://datproject.org/)، [ممول من المنحة](https://changelog.com/rfc/6)، مفتوح المصدر ، أداة لامركزية لتوزيع مجموعات البيانات. تم بناء الجاذبية وصيانتها من قبل فريق [موزع جغرافيا](https://datproject.org/team)العديد منهم ساعد في كتابة هذه المشاركة.

---

[![لقطة شاشة للعرض الرئيسي لسطح البيانات، تظهر بضعة صفوف من البيانات المشتركة
](https://cloud.githubusercontent.com/assets/2289/23175925/dbaee7ec-f815-11e6-80cc-3041203c7842.png)](https://github.com/datproject/dat-desktop)

## أولاً ما هي البيانات؟

أردنا أن نجلب أفضل أجزاء النظراء إلى النظراء والنظم الموزعة لتقاسم البيانات. بدأنا بتبادل البيانات العلمية ثم بدأنا بالتفرع إلى مؤسسات البحوث والحكومة والخدمة العامة وأفرقة المصادر المفتوحة أيضا.

طريقة أخرى للتفكير فيها هي مزامنة وتحميل تطبيق مثل Dropbox أو BitTorrent Sync، باستثناء Dat هو [المصدر المفتوح](https://github.com/datproject). هدفنا هو أن نكون برمجيات قوية ومفتوحة المصدر لتبادل البيانات غير الربحية لبيانات كبيرة وصغيرة ومتوسطة وصغيرة ودفعة كبيرة

لاستخدام أداة `dat` CLI ، كل ما عليك كتابته هو:

```sh
دغ مسار المشاركة / إلى/my/مجلد
```

وسيقوم الأب بإنشاء رابط يمكنك استخدامه لإرسال هذا المجلد إلى شخص آخر -- لا توجد خوادم مركزية أو أطراف ثالثة تحصل على الوصول إلى بياناتك. على عكس BitTorrent، من المستحيل أيضا شم من يشارك ما ([أنظر إلى مسودة ورقة Dat لمزيد من التفاصيل](https://github.com/datproject/docs/blob/master/papers/dat-paper.md)).

## الآن نحن نعرف ما هو "دات". كيف يناسب Dat سطح المكتب ؟

[سطح المكتب](https://github.com/datproject/dat-desktop) هو طريقة لجعل Dat في متناول الناس الذين لا يستطيعون أو لا يريدون استخدام سطر الأوامر. يمكنك استضافة بيانات متعددة على جهازك وخدمة البيانات عبر الشبكة الخاصة بك.

## هل يمكنك مشاركة بعض حالات الاستخدام الرائع؟

### ملجأ البيانات + مشروع سفالبارد

نحن نعمل على شيء مشفر [مشروع سفالبارد](https://github.com/datproject/svalbard) له صلة بـ [ملجأ البيانات](http://www.ppehlab.org/datarefuge)، فريق يعمل على دعم البيانات الحكومية المتعلقة بالمناخ المعرضة لخطر الاختفاء. وسالبارد يسمى مستودع البذور العالمي في سفالبارد في المنطقة القطبية الشمالية الذي لديه مكتبة احتياطية كبيرة تحت الأرض للحمض النووي النباتي. نسختنا منها هي نسخة كبيرة من مجموعات البيانات العلمية العامة. بمجرد أن نعرف البيانات الوصفية ونثق بها، يمكننا بناء مشاريع رائعة أخرى مثل [شبكة تخزين البيانات التطوعية الموزعة](https://github.com/datproject/datasilo/).

### تحالف كاليفورنيا للبيانات المدنية

[CACivicData](http://www.californiacivicdata.org/) هو أرشيف مفتوح المصدر يخدم التنزيلات اليومية من CAL-ACCESS، قاعدة بيانات كاليفورنيا لتتبع الأموال في السياسة. هم يقومون [بإصدارات يومية](http://calaccess.californiacivicdata.org/downloads/0)، مما يعني استضافة الكثير من البيانات المكررة عبر ملفاتهم المضغوطة. نحن نعمل على استضافة بياناتهم كمستودع Dat الذي سيقلل من كمية القاعة وعرض النطاق الترددي اللازم للإشارة إلى إصدار محدد أو التحديث إلى إصدار أحدث.

## تحديثات إلكترون

هذه ليست ملموسة حتى الآن، لكننا نعتقد أن حالة استخدام ممتعة ستضع تطبيق إلكترون مجمع في مستودع Dat، ثم باستخدام عميل Dat في إلكترون لسحب أحدث دلاتس من التطبيق الثنائي المبني، لتوفير وقت التحميل ولكن أيضا لتقليل تكاليف عرض النطاق الترددي للخادم.

## من يجب أن يستخدم Dat سطح المكتب؟

أي شخص يريد مشاركة وتحديث البيانات عبر شبكة p2p. علماء البيانات، وقرصنة البيانات المفتوحة، والباحثون، والمطورين. نحن متجاوبون للغاية مع ردود الفعل إذا كان لدى أي شخص حالة استخدام رائعة لم نفكر فيها بعد. يمكنك أن تسقط بواسطة [دردشة Gitter](https://gitter.im/datproject/discussions) وأن تسألنا أي شيء!

## ما الذي سيأتي بعد ذلك في سطح المكتب من الدات و الدت؟

نشر حسابات المستخدم والبيانات الفوقية. نحن نعمل على تطبيق ويب لسجل Dat لنشره في [مشروع بيانات. rg](https://datproject.org/) الذي سيكون أساسا 'NPM لمجموعات البيانات', باستثناء التحذير الذي نحن بصدد أن نكون مجرد دليل بيانات فوقية والبيانات يمكن أن تعيش في أي مكان على الإنترنت (على عكس NPM أو GitHub حيث تستضيف جميع البيانات مركزياً، لأن شفرة المصدر صغيرة بما فيه الكفاية يمكنك تناسبها كلها في نظام واحد). وبما أن العديد من مجموعات البيانات ضخمة، فإننا بحاجة إلى سجل موحد (مماثل لكيفية عمل متعقبي بيتورنت). نريد أن نجعل من السهل على الناس العثور على مجموعات البيانات أو نشرها مع السجل من حاسوب Dat Office ، لجعل عملية تبادل البيانات عملية لا احتكاك.

وثمة سمة أخرى هي المجلدات المتعددة المؤلفين/التعاوني. لدينا خطط كبيرة للقيام بتدفقات عمل تعاونية، ربما مع الفروع، مشابهة لـ git، باستثناء مصمم حول تعاون مجموعة البيانات. لكننا لا نزال نعمل على تحقيق الاستقرار الشامل وتوحيد بروتوكولاتنا الآن!

## لماذا اخترت بناء سطح المكتب Dat على إلكترون؟

يتم بناء الدات باستخدام Node.js، لذلك كان مناسبا طبيعيا لتكاملنا. بالإضافة إلى ذلك، يستخدم مستخدمونا مجموعة متنوعة من الآلات منذ العلماء، قد يُجبر الباحثون والمسؤولون الحكوميون على استخدام بعض الإعدادات لمؤسساتهم -- وهذا يعني أننا بحاجة إلى أن نكون قادرين على استهداف ويندوز و لينكس فضلا عن ماك. "بات سطح المكتب" يعطينا ذلك بسهولة.

## ما هي بعض التحديات التي واجهتها أثناء بناء Dat و Dat سطح المكتب؟

معرفة ما يريده الناس. بدأنا بمجموعات بيانات جداول، لكننا أدركنا أن حل مشكلة معقدة بعض الشيء وأن معظم الناس لا يستخدمون قواعد البيانات. لذا في منتصف المشروع، قمنا بإعادة تصميم كل شيء من الصفر لاستخدام نظام الملفات ولم ننظر إلى الوراء.

كما واجهنا بعض المشاكل العامة في البنية التحتية الالكترونية، بما في ذلك:

- Telemetry - كيفية التقاط إحصائيات الاستخدام المجهول
- تحديثات - نوع من التجزئة والسحر لإعداد تحديثات تلقائية
- الإصدارات - توقيع XCode ، بناء الإصدارات على Travis، إجراء بنايات بيتا، كلها كانت تحديات.

نحن أيضا نستخدم Browserify و بعض التحولات الرائعة على "الواجهة الطرفية" في سطح المكتب Dat (والذي هو نوع من الغريب لأننا لا نزال نجمع حتى وإن كان لدينا `أصلي مطلوبين` -- ولكن لأننا نريد التحولات). للمساعدة بشكل أفضل في إدارة CSS الخاص بنا انتقلنا من Sass إلى استخدام [sheetify](https://github.com/stackcss/sheetify). لقد ساعدنا بشكل كبير على تعديل CSS الخاص بنا وجعل من الأسهل نقل واجهة المستخدم الخاصة بنا إلى بنية موجهة نحو المكونات مع تبعيات مشتركة. على سبيل المثال [بيانات الألوان](https://github.com/Kriesse/dat-colors) تحتوي على جميع ألواننا ويتم مشاركتها بين جميع مشاريعنا.

كنا دائما معجبا كبيرا بالمعايير و الحد الأدنى من المجردات. تم بناء واجهة كاملة باستخدام عقد DOM العادية مع بضع مكتبات مساعدة. لقد بدأنا في نقل بعض هذه المكونات إلى [عناصر أساسية](https://base.choo.io)، وهي مكتبة من مكونات منخفضة المستوى قابلة لإعادة الاستخدام. كما هو الحال مع معظم التكنولوجيا لدينا نواصل تكرارها حتى نحصل عليها بشكل صحيح. لكن كفريق لدينا إحساس بأننا نتجه في الاتجاه الصحيح هنا.

## في أي مجالات ينبغي تحسين إلكترون؟

نعتقد أن أكبر نقطة ألم هي الوحدات الأصلية. يؤدي إعادة بناء وحدات إلكترون مع npm إلى زيادة التعقيد في سير العمل. طور فريقنا وحدة تسمى [`تمهيدا لبناء`](http://npmjs.org/prebuild) التي تتعامل مع ثنائيات مبنية مسبقا، التي نجحت بشكل جيد في العقدة، ولكن سير عمل إلكترون لا يزال يتطلب خطوة مخصصة بعد التثبيت، عادة `npm تشغيل إعادة البناء`. كان ذلك مزعجا. لمعالجة هذا الأمر انتقلنا مؤخرا إلى استراتيجية حيث نجمع كل النسخ الثنائية المجمعة من جميع المنصات داخل كرة القطران npm وهذا يعني أن كرات القطران تصبح أكبر (رغم أنه يمكن تحسين هذا مع `. o` ملفات - المكتبات المشتركة)، هذا النهج يتفادى ضرورة تشغيل برامج ما بعد التثبيت ويتفادى أيضاً نمط تشغيل `npm لإعادة البناء` تماماً. إنه يعني أن `npm install` يقوم بالشيء الصحيح لإلكترون لأول مرة.

## ما هي الأشياء المفضلة لديك عن إلكترون؟

يبدو أن واجهة برمجة التطبيقات مدروسة جيداً، إنها مستقرة نسبياً، وهي تقوم بعمل جيد جداً في مواكبة الإصدارات العلوية للعقدة ، ليس هناك الكثير الذي يمكننا أن نطلبه !

## أي نصائح إلكترون قد تكون مفيدة للمطورين الآخرين؟

إذا كنت تستخدم وحدات أصلية، أعطِ [بناء مسبقًا](https://www.npmjs.com/package/prebuild) لق!

## ما هي أفضل طريقة لمتابعة تطورات الجدار؟

تابع [@dat_Project](https://twitter.com/dat_project) على تويتر، أو الاشتراك في رسالة البريد الإلكتروني [الخاصة بنا](https://tinyletter.com/datdata).

