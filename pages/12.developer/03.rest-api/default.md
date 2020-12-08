---
title: 'Rest API'
---

## POST /api/batchtransactions

Spiff supports building designs directly via an API call. This feature is known as a headless design. A headless design allows a new transaction resource to instruct the design stage of a typical spiff workflow. Doing this allows a merchants customer to bypass the spiff workflow experience entirely. 

_Note: Even for a headless design the workflow still needs to be built within the spiff hub as if it were being used in the conventional spiff experience._


Before starting with headless designs it would be best to first [understand how a typical spiff integration works](/developer/integrations) if you don't already. It's also vital to this process to understand how Spiff transactions work.

When creating a headless design all step data for that design must be submitted with the transaction. The transaction will then be created with the corresponding design in the spiff backend. The resulting `transactionId` can then be placed as an order to Spiff after which the normal flow will be initiated. Unlike the conventional workflow for spiff, headless workflows allow for multiple workflows to be executed within a single design allowing fine grained control over design outputs.

The spiff step types currently supported are outlined below. Please contact [spiff support](https://spiffassist.freshdesk.com/support/solutions) and submit a request for the relevant step type to be added. 

##Text
The [text step](/spiff-concepts/step-types/add-text) places text on to a design in a preconfigured location. It requires the following data

|Name|Type|Required|Description|
|----|----|
|text|text|Yes|The text that should appear on the design. Note that validation rules configured in the workflow will be applied here|
|fontVariantId|UUID|No|The fontVariantId of the font that should be applied. This is not required when a default font has been configured in the workflow|

##Illustration
An [illustration step](/spiff-concepts/step-types/add-illustrations) places a given illustration in to a design. Note that a valid Spiff asset URL must be provided. To add assets to spiff, log into your account in the [spiff hub](https://app.spiff.com.au) and go to Store => Assets => Illustrations => Create Asset. 

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
        	"integrationProductId": "52e4d8c2-eb30-42e5-982a-c89c8c3d557d",
            "steps": [
                {
                	"name": "52e4d8c2-eb30-42e5-982a-c89c8c3d557d",
                    "data": {
                        "answerVariantId": "52e4d8c2-eb30-42e5-982a-c89c8c3d557d"
                    }
                },
                {
                    "name": "52e4d8c2-eb30-42e5-982a-c89c8c3d557d",
                    "data": {
                        "text": "Steve",
                        "fontVariantId": "52e4d8c2-eb30-42e5-982a-c89c8c3d557d"
                    }
                },
                {
                	"name": "52e4d8c2-eb30-42e5-982a-c89c8c3d557d",
                    "data": {
                        "illustrationVariantId": "52e4d8c2-eb30-42e5-982a-c89c8c3d557d"
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
    "content": [
        {
            "data": {
                "id": "<uuid>",
                "exportedData": {
                    "<uuid>": {
                        "stepTitle": "Name - Enter name up to 14 characters",
                        "selections": [
                            "You"
                        ],
                        "selectionPriceModifiers": [
                            0
                        ],
                        "text": "Steve",
                        "color": "#ffffff"
                    },
                    "<uuid>": {
                        "stepTitle": "Add Share a Coke gift box - $4 each",
                        "selections": [
                            "Yes"
                        ],
                        "selectionPriceModifiers": [
                            0
                        ]
                    },
                    "<uuid>": {
                        "stepTitle": "Personalise your Share a Coke Bottle",
                        "selections": [
                            "Coke Classic"
                        ],
                        "selectionPriceModifiers": [
                            0
                        ]
                    }
                }
            }
        }
    ]
}
```