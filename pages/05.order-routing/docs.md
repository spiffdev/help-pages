---
title: 'Order Routing'
media_order: 'orders page.png,vieworders.png'
---

Your customer has just placed their order, what happens now ? Spiff has developed one of the most sophisticated order routing systems in the market. 

We deliver order information in two ways. **Order Metadata** and **Print Ready PDF's**

### Order Metadata (Order information)
Order Metadata is all the information your user has entered given to you in an order summary. By Default, this order summary appears against the order number on the Orders page in the spiff Hub. The orders page is set to show only todays orders. To show orders from the past click on the date picker in the top right of that page. Quickly naviagate to orders for yesterday and month to date or select a custom date range. 

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/07.order-routing/orders%20page.png)
When you click on view orders you see all the order information the user entered making it easy to fulfil your orders. Especially powerful for customization workflows
![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/07.order-routing/vieworders.png)

For Shopify users, Spiff Order Routing can also populate the order details straight into your shopify orders page. This means all the information you need is in one spot making it more efficient to fulfil.

Currently, the metadata supported by each step type is as follows:

#### Illustration

* Colors: The list of selected colors
* Image: The name of the selected illustration variant

#### Question

* Selections: The list of selected variants

#### Text

* Text: The entered message

#### Upload

* Image: A URL of the uploaded photo

### Ready to Print PDF's
The Spiff system also creates a print ready pdf built by your customers during their design experience. 
As a standard are created once the consumer orders their product. They are stored by default in the Spiff Order as shown in the above image to the left of the View order button. Clicking the pdf button will trigger a download to your local device. 

To add automation spiff can automate pdf routing to send them directly to an external location (your print device or 3rd Party Manufacturer). Pdf's are named after the order number from your ecommerce system. 

### Advanced Routing Options
- Auto send Pdf's to your customer via email
- Spiff Queues - Create multiple locations for fulfilment and route orders based on a set of business rules. Enterprise only (Geographical location, volume based and others). The spiff print server script is installed on a local machine and call on the spiff queue system to check for orders that are relevant to it. 
- Instore Campaigns - Manage internal in-store campaigns by having staff enter orders directly into the spiff hub and have those orders routed through the spiff Queue system back to the relevant machines for fulfilment.
- For companies that use Third party 3PL fulfillers - Once a sale gets made online, the order is routed via metadata and a pdf through to the fulfillers internal systems via our API. Through the API fulfillers can manage orders through their own system and trigger any number of events, including printing direct to a local device. 



 

 

Order Summary  - Spiff provides the ability to receive the purchase as Metadata instead of a pdf. This Metadata is then displayed as a summary of the users purchases which the merchant can then use to fulfil the order. 

Suitable for businesses wishing to provide customisation features where the end product may simply require the merchant to configure a product from a set of sub products rather than actually print onto the product. 

This is more suitable when items are not made to order, and they already have everything in stock. 


This is not appropriate when customers are personalising products by uploading images etc. Any form of personalisation will mean that a PDF is required. See exmamples