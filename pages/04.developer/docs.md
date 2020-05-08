---
title: Developer
---

# Spiff Javascript API

In order to open spiff workflows and allow your customers to customise their own versions of your products you must first interact with the Spiff Javascript API. The Spiff javascript API becomes avaiable to the pages of any shopfront that has the Spiff application installed. If you have not yet done this pelase [install one of our integrations](/quick-start).

## Spiff.openWorkflow()

Opening a workflow within Spiff. This will create an iframe on the page which will be styled as a modal. At this point the user will proceed though the spiff workflow. When the user is done or they exit out we will call the provided callback with all data collected during the workflow session.

### Example Usage

```javascript
const workflowOptions = {
	presentmentCurrency: "USD",
    integrationId: "1234",
    productId: "1234",
};

window.Spiff.openWorkflow(workflowOptions, (workflowResult) => {
    console.log(workflowResult.metaData);
});
```