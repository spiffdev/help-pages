---
title: 'Redirect Products'
---

Most uses cases which aren't covered by the default snippets will need to be handled with custom code that interfaces with the Javascript API, but for some very specific use cases, the only extra step needed is to add a tag to your Shopify product that fits a certain pattern. These uses cases involve launching workflows for one product from the product page of another product.

The product whose page should display the button is the product that you'll attach the tag to. For example, if you have a laptop product which has the tag "spiff-personalisable-product-handle-laptop-bag", then when customers visit the page for your laptop product they can launch a workflow for your product with the handle "laptop-bag".

## spiff-personalisable-product-handle-(product handle)

Both the customized product and the product for the page will be added to the cart, then the customer will be redirected to the cart page.

## spiff-only-product-handle-(product handle)

The customized product will be added to the cart but the product for the page will not be. The customer will then be redirected to the cart page.

## spiff-no-redirect-product-handle-(product handle)

The customized product will be added to the cart but the product for the page will not be. The customer will not be redirected away from the page.