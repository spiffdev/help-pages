---
title: Developer
---

Please check in with spiff support reguraliry for updates.   

Also we welcome feed back from developers in an effort to improve the API offering. 

### [Integration with a non Shopify or Wordpress Website ( Or if you want bespoke behaviour)](https://help.spiff.com.au/developer/integrations) 


### [Spiff Javascript API](https://help.spiff.com.au/developer/javascript-api)
The Spiff Javascript API allows you to execute the full customistion lifecycle of a product. This life cycle consists of two phases and involves the creation of two distinct entities. The first phase is based inside the user browser and executed via javascript most commonly on a eCommerce store front. This phase is executed by the customer anonymously and it's result is a transaction that is stored within the Spiff cloud.  The second phase takes this created transaction and orders it confirming the customer order has been executed by the merchant who owns the customer. When executing the second phase the order creation must include the `transactionId` provided by the execution@ of the first phase. It is this this `transactionId` that links the user customisation to an order.