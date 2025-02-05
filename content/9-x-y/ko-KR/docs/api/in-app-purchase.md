# inAppPurchase

> Mac App Store의 인앱 결제입니다.

프로세스:[Main](../glossary.md#main-process)

## Events

`inAppPurchase` 모듈은 다음 이벤트를 발생시킵니다:

### Event: 'transactions-updated'

하나 이상의 트랜잭션이 업데이트됐을 때 발생합니다.

반환:

* `event` Event
* `transactions` Transaction[] - [`Transaction`](structures/transaction.md) 객체의 Array.

## 메소드

`inAppPurchase` 모듈은 다음 메서드를 가지고 있습니다:

### `inAppPurchase.purchaseProduct(productID[, quantity])`

* `productID` String - 결제할 제품의 식별자. (`com.example.app.product1` 의 식별자는 `product1` 임).
* `quantity` Integer (선택적) - 사용자가 결제하기 원하는 항목의 수량.

Returns `Promise<Boolean>` - Returns `true` if the product is valid and added to the payment queue.

반드시 `purchaseProduct`를 수행하기 전에 최대한 빨리 `transactions-updated` 이벤트를 등록해야 합니다.

### `inAppPurchase.getProducts(productIDs)`

* `productIDs` String[] - 받을 제품의 식별자.

Returns `Promise<Product[]>` - Resolves with an array of [`Product`](structures/product.md) objects.

제품 정보를 받아옵니다.

### `inAppPurchase.canMakePayments()`

Returns `Boolean` - whether a user can make a payment.

### `inAppPurchase.restoreCompletedTransactions()`

Restores finished transactions. This method can be called either to install purchases on additional devices, or to restore purchases for an application that the user deleted and reinstalled.

[The payment queue](https://developer.apple.com/documentation/storekit/skpaymentqueue?language=objc) delivers a new transaction for each previously completed transaction that can be restored. Each transaction includes a copy of the original transaction.

### `inAppPurchase.getReceiptURL()`

Returns `String` - the path to the receipt.

### `inAppPurchase.finishAllTransactions()`

모든 보류중인 트랜잭션을 완료합니다.

### `inAppPurchase.finishTransactionByDate(date)`

* `date` String - ISO 포맷의 트랜잭션을 끝낼 날짜.

날짜에 맞는 보류중인 트랜잭션을 완료합니다.
