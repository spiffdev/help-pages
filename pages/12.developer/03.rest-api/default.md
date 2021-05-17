---
title: 'Rest API'
---

The Spiff REST API can be interacted with via an HTTPS request that has been signed with a client key and secret. A request to the API might look like the following:

```
POST /api/v2/orders HTTP/1.1
Host: api.spiff.com.au
Date: Mon, 23 Apr 2012 12:45:19 GMT
Authorization: SOA df8d23140eb443505c0661c5b58294ef472baf64:jHX6oLeqTXpynyqcvVC2MSHarhU
Content-Type: application/json
{
    "orderItems":[
        {"amountToOrder":1,"transactionId":"e3ac7f3a-a117-46d7-a5f0-232fbc7cfe38"}
    ]
}
```

Signing a request must be done by appending a base64 encoded signature string to an auth header with the client key. See below for an example of what this header should look like.

```
Authorization: SOA  ${ClientKey}:${Base64EncodedRequestSignature}
```

The request signature is computed from a hmac hash value of the following appeneded strings. To generate this hash the client secret should be used as the hash key.

```
${RequestMethod}\n${MD5(RequestBody)}\n${RequestContentType}\n${RequestDate}\n${RequestPath}
```

In the following PHP example, spiff_request_headers is a function that generates the expected headers:

```php
function spiff_hex_to_base64($hex) {
    $return = "";
    foreach (str_split($hex, 2) as $pair) {
        $return .= chr(hexdec($pair));
    }
    return base64_encode($return);
}

function spiff_auth_header($access_key, $secret_key, $method, $body, $content_type, $date_string, $path) {
    $md5 = md5($body, false);
    $string_to_sign = $method . "\n" . $md5 . "\n" . $content_type . "\n" . $date_string . "\n" . $path;
    $signature = spiff_hex_to_base64(hash_hmac("sha1", $string_to_sign, $secret_key));
    return 'SOA '  . $access_key . ':' . $signature;
}

function spiff_request_headers($access_key, $secret_key, $body, $path) {
    $content_type = 'application/json';
    $date = new DateTime("now", new DateTimeZone("GMT"));
    $date_string = $date->format("D, d M Y H:i:s") . " GMT";
    return array(
        'Authorization' => spiff_auth_header($access_key, $secret_key, 'POST', $body, $content_type, $date_string, $path),
        'Content-Type' => $content_type,
        'Date' => $date_string,
    );
}
```

## POST /api/v2/orders

An order consists of a set of items which each have a transaction ID, along with a quantity of each to order.

### Example Payload

```json
{
    "orderItems":[
        {"amountToOrder":1,"transactionId":"e3ac7f3a-a117-46d7-a5f0-232fbc7cfe38"}
    ]
}
```

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
|color|hex code|No|The color of the text. Defaults to the step's default color.|
|fontVariantId|UUID|Yes|The fontVariantId of the font that should be applied.|

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
```json
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
                        "color": "#ffffff",
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
```json
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