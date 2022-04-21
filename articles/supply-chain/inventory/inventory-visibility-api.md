---
title: Inventory Visibility public APIs
description: This topic describes the public APIs that are provided by Inventory Visibility.
author: yufeihuang
ms.date: 12/09/2021
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


This topic describes the public APIs that are provided by Inventory Visibility.

The public REST API of the Inventory Visibility Add-in presents several specific endpoints for integration. It supports four main interaction types:

- Posting on-hand inventory changes to the add-in from an external system
- Setting or overriding on-hand inventory quantities in the add-in from an external system
- Posting reservation events to the add-in from an external system
- Querying current on-hand quantities from an external system

The following table lists the APIs that are currently available:

| Path | Method | Description |
|---|---|---|
| /api/environment/{environmentId}/onhand | Post | [Create one on-hand change event](#create-one-onhand-change-event) |
| /api/environment/{environmentId}/onhand/bulk | Post | [Create multiple change events](#create-multiple-onhand-change-events) |
| /api/environment/{environmentId}/setonhand/{inventorySystem}/bulk | Post | [Set/override on-hand quantities](#set-onhand-quantities) |
| /api/environment/{environmentId}/onhand/reserve | Post | [Create one reservation event](#create-one-reservation-event) |
| /api/environment/{environmentId}/onhand/reserve/bulk | Post | [Create multiple reservation events](#create-multiple-reservation-events) |
| /api/environment/{environmentId}/on-hand/changeschedule | Post | [Create one scheduled on-hand change](inventory-visibility-available-to-promise.md) |
| /api/environment/{environmentId}/on-hand/changeschedule/bulk | Post | [Create multiple scheduled on-hand changes](inventory-visibility-available-to-promise.md) |
| /api/environment/{environmentId}/onhand/indexquery | Post | [Query by using the post method](#query-with-post-method) |
| /api/environment/{environmentId}/onhand | Get | [Query by using the get method](#query-with-get-method) |

> [!NOTE]
> The {environmentId} part of the path is the environment ID in Microsoft Dynamics Lifecycle Services (LCS).
> 
> The bulk API can return a maximum of 512 records for each request.

Microsoft has provided an out-of-box *Postman* request collection. You can import this collection into your *Postman* software by using the following shared link: <https://www.getpostman.com/collections/90bd57f36a789e1f8d4c>.

## Find the endpoint according to your Lifecycle Services environment

The microservice of Inventory Visibility is deployed on Microsoft Azure Service Fabric, in multiple geographies and multiple regions. There isn't currently a central endpoint that can automatically redirect your request to the corresponding geography and region. Therefore, you must compose the pieces of information into a URL by using the following pattern:

`https://inventoryservice.<RegionShortName>-il<IsLandNumber>.gateway.prod.island.powerapps.com`

The region short name can be found in the Microsoft Dynamics Lifecycle Services (LCS) environment. The following table lists the regions that are currently available.

| Azure region        | Region short name |
| ------------------- | ----------------- |
| Australia east      | eau               |
| Australia southeast | seau              |
| Canada central      | cca               |
| Canada east         | eca               |
| North Europe        | neu               |
| West Europe         | weu               |
| East US             | eus               |
| West US             | wus               |
| South UK            | suk               |
| West UK             | wuk               |
| East Japan          | ejp               |
| West Japan          | wjp               |
| South Brazil        | sbr               |
| South Central US    | scus              |

The island number is where your LCS environment is deployed on Service Fabric. There is currently no way to get this information from the user side.

Microsoft has built a user interface (UI) in Power Apps so that you can get the complete endpoint of the microservice. For more information, see [Find the service endpoint](inventory-visibility-configuration.md#get-service-endpoint).

## <a name="inventory-visibility-authentication"></a>Authentication

The platform security token is used to call the Inventory Visibility public API. Therefore, you must generate an _Azure Active Directory (Azure AD) token_ by using your Azure AD application. You must then use the Azure AD token to get the _access token_ from the security service.

Microsoft provides an out-of-box *Postman* get token collection. You can import this collection into your *Postman* software by using the following shared link: <https://www.getpostman.com/collections/496645018f96b3f0455e>.

To get a security service token, follow these steps.

1. Sign in to the Azure portal, and use it to find the `clientId` and `clientSecret` values for your Dynamics 365 Supply Chain Management app.
1. Fetch an Azure AD token (`aadToken`) by submitting an HTTP request that has the following properties:

   - **URL:** `https://login.microsoftonline.com/${aadTenantId}/oauth2/token`
   - **Method:** `GET`
   - **Body content (form data):**

     | Key           | Value                                |
     | ------------- | ------------------------------------ |
     | client_id     | ${aadAppId}                          |
     | client_secret | ${aadAppSecret}                      |
     | grant_type    | client_credentials                   |
     | resource      | 0cdb527f-a8d1-4bf8-9436-b352c68682b2 |

   You should receive an Azure AD token (`aadToken`) in response. It should resemble the following example.

   ```json
   {
       "token_type": "Bearer",
       "expires_in": "3599",
       "ext_expires_in": "3599",
       "expires_on": "1610466645",
       "not_before": "1610462745",
       "resource": "0cdb527f-a8d1-4bf8-9436-b352c68682b2",
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
       "context": "5dbf6cc8-255e-4de2-8a25-2101cd5649b4",
       "context_type": "finops-env"
   }
   ```

   Note the following points:

   - The `client_assertion` value must be the Azure AD token (`aadToken`) that you received in the previous step.
   - The `context` value must be the LCS environment ID where you want to deploy the add-in.
   - Set all the other values as shown in the example.

1. Fetch an access token (`access_token`) by submitting an HTTP request that has the following properties:

   - **URL:** `https://securityservice.operations365.dynamics.com/token`
   - **Method:** `POST`
   - **HTTP header:** Include the API version. (The key is `Api-Version`, and the value is `1.0`.)
   - **Body content:** Include the JSON request that you created in the previous step.

   You should receive an access token (`access_token`) in response. You must use this token as a bearer token to call the Inventory Visibility API. Here is an example.

   ```json
   {
       "access_token": "{Returned_Token}",
       "token_type": "bearer",
       "expires_in": 3600
   }
   ```

> [!IMPORTANT]
> When you use the *Postman* request collection to call Inventory Visibility public APIs, you must add a bearer token for each request. To find your bearer token, select the **Authorization** tab under the request URL, select the **Bearer Token** type, and copy the access token that was fetched in the last step. In later sections of this topic, `$access_token` will be used to represent the token that was fetched in the last step.

## <a name="create-onhand-change-event"></a>Create on-hand change events

There are two APIs for creating on-hand change events:

- Create one record: `/api/environment/{environmentId}/onhand`
- Create multiple records: `/api/environment/{environmentId}/onhand/bulk`

The following table summarizes the meaning of each field in the JSON body.

| Field ID | Description |
|---|---|
| `id` | A unique ID for the specific change event. This ID is used to ensure that, if communication with the service fails during posting, the same event won't be counted twice in the system if it's resubmitted. |
| `organizationId` | The identifier of the organization that is linked to the event. This value is mapped to an organization or data area ID in Supply Chain Management. |
| `productId` | The identifier of the product. |
| `quantities` | The quantity that the on-hand quantity must be changed by. For example, if 10 new books are added to a shelf, this value will be `quantities:{ shelf:{ received: 10 }}`. If three books are removed from the shelf or sold, this value will be `quantities:{ shelf:{ sold: 3 }}`. |
| `dimensionDataSource` | The data source of the dimensions that are used in the posting change event and query. If you specify the data source, you can use the custom dimensions from the specified data source. Inventory Visibility can use the dimension configuration to map the custom dimensions to the general default dimensions. If no `dimensionDataSource` value is specified, you can use only the general [base dimensions](inventory-visibility-configuration.md#data-source-configuration-dimension) in your queries. |
| `dimensions` | A dynamic key-value pair. The values are mapped to some of the dimensions in Supply Chain Management. However, you can also add custom dimensions (for example, _Source_) to indicate whether the event is coming from Supply Chain Management or an external system. |

> [!NOTE]
> The `SiteId` and `LocationId` parameters construct the [partition configuration](inventory-visibility-configuration.md#partition-configuration). Therefore, you must specify them in dimensions when you create on-hand change events, set or override on-hand quantities, or create reservation events.

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

The following example shows sample body content. In this sample, you post a change event for the *T-shirt* product. This event is from the point of sale (POS) system, and the customer has returned a red T-shirt back to your store. This event will increase the quantity of the *T-shirt* product by 1.

```json
{
    "id": "123456",
    "organizationId": "usmf",
    "productId": "T-shirt",
    "dimensionDataSource": "pos",
    "dimensions": {
        "SiteId": "1",
        "LocationId": "11",
        "PosMachineId": "0001",
        "ColorId": "Red"
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
    "id": "123456",
    "organizationId": "usmf",
    "productId": "T-shirt",
    "dimensions": {
        "SiteId": "1",
        "LocationId": "11",
        "ColorId": "Red"
    },
    "quantities": {
        "pos": {
            "inbound": 1
        }
    }
}
```

### <a name="create-multiple-onhand-change-events"></a>Create multiple change events

This API can create multiple records at the same time. The only differences between this API and the [single-event API](#create-one-onhand-change-event) are the `Path` and `Body` values. For this API, `Body` provides an array of records. The maximum number of records is 512, which means that the on-hand change bulk API  can support up to 512 change events at a time.

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
        "id": "123456",
        "organizationId": "usmf",
        "productId": "T-shirt",
        "dimensionDataSource": "pos",
        "dimensions": {
            "PosSiteId": "1",
            "PosLocationId": "11",
            "PosMachineId": "0001"
        },
        "quantities": {
            "pos": { "inbound": 1 }
        }
    },
    {
        "id": "654321",
        "organizationId": "usmf",
        "productId": "Pants",
        "dimensions": {
            "SiteId": "1",
            "LocationId": "11",
            "ColorId": "black"
        },
        "quantities": {
            "pos": { "outbound": 3 }
        }
    }
]
```

## <a name="set-onhand-quantities"></a>Set/override on-hand quantities

The _Set on-hand_ API overrides the current data for the specified product.

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

The following example shows sample body content. The behavior of this API differs from the behavior of the APIs that are described in the [Create on-hand change events](#create-onhand-change-event) section earlier in this topic. In this sample, the quantity of the *T-shirt* product will be set to 1.

```json
[
    {
        "id": "123456",
        "organizationId": "usmf",
        "productId": "T-shirt",
        "dimensionDataSource": "pos",
        "dimensions": {
             "PosSiteId": "1",
            "PosLocationId": "11",
            "PosMachineId": "0001"
        },
        "quantities": {
            "pos": {
                "inbound": 1
            }
        }
    }
]
```

## Create reservation events

To use the *Reserve* API, you must open the reservation feature and complete the reservation configuration. For more information, see [Reservation configuration (optional)](inventory-visibility-configuration.md#reservation-configuration).

### <a name="create-one-reservation-event"></a>Create one reservation event

A reservation can be made against different data source settings. To configure this type of reservation, first specify the data source in the `dimensionDataSource` parameter. Then, in the `dimensions` parameter, specify dimensions according to the dimension settings in the target data source.

When you call the reservation API, you can control the reservation validation by specifying the Boolean `ifCheckAvailForReserv` parameter in the request body. A value of `True` means that the validation is required, whereas a value of `False` means that the validation isn't required. The default value is `True`.

If you want to cancel a reservation or unreserve specified inventory quantities, set the quantity to a negative value, and set the `ifCheckAvailForReserv` parameter to `False` to skip the validation.

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
    "organizationId": "usmf",
    "productId": "T-shirt",
    "quantity": 1,
    "quantityDataSource": "iv",
    "modifier": "softreservordered",
    "ifCheckAvailForReserv": true,
    "dimensions": {
        "SiteId": "1",
        "LocationId": "11",
        "ColorId": "Red",
        "SizeId": "Small"
    }
}
```

### <a name="create-multiple-reservation-events"></a>Create multiple reservation events

This API is a bulk version of the [single-event API](#create-one-reservation-event).

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

## Query on-hand

Use the _Query on-hand_ API to fetch current on-hand inventory data for your products. The API currently supports querying up to 100 individual items by `ProductID` value. Multiple `SiteID` and `LocationID` values can also be specified in each query. The maximum limit is defined as `NumOf(SiteID) * NumOf(LocationID) <= 100`.

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

- `organizationId` should contains only one value, but it's still an array.
- `productId` can contains one or more values. If it's an empty array, all products will be returned.
- `siteId` and `locationId` are used for partitioning in Inventory Visibility. You can specify more than one `siteId` and `locationId` value in a *Query on-hand* request. In the current release, you must specify both `siteId` and `locationId` values.

The `groupByValues` parameter should follow your configuration for indexing. For more information, see [Product index hierarchy configuration](./inventory-visibility-configuration.md#index-configuration).

The `returnNegative` parameter controls whether the results contain negative entries.

> [!NOTE]
> If you've enabled the on-hand change schedule and available-to-promise (ATP) features, your query can also include the `QueryATP` Boolean parameter, which controls whether the query results include ATP information. For more information and examples, see [Inventory Visibility on-hand change schedules and available to promise](inventory-visibility-available-to-promise.md).

The following example shows sample body content.

```json
{
    "dimensionDataSource": "pos",
    "filters": {
        "organizationId": ["usmf"],
        "productId": ["T-shirt"],
        "siteId": ["1"],
        "LocationId": ["11"],
        "ColorId": ["Red"]
    },
    "groupByValues": ["ColorId", "SizeId"],
    "returnNegative": true
}
```

The following examples shows how to query all products in a specific site and location.

```json
{
    "filters": {
        "organizationId": ["usmf"],
        "productId": [],
        "siteId": ["1"],
        "LocationId": ["11"],
    },
    "groupByValues": ["ColorId", "SizeId"],
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

Here is a sample get URL. This get request is exactly the same as the post sample that was provided earlier.

```txt
/api/environment/{environmentId}/onhand?organizationId=usmf&productId=T-shirt&SiteId=1&LocationId=11&ColorId=Red&groupBy=ColorId,SizeId&returnNegative=true
```

## Available to promise

You can set up Inventory Visibility to let you schedule future on-hand changes and calculate ATP quantities. ATP is the quantity of an item that is available and can be promised to a customer in the next period. Use of the ATP calculation can greatly increase your order fulfillment capability. For information about how to enable this feature, and how to interact with Inventory Visibility through its API after the feature is enabled, see [Inventory Visibility on-hand change schedules and available to promise](inventory-visibility-available-to-promise.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
