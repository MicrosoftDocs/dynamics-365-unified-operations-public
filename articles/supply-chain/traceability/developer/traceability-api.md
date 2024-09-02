---
title: Traceability API (preview)
description: Learn how to integrate the Traceability Add-in for Dynamics 365 Supply Chain Management with external systems through its API.
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

This article describes how to integrate the Traceability Add-in for Dynamics 365 Supply Chain Management with external systems through its API.

## Authentication

The platform security token is used to call the Traceability public API. Therefore, you must generate a *Microsoft Entra token* by using your Microsoft Entra application. You must then use the Microsoft Entra token to get the *access token* from the security service.

To obtain an access token, follow these steps:

1. Sign in to the [Azure portal](https://ms.portal.azure.com/).
1. Search for or navigate to the **App registrations** page.
1. Open the [app registration](traceability-install.md) you created for the Traceability app.
1. From the left navigator, select **Overview**. Copy the value shown for **Application (client) ID** to a temporary text file.
1. From the toolbar, select **Endpoints**.
1. The **Endpoints** dialog opens. Copy the value shown for **OAuth 2.0 token endpoint (v2)** to a temporary text file.
1. Fetch a Microsoft Entra token by submitting an HTTP request that has the following properties:

    - **URL** – Use the **OAuth 2.0 token endpoint (v2)** value you found earlier in this procedure.
    - **Method** – GET
    - **Body content** – Submit the body content listed in the following table as form data.

        | Key | Value |
        |--|--|
        | client\_id | {Application (client) ID in Microsoft Azure} |
        | client\_secret | {Client secret value} |
        | grant\_type | client\_credentials |
        | scope | 0cdb527f-a8d1-4bf8-9436-b352c68682b2/.default |

1. You should receive a Microsoft Entra token in response. It should resemble the following example:

    ```json
    {
        "token_type": "Bearer",
        "expires_in": 3599,
        "ext_expires_in": 3599,
        "access_token": "eyJ0eXAiOiJKV1QiLC…OUppUdgPQ"
    }
    ```

1. Use the Microsoft Entra token to generate a bearer token by submitting an HTTP request that has the following properties:

    - **URL** – `https://securityservice.operations365.dynamics.com/token`
    - **Method** – POST
    - **Body content** – Submit the following body content as JSON content:

        ```json
        {
            "grant_type": "client_credentials",
            "client_assertion_type": "aad_app",
            "client_assertion": "{Microsoft Entra token}",
            "scope": "https://traceabilityservice.operations365.dynamics.com/.default",
            "context": "{environmentId}",
            "context_type": "finops-env"
        }
        ```

        Where *{environmentId}* is the environment ID of your Supply Chain Management environment in Lifecycle Services.

1. You should receive an access token in response. You must use this token as a bearer token to call the Traceability API. Here's an example of a response:

    ```json
    {
        "access_token": "{access token}",
        "token_type": "bearer",
        "expires_in": 3600
    }
    ```

## Find the Traceability API URL

To find the URL for accessing your Traceability API, follow the instructions provided in [API endpoint](traceability-configure.md#api-endpoint).

## Available APIs

The following table lists the APIs available for Traceability.

| Path | Method | Description |
|--|--|--|
| /api/environments/{environmentId}/events/post-batch-events | Post | Create genealogy node and activity |
| /api/environments/{environmentId}/traces/Query | Post | Query by tracking ID |
| /api/environments/{environmentId}/traces/Query | Post | Unlink genealogy node and insert activity for unlink |

Where *{environmentId}* is the environment ID of your Supply Chain Management environment in Lifecycle Services.

The remaining sections provide detailed information about each API.

## Post activity events API

This API lets external systems post activity events to the Traceability service. Activity events include production component assembly and goods receipt in business activities.

- **Path** – `/api/environments/{environmentId}/events/post-batch-events`
- **Method** – `POST`

Where *{environmentId}* is the environment ID of your Supply Chain Management environment in Lifecycle Services.

### Post activity events request payload

```txt
[
    {
        "eventId": string,
        "description": string,
        "activityType": string, refer to predefined "Activity Type",
        "activityCode": string, refer to configured "Activity Code" linked to "Activity Type",
        "datetime": YYYY-MM-DDThh:mm:ss.sssz,
        "operator": string,
        "companyCode": string,
        "details": {
            "<data collection name>": <data collection value>
            },
        "consumptionTransactions": [
            {
                "transactionId": string,
                "companyCode": string,
                "itemId": string, refer to configured "item" for tracing,
                "trackingId": string,
                "serialId": string,
                "batchId": string,
                "assetId": string,
                "lotId": string,
                "quantity": decimal,
                "unitOfMeasure": string
            }
        ],
        "productTransactions": [
            {
                "transactionId": string,
                "companyCode": string,
                "itemId": string, refer to configured "item",
                "trackingId": string,
                "serialId": string,
                "batchId": string,
                "assetId": string,
                "lotId": string,
                "quantity": decimal，
                "unitOfMeasure": string
            }
        ]
    }
]
```

### Events post header field descriptions

| Field Name | Description |
|--|--|
| `eventId` | Unique identifier for the activity (`SerialId`/`BatchId`). Duplicate values aren't allowed. The system generates this value if none is specified. |
| `description` | Description of the activity event. |
| `activityType` | Refers to a predefined "Activity Type" (*Purchase*, *Sales*, *Production*, and so on). |
| `activityCode` | Refers to a configured "Activity Code" (*GoodsReceipt*, *Add*, *Remove*, and so on). |
| `dateTime` | The date and time the activity event happened. |
| `operator` | The operator who executed the activity event. The value can be a user ID, employee ID, or similar. |
| `companyCode` | For Supply Chain Management, this field maps to a legal entity. |
| *&lt;data collection name&gt;* | These fields are used to collect custom values. |

### Events post productTransactions element field descriptions

| Field Name | Description |
|--|--|
| `transactionId` | Unique identifier for the transaction. Duplicate values aren't allowed. |
| `companyCode` | The legal entity of product element. |
| `itemId` | Item number of the top finished good. |
| `trackingId` | Key value for the genealogy node. It's a combination of the `itemId`, `companyCode`, `batchId`, and `serialId`. |
| `serialId` | The serial number of the top finished good. |
| `batchId` | The batch number of the top finished good. |
| `assetId` | The asset number of parent node. This field can be used as equipment number. |
| `lotId` | The lot number of parent node. This field can be used as container number. |
| `quantity` | The operation quantity of the top finished good. |
| `unitOfMeasure` | The unit of measure of the received quantity. |

### Events post consumptionTransactions element field descriptions

| Field Name | Description |
|--|--|
| `transactionId` | Unique identifier for the transaction. Duplicate values aren't allowed. |
| `companyCode` | The legal entity of component element. |
| `itemId` | Item number of component. |
| `trackingId` | Key value for the genealogy node. It's a combination of the `itemId`, `companyCode`, `batchId`, and `serialId`. |
| `serialId` | The serial number of the component. |
| `batchId` | The batch number of the component. |
| `assetId` | The asset number of child node. This field can be used as equipment number. |
| `lotId` | The lot number of child node. This field can be used as container number. |
| `quantity` | The consumption quantity of the component. |
| `unitOfMeasure` | The unit of measure of the consumption quantity. |

### Events post API response

On success, status code 204 is returned.

### Events post example

Produce finished good **A** with component **B** and **C** by different events.

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

If you were to post the example events shown previously, the Traceability Add-in would display the results shown in the following screenshot.

:::image type="content" source="../media/events-post-api-result-example.png" alt-text="Results of the events post example, shown in the Traceability Add-in" lightbox="../media/events-post-api-result-example.png":::

## Single query API

This API accepts queries for traceability information and returns genealogy, activity, and data collection information.

- **Path** – `/api/environments/{environmentId}/traces/Query`
- **Method** – `POST`

Where *{environmentId}* is the environment ID of your Supply Chain Management environment in Lifecycle Services.

### Single query request payload

```txt
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
| `tracingDirection` | Controls the search direction: *Backward* or *Forward*. *Backward* means from top finished good to raw materials; *Forward* means from raw materials to top finished good. |
| `trackingId` | Key value for the genealogy node. It's a combination of the `itemNumber`,`company`, `batchNumber`, and `serialNumber`. |
| `company` | The company of the top finished good. For Supply Chain Management, this field maps to the legal entity. |
| `itemNumber` | The item number of the top finished good. |
| `serialNumber` | The serial number of the top finished good. |
| `batchNumber` | The batch number of the top finished good. |
| `ShouldIncludeEvents` | Controls whether event details should be included. Default is *false*. |

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

### Single query response header field descriptions

| Field | Description |
|--|--|
| `TracingDirection` | Controls the search direction: *Backward* or *Forward*. *Backward* means from top finished good to raw materials; *Forward* means from raw materials to top finished good. Only returns one level above or below the result. |

### Single query response root element field descriptions

| Field | Description |
|--|--|
| `trackingId` | Key value for the genealogy node. It's a combination of the `itemId`,`companyCode`, `batchId`, and `serialId`. |

### Single query response events element field descriptions

| Field | Description |
|--|--|
| `eventId` | Unique identifier for the event (`SerialId`/`BatchId`). Duplicate values aren't allowed. The system generates this value if no value is provided. |
| `companyCode` | The company code of the top finished good. For Supply Chain Management, this field maps to the legal entity. |
| `operator` | The operator who executed the activity event. The value can be a user ID, employee ID, or similar. |
| `description` | Activity event description. |
| `activityType` | Refers to a predefined activity type (*Purchase*, *Sales*, *Production*, and so on). |
| `activityCode` | Refers to a configured activity type (*GoodsReceipt*, *Add*, *Remove*, and so on). |
| `dateTime` | Date and time the activity event occurred. |
| *&lt;data collection name&gt;* | These fields are used to collect customization values. |

### Single query response productTransaction element field descriptions

| Field | Description |
|--|--|
| `transactionId` | Unique identifier for the transaction. Duplicate values aren't allowed. |
| `itemId` | Item number of the top finished good. |
| `trackingId` | Key value for the genealogy node. It's a combination of `itemId`, `companyCode`, `batchId`, and `serialId`. |
| `serialId` | Serial number of the top finished good. |
| `batchId` | Batch number of the top finished good. |
| `quantity` | Operation quantity of the top finished good. |
| `unitOfMeasure` | Unit of measure of the received quantity. |

### Single query response consumptionTransactions element field descriptions

| Field | Description |
|--|--|
| `transactionId` | Unique identifier for the transaction. Duplicate values aren't allowed. |
| `itemId` | Item number of the component. |
| `trackingId` | Key value for the genealogy node. It's a combination of `itemId`, `companyCode`, `batchId`, and `serialId`. |
| `serialId` | Serial number of the component. |
| `batchId` | Batch number of the component. |
| `quantity` | The consumption quantity of the component. |
| `unitOfMeasure` | Unit of measure of the consumption quantity. |

### Single query request example

Produce finished good **A** with component **B** and **C** by different events. Query the result of finished good **A**.

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

## API for Unlink genealogy node and insert activity for unlink

This API is for genealogy node unlink which can be used for production component disassembly, equipment uninstallation, container unload in business activities.

- **Path** – `/api/environments/{environmentId}/events/unlink-components`
- **Method** – `POST`

Where *{environmentId}* is the environment ID of your Supply Chain Management environment in Lifecycle Services.

### Post unlink events request payload

```txt
{
  "requestId": string,
  "Eventlist":
  [
    {
        "eventId": string,
        "description": string,
        "activityType": string, refer to predefined "Activity Type",
        "activityCode": string, refer to configured "Activity Code" linked to "Activity Type",
        "datetime": YYYY-MM-DDThh:mm:ss.sssz,
        "operator": string,
        "companyCode": string,
        "details": {
            "<data collection name>": <data collection value>
            },
        "consumptionTransactions": [
            {
                "transactionId": string,
                "companyCode": string,
                "itemId": string, refer to configured "item" for tracing,
                "trackingId": string,
                "serialId": string,
                "batchId": string,
                "assetId": string,
                "lotId": string,
                "quantity": decimal,
                "unitOfMeasure": string
            }
        ],
        "productTransactions": [
            {
                "transactionId": string,
                "companyCode": string,
                "itemId": string, refer to configured "item",
                "trackingId": string,
                "serialId": string,
                "batchId": string,
                "assetId": string,
                "lotId": string,
                "quantity": decimal，
                "unitOfMeasure": string
            }
        ]
    }
  ]
}
```

### Unlink events post header field descriptions

| Field Name | Description |
|--|--|
| `RequestId` | Random UUID. |
| `eventId` | Unique identifier for the activity (`SerialId`/`BatchId`). Duplicate values aren't allowed. The system generates this value if none is specified. |
| `description` | Description of the activity event. |
| `activityType` | Refers to a predefined "Activity Type" (*Purchase*, *Sales*, *Production*, and so on). |
| `activityCode` | Refers to a configured "Activity Code" (*GoodsReceipt*, *Add*, *Remove*, and so on). |
| `dateTime` | The date and time the activity event happened. |
| `operator` | The operator who executed the activity event. The value can be a user ID, employee ID, or similar. |
| `companyCode` | For Supply Chain Management, this field maps to a legal entity. |
| *&lt;data collection name&gt;* | These fields are used to collect custom values. |

### Unlink events post productTransactions element field descriptions

| Field Name | Description |
|--|--|
| `transactionId` | Unique identifier for the transaction. Duplicate values aren't allowed. This field can be null. |
| `companyCode` | The legal entity of parent node. |
| `itemId` | Item number of parent node. |
| `trackingId` | Key value for the genealogy node. It's a combination of the `itemId`, `companyCode`, `batchId`, and `serialId`. |
| `serialId` | The serial number of parent node. |
| `batchId` | The batch number of parent node. |
| `assetId` | The asset number of parent node. This field can be used as equipment number. |
| `lotId` | The lot number of parent node. This field can be used as container number. |
| `quantity` | The operation quantity of parent node. |
| `unitOfMeasure` | The unit of measure of parent node. |

### Unlink events post consumptionTransactions element field descriptions

| Field Name | Description |
|--|--|
| `transactionId` | Unique identifier for the transaction. Duplicate values aren't allowed. This field can be null. |
| `companyCode` | The legal entity of child node to be removed. |
| `itemId` | Item number of child node. |
| `trackingId` | Key value for the genealogy node. It's a combination of the `itemId`, `companyCode`, `batchId`, and `serialId`. |
| `serialId` | The serial number of child node to be removed. |
| `batchId` | The batch number of child node to be removed. |
| `assetId` | The asset number of child node to be removed. This field can be used as equipment number. |
| `lotId` | The lot number of child node to be removed. This field can be used as container number. |
| `quantity` | The consumption quantity of child node to be removed. |
| `unitOfMeasure` | The unit of measure of the removed quantity. |

### Unlink events post API response

On success, status code 204 is returned.

### Unlink events post example

Creat new activity code "FullRemove" for activity type "Production" for all company code in menu "Activity" first. Post below example to remove component C from product A from previous example.


#### Unlink events post example request payload 1

```json
{
	"RequestId": "a8fbd235-f56d-4d10-b4de-9b125eb814ea",
	"EventList": 
  [
    {
        "EventId": "remove c -a8f441b3-2f15-5b92-8d84-20240821112003",
        "CompanyCode": "USMF",
        "Operator": "Terry Alvarado",
        "Description": "Component C Full Remove",
        "ActivityType": "Production",
        "ActivityCode": "FullRemove",
        "Datetime": "2023-08-15T06:14:06.653Z",
        "Details": {
            "Operation Step": "OP2",
            "Resource": "RES2",
            "Reference Location": "RES-L02"
        },
        "ConsumptionTransactions": [
            {
                "TransactionId": null,
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
                "TransactionId": null,
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
}
```

#### Unlink events post example results

If you were to post the example events shown previously, the Traceability Add-in would display the results shown in the following screenshot.
Component C is unlinked from product A. A new activity of “Production-Full Remove” is inserted for product A with removed component information included.

:::image type="content" source="../media/unlink-post-api-result-example.png" alt-text="Results of the unlink events post example, shown in the Traceability Add-in" lightbox="../media/unlink-post-api-result-example.png":::
