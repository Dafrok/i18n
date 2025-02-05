# Покупка в додатку (macOS)

## Підготовка

### Платна угода про додатки

Якщо цього ще немає, вам потрібно буде підписати Платну Угоду про додатки, а також налаштувати банківську та податкову інформацію в iTunes Connect.

[iTunes Connect Developer Help: Угода, податки й банківський огляд](https://help.apple.com/itunes-connect/developer/#/devb6df5ee51)

### Створіть свої покупки в додатку

Потім потрібно налаштувати покупки у додатку iTunes Connect, та включити такі деталі, як ім'я, ціни, а також опис того, що виділяє функції і функціональність Вашої покупки в додатку.

[iTunes Connect Developer Help: Створити покупку в додатку](https://help.apple.com/itunes-connect/developer/#/devae49fb316)

### Зміна CFBundleIdentifier

Щоб перевірити In-App покупки в розробці з Electron вам доведеться змінити `CFBundleIdentifier` в `node_modules/electron/dist/Electron.app/Contents/Info.plist`. Вам потрібно замінити `com.github.electron` на свій спільний ідентифікатор програми, створений iTunes Connect.

```xml
<key>CFBundleIdentifier</key>
<string>com.example.app</string>
```

## Приклад коду

Ось приклад, який показує, як використовувати покупки в програмі в Electron. Вам доведеться замінити ідентифікатори товару ідентифікаторами товарів, створених за допомогою iTunes Connect (ідентифікатор `com. xapp.app.product1` є `продуктом 1`). Зверніть увагу, що ви повинні послухати подію `під час транзакції` якомога швидше в вашому додатку.

```javascript
// Основний процес
const { inAppPurchase } = require('electron')
const PRODUCT_IDS = ['id1', 'id2']

// Слухайте транзакції якомога швидше.
inAppPurchase.on('transactions-updated', (event, transactions) => {
  if (!Array.isArray(transactions)) {
    return
  }

  // Перевірте кожну транзакцію.
  transactions.forEach(функція (transaction) {
    const payment = транзакцію. введення

    вимикач (транзакція. ransactionState) {
      case 'purchasing':
        консоль. og(`Придбання ${payment.productIdentifier}... )
        розірвати

      кейс 'придбано': {
        консолі. og(`${payment.productIdentifier} куплено.`)

        // Отримайте URL-адресу чеку.
        const receiptURL = inAppPurchase.getReceiptURL

        console.log(`ReceipURL: ${receiptURL}`)

        // Переслати файл чека на сервер і перевірити, якщо він дійсний.
        // @перегляньте
https://developer.apple.com/library/content/releasenotes/General/ValidateAppStoreReceipt/Chapters/ValidateRemotely.html
        // ...
        // Якщо чек дійсний, продукт придбаний
        // ...

        // Завершити транзакцію.
        inAppPurchase.finishTransactionByDate(transaction.Date)

        розірвати


      (у разі 'failed':

        console.log(`Помилка при покупці ${payment.productIdentifier}.`)

        // Закінчить транзакцію.
        inAppPurchase.finishTransactionByDate(транзакція. ransactionDate)

        розірвати
      випадок 'restored':

        консоль. og(`Придбання ${payment.productIdentifier} відновлено. )

        розірвати
      випадок 'deferred':

        консоль. og(`Придбання ${payment.productIdentifier} було відкладено. )

        розрив
      за замовчуванням:
        перерва
    }
  })
})

// Перевірте, чи дозволено користувачу покупку в додатку.
if (!inAppPurchase.canePayments()) {
  console.log('Користувач не має права робити in-app покупки.')


// Повторити і показати опис товару.
inAppPurchase.getProducts(PRODUCT_IDS).then(products => {
  // Перевірте параметри.
  if (!Array.isArray(products) || products.length <= 0) {
    console.log('Unable to retrieve the product informations.')
    return
  }

  // Display the name and price of each product.
  products.forEach(product => {
    console.log(`Ціна ${product.localizedTitle} це ${product.formattedPrice}.`)
  })

  // Запитайте користувача, який продукт він/вона хоче придбати.
  const selectedProduct = products[0]
  const selectedquantity = 1

  // Придбайте обраний продукт.
  inAppPurchase.purchaseProduct(selectedProduct.productIdentifier, selectedQuantQuantity).then(isProductValid => {
    якщо (!isProductValid) {
      консолі. og('Продукт є неприпустимим.')
      повертати
    }

    . og('Платіж було додано в чергу платежу.')
  })
})
```
