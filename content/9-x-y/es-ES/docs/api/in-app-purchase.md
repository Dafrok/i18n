# Compras integradas

> Compras In-app en Mac App Store.

Proceso: [Main](../glossary.md#main-process)

## Eventos

El módulo `inAppPurchase` emite los siguientes eventos:

### Event: 'transactions-updated'

Emitido cuando una o más transacciones han sido actualizadas.

Devuelve:

* `event` Event
* `transactions` Transaction[] - Un array de objetos [`Transaction`](structures/transaction.md).

## Métodos

El módulo `inAppPurchase` tiene los siguientes métodos:

### `inAppPurchase.purchaseProduct(productID[, quantity])`

* `productID` String - El identificador del producto a comprar. (El identificador de `com.example.app.product1` es `product1`).
* `quantity` Integer (opcional) - El número de ítems que el usuario quiere comprar.

Devuelve `Promise<Boolean>` - Devuelve `true` si el producto es valido y añadido a la cola de pago.

Usted debería escuchar por el evento `transactions-updated` tan pronto como sea posible y sin dudas antes de llamar a `purchaseProduct`.

### `inAppPurchase.getProducts(productIDs)`

* `productIDs` String[] - Los identificadores de los productos a obtener.

Devuelve `Promise<Product[]>` - Resuelve con un array de objetos [`Product`](structures/product.md).

Recupera las descripciones del producto.

### `inAppPurchase.canMakePayments()`

Returns `Boolean` - whether a user can make a payment.

### `inAppPurchase.restoreCompletedTransactions()`

Restores finished transactions. This method can be called either to install purchases on additional devices, or to restore purchases for an application that the user deleted and reinstalled.

[The payment queue](https://developer.apple.com/documentation/storekit/skpaymentqueue?language=objc) delivers a new transaction for each previously completed transaction that can be restored. Each transaction includes a copy of the original transaction.

### `inAppPurchase.getReceiptURL()`

Returns `String` - the path to the receipt.

### `inAppPurchase.finishAllTransactions()`

Completa todas las transacciones pendientes.

### `inAppPurchase.finishTransactionByDate(date)`

* `date` String - La fecha en formato ISO de la transacción para terminar.

Completa las pendientes transacciones correspondiendo al día.
