---
title: Traceability API (preview)
description: Learn how to integrate the Traceability add-in for Dynamics 365 Supply Chain Management with third-party system through its API.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Traceability API (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

## Authentication

The platform security token is used to call the Traceability public API. Therefore, you must generate a *Microsoft Entra token* by using your Microsoft Entra application. You must then use the Microsoft Entra token to get the *access token* from the security service.

In Microsoft Azure \> App registrations \> Endpoints, you can get **OAuth 2.0 token endpoint (v2)** for *Entra token* generation.

![A screenshot of a computer Description automatically generated](media/image30.png)

Fetch a Microsoft Entra token by submitting an HTTP request that has following properties:

- URL: OAuth 2.0 token endpoint (v2)
- Method: GET
- Body content (form data):

| Key            | Value                                         |
|----------------|-----------------------------------------------|
| client\_id     | {Application (client) ID in Microsoft Azure}  |
| client\_secret | {Client secretes value}                       |
| grant\_type    | client\_credentials                           |
| scope          | 0cdb527f-a8d1-4bf8-9436-b352c68682b2/.default |

You should receive a Microsoft Entra token in response. It should resemble the following example.

Use Entra token (access token) to generate bear token by submitting an HTTP request that has following properties:

- URL: `https://securityservice.operations365.dynamics.com/token`
- Method: POST
- Body content (JSON)

You should receive an access token in response. You must use this token as a bearer token to call the Supply Chain Traceability API. Below is the example of response:

## Available APIs

You can create the API URL by combining the General setup \> App setting \> Endpoint with the Path from below list.

![A screenshot of a computer Description automatically generated](media/image31.png)

| Path | Method | Description |
|--|--|--|
| /api/environments/{environmentId}/events/PostBatchEvents | Post | Create genealogy node and activity |
| /api/environments/{environmentId}/traces/Query | Post | Query by tracking ID |

<!--KFM: Do we have *Remove genealogy node*? -->

## API for events post (Add)

This API is for events post which can be used for production component assembly, goods receipt in business activities. <!--KFM: A better/clearer description is needed. Also a better section heading. -->

- **Path:** `/api/environments/{environmentId}/events/PostBatchEvents`
- **Method**： `POST`

### Events post request payload

```json
[
    {
        "eventId": string,
        "description": string,
        "activityType": string, refer to predefined “Activity Type”,
        "activityCode": string, refer to configured “Activity Code” linked to “Activity Type”,
        "datetime": YYYY-MM-DDThh:mm:ss.sssz,
        "operator": string,
        "companyCode": string,
        "details": {
            "<data collection name>": <data collection value>
            },
        "consumptionTransactions": [
            {
                "transactionId": string,
                "itemId": string, refer to configured “item” for tracing,
                "trackingId": string,
                "serialId": string,
                "batchId": string,
                "quantity": decimal,
                "unitOfMeasure": string
            }
        ],
        "productTransactions": [
            {
                "transactionId": string,
                "itemId": string, refer to configured “item”,
                "trackingId": string,
                "serialId": string,
                "batchId": string,
                "quantity": decimal，
                "unitOfMeasure": string
            }
        ]
    }
]
```

### Events post top-level field descriptions

<!--KFM: I wasn't sure how to categorize these fields. Is "top-level" correct? -->

| Field Name | Description |
|--|--|
| `eventId` | The key to each activity against unique identity (SerialId/BatchId). Duplicated value is not allowed. System generates value if there is no value input by user. |
| `description` | The text of activity event description. |
| `activityType` | This field refers to predefined "Activity Type": Purchase, Sales, Production etc. |
| `activityCode` | This field refers to configured "Activity Code": GoodsReceipt, Add, Remove etc. |
| `dateTime` | The date and time of activity event happened. |
| `operator` | The operator who executed the activity event. You can input UserID, EmployeeID or more. |
| `companyCode` | For FnO, this field maps to legal entity. |
| *&lt;data collection name&gt;* | These fields are used to collect customization value. |

### Events post productTransactions element field descriptions

| Field Name | Description |
|--|--|
| `transactionId` | The key of transactions against per event. Duplicated value is not allowed. |
| `itemId` | Item number of top finished goods. |
| `trackingId` | This field is the key of genealogy node and is the combination of `itemId` and `companyCode` and `batchId` and `serialId`. |
| `serialId` | The serial number of top finished goods. |
| `batchId` | The batch number of top finished goods. |
| `quantity` | The operation quantity of top finished goods. |
| `unitOfMeasure` | The UoM of received quantity. |

### Events post consumptionTransactions element field descriptions

| Field Name | Description |
|--|--|
| `transactionId` | The key of transactions against per event. Duplicated value is not allowed. |
| `itemId` | Item number of component. |
| `trackingId` | This field is the key of genealogy node and is the combination of `itemId` and `companyCode` and `batchId` and `serialId`. |
| `serialId` | The serial number of component. |
| `batchId` | The batch number of component. |
| `quantity` | The consumption quantity of component. |
| `unitOfMeasure` | The UoM of consumption quantity. |

### Events post API response

On success, status code 204 will be returned.

### Events post example

Produce finished goods **A** with component **B** and **C** by different event.

#### Events post example request payload 1

```json
[
    {
        "EventId": "item B consumption-a8f441b3-2f15-5b92-8d84-230616113700",
        "CompanyCode": "USMF",
        "Operator": "Terry Alvarado",
        "Description": "Consumption for production A",
        "ActivityType": "Production",
        "ActivityCode": "Consumption",
        "Datetime": "2023-06-15T06:14:06.653Z",
        "Details": {
            "Operation Step": "OP1",
            "Resource": "RES1",
            "Reference Location": "RES-L01"
        },
        "ConsumptionTransactions": [
            {
                "TransactionId": "a8f441b3-2f15-5b92-8d84-230616113702",
                "ItemId": "B",
                "TrackingId": null,
                "Details": {},
                "Quantity": 1.0,
                "UnitOfMeasure": "ea",
                "BatchId": "B-001",
                "SerialId": null
            }
        ],
        "ProductTransactions": [
            {
                "TransactionId": "a8f441b3-2f15-5b92-8d84-230616113701",
                "ItemId": "A",
                "TrackingId": null,
                "Details": {},
                "Quantity": 1.0,
                "UnitOfMeasure": "ea",
                "TransactionType": 0,
                "BatchId": null,
                "SerialId": "A-001"
            }
        ]
    }
]
```

#### Events post example request payload 2

<!--KFM: Original used a table with the two payloads next to each other. That formatting won't work well here, and I'm not sure what it means, so I split into two sections. Is this correct? -->

```json
[
    {
        "EventId": "item C consumption-a8f441b3-2f15-5b92-8d84-230616113703",
        "CompanyCode": "USMF",
        "Operator": "Terry Alvarado",
        "Description": "Consumption for production A",
        "ActivityType": "Production",
        "ActivityCode": "Consumption",
        "Datetime": "2023-06-15T07:14:06.653Z",
        "Details": {
            "Operation Step": "OP2",
            "Resource": "RES2",
            "Reference Location": "RES-L02"
        },
        "ConsumptionTransactions": [
            {
                "TransactionId": "a8f441b3-2f15-5b92-8d84-230616113705",
                "ItemId": "C",
                "TrackingId": null,
                "Details": {},
                "Quantity": 1.0,
                "UnitOfMeasure": "ea",
                "BatchId": "C-001",
                "SerialId": null
            }
        ],
        "ProductTransactions": [
            {
                "TransactionId": "a8f441b3-2f15-5b92-8d84-230616113704",
                "ItemId": "A",
                "TrackingId": null,
                "Details": {},
                "Quantity": 1.0,
                "UnitOfMeasure": "ea",
                "TransactionType": 0,
                "BatchId": null,
                "SerialId": "A-001"
            }
        ]
    }
]
```

#### Events post example results

After posting the above events, the Traceability app would show the results shown in the following screenshot.

:::image type="content" source="media/events-post-api-result-example.png" alt-text="Results of the events post example, shown in the Traceability app" lightbox="media/events-post-api-result-example.png":::

## API for single query

This API is for traceability information query and retrieves genealogy, activity, and data collection information.

- **Path:** `/api/environments/{environmentId}/traces/Query`
- **Method:** `POST`

### Single query request payload

```json
{
    "tracingDirection": Backward/Forward,
    "trackingId": string,
    "company": string,
    "itemNumber": string,
    "serialNumber": string,
    "batchNumber": string,
    "shouldIncludeEvents": true/false
}
```

### Single query request field descriptions

| Field | Description |
|--|--|
| `tracingDirection` | This field control the search direction: Backward or Forward. Backward – From top finished goods to raw materials; Forward – From raw materials to top finished goods. |
| `trackingId` | This field is the key of genealogy node and is the combination of `itemNumber` and `company` and `batchNumber` and `serialNumber`. |
| `company` | The company of top finished goods. For FnO, this field maps to legal entity. |
| `itemNumber` | item number of top finished goods. |
| `serialNumber` | The serial number of top finished goods. |
| `batchNumber` | The batch number of top finished goods. |
| `ShouldIncludeEvents` | This parameter controls whether or not event details be included. Default as "false". |

### Single query request API response

```json
{
    "tracingDirection": "Backward",
    "root": {
        "trackingId": string,
        "next": [
            {
                "trackingId": string,
                "next": [],
                "events": []
            }
        ],
        "events": [
            {
                "eventId": string,
                "companyCode": string,
                "operator": string,
                "description": string,
                "activityType": string,
                "activityCode": string,
                "datetime": YYYY-MM-DDThh:mm:ss.sssz,
                "details": {
                    "<data collection name>": <data collection value>
                    },
                "consumptionTransactions": [
                    {
                        "transactionId": string,
                        "itemId": string,
                        "trackingId": string,
                        "eventId": string,
                        "quantity": decimal,
                        "unitOfMeasure": string,
                        "transactionType": string,
                        "batchId": string
                    }
                ],
                "productTransactions": [
                    {
                        "transactionId": string,
                        "itemId": string,
                        "trackingId": string,
                        "details": {},
                        "eventId": string,
                        "quantity": decimal,
                        "unitOfMeasure": string,
                        "transactionType": string,
                        "serialId": string
                    }
                ]
            }            
        ]
    }
}
```

### Single query request API response top-level field descriptions

<!--KFM: I wasn't sure how to categorize these fields. Is "top-level" correct? -->

| Field | Description |
|--|--|
| `TracingDirection` | This field advises the search direction: Backward or Forward. Backward – From top finished goods to raw materials; Forward – From raw materials to top finished goods. Only return 1 level above or below result. |

### Single query request API response root element field descriptions

| Field | Description |
|--|--|
| `trackingId` | This field is the key of genealogy node and is the combination of "itemId" and "companyCode" and "batchId" and "serialId". |

### Single query request API response events element field descriptions

| Field | Description |
|--|--|
| `eventId` | The key to each activity against unique identity (SerialId/BatchId). Duplicated value is not allowed. System generates value if there is no value input by user. |
| `companyCode` | The companyCode of top finished goods. For FnO, this field maps to legal entity. |
| `operator` | The operator who executed the activity event. You can input UserID, EmployeeID or more. |
| `description` | The text of activity event description. |
| `activityType` | This field refers to predefined activity type (*Purchase*, *Sales*, *Production*, and so on). |
| `activityCode` | This field refers to configured activity type (*GoodsReceipt*, *Add*, *Remove*, and so on). |
| `dateTime` | The date and time of activity event happened. |
| *&lt;data collection name&gt;* | These fields are used to collect customization value. |

### Single query request API response productTransaction element field descriptions

| Field | Description |
|--|--|
| `transactionId` | The key of transactions against per event. Duplicated value is not allowed. |
| `itemId` | Item number of top finished goods. |
| `trackingId` | This field is the key of genealogy node and is the combination of `itemId` and `companyCode` and `batchId` and `serialId`. |
| `serialId` | The serial number of top finished goods. |
| `batchId` | The batch number of top finished goods. |
| `quantity` | The operation quantity of top finished goods. |
| `unitOfMeasure` | The UoM of received quantity. |

### Single query request API response consumptionTransactions element field descriptions

| Field | Description |
|--|--|
| `transactionId` | The key of transactions against per event. Duplicated value is not allowed. |
| `itemId` | Item number of component. |
| `trackingId` | This field is the key of genealogy node and is the combination of `itemId` and `companyCode` and `batchId` and `serialId`. |
| `serialId` | The serial number of component. |
| `batchId` | The batch number of component. |
| `quantity` | The consumption quantity of component. |
| `unitOfMeasure` | The UoM of consumption quantity. |

### Single query request example

Produce finished goods **A** with component **B** and **C** by different event. Query the result of finished goods **A**.

#### Single query request example request payload

```json
{
    "tracingDirection": "Backward",
    "company": "USMF",
    "itemNumber": "A",
    "serialNumber": "A-001",
    "shouldIncludeEvents": "true"
}
```

#### Single query request example API response

```json
{
    "tracingDirection": "Backward",
    "root": {
        "trackingId": "A~USMF~~A-001~~",
        "next": [
            {
                "trackingId": "B~USMF~B-001~~~",
                "next": [],
                "events": [
                    {
                        "eventId": "item B consumption-a8f441b3-2f15-5b92-8d84-230616113700",
                        "companyCode": "USMF",
                        "operator": "Terry Alvarado",
                        "description": "Consumption for production A",
                        "activityType": "Production",
                        "activityCode": "Consumption",
                        "datetime": "2023-06-15T06:14:06",
                        "details": {
                            "operation Step": "OP1",
                            "resource": "RES1",
                            "reference Location": "RES-L01"
                        },
                        "consumptionTransactions": [
                            {
                                "transactionId": "a8f441b3-2f15-5b92-8d84-230616113702",
                                "itemId": "B",
                                "trackingId": "B~USMF~B-001~~~",
                                "details": {},
                                "eventId": "item B consumption-a8f441b3-2f15-5b92-8d84-230616113700",
                                "quantity": 1.0,
                                "unitOfMeasure": "ea",
                                "transactionType": "Consumption",
                                "batchId": "B-001"
                            }
                        ],
                        "productTransactions": [
                            {
                                "transactionId": "a8f441b3-2f15-5b92-8d84-230616113701",
                                "itemId": "A",
                                "trackingId": "A~USMF~~A-001~~",
                                "details": {},
                                "eventId": "item B consumption-a8f441b3-2f15-5b92-8d84-230616113700",
                                "quantity": 1.0,
                                "unitOfMeasure": "ea",
                                "transactionType": "Product",
                                "serialId": "A-001"
                            }
                        ]
                    }
                ]
            },
            {
                "trackingId": "C~USMF~C-001~~~",
                "next": [],
                "events": [
                    {
                        "eventId": "item C consumption-a8f441b3-2f15-5b92-8d84-230616113703",
                        "companyCode": "USMF",
                        "operator": "Terry Alvarado",
                        "description": "Consumption for production A",
                        "activityType": "Production",
                        "activityCode": "Consumption",
                        "datetime": "2023-06-15T07:14:06",
                        "details": {
                            "operation Step": "OP2",
                            "resource": "RES2",
                            "reference Location": "RES-L02"
                        },
                        "consumptionTransactions": [
                            {
                                "transactionId": "a8f441b3-2f15-5b92-8d84-230616113705",
                                "itemId": "C",
                                "trackingId": "C~USMF~C-001~~~",
                                "details": {},
                                "eventId": "item C consumption-a8f441b3-2f15-5b92-8d84-230616113703",
                                "quantity": 1.0,
                                "unitOfMeasure": "ea",
                                "transactionType": "Consumption",
                                "batchId": "C-001"
                            }
                        ],
                        "productTransactions": [
                            {
                                "transactionId": "a8f441b3-2f15-5b92-8d84-230616113704",
                                "itemId": "A",
                                "trackingId": "A~USMF~~A-001~~",
                                "details": {},
                                "eventId": "item C consumption-a8f441b3-2f15-5b92-8d84-230616113703",
                                "quantity": 1.0,
                                "unitOfMeasure": "ea",
                                "transactionType": "Product",
                                "serialId": "A-001"
                            }
                        ]
                    }
                ]
            }
        ],
        "events": [
            {
                "eventId": "item B consumption-a8f441b3-2f15-5b92-8d84-230616113700",
                "companyCode": "USMF",
                "operator": "Terry Alvarado",
                "description": "Consumption for production A",
                "activityType": "Production",
                "activityCode": "Consumption",
                "datetime": "2023-06-15T06:14:06",
                "details": {
                    "operation Step": "OP1",
                    "resource": "RES1",
                    "reference Location": "RES-L01"
                },
                "consumptionTransactions": [
                    {
                        "transactionId": "a8f441b3-2f15-5b92-8d84-230616113702",
                        "itemId": "B",
                        "trackingId": "B~USMF~B-001~~~",
                        "details": {},
                        "eventId": "item B consumption-a8f441b3-2f15-5b92-8d84-230616113700",
                        "quantity": 1.0,
                        "unitOfMeasure": "ea",
                        "transactionType": "Consumption",
                        "batchId": "B-001"
                    }
                ],
                "productTransactions": [
                    {
                        "transactionId": "a8f441b3-2f15-5b92-8d84-230616113701",
                        "itemId": "A",
                        "trackingId": "A~USMF~~A-001~~",
                        "details": {},
                        "eventId": "item B consumption-a8f441b3-2f15-5b92-8d84-230616113700",
                        "quantity": 1.0,
                        "unitOfMeasure": "ea",
                        "transactionType": "Product",
                        "serialId": "A-001"
                    }
                ]
            },
            {
                "eventId": "item C consumption-a8f441b3-2f15-5b92-8d84-230616113703",
                "companyCode": "USMF",
                "operator": "Terry Alvarado",
                "description": "Consumption for production A",
                "activityType": "Production",
                "activityCode": "Consumption",
                "datetime": "2023-06-15T07:14:06",
                "details": {
                    "operation Step": "OP2",
                    "resource": "RES2",
                    "reference Location": "RES-L02"
                },
                "consumptionTransactions": [
                    {
                        "transactionId": "a8f441b3-2f15-5b92-8d84-230616113705",
                        "itemId": "C",
                        "trackingId": "C~USMF~C-001~~~",
                        "details": {},
                        "eventId": "item C consumption-a8f441b3-2f15-5b92-8d84-230616113703",
                        "quantity": 1.0,
                        "unitOfMeasure": "ea",
                        "transactionType": "Consumption",
                        "batchId": "C-001"
                    }
                ],
                "productTransactions": [
                    {
                        "transactionId": "a8f441b3-2f15-5b92-8d84-230616113704",
                        "itemId": "A",
                        "trackingId": "A~USMF~~A-001~~",
                        "details": {},
                        "eventId": "item C consumption-a8f441b3-2f15-5b92-8d84-230616113703",
                        "quantity": 1.0,
                        "unitOfMeasure": "ea",
                        "transactionType": "Product",
                        "serialId": "A-001"
                    }
                ]
            }
        ]
    }
}
```



<!--KFM: Do we need to add this now?

## Remove genealogy node

&lt;To be updated before public preview release&gt;

-->