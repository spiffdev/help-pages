---
title: 'Rest API'
---

## POST /transactions

Spiff supports headless designs. A headless design allows a new transaciton resource to instruct the design stage of a typical spiff workflow allowing the user to bypass the spiff workflow experance entirley. Before starting with headless designs it would be best to first [understand how a typical spiff integration works](/developer/integrations) if you don't already. 

When creating a headless design all step data for that design must be submitted with the transaction. The transaction will then be created with the corrsponding design in the spiff backend. The resulting transactionId can then be placed as an order to Spiff and the normal flow will be initiated there after.

When headless transactions are created a spiff workflow is instancited and all submitted step data must be provided in order and must also be validted according to the configured workflows. As each step is different and configurable the step types will represent different data shaps. These shapes are described below.

##Text
The [text step](/spiff-concepts/step-types/add-text) places text on to a design in a preconfigured location. It requires the following data

|Name|Type|Required|Description|
|----|----|
|text|text|Yes|The text that should appear on the design. Note that validation rules configured in the workflow will be applied here|
|font|SpiffAssetKey|No|The asset URL of the font that should be applied. This is not required when a default font has been configured in the workflow|

##Illustration
An [illustration step](/spiff-concepts/step-types/add-illustrations) places a given illustration in to a design. Note that a valid Spiff asset URL must be provided.

|Name|Type|Required|Descripiton|
|----|----|
|url|SpiffAssetKey|Yes|The Spiff asset key for the illustration|

##Question
A [question step collects information from a user as part of the workflow process](/spiff-concepts/step-types/add-question). This information is then populated to metadata that can then be used by downstram applications to aid in order delivery.

|Name|Type|Required|Descripiton|
|----|----|
|answer|text|Yes|The answer to the question in the workflow|


### Example Payload
```
{
	"integrationProductId": "<UUID>",
	"steps": [
    	{
        	"type": "question",
            "data": {
            	"answer": "True"
            }
        },
    	{
        	"type": "text",
            "data": {
            	"text": "Happy Birthday Steve",
                "font": "fonts/font.ttf"
            }
        },
        {
        	"type": "illustration",
            "data": {
            	"url": "illustrations/illustration.svg"
            }
        }
    ]
}
```