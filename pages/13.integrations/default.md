---
title: Integrations
media_order: 'flow.png,flow-order.png'
---

## Overview
The Spiff API allows you to execute the full customistion lifecycle of a product. This life cycle consists of two phases and involves the creation of two distinct entities. The first phase is based inside the user browser and executed via javascript most commonly on a eCommerce store front. This phase is executed by the customer anonymously and it's result is a transaction that is stored within the Spiff cloud.  The second phase is takes the form of a secure API call confirming the customer order and is executed by the merchant who owns the customer. When execiting the second phase the order creation must include the transactionId provided by the exection of the first phase.

It is up to the developer of the integration to store the transactionId between phases in order to provide it for the second phase to be exected. Many existing integrations store the transactionId with the line item in their order allowing many customisations to be ordered at one time.

## Phase 1 : Transaction
The first step in the customisation of any product is creating a transaction. A transaction is created publiclly and stored with a design in spiff. To create a transaction the front end javascript API of spiff will need to be called. This front end API should be loaded form our CDN in to the merchants web page. For full details on using this API and creating a transaction please refer to the [Javascript API](/developer) page.

![](flow.png)

## Phase 2: Order
Once an order for the customisable product takes place spiff must be notified when it is time for the order to be processed. For a typical e-Commerce integration this would take place once the user has rendered payment to the merchant for their prodcuts. Orders are assiocated with a transactionId that was used during phase one to setup the inital customisation and a transactionId is always required to create an order.

![](flow-order.png)

### Example Orders Request
```
POST /targets HTTP/1.1
Host: api.spiff.com.au
Date: Mon, 23 Apr 2012 12:45:19 GMT
Authorization: VWS df8d23140eb443505c0661c5b58294ef472baf64:jHX6oLeqTXpynyqcvVC2MSHarhU
Content-Type: application/json
{
    "autoPrint":false,
    "orderItems":[
        {"amountToOrder":1,"transactionId":"e3ac7f3a-a117-46d7-a5f0-232fbc7cfe38"}
    ]
}
```

## Signing Requests

