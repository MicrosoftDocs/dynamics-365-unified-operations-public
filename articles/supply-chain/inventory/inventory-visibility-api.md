---
title: Inventory Visibility public APIs
description: Learn about the public APIs that are provided by Inventory Visibility, including an outline and step-by-step process for authentication.
author: yufei-huang
ms.author: yufeihuang
ms.topic: how-to
ms.date: 06/03/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: 
---

# Inventory Visibility public APIs

[!include [banner](../includes/banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

This article describes the public APIs that are provided by Inventory Visibility.

The public REST API of the Inventory Visibility Add-in presents several specific endpoints for integration. It supports four main interaction types:

- Posting on-hand inventory changes to the add-in from an external system
- Setting or overriding on-hand inventory quantities in the add-in from an external system
- Posting reservation events to the add-in from an external system
- Querying current on-hand quantities from an external system

The following table lists the APIs that are currently available:

| Path | Method | Description |
|---|---|---|
| `/api/environment/{environmentId}/onhand` | Post | [Create one on-hand change event](#create-one-onhand-change-event)|
| `/api/environment/{environmentId}/onhand/bulk` | Post | [Create multiple change events](#create-multiple-onhand-change-events) |
| `/api/environment/{environmentId}/setonhand/{inventorySystem}/bulk` | Post | [Set/override on-hand quantities](#set-onhand-quantities) |
| `/api/environment/{environmentId}/onhand/reserve` | Post | [Create one soft reservation event](#create-one-reservation-event) |
| `/api/environment/{environmentId}/onhand/reserve/bulk` | Post | [Create multiple soft reservation events](#create-multiple-reservation-events) |
| `/api/environment/{environmentId}/onhand/unreserve` | Post | [Reverse one soft reservation event](#reverse-one-reservation-event) |
| `/api/environment/{environmentId}/onhand/unreserve/bulk` | Post | [Reverse multiple soft reservation events](#reverse-multiple-reservation-events) |
| `/api/environment/{environmentId}/onhand/reserve/resyncjob` |Post | [Clean up reservation data](#clean-up-reservation-data) |
| `/api/environment/{environmentId}/getJobProgress` | Get | [Get job execution progress](#get-job-execution-progress) |
| `/api/environment/{environmentId}/onhand/changeschedule` | Post | [Create one scheduled on-hand change](inventory-visibility-available-to-promise.md) |
| `/api/environment/{environmentId}/onhand/changeschedule/bulk` | Post | [Create multiple on-hand changes with dates](inventory-visibility-available-to-promise.md) |
| `/api/environment/{environmentId}/onhand/indexquery` | Post | [Query by using the post method](#query-with-post-method) (recommended) |
| `/api/environment/{environmentId}/onhand` | Get | [Query by using the get method](#query-with-get-method) |
| `/api/environment/{environmentId}/onhand/exactquery` | Post | [Exact query by using the post method](#exact-query-with-post-method) |
| `/api/environment/{environmentId}/allocation/allocate` | Post | [Create one allocate event](inventory-visibility-allocation.md#using-allocation-api) |
| `/api/environment/{environmentId}/allocation/unallocate` | Post | [Create one unallocate event](inventory-visibility-allocation.md#using-allocation-api) |
| `/api/environment/{environmentId}/allocation/reallocate` | Post | [Create one reallocate event](inventory-visibility-allocation.md#using-allocation-api) |
| `/api/environment/{environmentId}/allocation/consume` | Post | [Create one consume event](inventory-visibility-allocation.md#using-allocation-api) |
| `/api/environment/{environmentId}/allocation/query` | Post | [Query allocation result](inventory-visibility-allocation.md#using-allocation-api) |
| `/api/environment/{environmentId}/onhand/productsearch/indexquery` | Post | [Post index query with product search](#query_with_product_search) |
| `/api/environment/{environmentId}/onhand/productsearch/exactquery` | Post | [Post exact query with product search](#exact-query-with-product-search) |
| `/api/environment/{environmentId}/transaction/adjustment/bulk` | Post | [Sync external inventory changes through Inventory Visibility](inventory-visibility-sync-changes.md) |

> [!NOTE]
> The {environmentId} part of the path is the environment ID of Microsoft Dynamics 365 Supply Chain Management.
>
> The bulk API can return a maximum of 512 records for each request.

## <a name="inventory-visibility-authentication"></a>Authentication

The platform security token is used to call the Inventory Visibility public API. Therefore, you must generate a *Microsoft Entra token* by using your Microsoft Entra application. You must then use the Microsoft Entra token to get the *access token* from the security service.

To get a security service token, follow these steps.

1. Sign in to the Azure portal, and use it to find the `clientId` and `clientSecret` values for your Dynamics 365 Supply Chain Management app.
1. Fetch a Microsoft Entra token (`aadToken`) by submitting an HTTP request that has the following properties:

    - **URL:** `https://login.microsoftonline.com/${aadTenantId}/oauth2/v2.0/token`
    - **Method:** `GET`
    - **Body content (form data):**

        | Key           | Value                                            |
        | ------------- | -------------------------------------------------|
        | client_id     | ${aadAppId}                                      |
        | client_secret | ${aadAppSecret}                                  |
        | grant_type    | client_credentials                               |
        | scope         | 0cdb527f-a8d1-4bf8-9436-b352c68682b2/.default    |

    You should receive a Microsoft Entra token (`aadToken`) in response. It should resemble the following example.

    ```json
    {
        "token_type": "Bearer",
        "expires_in": "3599",
        "ext_expires_in": "3599",
        "access_token": "eyJ0eX...8WQ"
    }
    ```

1. Formulate a JavaScript Object Notation (JSON) request that resembles the following example.

    ```json
    {
        "grant_type": "client_credentials",
        "client_assertion_type": "aad_app",
        "client_assertion": "{Your_Microsoft EntraToken}",
        "scope": "https://inventoryservice.operations365.dynamics.com/.default",
        "context": "{$fno_environment_id}",
        "context_type": "finops-env"
    }
    ```

    Note the following points:

    - The `client_assertion` value must be the Microsoft Entra token (`aadToken`) that you received in the previous step.
    - The `context` value must be the Supply Chain Management environment ID where you want to deploy the add-in.
    - Set all the other values as shown in the example.

1. Fetch an access token (`access_token`) by submitting an HTTP request that has the following properties:

    - **URL:** `https://securityservice.operations365.dynamics.com/token`
    - **Method:** `POST`
    - **HTTP header:**

        | Key | Value |
        |--|--|
        | Api-Version | 1.0 |
        | Content-Type | application/json |

    - **Body content:** Include the JSON request that you created in the previous step.

    You should receive an access token (`access_token`) in response. You must use this token as a bearer token to call the Inventory Visibility API. Here's an example.

    ```json
    {
        "access_token": "{Returned_Token}",
        "token_type": "bearer",
        "expires_in": 3600
    }
    ```

## <a name="create-onhand-change-event"></a>Create on-hand change events

There are two APIs for creating on-hand change events:

- Create one record: `/api/environment/{environmentId}/onhand`
- Create multiple records: `/api/environment/{environmentId}/onhand/bulk`

The following table summarizes the meaning of each field in the JSON body.

| Field ID | Description |
|---|---|
| `id` | A unique ID for the specific change event. If a resubmission occurs due to a service failure, this ID is used to ensure the same event won't be counted twice in the system. |
| `organizationId` | The identifier of the organization that's linked to the event. This value is mapped to an organization or data area ID in Supply Chain Management. |
| `productId` | The identifier of the product. |
| `quantities` | The quantity that the on-hand quantity must be changed by. For example, if 10 new books are added to a shelf, this value will be `quantities:{ shelf:{ received: 10 }}`. If three books are removed from the shelf or sold, this value will be `quantities:{ shelf:{ sold: 3 }}`. |
| `dimensionDataSource` | The data source of the dimensions that are used in the posting change event and query. If you specify the data source, you can use the custom dimensions from the specified data source. Inventory Visibility can use the dimension configuration to map the custom dimensions to the general default dimensions. If no `dimensionDataSource` value is specified, you can use only the general [base dimensions](inventory-visibility-configuration.md#data-source-configuration-dimension) in your queries. |
| `dimensions` | A dynamic key-value pair. The values are mapped to some of the dimensions in Supply Chain Management. However, you can also add custom dimensions (for example, *Source*) to indicate whether the event is coming from Supply Chain Management or an external system. |

> [!NOTE]
> If your [data partition rule](inventory-visibility-power-platform.md#data-partition) is set to *By product ID*, `siteId` and `locationId` are optional dimensions. Otherwise, they're required dimensions. This rule also applies to the allocation, soft reserve, and change schedule APIs.

The following subsections provide examples that show how to use these APIs.

### <a name="create-one-onhand-change-event"></a>Create one on-hand change event

This API creates a single on-hand change event.

```txt
Path:
    /api/environment/{environmentId}/onhand
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    {
        id: string,
        organizationId: string,
        productId: string,
        dimensionDataSource: string, # Optional
        dimensions: {
            [key:string]: string,
        },
        quantities: {
            [dataSourceName:string]: {
                [key:string]: number,
            },
        },
    }
```

The following example shows sample body content. In this example, the company has a point-of-sale (POS) system that processes in-store transactions and therefore inventory changes. The customer has returned a red T-shirt to your store. To reflect the change, you post a single change event for the *T-shirt* product. This event will increase the quantity of the *T-shirt* product by 1.

```json
{
    "id": "Test201",
    "organizationId": "usmf",
    "productId": "T-shirt",
    "dimensionDataSource": "pos",
    "dimensions": {
        "siteId": "1",
        "locationId": "11",
        "posMachineId": "0001",
        "colorId": "red"
    },
    "quantities": {
        "pos": {
            "inbound": 1
        }
    }
}
```

The following example shows sample body content without `dimensionDataSource`. In this case, `dimensions` will be the [base dimensions](inventory-visibility-configuration.md#data-source-configuration-dimension). If `dimensionDataSource` is set, `dimensions` can be either the data source dimensions or the base dimensions.

```json
{
    "id": "Test202",
    "organizationId": "usmf",
    "productId": "T-shirt",
    "dimensions": {
        "siteId": "1",
        "locationId": "11",
        "colorId": "red"
    },
    "quantities": {
        "pos": {
            "inbound": 1
        }
    }
}
```

### <a name="create-multiple-onhand-change-events"></a>Create multiple change events

This API can create change events, just as the [single-event API](#create-one-onhand-change-event) can. The only difference is that this API can create multiple records at the same time. Therefore, the `Path` and `Body` values differ. For this API, `Body` provides an array of records. The maximum number of records is 512. Therefore, the on-hand change bulk API can support up to 512 change events at a time.

For example, a retail store POS machine processed the following two transactions:

- One return order of one red T-shirt
- One sales transaction of three black T-shirts

In this case, you can include both inventory updates in one API call.

```txt
Path:
    /api/environment/{environmentId}/onhand/bulk
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    [
        {
            id: string,
            organizationId: string,
            productId: string,
            dimensionDataSource: string, # Optional
            dimensions: {
                [key:string]: string,
            },
            quantities: {
                [dataSourceName:string]: {
                    [key:string]: number,
                },
            },
        },
        ...
    ]
```

The following example shows sample body content.

```json
[
    {
        "id": "Test203",
        "organizationId": "usmf",
        "productId": "T-shirt",
        "dimensionDataSource": "pos",
        "dimensions": {
            "SiteId": "Site1",
            "LocationId": "11",
            "posMachineId": "0001"
            "colorId": "red"
        },
        "quantities": {
            "pos": { "inbound": 1 }
        }
    },
    {
        "id": "Test204",
        "organizationId": "usmf",
        "productId": "T-shirt",
        "dimensions": {
            "siteId": "1",
            "locationId": "11",
            "colorId": "black"
        },
        "quantities": {
            "pos": { "outbound": 3 }
        }
    }
]
```

## <a name="set-onhand-quantities"></a>Set/override on-hand quantities

The *Set on-hand* API overrides the current data for the specified product. This functionality is typically used to do inventory counting updates. For example, during its daily inventory counting, a store might find that the actual on-hand inventory for a red T-shirt is 100. Therefore, the POS inbound quantity must be updated to 100, regardless of what the previous quantity was. You can use this API to override the existing value.

```txt
Path:
    /api/environment/{environmentId}/setonhand/{inventorySystem}/bulk
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    [
        {
            id: string,
            organizationId: string,
            productId: string,
            dimensionDataSource: string, # Optional
            dimensions: {
                [key:string]: string,
            },
            quantities: {
                [dataSourceName:string]: {
                    [key:string]: number,
                },
            },
            modifiedDateTimeUTC: datetime,
        },
        ...
    ]
```

The following example shows sample body content. The behavior of this API differs from the behavior of the APIs that are described in the [Create on-hand change events](#create-onhand-change-event) section earlier in this article. In this sample, the quantity of the *T-shirt* product will be set to 1.

```json
[
    {
        "id": "Test204",
        "organizationId": "usmf",
        "productId": "T-shirt",
        "dimensionDataSource": "pos",
        "dimensions": {
            "SiteId": "1",
            "LocationId": "11",
            "posMachineId": "0001"
            "colorId": "red"
        },
        "quantities": {
            "pos": {
                "inbound": 100
            }
        }
    }
]
```

## Create reservation events

To use the *Reserve* API, you must turn on the reservation feature and complete the reservation configuration. For more information (including a dataflow and sample scenario), see [Inventory Visibility reservations](inventory-visibility-reservations.md).

### <a name="create-one-reservation-event"></a>Create one reservation event

A reservation can be made against different data source settings. To configure this type of reservation, first specify the data source in the `dimensionDataSource` parameter. Then, in the `dimensions` parameter, specify dimensions according to the dimension settings in the target data source.

When you call the reservation API, you can control the reservation validation by specifying the Boolean `ifCheckAvailForReserv` parameter in the request body. A value of `True` means that the validation is required, whereas a value of `False` means that the validation isn't required. The default value is `True`.

If you want to reverse a reservation or unreserve specified inventory quantities, set the quantity to a negative value, and set the `ifCheckAvailForReserv` parameter to `False` to skip the validation. There's also a dedicated unreserve API to do the same. The difference is only in the way the two APIs are called. It's easier to reverse a specific reservation event by using `reservationId` with the *unreserve* API. Learn more in [Unreserve one reservation event](#reverse-reservation-events) section.

```txt
Path:
    /api/environment/{environmentId}/onhand/reserve
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    {
        id: string,
        organizationId: string,
        productId: string,
        dimensionDataSource: string,
        dimensions: {
            [key:string]: string,
        },
        quantityDataSource: string, # optional
        quantities: {
            [dataSourceName:string]: {
                [key:string]: number,
            },
        },
        modifier: string,
        quantity: number,
        ifCheckAvailForReserv: boolean,
    }
```

The following example shows sample body content.

```json
{
    "id": "reserve-0",
    "organizationId": "SCM_IV",
    "productId": "iv_contoso_product",
    "quantity": 1,
    "quantityDataSource": "iv",
    "modifier": "softReservOrdered",
    "ifCheckAvailForReserv": true,
    "dimensions": {
        "siteId": "iv_contoso_site",
        "locationId": "iv_contoso_location",
        "colorId": "red",
        "sizeId": "small"
    }
}
```

The following example shows a successful response.

```json
{
    "reservationId": "RESERVATION_ID",
    "id": "ohre~id-822-232959-524",
    "processingStatus": "success",
    "message": "",
    "statusCode": 200
}
```

### <a name="create-multiple-reservation-events"></a>Create multiple reservation events

This API is a bulk version of the [single-event API](#create-reservation-events).

```txt
Path:
    /api/environment/{environmentId}/onhand/reserve/bulk
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    [
        {
            id: string,
            organizationId: string,
            productId: string,
            dimensionDataSource: string,
            dimensions: {
                [key:string]: string,
            },
            quantityDataSource: string, # optional
            quantities: {
                [dataSourceName:string]: {
                    [key:string]: number,
                },
            },
            modifier: string,
            quantity: number,
            ifCheckAvailForReserv: boolean,
        },
        ...
    ]
```

## Reverse reservation events

The *Unreserve* API serves as the reverse operation for [*Reservation*](#create-reservation-events) events. It provides a way to reverse a reservation event specified by `reservationId` or to decrease the reservation quantity.

### <a name="reverse-one-reservation-event"></a>Reverse one reservation event

When a reservation is created, a `reservationId` will be included in the response body. You must provide the same `reservationId` to cancel the reservation, and include the same `organizationId`, `productId`, and `dimensions` used for the reservation API call. Finally, specify an `OffsetQty` value that represents the number of items to be freed from the previous reservation. A reservation can either be fully or partially reversed depending on the specified `OffsetQty`. For example, if *100* units of items were reserved, you can specify `OffsetQty: 10` to unreserve *10* of the initial reserved amount.

```txt
Path:
    /api/environment/{environmentId}/onhand/unreserve
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    {
        id: string,
        organizationId: string,
        productId: string,
        reservationId: string,
        dimensions: {
            [key:string]: string,
        },
        OffsetQty: number
    }
```

The following code shows an example of body content.

```json
{
    "id": "unreserve-0",
    "organizationId": "SCM_IV",
    "productId": "iv_contoso_product",
    "reservationId": "RESERVATION_ID",
    "dimensions": {
        "siteid":"iv_contoso_site",
        "locationid":"iv_contoso_location",
        "ColorId": "red",
        "SizeId": "small"
    },
    "OffsetQty": 1
}
```

The following code shows an example of a successful response body.

```json
{
    "reservationId": "RESERVATION_ID",
    "totalInvalidOffsetQtyByReservId": 0,
    "id": "ohoe~id-823-11744-883",
    "processingStatus": "success",
    "message": "",
    "statusCode": 200
}
```

> [!NOTE]
> In the response body, when `OffsetQty` is less than or equal to the reservation quantity, `processingStatus` will be "*success*" and `totalInvalidOffsetQtyByReservId` will be *0*.
>
> If `OffsetQty` is greater than the reserved amount, `processingStatus` will be "*partialSuccess*" and `totalInvalidOffsetQtyByReservId` will be the difference between `OffsetQty` and the reserved amount.
>
>For example, if the reservation has a quantity of *10*, and `OffsetQty` has a value of *12*, `totalInvalidOffsetQtyByReservId` would be *2*.

### <a name="reverse-multiple-reservation-events"></a>Reverse multiple reservation events

This API is a bulk version of the [single-event API](#reverse-one-reservation-event).

```txt
Path:
    /api/environment/{environmentId}/onhand/unreserve/bulk
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    [      
        {
            id: string,
            organizationId: string,
            productId: string,
            reservationId: string,
            dimensions: {
                [key:string]: string,
            },
            OffsetQty: number
        }
        ...
    ]
```

## Clean up reservation data

The *clean up reservation data* API is used to clean up historical reservation data. The body should be a list of data sources. If the list is empty, all data sources will be cleaned up.

```txt
Path:
    /api/environment/{environmentId}/onhand/reserve/resyncjob
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    [      
        "iv",
        "pos"
    ]
```

If the cleanup job is successfully created, a job ID will be returned in the response, which can be used to [get job execution progress](#get-job-execution-progress).

## Get job execution progress

Use the *get job execution progress* API to obtain the execution progress of a job. A job ID is required to identify the job.

```txt
Path:
    /api/environment/{environmentId}/getJobProgress
Method:
    Get
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Query(Url Parameters):
    jobId
```

Here's a sample get URL.

```txt
/api/environment/{environmentId}/getJobProgress?jobId=SomeJob:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

## Query on-hand

Use the *Query on-hand* API to fetch current on-hand inventory data for your products. You can use this API whenever you must know the stock, such as when you want to review product stock levels on your e-commerce website, or when you want to check product availability across regions or in nearby stores and warehouses. The API currently supports querying up to 5,000 individual items by `productID` value. Multiple `siteID` and `locationID` values can also be specified in each query. When your [data partition rule](inventory-visibility-power-platform.md#data-partition) is set to *By location*, the maximum limit is defined by the following equation:

*NumOf(SiteID) &times; NumOf(LocationID) <= 10,000*.

### <a name="query-with-post-method"></a>Query by using the post method

The query by post API is available in two versions. The following table outlines the differences.

| API version 1.0 | API version 2.0 |
|---|---|
| Can only query one organization ID. | Can query multiple organization IDs. |
| Can query up to 10,000 combinations of sites and warehouses. | Can query more than 10,000 combinations of organization IDs, sites, and warehouses. Can return results in multiple pages. |

The following subsections show how to use each API version.

#### Query by post API version 1.0

```txt
Path:
    /api/environment/{environmentId}/onhand/indexquery
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    {
        dimensionDataSource: string, # Optional
        filters: {
            organizationId: string[],
            productId: string[],
            siteId: string[],
            locationId: string[],
            [dimensionKey:string]: string[],
        },
        groupByValues: string[],
        returnNegative: boolean,
    }
```

In the body part of this request, `dimensionDataSource` is an optional parameter. If it isn't set, `filters` will be treated as *base dimensions*.

The `returnNegative` parameter controls whether the results contain negative entries.

### Query data stored by location

This section applies when your [data partition rule](inventory-visibility-power-platform.md#data-partition) is set to *By location*.

- `organizationId` should be an array containing exactly one value.
- `productId` can contain one or more values. If it's an empty array, the system will return all products for the specified sites and locations. In this case, `siteId` and `locationId` shouldn't be empty.
- `siteId` and `locationId` are used for partitioning. You can specify more than one `siteId` and `locationId` value in a *Query on-hand* request. If both arrays are empty, the system will return all sites and locations for the specified products. In this case, `productId` shouldn't be empty.

We recommend to use the `groupByValues` parameter in a way that's consistent with your index configuration. Learn more in [On-hand index configuration](inventory-visibility-power-platform.md#index).

### Query data stored by product ID

This section applies when your [data partition rule](inventory-visibility-power-platform.md#data-partition) is set to *By product ID*. In this case, two `filters` fields are required: `organizationId`, `productId`.

- `organizationId` should be an array containing exactly one value.
- `productId` should be an array with at least one value.

Unlike when storing data by location, if you don't specify values for `siteId` and `locationId`, inventory information for each product ID will be aggregated across all sites and/or locations.

> [!NOTE]
> If you've enabled the on-hand change schedule and available-to-promise (ATP) features, your query can also include the `QueryATP` Boolean parameter, which controls whether the query results include ATP information. For more information and examples, see [Inventory Visibility on-hand change schedules and available to promise](inventory-visibility-available-to-promise.md).

The following example shows sample body content. It shows that you can query the on-hand inventory from multiple locations (warehouses).

```json
{
    "dimensionDataSource": "pos",
    "filters": {
        "organizationId": ["usmf"],
        "productId": ["T-shirt"],
        "siteId": ["1"],
        "locationId": ["11","12","13"],
        "colorId": ["red"]
    },
    "groupByValues": ["colorId", "sizeId"],
    "returnNegative": true
}
```

The following example shows how to query all products in a specific site and location.

```json
{
    "filters": {
        "organizationId": ["usmf"],
        "productId": [],
        "siteId": ["1"],
        "locationId": ["11"],
    },
    "groupByValues": ["colorId", "sizeId"],
    "returnNegative": true
}
```

#### Query by post API version 2.0

```txt
Path:
    /api/environment/{environmentId}/onhand/indexquery?pageNumber={pageNumber}&pageSize={pageSize}
Method:
    Post
Headers:
    Api-Version="2.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    # Same as version 1.0
```

The request format for API version 2.0 is similar to that of version 1.0, but also supports two optional parameters: `pageNumber` and `pageSize`, which allow the system to split a single large result into several smaller documents. The results are sorted by warehouse (`locationId`), and the parameters are used as follows to split results into pages:

- `pageSize` establishes the number of warehouses (`locationId` values) that are returned in each page.
- `pageNumber` establishes the page number that's returned.

A request of this format returns on-hand inventory data starting from warehouse number *({pageNumber} &minus; 1) &times; {pageSize}* and includes data for the next *{pageSize}* warehouses.

API version 2.0 responds with a document that uses the following structure:

```txt
{
    Value: { # Response same as Api-Version=1.0 }
    nextLink: onhand/indexquery?pageNumber={pageNumber+1}&pageSize={pageSize}
}
```

When the request reaches the last warehouse (`locationId`), the `nextLink` value is an empty string.

API version 2.0 also lets you specify more than one organization ID in your request. To do so, include a comma-separated list of organization IDs in the `organizationId` filter of your request document. For example, `"organizationId": ["org1", "org2", "org3"]`.

### <a name="query-with-get-method"></a>Query by using the get method

```txt
Path:
    /api/environment/{environmentId}/onhand
Method:
    Get
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Query(Url Parameters):
    groupBy
    returnNegative
    [Filters]
```

Here's a sample get URL. This get request is exactly the same as the post sample that was provided earlier.

```txt
/api/environment/{environmentId}/onhand?organizationId=SCM_IV&productId=iv_contoso_product&siteId=iv_contoso_site&locationId=iv_contoso_location&colorId=red&groupBy=colorId,sizeId&returnNegative=true
```

The system doesn't support querying inventory over multiple organization IDs with the GET method.

## On-hand exact query

On-hand exact queries resemble regular on-hand queries, but they let you specify a mapping hierarchy between a site and a location. For example, you have the following two sites:

- Site 1, which is mapped to location A
- Site 2, which is mapped to location B

For a regular on-hand query, if you specify `"siteId": ["1","2"]` and `"locationId": ["A","B"]`, Inventory Visibility will automatically query the result for the following sites and locations:

- Site 1, location A
- Site 1, location B
- Site 2, location A
- Site 2, location B

As you see, the regular on-hand query doesn't recognize that location A exists only in site 1, and location B exists only in site 2. Therefore, it makes redundant queries. To accommodate this hierarchical mapping, you can use an on-hand exact query and specify the location mappings in the query body. In this case, you'll query and receive results for only site 1, location A and site 2, location B.

### <a name="exact-query-with-post-method"></a>On-hand exact query query using the post method

The on-hand exact query by post API is available in two versions. The following table outlines the differences.

| API version 1.0 | API version 2.0 |
|---|---|
| Can only query one organization ID. | Can query multiple organization IDs. |

#### On-hand exact query by post API version 1.0

```txt
Path:
    /api/environment/{environmentId}/onhand/exactquery
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    {
        dimensionDataSource: string, # Optional
        filters: {
            organizationId: string[],
            productId: string[],
            dimensions: string[],
            values: string[][],
        },
        groupByValues: string[],
        returnNegative: boolean,
    }
```

In the body part of this request, `dimensionDataSource` is an optional parameter. If it isn't set, `dimensions` in `filters` will be treated as *base dimensions*. There are four required fields for `filters`: `organizationId`, `productId`, `dimensions`, and `values`.

- `organizationId` should contain only one value, but it's still an array.
- `productId` could contain one or more values. If it's an empty array, all products will be returned.
- In the `dimensions` array, `siteId` and `locationId` are required if and only if your [data partition rule](inventory-visibility-power-platform.md#data-partition) is set to *By location*. In this case, they could appear with other elements in any order.
- `values` could contain one or more distinct tuples of values corresponding to `dimensions`.

`dimensions` in `filters` will be automatically added to `groupByValues`.

The `returnNegative` parameter controls whether the results contain negative entries.

The following example shows sample body content.

```json
{
    "dimensionDataSource": "pos",
    "filters": {
        "organizationId": ["SCM_IV"],
        "productId": ["iv_contoso_product"],
        "dimensions": ["siteId", "locationId", "colorId"],
        "values" : [
            ["iv_contoso_site", "iv_contoso_location", "red"],
            ["iv_contoso_site", "iv_contoso_location", "blue"],
        ]
    },
    "groupByValues": ["colorId", "sizeId"],
    "returnNegative": true
}
```

The following example shows how to query all products in multiple sites and locations.

```json
{
    "filters": {
        "organizationId": ["SCM_IV"],
        "productId": [],
        "dimensions": ["siteId", "locationId"],
        "values" : [
            ["iv_contoso_site_1", "iv_contoso_location_1"],
            ["iv_contoso_site_2", "iv_contoso_location_2"],
        ]
    },
    "groupByValues": ["colorId", "sizeId"],
    "returnNegative": true
}
```

#### On-hand exact query by post API version 2.0

```txt
Path:
    /api/environment/{environmentId}/onhand/exactquery
Method:
    Post
Headers:
    Api-Version="2.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    {
        dimensionDataSource: string, # Optional
        filters: {
            productId: string[],
            keys: string[],
            values: string[][],
        },
        groupByValues: string[],
        returnNegative: boolean,
    }
```

API version 2.0 differs from version 1.0 in the following ways:

- The `filters` section now has a `keys` field instead of a `dimensions` field. The `keys` field works like the `dimensions` field in version 1.0, but can now also include `organizationId`. You can specify the keys in any order.
- The `filters` section no longer supports the `organizationId` field. Instead, you can include `organizationId` among the dimensions in the `keys` field (for example, `keys: ["organizationId", "siteId", "locationId"]`) and define organization ID values at the matching position in the `values` field (for example, `values: ["SCM_IV", "iv_contoso_site_1", "iv_contoso_location_1"]`).

Other fields are identical to API version 1.0.

## <a name="product-search-query"></a>Query with product search

The following on-hand query APIs are enhanced to support product search:

- [Query by using the post method](#query-with-post-method)
- [Exact query by using the post method](#exact-query-with-post-method)

> [!NOTE]
> When you post an Inventory Visibility query that uses product search, use the `productSearch` request parameter (with a `ProductAttributeQuery` object inside) to find or filter by product ID. The newer APIs no longer support the older `productid` request parameter in the request body.

### Prerequisites

Before you can start to use the product search APIs, your system must meet the following requirements:

- You must be running Dynamics 365 Supply Chain Management 10.0.36 or later.
- Inventory Visibility version 1.2.2.54 or later must be installed and set up as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- The Inventory Visibility search service must be installed and set up as described in [Set up product search for Inventory Visibility](inventory-visibility-product-search.md).

### Product search contract

The product search contract defines the rules for communicating with the product search APIs. It provides a standardized way to describe the capabilities and behavior of the product search capabilities. Therefore, users can more easily understand, interact with, and build applications that consume the Inventory Visibility APIs.

The following example shows a sample contract.

```json
{
    "productFilter": {
        "logicalOperator": "And",
        "conditions": [
            {
                "conditionOperator": "Contains",
                "productName": [
                    "Deluxe"
                ],
            },
        ],
        "subFilters": [
            {
                "conditions": [
                    {
                        "conditionOperator": "IsExactly",
                        "productType": [
                            "Item"
                        ]
                    }
                ]
            }
        ]
    },
    "attributeFilter": {
        "logicalOperator": "Or",
        "conditions": [
            {
                "attributeName": "Weight Limit",
                "attributeTypeName":"PoundDomain",
                "attributeArea": " ProductAttribute",
                "attributeValues": [
                    "370"
                ],
                "conditionOperator": "GreaterEqual"
            }
        ],
        "subFilters": [
            {
                "conditions": [
                    {
                        "attributeName": "Weight Limit",
                        "attributeTypeName":"PoundDomain",
                        "attributeArea": " ProductAttribute",
                        "attributeValues": [
                            "330"
                        ],
                        "conditionOperator": "LessEqual"
                    }
                ]
            }
        ]
    },
}
```

The following table describes the fields that are used in the contract.

| Field ID | Description |
|---|---|
| `logicalOperator` | The possible values are `And` and `Or`. Use this field to connect multiple conditions or conditions and sub-filters. Note that `subFilters` is actually a `productFilter` or `attributeFilter` object. Therefore, you can have `subFilters` inside `subFilters`. |
| `conditionOperator` | The possible values are `IsExactly`, `IsNot`, `Contains`, `DoesNotContain`, `BeginsWith`, `IsOneOf`, `GreaterEqual`, `LessEqual`, and `Between`. |
| `ProductFilter`  | Use this field to filter products by product-related information. For example, you can change `productName` in the contract to `Company`, `itemNumber`, `productSearchName`, `productType`, `productName`, `productDescription`, `inventoryUnitSymbol`, `salesUnitSymbol`, or `purchaseUnitSymbol` to fit your business needs. |
| `AttributeFilter`   | Use this field to filter products by attribute-related information. |
| `attributeArea` | The possible values are `ProductAttribute`, `DimensionAttribute`, and `BatchAttribute`. |

### <a name="query_with_product_search"></a>Query with product search

```txt
Path:
    /api/environment/{environmentId}/onhand/productsearch/indexquery
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    {
        productSearch: {ProductAttributeQuery contract object inherited from Product Search}
            dimensionDataSource: string, # Optional
            filters: {
                organizationId: string[],
                siteId: string[],
                locationId: string[],
                [dimensionKey:string]: string[],
            },
            groupByValues: string[],
            returnNegative: boolean,
    }
```

The following example shows sample body content.

```JSON
{
    "productSearch": {
        "productFilter": {
            "conditions": [
                {
                    "conditionOperator": "contains",
                    "productName": [
                        "speaker cable"
                    ],
                },
            ],
        },
    },
    "returnNegative": true, 
    "filters": 
    {
        "organizationId": ["usmf"], 
        "siteId": ["1"], 
        "locationId": ["13"],
    },
    "groupByValues": ["colorid"],
}
```

The following example shows a successful response.

```JSON
[
    {
        "productId": "M0030",
        "dimensions": {
            "ColorId": "White",
            "siteid": "1",
            "locationid": "13"
        },
        "quantities": {
            "fno": {
                "arrived": 0,
                "availordered": 20,
                "onorder": 5,
                "ordered": 20,
                "physicalinvent": 0,
                "reservordered": 0,
                "reservphysical": 0,
                "orderedsum": 20,
                "softreserved": 0
            },
            "iv": {
                "ordered": 0,
                "softreserved": 0,
                "softreservphysical": 0,
                "softreservordered": 0,
                "total ordered": 20,
                "total on order": 5,
                "availabletoreserve": 20,
                "totalavailable": 20,
                "totalordered": 20,
                "totalonorder": 5
            },
            "pos": {
                "inbound": 0,
                "outbound": 0
            },
            "@iv": {
                "@allocated": 0
            }
        }
    },
    {
        "productId": "M0030",
        "dimensions": {
            "ColorId": "Black",
            "siteid": "1",
            "locationid": "13"
        },
        "quantities": {
            "fno": {
                "arrived": 0,
                "availordered": 3,
                "ordered": 3,
                "physicalinvent": 0,
                "reservordered": 0,
                "reservphysical": 0,
                "orderedsum": 3,
                "softreserved": 0
            },
            "iv": {
                "ordered": 0,
                "softreserved": 0,
                "softreservphysical": 0,
                "softreservordered": 0,
                "total ordered": 3,
                "availabletoreserve": 3,
                "totalavailable": 3,
                "totalordered": 3
            },
            "pos": {
                "inbound": 0,
                "outbound": 0
            },
            "@iv": {
                "@allocated": 0
            }
        }
    }
]
```

### <a name="exact-query-with-product-search"></a>Exact query with product search

```txt
Path:
    /api/environment/{environmentId}/onhand/productsearch/exactquery
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    {
        productSearch: {ProductAttributeQuery contract object inherited from Product Search}
            dimensionDataSource: string, # Optional
            filters: {
                organizationId: string[],
                dimensions: string[],
                values: string[][],
            },
            groupByValues: string[],
            returnNegative: boolean,
    }
```

The following example shows sample body content.

```JSON
{
    "productSearch": {
        "productFilter": {
            "conditions": [
                {
                    "conditionOperator": "contains",
                    "productName": [
                        "speaker cable"
                    ],
                },
            ],
        },
    },
    "filters": {
        "organizationId": ["usmf"],
        "dimensions": ["siteId", "locationId", "colorid"],
        "values" : [
            ["1", "13", "Black"],
        ]
    },
    "groupByValues": [],
    "returnNegative": true
}
```

The following example shows a successful response.

```JSON
[
    {
        "productId": "M0030",
        "dimensions": {
            "ColorId": "Black",
            "siteid": "1",
            "locationid": "13"
        },
        "quantities": {
            "fno": {
                "arrived": 0,
                "availordered": 3,
                "ordered": 3,
                "physicalinvent": 0,
                "reservordered": 0,
                "reservphysical": 0,
                "orderedsum": 3,
                "softreserved": 0
            },
            "iv": {
                "ordered": 0,
                "softreserved": 0,
                "softreservphysical": 0,
                "softreservordered": 0,
                "total ordered": 3,
                "availabletoreserve": 3,
                "totalavailable": 3,
                "totalordered": 3
            },
            "pos": {
                "inbound": 0,
                "outbound": 0
            },
            "@iv": {
                "@allocated": 0
            }
        }
    }
]
```

## Available to promise

You can set up Inventory Visibility to let you schedule future on-hand changes and calculate ATP quantities. ATP is the quantity of an item that's available and can be promised to a customer in the next period. Use of the ATP calculation can greatly increase your order fulfillment capability. For information about how to enable this feature, and how to interact with Inventory Visibility through its API after the feature is enabled, see [Inventory Visibility on-hand change schedules and available to promise](inventory-visibility-available-to-promise.md#api-urls).

## Allocation

Allocation related APIs are located in [Inventory Visibility allocation](inventory-visibility-allocation.md#using-allocation-api).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
