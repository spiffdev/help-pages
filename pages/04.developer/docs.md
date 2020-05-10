---
title: Developer
---

# Spiff Javascript API

In order to open spiff workflows and allow your customers to customise their own versions of your products you must first interact with the Spiff Javascript API. The Spiff javascript API becomes avaiable to the pages of any shopfront that has the Spiff application installed. If you have not yet done this pelase [install one of our integrations](/quick-start).

## Spiff.Transaction

When ordering product on spiff a client needs to first create a transaction. A transaction represents all of the the customer's personalisation data for a given item in a given order order. Once created the transaction is saved in the spiff platform and ready for order. If your using the Spiff shopify application this ordering process happens by attaching the spiff transactionId to a line item. Spiff will then listen for orders with spiff transaction Id's and route the order to the approate store / location. The Spiff platfrom also has solutions for many advanced [routing options](/spiff-concepts/routing).

### Constructor Transaction(transactionOptions)

#### Useage

```javascript
const transactionOptions = {
	presentmentCurrency: "USD",
    integrationId: "1234",
    productId: "1234",
    shouldCreateDesignProduct: true,
    embedElement: HTMLDOMElement // Optional: If not provided spiff will popup a frame on top of everything else.
};
const transaction = new window.Spiff.Transaction(transactionOptions);
```

### Transaction.on(eventName, callback);

Registering callback methods with a given transaction is done via the on method. There are different kinds of callbacks detailed in the table below.

| Callback | Description |
| ------ | --- |
| complete | Called when the user has completed the transaction. | 
| quit | Called when the user has stopped the customisation process. Note that in this case no transactionId will be issued. | 

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