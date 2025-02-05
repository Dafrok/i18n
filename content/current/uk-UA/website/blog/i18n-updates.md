---
title: "Оновлення інтернаціоналізації"
author: vanessayuenn
date: '2018-06-20'
---

З тих пір, як [запустити](https://electronjs.org/blog/new-website) нового інтернаціоналізованого сайту Electron, ми наполегливо працювали, щоб зробити досвід розробки Electron ще більш доступним для розробників за межами англомовного світу.

Ось, наші захоплюючі оновлення i18n!

---

## 🌐 Перемикач мови

Чи знаєте ви, що багато людей, які читають перекладену документацію часто спрощують посилання на оригінал англійської документації? Вони роблять це, щоб ознайомитися з англійськими документаціями та уникнути застарілих або неточних перекладів, однієї застереження міжнародних документацій.

<figure>
  <img class="screenshot" src="https://user-images.githubusercontent.com/6842965/35578586-cae629e2-05e4-11e8-9431-0278f8c2b39f.gif" alt="Мовний перемикач для документації Electron">
</figure>

Щоб спростити перехресне посилання на англійські доки, ми нещодавно відправили функцію, яка дозволяє вам легко увімкнути розділ документації Electron між англійською і будь-якою мовою, яку ви переглядаєте сайт. Перемикач мови буде показано, якщо на веб-сайті є неангломовна локальна.

## ⚡ Швидкий доступ до сторінки перекладу

<figure>
  <img class="screenshot" src="https://user-images.githubusercontent.com/6842965/36511386-c32e31fc-1766-11e8-8484-7466be6a5eb0.png" alt="Новий нижній колонтитул для документації Electron в японській">
  <figcaption>Конструктор документації Electron в японській мові</figcaption>
</figure>

Зауважте введене слово або неправильний переклад під час читання документації? Вам більше не потрібно входити в Crowdin, обирати локальний, знайдіть файл, який ви хочете виправити, і т. д. Замість цього, ви можете просто перегорнути вниз до заявленої документації та натиснути "Перекласти цю документацію" (або еквівалент вашою мовою). Voila! Ви непрямо переведені на сторінку перекладу Crowdin. Тепер підтвердіть свій переклад!

## 📈 Деяка статистика

Ever since we have publicized the Electron documentation i18n effort, we have seen _huge_ growth in translation contributions from Electron community members from all around the world. На сьогоднішній день у нас є **1,719,029 рядків перекладених - з 1,066 перекладачів спільноти і на 25 мовах**.

<figure>
  <a href="https://crowdin.com/project/electron/">
    <img class="screenshot" src="https://user-images.githubusercontent.com/6842965/41649826-ca26037c-747c-11e8-9594-5ce12d2978e2.png" alt="Прогноз перекладу наданий Crowdin">
    <figcaption>Прогноз перекладу надано Crowdin</figcaption>
  </a>
</figure>

Ось веселий графік, що показує приблизний час, необхідний для перекладу проекту на кожну мову, якщо існуючий темп (заснований на активності проекту протягом останніх 14 днів в момент письма).

## 📃 Опитування перекладача

Ми хотіли б дати величезний ❤️ дякуємо ❤️ кожному, хто зробив свій час, щоб допомогти покращити Electron! Щоб належним чином визнати важку роботу нашої спільноти перекладачів, ми створили опитування, щоб зібрати деяку інформацію (а саме зіставлення між їхніми користувачами Crowdin і Github іменами) про наших перекладачів.

Якщо ви один з наших неймовірних перекладачів, будь ласка, пройдіть кілька хвилин, щоб заповнити це: https://goo.gl/forms/b46sjdcHmlpV0GKT2.

## 🙌 Інтернаціоналізація вузла

Через успіх ініціативності Electron на сайті 18n Node.js вирішив моделити [їхнє оновлене зусилля i18n у](https://github.com/nodejs/i18n) після цієї схеми, яку ми так і використовуємо! 🎉 The [Node.js i18n initiative](https://github.com/nodejs/i18n) has now been launched and gained great momentum, but you can stil read about the early proposal and reasoning behind it [here](https://medium.com/the-node-js-collection/internationalizing-node-js-fe7761798b0a).

## 🔦 Посібник з участі

Якщо ви зацікавлені у приєднанні до наших зусиль, щоб зробити Electron більш доброзичливим, тут ми маємо зручний денді [допоміжний посібник](https://github.com/electron/i18n/blob/master/contributing.md) для того, щоб допомогти вам розпочати роботу. Щасливої інтернаціоналізації! 📚
