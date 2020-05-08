---
title: Developer
---

# Spiff Javascript API

In order to open spiff workflows and allow your customers to customise their own versions of your products you must first interact with the Spiff Javascript API. The Spiff javascript API becomes avaiable to the pages of any shopfront that has the Spiff application installed. If you have not yet done this pelase [install one of our integrations](/quick-start).

## Spiff.openWorkflow()

Opening a workflow within Spiff. This will create an iframe on the page which will be styled as a modal. At this point the user will proceed though the spiff workflow. When the user is done or they exit out we will call the provided callback with all data collected during the workflow session.

### Example Usage

```javascript
const transactionOptions = {
	presentmentCurrency: "USD",
    integrationId: "1234",
    productId: "1234",
    shouldCreateDesignProduct: true,
    embedElement: HTMLDOMElement // Optional: If not provided spiff will popup a frame on top of everything else.
};


const transaction = new window.Spiff.Transaction(transactionOptions);

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