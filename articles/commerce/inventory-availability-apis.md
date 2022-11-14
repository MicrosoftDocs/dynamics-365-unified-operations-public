---
title: Inventory availability APIs for e-commerce
description: This article describes the inventory availability APIs for e-commerce in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 11/14/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2022-11-10

---
# Inventory availability APIs for e-commerce

[!include [banner](../includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes the inventory availability APIs for e-commerce in Microsoft Dynamics 365 Commerce.

Commerce provides the following APIs for e-commerce scenarios to query inventory availability of a product:

- **GetEstimatedAvailability** – Use this API to query inventory for a product or product variant in the online channel's default warehouse or warehouses that are linked to the online channel's fulfillment group.
- **GetEstimatedProductWarehouseAvailability** – Use this API to query inventory for a product or product variant from a specific warehouse.
- **GetDimensionValuesWithEstimatedAvailabilities** – Use this API to query inventory levels aggregated on the dimensions for a product, either in the online channel's default warehouse or warehouses that are linked to the online channel's fulfillment group.

> [!NOTE]
> The **GetEstimatedAvailability** and **GetEstimatedProductWarehouseAvailability** APIs replace the **GetProductAvailabilities** and **GetAvailableInventoryNearby** APIs used in Commerce versions 10.0.7 and earlier.

For more information about how to consume Retail Server APIs in external applications, see [Consume Retail Server APIs in external applications](dev-itpro/consume-retail-server-api.md).

## GetEstimatedAvailability

### Input parameters

| Name | Type | Required/Optional | Description |
|:----|:----|:----|:----|
| searchCriteria | InventoryAvailabilitySearchCriteria | Required | |

#### InventoryAvailabilitySearchCriteria

| Name | Type | Required/Optional | Description |
|:----|:----|:----|:----|
| ProductIds | IEnumberable\<long\> | Required | |
| DefaultWarehouseOnly | bool | Optional | **True** to query online channel's default warehouse only; otherwise, query warehouses that are linked to the online channel's fulfillment group. |
| SearchArea | SearchArea | Optional | The area to search stores for pickup within the fulfillment groups. |
| FilterByChannelFulfillmentGroup | bool | Optional | Decides the fulfillment groups when DefaultWarehouseOnly is set to **false**. |
| DeliveryModeTypeFilterValue | (int) DeliveryModeTypeFilter | Optional | Filter warehouses by their supported delivery modes: <br/> • (0) All: all warehouses. This is the default value. <br/> • (1) Shipping: find warehouses eligible for shipping. <br/> • (2) Pickup: find warehouses eligible for pickup. |
| QuantityUnitTypeValue | (int) QuantityUnitType | Optional | Which unit of measure to return quantity: <br/> • (0) Inventory: inventory unit of measure. This is the default value. <br/> • (1) Purchase: purchase unit of measure. <br/> • (2) Sales: sales unit of measure. |

#### SearchArea

| Name | Type | Required/Optional | Description |
|:----|:----|:----|:----|
| Latitude | decimal | Optional | |
| Longitude | decimal | Optional | |
| Radius | double | Optional | |
| DistanceUnit | (int) DistanceUnit | Optional | • (0) Miles. <br/>• (1) Kilometers. |
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
|:----|:----|:----|:----|
| productWarehouses | IEnumerable\<ProductWarehouse\> | Required | |

#### ProductWarehouse

| Name | Type | Required/Optional | Description |
|:----|:----|:----|:----|
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
|:----|:----|:----|:----|
| searchCriteria | ProductDimensionAvailabilitySearchCriteria | Required | |

#### ProductDimensionAvailabilitySearchCriteria

| Name | Type | Required/Optional | Description |
|:----|:----|:----|:----|
| RequestedDimensionTypeValue | (int) ProductDimensionType | Required | The product dimension type to request and to aggregate inventory quantities.<br/>• (1) Color: color dimension.<br/>• (2) Configuration: configuration dimension.<br/>• (3) Size: size dimension.<br/>• (4) Style: style dimension. |
| MatchingDimensionValues | ICollection\<ProductDimension\> | Optional | Only aggregate products that have matching dimension values. |
| DefaultWarehouseOnly | bool | Optional | **True** to query online channel's default warehouse only; otherwise, query warehouses that are linked to the online channel's fulfillment group. |
| FilterByChannelFulfillmentGroup | bool | Optional | Decides the fulfillment groups when DefaultWarehouseOnly is set to **false**. |
| DeliveryModeTypeFilterValue | (int) DeliveryModeTypeFilter | Optional | Filter warehouses by their supported delivery modes: <br/> • (0) All: all warehouses. This is the default value. <br/> • (1) Shipping: find warehouses eligible for shipping. <br/> • (2) Pickup: find warehouses eligible for pickup. |
| CatalogId | long | Optional | Which catalog identifier the product belong to. |

#### ProductDimension

| Name | Type | Required/Optional | Description |
|:----|:----|:----|:----|
| DimensionTypeValue | (int) ProductDimensionType | Required | The product dimension type to request and to aggregate inventory quantities.<br/>• (1) Color: color dimension.<br/>• (2) Configuration: configuration dimension.<br/>• (3) Size: size dimension.<br/>• (4) Style: style dimension. |
| DimensionValue | ProductDimensionValue | Required | |

#### ProductDimensionValue

| Name | Type | Required/Optional | Description |
|:----|:----|:----|:----|
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

Both the **GetEstimatedAvailability** and **GetEstimatedProductWarehouseAvailability** APIs internally use the channel-side calculation logic and return estimated **physical available** quantity, **total available** quantity, **unit of measure (UoM)**, and **inventory level** for the requested product and warehouse. The returned values can be shown on your e-commerce site if you want, or they can be used to trigger other business logic on your e-commerce site. For example, you can prevent the purchase of products with an "out of stock" inventory level.

Although other APIs that are available in Commerce can directly access headquarters to fetch on-hand quantities for products, it isn't recommended they be used in an e-commerce environment because of potential performance issues and the impact that such frequent requests can have on your headquarters servers. With channel-side calculation, the two APIs mentioned above can provide a more accurate estimate of a product's availability by taking into account the transactions created in the channels that aren't yet known to headquarters.

To define how product quantity should be returned in the API output, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. Select the **Inventory** tab, and then on the **Inventory availability APIs for e-Commerce** FastTab, configure the value of the **Quantity in API output** setting.
1. Run the **1070** (**Channel configuration**) job to sync the latest setting to channels.

The **Quantity in API output** setting provides three options:

- **Return inventory quantity** – Physical available and total available quantity of a requested product are returned in API output.
- **Return inventory quantity subtracting inventory buffer** – The quantity returned in the API output is adjusted by subtracting the inventory buffer value. For more information about the inventory buffer, see [Configure inventory buffers and inventory levels](inventory-buffers-levels.md).
- **Not return inventory quantity** – Only the inventory level is returned in the API output. For more information about inventory levels, see [Configure inventory buffers and inventory levels](inventory-buffers-levels.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
