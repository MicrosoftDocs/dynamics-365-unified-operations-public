---
title: Inventory availability APIs for e-commerce
description: This article describes the inventory availability APIs for e-commerce in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 01/30/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2022-11-10

---
# Inventory availability APIs for e-commerce

[!include [banner](../includes/banner.md)]

This article describes the inventory availability APIs for e-commerce in Microsoft Dynamics 365 Commerce.

Commerce provides the following APIs to query inventory availability of a product in e-commerce scenarios:

- **GetEstimatedAvailability** – Use this API to query inventory for a product or product variant in the online channel's default warehouse or warehouses that are linked to the online channel's fulfillment group.
- **GetEstimatedProductWarehouseAvailability** – Use this API to query inventory for a product or product variant in a specific warehouse.
- **GetDimensionValuesWithEstimatedAvailabilities** – Use this API to query inventory levels that are aggregated on the dimensions for a product, either in the online channel's default warehouse or in warehouses that are linked to the online channel's fulfillment group.

> [!NOTE]
> The **GetEstimatedAvailability** and **GetEstimatedProductWarehouseAvailability** APIs replace the **GetProductAvailabilities** and **GetAvailableInventoryNearby** APIs that are used in Commerce version 10.0.7 and earlier.

For more information about how to consume Retail Server APIs in external applications, see [Consume Retail Server APIs in external applications](dev-itpro/consume-retail-server-api.md).

## GetEstimatedAvailability

### Input parameters

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| searchCriteria | InventoryAvailabilitySearchCriteria | Required | |

#### InventoryAvailabilitySearchCriteria

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ProductIds | IEnumberable\<long\> | Required | |
| DefaultWarehouseOnly | bool | Optional | If the value is **true**, only the online channel's default warehouse is queried. If the value is **false**, warehouses that are linked to the online channel's fulfillment group, and have same legal entity with the online channel, are queried. |
| SearchArea | SearchArea | Optional | The area to search for stores for pickup in the fulfillment groups. |
| FilterByChannelFulfillmentGroup | bool | Optional | This parameter determines the fulfillment groups when **DefaultWarehouseOnly** is set to **false**. |
| DeliveryModeTypeFilterValue | (int) DeliveryModeTypeFilter | Optional | <p>Filter warehouses by their supported delivery modes:</p><ul><li>**(0) All** – Find all warehouses. This value is the default value.</li><li>**(1) Shipping** – Find warehouses that are eligible for shipping.</li><li>**(2) Pickup** – Find warehouses that are eligible for pickup.</li></ul> |
| QuantityUnitTypeValue | (int) QuantityUnitType | Optional | <p>The unit of measure to return the quantity in:</p><ul><li>**(0) Inventory** – The inventory unit of measure. This value is the default value.</li><li>**(1) Purchase** – The purchase unit of measure.</li><li>**(2) Sales** – The sales unit of measure.</li></ul> |

#### SearchArea

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| Latitude | decimal | Optional | |
| Longitude | decimal | Optional | |
| Radius | double | Optional | |
| DistanceUnit | (int) DistanceUnit | Optional | <ul><li>(0) Miles</li><li>(1) Kilometers</li></ul> |
| IsUnbounded | bool | Optional | |

### Sample request body

```json
{
    "searchCriteria": {
        "ProductIds": [
            123456
        ],
        "QuantityUnitTypeValue": 2,
        "DefaultWarehouseOnly": true
    }
}
```

### Sample response body

```json
{
    "ProductWarehouseInventoryAvailabilities": [
        {
            "ProductId": 123456,
            "InventLocationId": "{OnlineChannelWarehouse}",
            "DataAreaId": "{DataAreaId}",
            "PhysicalInventory": 0,
            "PhysicalReserved": 0,
            "TotalAvailable": 1,
            "TotalAvailableInventoryLevelLabel": "Available",
            "TotalAvailableInventoryLevelCode": "AVAIL",
            "OrderedInTotal": 0,
            "PhysicalAvailable": 0,
            "PhysicalAvailableInventoryLevelLabel": "Out of stock",
            "PhysicalAvailableInventoryLevelCode": "OOS",
            "LastInventoryTransactionId": 987654,
            "UnpostedOnlineOrderedQuantity": 0,
            "UnpostedFulfilledQuantity": 0,
            "IsInventoryAvailabilityQuantityReturned": true,
            "UnprocessedQuantity": 0,
            "QuantityUnitTypeValue": 2,
            "UnitOfMeasure": "ea",
            "MaximumPurchasablePhysicalAvailableQuantity": 0,
            "MaximumPurchasableTotalAvailableQuantity": 1,
            "SumUncountedTransactions": 0,
            "ExtensionProperties": []
        }
    ],
    "AggregatedProductInventoryAvailabilities": [
        {
            "ProductId": 123456,
            "DataAreaId": "{DataAreaId}",
            "TotalAvailableQuantity": 1,
            "TotalAvailableInventoryLevelLabel": "Available",
            "TotalAvailableInventoryLevelCode": "AVAIL",
            "PhysicalAvailableQuantity": 0,
            "PhysicalAvailableInventoryLevelLabel": "Out of stock",
            "PhysicalAvailableInventoryLevelCode": "OOS",
            "QuantityUnitTypeValue": 2,
            "UnitOfMeasure": "ea",
            "MaximumPurchasablePhysicalAvailableQuantity": 0,
            "MaximumPurchasableTotalAvailableQuantity": 1,
            "ExtensionProperties": []
        }
    ],
    "ExtensionProperties": []
}
```

## GetEstimatedProductWarehouseAvailability

### Input parameters

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| productWarehouses | IEnumerable\<ProductWarehouse\> | Required | |

#### ProductWarehouse

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| ProductId | long | Required | |
| InventLocationId | string | Required | The ID of the warehouse. |
| DataAreaId | string | Required | |

### Sample request body

```json
{
    "productWarehouses": [
        {
            "ProductId": 123456,
            "InventLocationId": "{WarehouseId}",
            "DataAreaId": "{DataAreaId}"
        }
    ]
}
```

### Sample response body

```json
{
    "ProductWarehouseInventoryAvailabilities": [
        {
            "ProductId": 123456,
            "InventLocationId": "{OnlineChannelWarehouse}",
            "DataAreaId": "{DataAreaId}",
            "PhysicalInventory": 0,
            "PhysicalReserved": 0,
            "TotalAvailable": 1,
            "TotalAvailableInventoryLevelLabel": "Available",
            "TotalAvailableInventoryLevelCode": "AVAIL",
            "OrderedInTotal": 0,
            "PhysicalAvailable": 0,
            "PhysicalAvailableInventoryLevelLabel": "Out of stock",
            "PhysicalAvailableInventoryLevelCode": "OOS",
            "LastInventoryTransactionId": 987654,
            "UnpostedOnlineOrderedQuantity": 0,
            "UnpostedFulfilledQuantity": 0,
            "IsInventoryAvailabilityQuantityReturned": true,
            "UnprocessedQuantity": 0,
            "QuantityUnitTypeValue": 2,
            "UnitOfMeasure": "ea",
            "MaximumPurchasablePhysicalAvailableQuantity": 0,
            "MaximumPurchasableTotalAvailableQuantity": 1,
            "SumUncountedTransactions": 0,
            "ExtensionProperties": []
        }
    ],
    "AggregatedProductInventoryAvailabilities": [
        {
            "ProductId": 123456,
            "DataAreaId": "{DataAreaId}",
            "TotalAvailableQuantity": 1,
            "TotalAvailableInventoryLevelLabel": "Available",
            "TotalAvailableInventoryLevelCode": "AVAIL",
            "PhysicalAvailableQuantity": 0,
            "PhysicalAvailableInventoryLevelLabel": "Out of stock",
            "PhysicalAvailableInventoryLevelCode": "OOS",
            "QuantityUnitTypeValue": 2,
            "UnitOfMeasure": "ea",
            "MaximumPurchasablePhysicalAvailableQuantity": 0,
            "MaximumPurchasableTotalAvailableQuantity": 1,
            "ExtensionProperties": []
        }
    ],
    "ExtensionProperties": []
}
```

## GetDimensionValuesWithEstimatedAvailabilities

### Input parameters

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| searchCriteria | ProductDimensionAvailabilitySearchCriteria | Required | |

#### ProductDimensionAvailabilitySearchCriteria

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| RequestedDimensionTypeValue | (int) ProductDimensionType | Required | <p>The product dimension type to request and to aggregate inventory quantities by.</p><ul><li>**(1) Color** – The color dimension.</li><li>**(2) Configuration** – The configuration dimension.</li><li>**(3) Size** – The size dimension.</li><li>**(4) Style** – The style dimension.</li></ul> |
| MatchingDimensionValues | ICollection\<ProductDimension\> | Optional | Aggregate only products that have matching dimension values. |
| DefaultWarehouseOnly | bool | Optional | If the value is **true**, only the online channel's default warehouse is queried. If the value is **false**, warehouses that are linked to the online channel's fulfillment group, and have same legal entity with the online channel, are queried. |
| FilterByChannelFulfillmentGroup | bool | Optional | This parameter determines the fulfillment groups when **DefaultWarehouseOnly** is set to **false**. |
| DeliveryModeTypeFilterValue | (int) DeliveryModeTypeFilter | Optional | <p>Filter warehouses by their supported delivery modes:</p><ul><li>**(0) All** – Find all warehouses. This value is the default value.</li><li>**(1) Shipping** – Find warehouses that are eligible for shipping.</li><li>**(2) Pickup** – Find warehouses that are eligible for pickup.</li></ul> |
| CatalogId | long | Optional | The identifier of the catalog that the product belongs to. |

#### ProductDimension

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| DimensionTypeValue | (int) ProductDimensionType | Required | <p>The product dimension type to request and to aggregate inventory quantities by.</p><ul><li>**(1) Color** – The color dimension.</li><li>**(2) Configuration** – The configuration dimension.</li><li>**(3) Size** – The size dimension.</li><li>**(4) Style** – The style dimension.</li></ul> |
| DimensionValue | ProductDimensionValue | Required | |

#### ProductDimensionValue

| Name | Type | Required/Optional | Description |
|----|----|----|----|
| RecordId | long | Required | |
| Value | string | Required | |

### Sample request body

```json
{
    "searchCriteria": {
        "RequestedDimensionTypeValue": 3,
        "MatchingDimensionValues": [
            {
                "DimensionTypeValue": 3,
                "DimensionValue": {
                    "RecordId": 0,
                    "Value": "{Size}"
                }
            }
        ],
        "DefaultWarehouseOnly": true,
        "FilterByChannelFulfillmentGroup": true,
        "DeliveryModeTypeFilterValue": 1,
        "CatalogId": 0
    }
}
```

### Sample response body

```json
{
    "value": [
        {
            "DimensionTypeValue": 3,
            "DimensionValue": {
                "RecordId": 456789,
                "Value": "{Size}",
                "DimensionId": "{DimensionId}",
                "ColorHexCode": "",
                "ImageUrl": "",
                "RefinerGroup": "",
                "ExtensionProperties": []
            },
            "ProductIds": [
                123456
            ],
            "TotalAvailableInventoryLevelLabel": "Available",
            "TotalAvailableInventoryLevelCode": "AVAIL",
            "PhysicalAvailableInventoryLevelLabel": "Available",
            "PhysicalAvailableInventoryLevelCode": "AVAIL"
        }
    ]
}
```

## The quantity output of APIs

Both the **GetEstimatedAvailability** API and the **GetEstimatedProductWarehouseAvailability** API internally use the channel-side calculation logic and return an estimated *physical available* quantity, *total available* quantity, *unit of measure*, and *inventory level* for the requested product and warehouse. The returned values can be shown on your e-commerce site if you want, or they can be used to trigger other business logic on your e-commerce site. For example, you can prevent the purchase of products that have an "out of stock" inventory level.

Other APIs that are available in Commerce can also directly access Commerce headquarters to fetch on-hand quantities for products. However, we don't recommend that you use them in an e-commerce environment because of potential performance issues and the impact that such frequent requests can have on your Commerce headquarters servers. For channel-side calculation, the **GetEstimatedAvailability** and **GetEstimatedProductWarehouseAvailability** APIs can provide a more accurate estimate of a product's availability by considering the transactions that have been created in the channels but that aren't yet known to Commerce headquarters.

To define how product quantity should be returned in the API output, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Inventory** tab, on the **Inventory availability APIs for e-Commerce** FastTab, in the **Quantity in API output** field, select one of the following options:

    - **Return inventory quantity** – The physical available and total available quantities of a requested product are returned in the API output.
    - **Return inventory quantity subtracting inventory buffer** – The quantity that's returned in the API output is adjusted by subtracting the inventory buffer value. For more information about the inventory buffer, see [Configure inventory buffers and inventory levels](inventory-buffers-levels.md).
    - **Not return inventory quantity** – Only the inventory level is returned in the API output. For more information about inventory levels, see [Configure inventory buffers and inventory levels](inventory-buffers-levels.md).

1. Run the **1070** (**Channel configuration**) job to sync the latest setting to channels.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
