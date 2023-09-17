---
title: Inventory Visibility public APIs
description: This article describes the public APIs that are provided by Inventory Visibility.
author: yufeihuang
ms.date: 11/04/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.22
---

# Inventory Visibility public APIs

[!include [banner](../includes/banner.md)]

This article describes the public APIs that are provided by Inventory Visibility.

The public REST API of the Inventory Visibility Add-in presents several specific endpoints for integration. It supports four main interaction types:

- Posting on-hand inventory changes to the add-in from an external system
- Setting or overriding on-hand inventory quantities in the add-in from an external system
- Posting reservation events to the add-in from an external system
- Querying current on-hand quantities from an external system

The following table lists the APIs that are currently available:

| Path | Method | Description |
|---|---|---|
| /api/environment/{environmentId}/onhand | Post | [Create one on-hand change event](#create-one-onhand-change-event)|
| /api/environment/{environmentId}/onhand/bulk | Post | [Create multiple change events](#create-multiple-onhand-change-events) |
| /api/environment/{environmentId}/setonhand/{inventorySystem}/bulk | Post | [Set/override on-hand quantities](#set-onhand-quantities) |
| /api/environment/{environmentId}/onhand/reserve | Post | [Create one soft reservation event](#create-one-reservation-event) |
| /api/environment/{environmentId}/onhand/reserve/bulk | Post | [Create multiple soft reservation events](#create-multiple-reservation-events) |
| /api/environment/{environmentId}/onhand/unreserve | Post | [Reverse one soft reservation event](#reverse-one-reservation-event) |
| /api/environment/{environmentId}/onhand/unreserve/bulk | Post | [Reverse multiple soft reservation events](#reverse-multiple-reservation-events) |
| /api/environment/{environmentId}/onhand/changeschedule | Post | [Create one scheduled on-hand change](inventory-visibility-available-to-promise.md) |
| /api/environment/{environmentId}/onhand/changeschedule/bulk | Post | [Create multiple on-hand changes with dates](inventory-visibility-available-to-promise.md) |
| /api/environment/{environmentId}/onhand/indexquery | Post | [Query by using the post method](#query-with-post-method) (recommended) |
| /api/environment/{environmentId}/onhand | Get | [Query by using the get method](#query-with-get-method) |
| /api/environment/{environmentId}/onhand/exactquery | Post | [Exact query by using the post method](#exact-query-with-post-method) |
| /api/environment/{environmentId}/allocation<wbr>/allocate | Post | [Create one allocate event](inventory-visibility-allocation.md#using-allocation-api) |
| /api/environment/{environmentId}/allocation<wbr>/unallocate | Post | [Create one unallocate event](inventory-visibility-allocation.md#using-allocation-api) |
| /api/environment/{environmentId}/allocation<wbr>/reallocate | Post | [Create one reallocate event](inventory-visibility-allocation.md#using-allocation-api) |
| /api/environment/{environmentId}/allocation<wbr>/consume | Post | [Create one consume event](inventory-visibility-allocation.md#using-allocation-api) |
| /api/environment/{environmentId}/allocation<wbr>/query | Post | [Query allocation result](inventory-visibility-allocation.md#using-allocation-api) |

> [!NOTE]
> The {environmentId} part of the path is the environment ID in Microsoft Dynamics Lifecycle Services.
> 
> The bulk API can return a maximum of 512 records for each request.

Microsoft has provided an out-of-box *Postman* request collection. You can import this collection into your *Postman* software by using the following shared link: <https://www.getpostman.com/collections/95a57891aff1c5f2a7c2>.

## <a name = "endpoint-lcs"></a>Find the endpoint according to your Lifecycle Services environment

The microservice of Inventory Visibility is deployed on Microsoft Azure Service Fabric, in multiple geographies and multiple regions. There isn't currently a central endpoint that can automatically redirect your request to the corresponding geography and region. Therefore, you must compose the pieces of information into a URL by using the following pattern:

`https://inventoryservice.<RegionShortName>-il<IsLandNumber>.gateway.prod.island.powerapps.com`

The region short name can be found in the Lifecycle Services environment. For a list of regions (and region short names) that are currently supported, see [Install and set up Inventory Visibility](inventory-visibility-setup.md).

The island number is where your Lifecycle Services environment is deployed on Service Fabric. There's currently no way to get this information from the user side.

Microsoft has built a user interface (UI) in Power Apps so that you can get the complete endpoint of the microservice. For more information, see [Find the service endpoint](inventory-visibility-configuration.md#get-service-endpoint).

## <a name="inventory-visibility-authentication"></a>Authentication

The platform security token is used to call the Inventory Visibility public API. Therefore, you must generate an *Azure Active Directory (Azure AD) token* by using your Azure AD application. You must then use the Azure AD token to get the *access token* from the security service.

Microsoft provides an out-of-box *Postman* get token collection. You can import this collection into your *Postman* software by using the following shared link: <https://www.getpostman.com/collections/496645018f96b3f0455e>.

To get a security service token, follow these steps.

1. Sign in to the Azure portal, and use it to find the `clientId` and `clientSecret` values for your Dynamics 365 Supply Chain Management app.
1. Fetch an Azure AD token (`aadToken`) by submitting an HTTP request that has the following properties:

    - **URL:** `https://login.microsoftonline.com/${aadTenantId}/oauth2/v2.0/token`
    - **Method:** `GET`
    - **Body content (form data):**

        | Key           | Value                                            |
        | ------------- | -------------------------------------------------|
        | client_id     | ${aadAppId}                                      |
        | client_secret | ${aadAppSecret}                                  |
        | grant_type    | client_credentials                               |
        | scope         | 0cdb527f-a8d1-4bf8-9436-b352c68682b2/.default    |

    You should receive an Azure AD token (`aadToken`) in response. It should resemble the following example.

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
        "client_assertion": "{Your_AADToken}",
        "scope": "https://inventoryservice.operations365.dynamics.com/.default",
        "context": "{$LCS_environment_id}",
        "context_type": "finops-env"
    }
    ```

    Note the following points:

    - The `client_assertion` value must be the Azure AD token (`aadToken`) that you received in the previous step.
    - The `context` value must be the Lifecycle Services environment ID where you want to deploy the add-in.
    - Set all the other values as shown in the example.

1. Fetch an access token (`access_token`) by submitting an HTTP request that has the following properties:

    - **URL:** `https://securityservice.operations365.dynamics.com/token`
    - **Method:** `POST`
    - **HTTP header:** Include the API version. (The key is `Api-Version`, and the value is `1.0`.)
    - **Body content:** Include the JSON request that you created in the previous step.

    You should receive an access token (`access_token`) in response. You must use this token as a bearer token to call the Inventory Visibility API. Here's an example.

    ```json
    {
        "access_token": "{Returned_Token}",
        "token_type": "bearer",
        "expires_in": 3600
    }
    ```

> [!NOTE]
> The `https://securityservice.operations365.dynamics.com/token` URL is a general URL for the security service. When you call the URL, the first response is an http redirect response with the status code `307` in the response headers, and an entry with the key "Location" that contains the target URL for the security service. The URL is in this format: `https://gw.{$geo}-il101.gateway.prod.island.powerapps.com/securityservice/token`. For example, if your environment locates in US geo, the URL could be "https://gw.us-il101.gateway.prod.island.powerapps.com/securityservice/token". If the 307 response status code is not acceptable for you, you can manually construct the actual URL according to your FinOps environment location. The simplest way is to open `https://gw.as-il101.gateway.prod.island.powerapps.com/securityservice/token` with your browser, and then copy the address in address bar.

> [!IMPORTANT]
> When you use the *Postman* request collection to call Inventory Visibility public APIs, you must add a bearer token for each request. To find your bearer token, select the **Authorization** tab under the request URL, select the **Bearer Token** type, and copy the access token that was fetched in the last step. In later sections of this article, `$access_token` will be used to represent the token that was fetched in the last step.

## <a name="create-onhand-change-event"></a>Create on-hand change events

There are two APIs for creating on-hand change events:

- Create one record: `/api/environment/{environmentId}/onhand`
- Create multiple records: `/api/environment/{environmentId}/onhand/bulk`

The following table summarizes the meaning of each field in the JSON body.

| Field ID | Description |
|---|---|
| `id` | A unique ID for the specific change event. If a resubmission occurs due to a service failure, this ID is used to ensure the same event won't be counted twice in the system. |
| `organizationId` | The identifier of the organization that is linked to the event. This value is mapped to an organization or data area ID in Supply Chain Management. |
| `productId` | The identifier of the product. |
| `quantities` | The quantity that the on-hand quantity must be changed by. For example, if 10 new books are added to a shelf, this value will be `quantities:{ shelf:{ received: 10 }}`. If three books are removed from the shelf or sold, this value will be `quantities:{ shelf:{ sold: 3 }}`. |
| `dimensionDataSource` | The data source of the dimensions that are used in the posting change event and query. If you specify the data source, you can use the custom dimensions from the specified data source. Inventory Visibility can use the dimension configuration to map the custom dimensions to the general default dimensions. If no `dimensionDataSource` value is specified, you can use only the general [base dimensions](inventory-visibility-configuration.md#data-source-configuration-dimension) in your queries. |
| `dimensions` | A dynamic key-value pair. The values are mapped to some of the dimensions in Supply Chain Management. However, you can also add custom dimensions (for example, *Source*) to indicate whether the event is coming from Supply Chain Management or an external system. |

> [!NOTE]
> The `siteId` and `locationId` parameters construct the [partition configuration](inventory-visibility-configuration.md#partition-configuration). Therefore, you must specify them in dimensions when you create on-hand change events, set or override on-hand quantities, or create reservation events.

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

To use the *Reserve* API, you must turn on the reservation feature and complete the reservation configuration. For more information (including a dataflow and sample scenario), see [Reservation configuration (optional)](inventory-visibility-configuration.md#reservation-configuration).

### <a name="create-one-reservation-event"></a>Create one reservation event

A reservation can be made against different data source settings. To configure this type of reservation, first specify the data source in the `dimensionDataSource` parameter. Then, in the `dimensions` parameter, specify dimensions according to the dimension settings in the target data source.

When you call the reservation API, you can control the reservation validation by specifying the Boolean `ifCheckAvailForReserv` parameter in the request body. A value of `True` means that the validation is required, whereas a value of `False` means that the validation isn't required. The default value is `True`.

If you want to reverse a reservation or unreserve specified inventory quantities, set the quantity to a negative value, and set the `ifCheckAvailForReserv` parameter to `False` to skip the validation. There's also a dedicated unreserve API to do the same. The difference is only in the way the two APIs are called. It's easier to reverse a specific reservation event by using `reservationId` with the *unreserve* API. For more information, see [Unreserve one reservation event](#reverse-reservation-events) section.

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
    "productId": "iv_postman_product",
    "quantity": 1,
    "quantityDataSource": "iv",
    "modifier": "softReservOrdered",
    "ifCheckAvailForReserv": true,
    "dimensions": {
        "siteId": "iv_postman_site",
        "locationId": "iv_postman_location",
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

When a reservation is created, a `reservationId` will be included in the response body. You must provide the same `reservationId` to cancel the reservation, and include the same `organizationId` and `dimensions` used for the reservation API call. Finally, specify an `OffsetQty` value that represents the number of items to be freed from the previous reservation. A reservation can either be fully or partially reversed depending on the specified `OffsetQty`. For example, if *100* units of items were reserved, you can specify `OffsetQty: 10` to unreserve *10* of the initial reserved amount.

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
    "reservationId": "RESERVATION_ID",
    "dimensions": {
        "siteid":"iv_postman_site",
        "locationid":"iv_postman_location",
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
            reservationId: string,
            dimensions: {
                [key:string]: string,
            },
            OffsetQty: number
        }
        ...
    ]
```

## Query on-hand

Use the *Query on-hand* API to fetch current on-hand inventory data for your products. You can use this API whenever you must know the stock, such as when you want to review product stock levels on your e-commerce website, or when you want to check product availability across regions or in nearby stores and warehouses. The API currently supports querying up to 5,000 individual items by `productID` value. Multiple `siteID` and `locationID` values can also be specified in each query. The maximum limit is defined by the following equation:

*NumOf(SiteID) \* NumOf(LocationID) <= 100*.

### <a name="query-with-post-method"></a>Query by using the post method

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

In the body part of this request, `dimensionDataSource` is still an optional parameter. If it isn't set, `filters` will be treated as *base dimensions*. There are four required fields for `filters`: `organizationId`, `productId`, `siteId`, and `locationId`.

- `organizationId` should contain only one value, but it's still an array.
- `productId` could contain one or more values. If it's an empty array, all products will be returned.
- `siteId` and `locationId` are used for partitioning in Inventory Visibility. You can specify more than one `siteId` and `locationId` value in a *Query on-hand* request. In the current release, you must specify both `siteId` and `locationId` values.

We suggest that you use the `groupByValues` parameter to follow your configuration for indexing. For more information, see [Product index hierarchy configuration](./inventory-visibility-configuration.md#index-configuration).

The `returnNegative` parameter controls whether the results contain negative entries.

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
/api/environment/{environmentId}/onhand?organizationId=SCM_IV&productId=iv_postman_product&siteId=iv_postman_site&locationId=iv_postman_location&colorId=red&groupBy=colorId,sizeId&returnNegative=true
```

## <a name="exact-query-with-post-method"></a>On-hand exact query

On-hand exact queries resemble regular on-hand queries, but they let you specify a mapping hierarchy between a site and a location. For example, you have the following two sites:

- Site 1, which is mapped to location A
- Site 2, which is mapped to location B

For a regular on-hand query, if you specify `"siteId": ["1","2"]` and `"locationId": ["A","B"]`, Inventory Visibility will automatically query the result for the following sites and locations:

- Site 1, location A
- Site 1, location B
- Site 2, location A
- Site 2, location B

As you see, the regular on-hand query doesn't recognize that location A exists only in site 1, and location B exists only in site 2. Therefore, it makes redundant queries. To accommodate this hierarchical mapping, you can use an on-hand exact query and specify the location mappings in the query body. In this case, you'll query and receive results for only site 1, location A and site 2, location B.

### <a name="exact-query-with-post-method"></a>Exact query by using the post method

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
- In the `dimensions` array, `siteId` and `locationId` are required but could appear with other elements in any order.
- `values` could contain one or more distinct tuples of values corresponding to `dimensions`.

`dimensions` in `filters` will be automatically added to `groupByValues`.

The `returnNegative` parameter controls whether the results contain negative entries.

The following example shows sample body content.

```json
{
    "dimensionDataSource": "pos",
    "filters": {
        "organizationId": ["SCM_IV"],
        "productId": ["iv_postman_product"],
        "dimensions": ["siteId", "locationId", "colorId"],
        "values" : [
            ["iv_postman_site", "iv_postman_location", "red"],
            ["iv_postman_site", "iv_postman_location", "blue"],
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
            ["iv_postman_site_1", "iv_postman_location_1"],
            ["iv_postman_site_2", "iv_postman_location_2"],
        ]
    },
    "groupByValues": ["colorId", "sizeId"],
    "returnNegative": true
}
```

## Available to promise

You can set up Inventory Visibility to let you schedule future on-hand changes and calculate ATP quantities. ATP is the quantity of an item that is available and can be promised to a customer in the next period. Use of the ATP calculation can greatly increase your order fulfillment capability. For information about how to enable this feature, and how to interact with Inventory Visibility through its API after the feature is enabled, see [Inventory Visibility on-hand change schedules and available to promise](inventory-visibility-available-to-promise.md#api-urls).

## Allocation

Allocation related APIs are located in [Inventory Visibility allocation](inventory-visibility-allocation.md#using-allocation-api).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
