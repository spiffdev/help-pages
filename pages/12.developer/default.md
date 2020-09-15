---
title: Developer
---

## Introduction

Welcome to Spiff Development. This section of our help is primarily aimed at developers who are looking to build integrations with the Spiff platform. If you’re a merchant you might consider starting on a [different page](/spiff-concepts) which provides a higher-level overview of spiff with less of a technical focus. 

While Spiff is aimed at eCommerce the platform has been built from the ground up to be as flexible as possible. Any customer-facing HTML interface should be able to support a Spiff integration. It’s also possible to integrate with Spiff even if your platform is not geared towards eCommerce.

A Spiff integration consists of two components. First, there is a [Javascript API](/developer/javascript-api) that is hosted within the Spiff CDN. A Restful API which is available at api.spiff.com.au makes up the second part of the integration. The Javascript API can be accessed publicly while the Rest API is secured with a key and secret. The key and secret will be issued to you from the Spiff Hub and requires server to server requests. More detail on the key and secret can be found below. Both Spiff APIs need to be utilized to create a full end to end integration.

## Before You Begin

Before you begin building any [integration](/developer/integrations) you will need to understand some key concepts of Spiff. The following list provides a summary of these concepts and acts as a checklist detailing what needs to be set up within the Spiff Hub.

1. A Spiff account. You can sign up for a Spff account at [app.spiff.com.au](https://app.spiff.com.au)
2. A [product](/spiff-concepts/product). A product in Spiff should form a 1 to 1 relationship with the products you have set up in your existing platform. Note here there is no explicit link between your platform and Spiff and that you will only need to create Spiff products for your platform products that you intend to make available for customisation.
3. A [Workflow](/spiff-concepts/workflows). This can be set up in the Spiff Hub which is accessed after signing up. Spiff workflows are a detailed topic and more information can be found on their documentation page.
4. An Integration. To integrate with Spiff you will need to create an integration. The integration will provide you with the key and secret necessary to place a secure order. For more information on this process please see your integrations page which is linked above.
5. An Integration Product.  An integration product provides the link between a product and an integration. This can be created from either the integration page in the Spiff Hub or  the product page itself.

## Integration Overview

As mentioned above, two phases constitute a Spiff integration. First is creating a public transaction with the Spiff Javascript API and second is creating an order based on that transaction with the Spiff Rest API. The Javascript portion of the integration would be ideally implemented within the templating system of your merchant frontend while the order portion should be implemented using backend code. In the case of popular eCommerce platforms such as Shopify and Bigcommerce this would be accomplished using a webhook.

## Code Examples

The following is an example of a typical Javascript API integration. Note the comments in the code. They explain and link back to key concepts that have been outlined above. In the below all user variables are denotedt by two sets of curly brackets `{{}}`. See the table below for detals explaining each variable. Also remember to check the [JavascriptAPI page](/developer/javascript-api) for full details of the API.

```javascript

// This function could run when the user clicks a customise button on your page.
function instantiateSpiffTransaction() {
    const product = new window.Spiff.Product({
        integrationId: '{{intergrationId}}',
        productId: '{{integrationProductId}}'
    });

    product.on('ready', function() {
        const transaction = new window.Spiff.Transaction({
            presentmentCurrency: "AUD",
            product: product,
            embedElement: document.querySelector("#query-selector-on-my-product-page")
        });
        
        // We recommend displaying a spinner to the user at this point.
        document.querySelector('#a-spinner-for-the-button').style.visibility = 'visible';

        transaction.on('complete', function(event) {
            // In this case the user would provide the implementation for this function.
            addProductToMyCart(event.transactionId);
        })

        transaction.execute();
    })

    product.on('invalid', function() {
        console.error("Spiff product could not be found")
    })

    product.confirmActive()
}

```

|variable|explanation|
|---------|-------------|
|integrationId|The id of the integration. This ID can be used site wide and it is recommned to create a sandbox integration for testing in a lower environment|
|integrationProductId|This is the id of the integration product. If your customising more than one product we recommnd extending your product backend entity so that this id can be injected in to the script automaticlly. To find the integration productId login to the spiff Hub and visit the product page |

