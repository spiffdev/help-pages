---
title: Developer
---

Opening a workflow within Spiff

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