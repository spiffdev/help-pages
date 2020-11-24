---
title: 'Rest API'
---

## POST /api/batchtransactions

Spiff supports building designs directly via an API call. This feature is known as a headless design. A headless design allows a new transaciton resource to instruct the design stage of a typical spiff workflow allowing the user to bypass the spiff workflow experance entirley. Before starting with headless designs it would be best to first [understand how a typical spiff integration works](/developer/integrations) if you don't already. It's also vital to this process to understand how Spiff transactions work.

When creating a headless design all step data for that design must be submitted with the transaction. The transaction will then be created with the corrsponding design in the spiff backend. The resulting transactionId can then be placed as an order to Spiff and the normal flow will be initiated there after. Unlike the conventianl workflow for spiff, headless workflows allow for multipule workflows to be executed within a single design allowing fine grained control over design outputs.

##Text
The [text step](/spiff-concepts/step-types/add-text) places text on to a design in a preconfigured location. It requires the following data

|Name|Type|Required|Description|
|----|----|
|text|text|Yes|The text that should appear on the design. Note that validation rules configured in the workflow will be applied here|
|fontVariantId|UUID|No|The asset variantId of the font that should be applied. This is not required when a default font has been configured in the workflow|

##Illustration
An [illustration step](/spiff-concepts/step-types/add-illustrations) places a given illustration in to a design. Note that a valid Spiff asset URL must be provided.

|Name|Type|Required|Descripiton|
|----|----|
|illustrationVariantId|UUID|Yes|The Spiff variant for the illustration|

##Question
A [question step collects information from a user as part of the workflow process](/spiff-concepts/step-types/add-question). This information is then populated to metadata that can then be used by downstram applications to aid in order delivery.

|Name|Type|Required|Descripiton|
|----|----|
|answerVariantId|UUID|Yes|The answer to the question in the workflow|


### Example Payload
```
{
    "transactions": [
        {
        	"workflowSlug": "workflow-slug",
        	"integrationProductId": "<UUID>",
            "steps": [
                {
                	"name": "<UUID>",
                    "data": {
                        "answerVariantId": "52e4d8c2-eb30-42e5-982a-c89c8c3d557d"
                    }
                },
                {
                    "name": "<UUID>",
                    "data": {
                        "text": "Happy Birthday Steve",
                        "fontVariantId": "52e4d8c2-eb30-42e5-982a-c89c8c3d557d"
                    }
                },
                {
                	"name": "<UUID>",
                    "data": {
                        "illustrationVariantId": "<UUID>"
                    }
                }
            ]
        }
    ]
}
```

### Example Response
```
{
	"transactions": [
    	{
        	"id": "<UUID>" 
        }
    ]
}
```