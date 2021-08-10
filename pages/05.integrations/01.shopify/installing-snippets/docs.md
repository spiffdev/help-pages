---
title: ' Installing Snippets'
visible: true
---

This page describes how to use out-of-the-box behaviour for opening workflows and adding the created design to the cart. Behaviours unique to your store will require use of the API.

# To add a new button (Customize Now)

In your shopify admin,  
click onto online store  
then go to your active theme 

Note: If you have a live site and you wish to test your spiff workflows without risking customers also seeing them, click duplicate in the actions tab of your active theme. Rename it to test theme and then continue following the steps below. This means that when you want to test your spiff workflows you will need to click into actions of the test theme and preview. 

Click on Actions and select Edit Code  
For the Debut theme (this position could vary for other themes and will be different again if you use a page builder)  
Click in the search bar and type product-template  
Click on the product-template.liquid which will open the code in that folder relevant to the product pages in your site
In the code section on the right click and press cntrl f to bring up finder  
Search for 'form'
Click the arrow to scroll through the results until you see the line that starts like this 

```{% form 'product' ... %}```

Below that line, add this:

```{% render 'spiff-button-standard', product_handle: product.handle %}```

Click Save and you are done and can now exit the code section

If you wish to customise the look of the button, you can supply arguments for text and colour.

```{% render 'spiff-button-standard', product_handle: product.handle, label_text: '&nbsp;&nbsp;&nbsp;  CUSTOMIZE AND ADD TO CART &nbsp;&nbsp;&nbsp; ', label_colour: '#FFFFFF', background_colour: '#000000' width: '175', height: '75', redirect_to_cart: true %}```

The spiff-button-standard snippet must take the following mandatory argument:

- product_handle: The handle of the product. The product handle is the same string that appears as the slug in the URL of that product's page.

The spiff-button snippet additionally may take the following optional arguments:

- background_colour: The background colour of the button. Defaults to Spiff Pink.

- height: The value to use as the height of the button, e.g. '20px'.

- label_colour: The colour of the text on the button. Defaults to white.

- label_text: The text to display on the button. Defaults to "Customise now on #spiff".

- redirect_to_cart: Whether to redirect the user to the cart page on completion of the workflow. Defaults to false,

- width: The value to use as the width of the button e.g. '100px',

# To add a new button that creates design products

A design product is a product that is created in your store when a customer completes a workflow. That product is associated with the customer's design and is the product that the customer checks out.

For a button that creates design products, follow the instructions for "To create a new button" but substitute "spiff-button-standard" with "spiff-button-design-product".

# Optional Steps

## Hiding existing elements

Suppose you have an element on product pages that you only want to hide if the product is personalisable, like this:

```<button>Hide Me For Spiff Products</button>```

Simply modify the element like so:

```
<button
    data-spiff-hide
    data-product-id='{{product.id}}'
>
Hide Me For Spiff Products
</button>
```
