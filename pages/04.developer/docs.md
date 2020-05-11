---
title: Developer
---

# Spiff Javascript API

In order to open spiff workflows and allow your customers to customise their own versions of your products you must first interact with the Spiff Javascript API. The Spiff javascript API becomes avaiable to the pages of any shopfront that has the Spiff application installed. If you have not yet done this pelase [install one of our integrations](/quick-start).

## Spiff.Transaction

When ordering product on spiff a client needs to first create a transaction. A transaction represents all of the the customer's personalisation data for a given item in a given order order. Once created the transaction is saved in the spiff platform and ready for order. If your using the Spiff shopify application this ordering process happens by attaching the spiff transactionId to a line item. Spiff will then listen for orders with spiff transaction Id's and route the order to the approate store / location. The Spiff platfrom also has solutions for many advanced [routing options](/spiff-concepts/routing).

#### Constructor new Transaction(transactionOptions: object)

##### Parameter: Transaction Options

The set of options to create the transaction with. See below table for constructing the options.

|Option|Description|
| ------ | --- |
|**presentmentCurrency**:string|The currency that the transaction amount should be calculated in. This should be set to what ever currency the users chooses to pay in. Use standard three letter currency codes such as "USD", "GBP" and "AUD"|
|**integrationId**: string|The integration for the given store front. If you don't know your integration ID login in to the spiff hub. It will be listed there|
|**productId**: string|The spiff product id for the current product. If you don't know your product ID loign to the spiff hub. It will be listed there|
|**\[shouldCreateDesignProduct\]**:boolean| Optional. A flag that will create a "design product" on your eCommerce. Currently this is only supported on shopify. Note in the on complete callback of the transaction this productId will be returned as designProductId allow you to add it to your cart|
|**\[embedElement\]**: DOMElement| Optional. The JavascriptDOM element you would like the spiff workflow Iframe to be inserted. Note if you don't set this Spiff will add the Iframe with a modal style treatment. Note as well if you do provide a DOM element the on quit callback will never be called.|

#### Useage

```javascript
const transactionOptions = {
	presentmentCurrency: "USD",
    integrationId: "1234",
    productId: "1234",
    shouldCreateDesignProduct: true,
    embedElement: document.querySelector("#spiff-workflow-container")
};
const transaction = new window.Spiff.Transaction(transactionOptions);
```

### Transaction.on(eventName: string, callback: () => );

Registering callback methods with a given transaction is done via the on method. There are different kinds of callbacks detailed in the table below.

| Callback | Description |
| ------ | --- |
| complete | Called when the user has completed the transaction. | 
| quit | Called when the user has stopped the customisation process. Note that in this case no transactionId will be issued. | 

#### Complete Callback

When a user has completed their transaction the complete callback provided will be called with a single result parameter detailed below.

| name | Useage |
| ------ | --- |
|designMetaData| All design meta data that has been collected during the customisation process. This |

#### Useage

```javascript

// called when the user has completed their transaction
transaction.on('complete', (result) => {
    console.log(result.designMetaData); //All of the selected options that the user has chosen during the customisation
    console.log(result.transactionId); // The spiff transactionId. This needs to be placed in the metadata of the order
    console.log(result.designProductId); // Only set if shouldCreateDesignProduct is set to true
    console.log(result.complete); // Did the user quit early
	console.log(result.baseCost); // The base cost of the customised item
    console.log(result.previewImage); // The preview image of the design
    console.log(result.designId); // The saved design ID that the user just created. This can be used in conjunction with window.Spiff.replayDesign
});

// Called if the user quit early
transaction.on('quit', () => {
	console.log("The user exited before completing their design");
});

// Start the whole process
transaction.execute();

//design meta data
{
    selectedOptions: {
    	questionStep: {
        	variantName: "blue",
            cost: 1000 // in subunits
        }
    },
    metaData: {
    	illustrationStep: "https://assets.spiff.com.au/images/something.svg"
    }
}

```