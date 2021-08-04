---
title: Inventory Visibility public APIs
description: This topic describes public API(Application Programming Interface) opened in Inventory Visibility.
author: yufeihuang
ms.date: 08/02/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21
---

# Inventory Visibility public APIs

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
[!INCLUDE [cc-data-platform-banner](../../includes/cc-data-platform-banner.md)]

This topic describes public API (application programming interface) provided by Inventory Visibility.

The public REST API of the Inventory Visibility presents several specific endpoints for integration. It supports four main interaction types:

- Posting on-hand inventory changes to the add-in from an external system
- Set/override on-hand inventory quantities to the add-in from an external system
- Posting reservation events to the add-in from an external system
- Querying current on-hand quantities from an external system

The following table lists the APIs that are currently available:

| Path | Method | Description |
| --- | --- | --- |
| /api/environment/{environmentId}/onhand | Post | [Create one on-hand change event](#create-one-onhand-change-event) |
| /api/environment/{environmentId}/onhand/bulk | Post | [Create multiple change events](#create-multiple-onhand-change-events) |
| /api/environment/{environmentId}/setonhand/{inventorySystem}/bulk | Post | [Set/override on-hand quantities](#set-onhand-quantities) |
| /api/environment/{environmentId}/onhand/reserve | Post | [Create one reservation event](#create-one-reservation-event) |
| /api/environment/{environmentId}/onhand/reserve/bulk | Post | [Create multiple reservation events](#create-multiple-reservation-events) |
| /api/environment/{environmentId}/onhand/indexquery | Get | [Query with post method](#query-with-post-method) |
| /api/environment/{environmentId}/onhand/indexquery | Post | [Query with get method](#query-with-get-method) |

We have provided an out of box *Postman* request collection. You can import it to your *Postman* software with this shared link: "https://www.getpostman.com/collections/90bd57f36a789e1f8d4c".

## Find endpoint according to your Life Cycle Service (LCS) environment

The microservice of Inventory Visibility is deployed on Service Fabric, in multi-geography and multi-region. Currently we don't have a central endpoint that can auto redirect your request to the corresponding geo and region, so you need to compose these information pieces to a URL using the following pattern:

`https://inventoryservice.<RegionShortName>-il<IsLandNumber>.gateway.prod.island.powerapps.com`

The region short name can be found in the LCS environment. The following table lists the regions that are currently available.

| Azure region | Region short name |
| --- | --- |
| Australia east | eau |
| Australia southeast | seau |
| Canada central | cca |
| Canada east | eca |
| North Europe | neu |
| West Europe | weu |
| East US | eus |
| West US | wus |
| South UK | suk |
| West UK | wuk |

The island number is where your LCS environment is deployed on Service Fabric. Currently, there is no way to get this information from the user side.

We have built an user interface in Power Apps for you to get the complete endpoint of the microservice. For details, see [Get service endpoint](inventory-visibility-power-platform.md#get-service-endpoint).

## <a name="inventory-visibility-authentication"></a>Authentication

The platform security token is used to call the Inventory Visibility public API. Therefore, you must generate an _Azure Active Directory (Azure AD) token_ using your Azure AD application. You must then use the Azure AD token to get the _access token_ from the security service.

Get a security service token by doing the following:

1. Sign in to Azure portal and use it to find the `clientId` and `clientSecret` for your Dynamics 365 Supply Chain Management application.
1. Fetch an Azure Active Directory token (`aadToken`) by submitting an HTTP request with the following properties:

   - **URL** - `https://login.microsoftonline.com/${aadTenantId}/oauth2/token`
   - **Method** - `GET`
   - **Body content (form data)**:

        | key | value |
        | --- | --- |
        | client_id | ${aadAppId} |
        | client_secret | ${aadAppSecret} |
        | grant_type | client_credentials |
        | resource | 0cdb527f-a8d1-4bf8-9436-b352c68682b2 |

1. You should receive an `aadToken` in response, which should resemble the following example:

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

1. Formulate a JSON request that resembles the following:

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

   Where:

   - The `client_assertion` value must be the `aadToken` you received in the previous step.
   - The `context` value must be the environment ID where you want to deploy the add-in.
   - Set all of other values as shown in the example.

1. Submit an HTTP request with the following properties:

   - **URL** - `https://securityservice.operations365.dynamics.com/token`
   - **Method** - `POST`
   - **HTTP header** - Include the API version (key is `Api-Version` and value is `1.0`)
   - **Body content** - Include the JSON request that you created in the previous step.

1. You will get an `access_token` in response. This is what you need as a bearer token to call the Inventory Visibility API. Here is an example.

   ```json
   {
     "access_token": "{Returned_Token}",
     "token_type": "bearer",
     "expires_in": 3600
   }
   ```

We will use `$access_token` in following sections to represent the token fetched in the last step.

## <a name="create-onhand-change-event"></a>Create on-hand change events

There are two APIs for creating on-hand change events:

- Create one record: `/api/environment/{environmentId}/onhand`
- Create multiple records: `/api/environment/{environmentId}/onhand/bulk`

The following table summarizes the meaning of each field in the JSON body.

| Field ID | Description |
| --- | --- |
| `id` | A unique ID for the specific change event. This ID is used to ensure that if communication with the service fails during posting, resubmitting the event would not result in the same event being counted twice in the system. |
| `organizationId` | The identifier of the organization linked to the event. This maps to a Dynamics 365 Supply Chain Management organization or data area ID. |
| `productId` | The identifier of the product in question. |
| `quantities` | The quantity by which the on-hand needs to be changed. If, for instance, 10 new books were added to a shelf, this value would be `quantities:{ shelf:{ received: 10 }}`. If 3 books were then removed from the shelf or sold, this value would be `quantities:{ shelf:{ sold: 3 }}`. |
| `dimensionDataSource` | The data source of the dimensions used in the posting change event and query. If you specify the data source, you can use the custom dimensions from the specified data source. With the dimension configuration, Inventory Visibility can map the custom dimensions to the general default dimensions. If the `dimensionDataSource` is not specified, you can only use the general [base dimensions](inventory-visibility-configuration.md#data-source-configuration-dimension) in your queries. |
| `dimensions` | A dynamic key/value pair. These will map to some of the dimensions in Dynamics 365 Supply Chain Management, but you could also add custom dimensions (like _Source_) to denote whether the event is coming from Supply Chain Management or an external system. |

### <a name="create-one-onhand-change-event"></a>Create one on-hand change event

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

This API creates a single on-hand change event.

The following example shows sample body content. In this sample, we post a change event for the product *T-shirt*. This event is from POS,
and the customer has returned a red T-shirt back to our store. This event will increase the quantity of *T-shirt* by 1.

```json
{
  "id": "123456",
  "organizationId": "usmf",
  "productId": "T-shirt",
  "dimensionDataSource": "pos",
  "dimensions": {
    "ColorId": "Red"
  },
  "quantities": {
    "pos": {
      "inbound": 1
    }
  }
}
```

The following example shows sample body content without `dimensionDataSource`:

```json
{
  "id": "123456",
  "organizationId": "usmf",
  "productId": "T-shirt",
  "dimensions": {
    "ColorId": "Red",
    "SiteId": "1",
    "LocationId": "11"
  },
  "quantities": {
    "pos": {
      "inbound": 1
    }
  }
}
```

### <a name="create-multiple-onhand-change-events"></a>Create multiple change events

This API is able to create multiple records at once. The only differences between this API and the single-event API are the `Path` and `Body`, where the `Body` provides an array of records.

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

The following example shows sample body content:

```json
[
  {
    "id": "123456",
    "organizationId": "usmf",
    "productId": "T-shirt",
    "dimensionDataSource": "pos",
    "dimensions": {
      "PosMachineId": "0001"
    },
    "quantities": {
      "pos": { "inbound": 1 }
    }
  },
  {
    "id": "654321",
    "organizationId": "usmf",
    "productId": "@PRODUCT1",
    "dimensionDataSource": "pos",
    "dimensions": {
      "PosMachineId": "0001"
    },
    "quantities": {
      "pos": { "outbound": 3 }
    }
  }
]
```

## <a name="set-onhand-quantities"></a>Set on-hand quantities

The _Set on-hand_ api will override the current data for the specified product.

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

The following example shows sample body content. The behavior of this API is different from [_Create on-hand change event_](#create-onhand-change-event). In this sample, the quantity of *T-shirt* will be set to 1.

```json
[
  {
    "id": "123456",
    "organizationId": "usmf",
    "productId": "T-shirt",
    "dimensionDataSource": "pos",
    "dimensions": {
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

## Create a reservation event

To use the *Reserve* API, you must open the reservation feature and finish the reservation configuration. For details, see [Reservation configuration](inventory-visibility-configuration.md#reservation-configuration).

### <a name="create-one-reservation-event"></a>Create one reservation event

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

This API is a bulk version of [Create one reservation event](#create-one-reservation-event).

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

The _Query on-hand_ API is used to fetch current on-hand inventory data for your products.

### <a name="query-with-post-method"></a>Query with post method

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
        organizationId: string,
        filters: {
            [dimensionKey:string]: string[],
        },
        groupByValues: string[],
        returnNegative: boolean,
    }
```

The following example shows sample body content:

```json
{
  "dimensionDataSource": "pos",
  "filters": {
    "organizationId": ["usmf"],
    "productId": ["T-shirt"],
    "ColorId": ["Red"]
  },
  "groupByValues": ["ColorId", "SizeId"],
  "returnNegative": true
}
```

### <a name="query-with-get-method"></a>Query with get method

```txt
Path:
    /api/environment/{environmentId}/onhand/indexquery
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

Here is a sample get URL This get request is exactly same as the post sample provided previously.

```txt
/api/environment/{environmentId}/onhand/indexquery?organizationId=usmf&productId=T-shirt&ColorId=Red&groupBy=ColorId,SizeId&returnNegative=true
```

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
