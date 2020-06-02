---
title: Developer
---

# Spiff Javascript API

In order to open spiff workflows and allow your customers to customise their own versions of your products you must first interact with the Spiff Javascript API. The Spiff javascript API becomes avaiable to the pages of any shopfront that has the Spiff application installed. If you have not yet done this pelase [install one of our integrations](/quick-start).

## Spiff.Product

### Constructor

```new Spiff.Product(productOptions)```

### ProductOptions

|Option|Type|Description|
| ------ | --- |
|integrationId|string|The integration for the given store front. If you don't know your integration ID login in to the spiff hub. It will be listed there. In the case of shopify it will be the URL to your store e.g. "store.myshopify.com"|
|productId|string|The spiff product id for the current product. If you don't know your product ID loign to your eCommerce integration and check it from that control panel. In the case of shopify it will be a number like "3584328925261"|

#### Usage

```javascript
const productOptions = {
    integrationId: "example.myshopify.com",
    productId: "1234"
};
const product = new window.Spiff.Product(productOptions);
```

### on(eventName: string, callback: (callbackOptions: object) => void): void

Register a callback method on the product object. There are different kinds of callbacks detailed in the table below.

| Callback|Description|
| ------ | --- |
| ready | The product has been determined to exist in Spiff's database and is enabled. | 
| invalid | Spiff could not find the product or it is not enabled. | 

### confirmActive(): Promise&lt;void&gt;

Confirm that the configured product exists and is enabled. Calling this method and waiting for the "ready" event to fire is required before a transaction amy be created.

## Spiff.Transaction

When ordering product on spiff a client needs to first create a transaction. A transaction represents all of the the customer's personalisation data for a given item in a given order order. Once created the transaction is saved in the spiff platform and ready for order. If your using the Spiff shopify application this ordering process happens by attaching the spiff transactionId to a line item. Spiff will then listen for orders with spiff transaction Id's and route the order to the approate store / location. The Spiff platfrom also has solutions for many advanced [routing options](/spiff-concepts/routing).

#### Constructor

```new Transaction(transactionOptions: object)```

##### Parameter: Transaction Options

The set of options to create the transaction with. See below table for constructing the options.

|Option|Type|Description|
| ------ | --- |
|presentmentCurrency|string|The currency that the transaction amount should be calculated in. This should be set to what ever currency the users chooses to pay in. Use standard three letter currency codes such as "USD", "GBP" and "AUD"|
|product|Product|A Spiff product which has been confirmed to be active.|
|shouldCreateDesignProduct|boolean| **Optional**. A flag that will create a "design product" on your eCommerce. Currently this is only supported on shopify. Note in the on complete callback of the transaction this productId will be returned as designProductId allow you to add it to your cart|
|embedElement|DOMElement| **Optional**. The JavascriptDOM element you would like the spiff workflow Iframe to be inserted. Note if you don't set this Spiff will add the Iframe with a modal style treatment. Note as well if you do provide a DOM element the on quit callback will never be called.|

#### Useage

```javascript
const transactionOptions = {
	presentmentCurrency: "USD",
    product: product, // See Spiff.Product
    shouldCreateDesignProduct: true,
    embedElement: document.querySelector("#spiff-workflow-container")
};
const transaction = new window.Spiff.Transaction(transactionOptions);
```

### on(eventName: string, callback: (callbackOptions: object) => void): void

Registering callback methods with a given transaction is done via the on method. There are different kinds of callbacks detailed in the table below.

| Callback|Description|
| ------ | --- |
| complete | Called when the user has completed the transaction. | 
| quit | Called when the user has stopped the customisation process. Note that in this case no transactionId will be issued. | 

#### Complete Callback

When a user has completed their transaction the complete callback provided will be called with a single result parameter detailed below.

| Name |Type| Useage |
| ------ | --- |
|designMetaData|object| All design meta data that has been collected during the customisation process. This will vary depending on the configured workflow.|
|transactionId|string| The transactionId assigned to the created transaction. Note this will only be created if the user completes the workflow process. |
|designProductId|string | **Optional**.  This will be set if the transaction has been setup to create a design product. Note this is currently only supported by shopify. If a design product has not been created it is up to the integration to either setup a different means of attaching the transactionId to the order or attaching the transactionId to the meta data of the approate line item. |
|designProductVariantId|string|**Optional** This will be set if the transaction has been setup to create a design product and the eCommerce platform supports variants. Note this is currently only supported by shopify. If a design product has not been created it is up to the integration to either setup a different means of attaching the transactionId to the order or attaching the transactionId to the meta data of the approate line item. |
|baseCost|number| The base cost of the item. This is based on the price of the spiff item and may be different in the e-Commernce platform. Costs will always be returned in subunits|
|optionsCost|number| Options cost will be calculated based on the users selected options. This will differ from product to product. See the options selection in the spiff hub for more details. Will be set to zero if no options are avaiable|
|previewImage|string| A url to a preview image that has been generated from the users design. This can be then hotlinked to from any where in the merchant shop|

##### Useage example of Complete callback

```javascript
// called when the user has completed their transaction
transaction.on('complete', (result) => {
    console.log(result.designMetaData);
    console.log(result.transactionId);
    console.log(result.designProductId);
    console.log(result.designProductVariantId);
	console.log(result.baseCost);
    console.log(result.optionsCost);
    console.log(result.previewImage);
});
```

#### Quit Callback

The quit callback is called if the transaction has been created with out a DOM element and the user as closed the modal before completing the transaction. In the case of quit no design will be created and the resulting transaction should be discarded. If the user wants to customise after this point a new transaction should be created.

```javascript

// Called if the user quit early
transaction.on('quit', () => {
	console.log("The user exited before completing their design");
});
```

### execute(): Promise&lt;void&gt;

Calling execute will trigger the created transaction to create and render the Iframe according to how the transaction has been cofigured. If no DOMElement has been prodvided setting up the transaction calling execute will open the spiff modal. If a DOM Element has been added then the spiff workflow will render in that provided element. The promise returned by this method will resolve once the transaction has been setup. Given the user might have a slow connection it might be worth displaying some sort of loading queue at this point. Once the promise resolves hide the loading state. Note as well this method will not timeout so setting a time out of perhaps 10 seconds might be a good idea.

```javascript
transaction.execute();
```