---
title: Developer
---

# window.Spiff

### Spiff.openWorkflow

Opening a workflow within Spiff. This will create an iframe on the page which will be styled as a modal. At this point the user will proceed though the spiff workflow. When the user is done or they exit out we will call the provided callback with all data collected during the workflow session.

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