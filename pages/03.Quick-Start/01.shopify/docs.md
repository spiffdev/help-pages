---
title: Shopify
media_order: 'Screen Shot 2020-04-29 at 5.47.30 am.png,Screen Shot 2020-04-29 at 6.09.24 am.png,Screen Shot 2020-04-29 at 6.22.55 am.png,Screen Shot 2020-05-05 at 6.32.01 am.png,Screen Shot 2020-05-05 at 6.32.58 am.png'
---

## Onboarding

Merchants will find spiff in the [Shopify app store ](https://apps.shopify.com/spiff-connect?surface_detail=product+customiser&surface_inter_position=1&surface_intra_position=4&surface_type=search).
![](Screen%20Shot%202020-04-29%20at%205.47.30%20am.png)

Install the app. 
No credit cards required upfront. Free trial period of 14 days applies so installing is risk free. 

The merchant must have an active Shopify Store in order to install spiff. If you install spiff whilst logged into your store, the install will begin automatically. If the merchant is not logged in, they will be prompted by Shopify to either login or sign up to create a store 
![](Screen%20Shot%202020-04-29%20at%206.09.24%20am.png)

Next, you are presented with the standard pre-install page from Shopify which makes you aware that you are about to install spiff. It also notifies you of personal details and store access that required. 

![](Screen%20Shot%202020-04-29%20at%206.22.55%20am.png)

Having succesfully installed, you will be automatically directed through the spiff create your first product onboarding. 
The primary goal of this process is to have you: 
- Select a product from your store that you want to Personalize/Customize
- Create a workflow - Configurable steps that build the customer journey
- Order content required to execute this experience or link to existing public asset.
- Render Personalise Now Button 
- Choose a Plan (You can start on the teaser with free trial) 
- Test - Display a 3D product with steps using spiff in your store

### Render the Personalise Now Button 
![](Screen%20Shot%202020-05-05%20at%206.32.01%20am.png?lightbox=1200,600&resize=600,400)![](Screen%20Shot%202020-05-05%20at%206.32.58%20am.png?lightbox=1200,800&resize=600,400)

In the 2 examples above you can see that the **spiff button can either augment or replace the add-to-cart button**.

>> the way that spiff opens in your site is customisable but would require a developer with shopify liquid templates experience to interact with our api 

It renders on the product page and is customisable via the [install snippet](http://help.spiff.com.au/#installation) that is inserted into your store.

Customizable Attributtes of the Personalize Now Button (Edited in your Liquid Templates)

- Position
- Button Color
- Button Text
- Choose to appear with or instead of the Add to Cart button.

In your liquid templates, Find the line that creates the product form, which will look like this:

```
{% form 'product' ... %}
```

Below that line, add this:

```
{% render 'spiff-button', product_handle: product.handle %}
```

If you wish to customise the look of the button, you can supply arguments for text and colour.

```
{% render 'spiff-button', product_handle: product.handle, label_text: 'Customise me!', label_colour: '#000000', background_colour: '#FFFFFF' %}
```

Once you have installed the snippet, created a workflow and linked a 3D model, your product should display in the live store. 

Onboarding complete!

