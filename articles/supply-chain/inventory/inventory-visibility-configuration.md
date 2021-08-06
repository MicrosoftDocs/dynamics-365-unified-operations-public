---
title: Inventory Visibility configuration
description: This topic describes how to configure Inventory Visibility.
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

# Inventory Visibility configuration

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
[!INCLUDE [cc-data-platform-banner](../../includes/cc-data-platform-banner.md)]

This topic describes how to configure Inventory Visibility.

## <a name="introduction"></a>Introduction

Before you start to work with Inventory Visibility, you must complete the following configuration as described in this topic:

- [Data source configuration](#data-source-configuration)
- [Partition configuration](#partition-configuration)
- [Product index hierarchy configuration](#index-configuration)
- [Reservation configuration (optional)](#reservation-configuration)
- [Default configuration sample](#default-configuration-sample)

> [!NOTE]
> You can view and edit Inventory Visibility configurations in [Microsoft Power Apps](./inventory-visibility-power-platform.md#configuration). After the configuration is completed, select **Update Configuration** in the app.

## <a name="data-source-configuration"></a>Data source configuration

The data source represents the system that your data comes from. Examples include `fno` (which stands for "Dynamics 365 Finance") and `pos` (which stands for "point of sale").

The data source configuration includes the following parts:

- Dimension (dimension mapping)
- Physical measure
- Calculated measure

> [!NOTE]
> The `fno` data source is reserved for Dynamics 365 Supply Chain Management.

### <a name="data-source-configuration-dimension"></a>Dimension (dimension mapping)

The purpose of the dimension configuration is to standardize the multi-system integration for posting events and queries, based on dimension combinations.

Inventory Visibility supports the following general base dimensions.

| Dimension type | Base dimension |
|---|---|
| Product | `ColorId` |
| Product | `SizeId` |
| Product | `StyleId` |
| Product | `ConfigId` |
| Tracking | `BatchId` |
| Tracking | `SerialId` |
| Location | `LocationId` |
| Location | `SiteId` |
| Inventory status | `StatusId` |
| Warehouse specific | `WMSLocationId` |
| Warehouse specific | `WMSPalletId` |
| Warehouse specific | `LicensePlateId` |
| Others | `VersionId` |
| Inventory (custom) | `InventDimension1` through `InventDimension12` |
| Extension | `ExtendedDimension1` through `ExtendedDimension8` |

> [!NOTE]
> The dimension types that are listed in the preceding table are for reference only. You don't have to define them in Inventory Visibility.
>
> Inventory (custom) dimensions might be reserved for Supply Chain Management. In that case, you can use the extended dimensions instead.

External systems can access Inventory Visibility through its RESTful APIs. For the integration, Inventory Visibility lets you configure the _external data source_ and the mapping from the _external dimensions_ to the _base dimensions_. Here is an example of a dimension mapping table.

| External dimension | Base dimension |
|---|---|
| `MyColorId` | `ColorId` |
| `MySizeId` | `SizeId` |
| `MyStyleId` | `StyleId` |
| `MyDimension1` | `ExtendedDimension1` |
| `MyDimension2` | `ExtendedDimension2` |

By configuring a dimension mapping, you can send the external dimensions directly to Inventory Visibility. Inventory Visibility will then automatically convert external dimensions to base dimensions.

### Physical measures

Physical measures modify the quantity and reflect the inventory status. You can define your own physical measures, based on your requirements.

Inventory Visibility provides a list of default physical measures that are linked to Supply Chain Management (the `fno` data source). The following table provides an example of physical measures.

| Physical measure name | Description |
|---|---|
| `NotSpecified` | Not specified |
| `Arrived` | Arrived |
| `AvailOrdered` | Available ordered |
| `AvailPhysical` | Available physical |
| `Deducted` | Deducted |
| `OnOrder` | OnOrder |
| `Ordered` | Ordered |
| `PhysicalInvent` | Physical inventory |
| `Picked` | Picked |
| `PostedQty` | Posted quantity |
| `QuotationIssue` | Quotation issue |
| `QuotationReceipt` | Quotation receipt |
| `Received` | Received |
| `Registered` | Registered |
| `ReservOrdered` | Ordered reserved |
| `ReservPhysical` | Physical reserved |

### <a name="data-source-configuration-calculated-measure"></a>Calculated measures

Calculated measures provide a customized computation formula that consists of a combination of physical measures. This functionality lets you define a set of physical measures that will be added, and/or a set of physical measures that will be subtracted, to form the customized measurement.

For example, you have the following query result.

```json
[
    {
        "productId": "T-shirt",
        "dimensions": {
            "SiteId": "1",
            "LocationId": "11",
            "ColorId": "Red"
        },
        "quantities": {
            "pos": {
                "inbound": 80.0,
                "outbound": 20.0
            },
            "fno": {
                "availphysical": 100.0,
                "orderedintotal": 50.0,
                "orderedreserved": 10.0
            },
            "externalchannel": {
                "received": 90.0,
                "scheduled": 30.0,
                "issued": 60.0,
                "reserved": 40.0
            }
        }
    }
]
```

You then configure a calculated measure that is named `MyCustomAvailableforReservation`, as shown in the following table. This calculated measure will be consumed by the consumption system.

| Consumption system | Calculated measure | Data source | Physical measure | Calculation type |
|---|---|---|---|---|
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `availphysical` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `orderedintotal` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `orderedreserved` | `Subtraction` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `pos` | `inbound` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `pos` | `outbound` | `Subtraction` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `received` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `scheduled` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `issued` | `Subtraction` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `reserved` | `Subtraction` |

When this computation formula is used, the new query result will include the customized measurement.

```json
[
    {
        "productId": "T-shirt",
        "dimensions": {
            "SiteId": "1",
            "LocationId": "11",
            "ColorId": "Red"
        },
        "quantities": {
            "pos": {
                "inbound": 80.0,
                "outbound": 20.0
            },
            "fno": {
                "availphysical": 100.0,
                "orderedintotal": 50.0,
                "orderedreserved": 10.0
            },
            "externalchannel": {
                "received": 90.0,
                "scheduled": 30.0,
                "issued": 60.0,
                "reserved": 40.0
            },
            "CustomChannel": {
                "MyCustomAvailableforReservation": 220.0
            }
        }
    }
]
```

The `MyCustomAvailableforReservation` output, based on the calculation setting in the custom measurements, is 100 + 50 + 80 + 90 + 30 – 10 – 20 – 60 – 40 = 220.

## <a name="partition-configuration"></a>Partition configuration

The partition configuration consists of a combination of base dimensions. It defines the data distribution pattern. Data operations in the same partition support high performance and don't cost too much. Therefore, good partition patterns can contribute significant benefits.

Inventory Visibility provides the following default partition configuration.

| Base dimension | Hierarchy |
|---|---|
| `SiteId` | 1 |
| `LocationId` | 2 |

> [!NOTE]
> The default partition configuration is for reference only. You don't have to define it in Inventory Visibility. Currently, the partition configuration upgrade isn't supported.

## <a name="index-configuration"></a>Product index hierarchy configuration

Most of the time, the inventory on-hand query won't be only at the highest "total" level. Instead, you might want also to see results that are aggregated based on the inventory dimensions.

Inventory Visibility provides flexibility by letting you set up the _indexes_. These indexes are based on a dimension or a combination of dimensions. An index consists of a *set number*, a *dimension*, and a *hierarchy*, as defined in the following table.

| Name | Description |
|---|---|
| Set number | Dimensions that belong to the same set (index) will be grouped together, and the same set number will be allocated to them. |
| Dimension | Base dimensions that the query result is aggregated on. |
| Hierarchy | The hierarchy is used to define the supported dimension combinations that can be queried. For example, you set up a dimension set that has a hierarchy sequence of `(ColorId, SizeId, StyleId)`. In this case, the system supports queries on four dimension combinations. The first combination is empty, the second is `(ColorId)`, the third is `(ColorId, SizeId)`, and the fourth is `(ColorId, SizeId, StyleId)`. The other combinations aren't supported. For more information, see the example that follows. |

### Example

This section provides an example that shows how the hierarchy works.

You have the following items in your inventory.

| Item | ColorId | SizeId | StyleId | Quantity |
|---|---|---|---|---|
| T-shirt | Black | Small | Wide | 1 |
| T-shirt | Black | Small | Regular | 2 |
| T-shirt | Black | Large | Wide | 3 |
| T-shirt | Black | Large | Regular | 4 |
| T-shirt | Red | Small | Wide | 5 |
| T-shirt | Red | Small | Regular | 6 |
| T-shirt | Red | Large | Regular | 7 |

Here is the index.

| Set Number | Dimension | Hierarchy |
|---|---|---|
| 1 | `ColorId` | 1 |
| 1 | `SizeId` | 2 |
| 1 | `StyleId` | 3 |

The index lets you query the on-hand inventory in the following ways:

- `()` – Grouped by all

    - T-shirt, 28

- `(ColorId)` – Grouped by `ColorId`

    - T-shirt, Black, 10
    - T-shirt, Red, 18

- `(ColorId, SizeId)` – Grouped by the combination of `ColorId` and `SizeId`

    - T-shirt, Black, Small, 3
    - T-shirt, Black, Large, 7
    - T-shirt, Red, Small, 11
    - T-shirt, Red, Large, 7

- `(ColorId, SizeId, StyleId)` – Grouped by the combination of `ColorId`, `SizeId`, and `StyleId`

    - T-shirt, Black, Small, Wide, 1
    - T-shirt, Black, Small, Regular, 2
    - T-shirt, Black, Large, Wide, 3
    - T-shirt, Black, Large, Regular, 4
    - T-shirt, Red, Small, Wide, 5
    - T-shirt, Red, Small, Regular, 6
    - T-shirt, Red, Large, Regular, 7

> [!NOTE]
> Base dimensions that are defined in the partition configuration should not be defined in index configurations.

## <a name="reservation-configuration"></a>Reservation configuration (optional)

Reservation configuration is required if you want to use the soft reservation feature. The configuration consists of two fundamental parts:

- Soft reservation mapping
- Soft reservation hierarchy

### Soft reservation mapping

When you make a reservation, you might want to know whether on-hand inventory is currently available for reservation. The validation is linked to a calculated measure that represents a computation formula of a combination of physical measures.

For example, a reservation measure is based on the `SoftReservOrdered` physical measure from the `iv` (Inventory Visibility) data source. In this case, you can set up the `AvailableToReserve` calculated measure of the `iv` data source as shown here.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `AvailPhysical` |
| Addition | `pos` | `Inbound` |
| Subtraction | `pos` | `Outbound` |
| Subtraction | `iv` | `SoftReservOrdered` |

Then set up a soft reservation mapping to provide a mapping from the `SoftReservOrdered` reservation measure to the `AvailableToReserve` calculated measure.

| Physical measure data source | Physical measure | Available for reservation data source | Available for reservation calculated measure |
|---|---|---|---|
| `iv` | `SoftReservOrdered` | `iv` | `AvailableToReserve` |

Now, when you do reservation on `SoftReservOrdered`, Inventory Visibility will automatically find `AvailableToReserve` and its related computation formula to do the reservation validation.

For example, you have the following on-hand inventory in Inventory Visibility.

```json
{
    "productId": "T-shirt",
    "dimensions": {
        "SiteId": "1",
        "LocationId": "11",
        "ColorId": "Red"
    },
    "quantities": {
        "iv": {
            "SoftReservOrdered": 90
        },
        "fno": {
            "availphysical": 70.0,
        },
        "pos": {
            "inbound": 50.0,
            "outbound": 20.0
        }
    }
}
```

In this case, the following calculation applies:

`AvailableToReserve` = `fno.availphysical` + `pos.inbound` – `pos.outbound` – `iv.SoftReservOrdered`  
= 70 + 50 – 20 – 90  
= 10

Therefore, if you try to make reservations on `iv.SoftReservOrdered`, and the quantity is less than or equal to `AvailableToReserve` (10), you can do the reservation.

### Soft reservation hierarchy

The reservation hierarchy describes the sequence of dimensions that must be specified when reservations are made. It works in the same way that the product index hierarchy works for on-hand queries.

The reservation hierarchy is independent of the product index hierarchy. This independence lets you implement category management where users can break down the dimensions into details to specify the requirements for making more precise reservations.

Here is an example of a soft reservation hierarchy.

| Base dimension | Hierarchy |
|---|---|
| `SiteId` | 1 |
| `LocationId` | 2 |
| `ColorId` | 3 |
| `SizeId` | 4 |
| `StyleId` | 5 |

In this example, you can do reservation in the following dimension sequences:

- `()` – No dimension is specified.
- `(SiteId)`
- `(SiteId, LocationId)`
- `(SiteId, LocationId, ColorId)`
- `(SiteId, LocationId, ColorId, SizeId)`
- `(SiteId, LocationId, ColorId, SizeId, StyleId)`

A valid dimension sequence should strictly follow the reservation hierarchy, dimension by dimension. For example, the hierarchy sequence `(SiteId, LocationId, SizeId)` isn't valid, because `ColorId` is missing.

## <a name="default-configuration-sample"></a>Default configuration sample

During its initialization stage, Inventory Visibility sets up a default configuration. You can modify the configuration as you require.

### Data source configuration

#### Configuration of the iv data source

This section describes how the `iv` data source is configured.

##### Physical measures configured for the iv data source

The following physical measures are configured for the `iv` data source:

- `Ordered`
- `SoftReservPhysical`
- `SoftReservOrdered`
- `ReservOrdered`
- `ReservPhysical`

##### OrderedTotal calculated measure

The `OrderedTotal` calculated measure is configured for the `iv` data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `Ordered` |
| Addition | `fno` | `Arrived` |
| Addition | `iv` | `Ordered` |

##### OnHand calculated measure

The `OnHand` calculated measure is configured for the `iv` data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `PhysicalInvent` |
| Addition | `iom` | `OnHand` |
| Addition | `sap` | `Unrestricted` |
| Addition | `sap` | `QualityInspection` |
| Addition | `pos` | `PosInbound` |
| Subtraction | `pos` | `PosOutbound` |

##### ReservedTotal calculated measure

The `ReservedTotal` calculated measure is configured for the `iv` data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `ReservPhysical` |
| Addition | `fno` | `ReservOrdered` |
| Addition | `iv` | `SoftReservPhysical` |
| Addition | `iv` | `SoftReservOrdered` |
| Addition | `iv` | `ReservPhysical` |
| Addition | `iv` | `ReservOrdered` |

##### SoftReserved calculated measure

The `SoftReserved` calculated measure is configured for the `iv` data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `iv` | `SoftReservPhysical` |
| Addition | `iv` | `SoftReservOrdered` |

##### HardReserved calculated measure

The `HardReserved` calculated measure is configured for the `iv` data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `ReservPhysical` |
| Addition | `fno` | `ReservOrdered` |
| Addition | `iv` | `ReservPhysical` |
| Addition | `iv` | `ReservOrdered` |

##### OpenOrder calculated measure

The `OpenOrder` calculated measure is configured for the `iv` data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `OnOrder` |
| Addition | `iom` | `OnOrder` |

##### OnHandAvailable calculated measure

The `OnHandAvailable` calculated measure is configured for the `iv` data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `PhysicalInvent` |
| Addition | `iom` | `OnHand` |
| Addition | `sap` | `Unrestricted` |
| Addition | `sap` | `QualityInspection` |
| Addition | `pos` | `PosInbound` |
| Subtraction | `fno` | `ReservPhysical` |
| Subtraction | `iv` | `SoftReservPhysical` |
| Subtraction | `pos` | `PosOutbound` |

##### AvailableToReserve calculated measure

The `AvailableToReserve` calculated measure is configured for the `iv` data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `PhysicalInvent` |
| Addition | `iom` | `OnHand` |
| Addition | `sap` | `Unrestricted` |
| Addition | `sap` | `QualityInspection` |
| Addition | `pos` | `PosInbound` |
| Addition | `fno` | `Ordered` |
| Addition | `fno` | `Arrived` |
| Addition | `iv` | `Ordered` |
| Subtraction | `fno` | `ReservPhysical` |
| Subtraction | `fno` | `ReservOrdered` |
| Subtraction | `iv` | `SoftReservPhysical` |
| Subtraction | `iv` | `SoftReservOrdered` |
| Subtraction | `iv` | `ReservPhysical` |
| Subtraction | `iv` | `ReservOrdered` |
| Subtraction | `pos` | `PosOutbound` |

##### InventorySupply calculated measure

The `InventorySupply` calculated measure is configured for the `iv` data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `Ordered` |
| Addition | `fno` | `Arrived` |
| Addition | `iv` | `Ordered` |
| Addition | `fno` | `PhysicalInvent` |
| Addition | `iom` | `OnHand` |
| Addition | `sap` | `Unrestricted` |
| Addition | `sap` | `QualityInspection` |
| Addition | `pos` | `PosInbound` |
| Subtraction | `pos` | `PosOutbound` |

##### InventoryDemand calculated measure

The `InventoryDemand` calculated measure is configured for the `iv` data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `OnOrder` |
| Addition | `iom` | `OnOrder` |
| Addition | `iv` | `SoftReservPhysical` |
| Addition | `iv` | `SoftReservOrdered` |
| Addition | `fno` | `ReservPhysical` |
| Addition | `fno` | `ReservOrdered` |
| Addition | `iv` | `ReservPhysical` |
| Addition | `iv` | `ReservOrdered` |

#### Configuration of the fno data source

This section describes how the `fno` data source is configured.

##### Dimension mappings for the fno data source

The dimension mappings that are listed in the following table are configured for the `fno` data source.

| External dimension | Base dimension |
|---|---|
| `InventBatchId` | `BatchId` |
| `InventColorId` | `ColorId` |
| `InventLocationId` | `LocationId` |
| `InventSerialId` | `SerialId` |
| `InventSiteId` | `SiteId` |
| `InventSizeId` | `SizeId` |
| `InventStatusId` | `StatusId` |
| `InventStyleId` | `StyleId` |
| `LicensePlateId` | `LicensePlateId` |
| `WMSLocationId` | `WMSLocationId` |
| `WMSPalletId` | `WMSPalletId` |
| `ConfigId` | `ConfigId` |
| `InventVersionId` | `VersionId` |
| `InventDimension1` | `CustomDimension1` |
| `InventDimension2` | `CustomDimension2` |
| `InventDimension3` | `CustomDimension3` |
| `InventDimension4` | `CustomDimension4` |
| `InventDimension5` | `CustomDimension5` |
| `InventDimension6` | `CustomDimension6` |
| `InventDimension7` | `CustomDimension7` |
| `InventDimension8` | `CustomDimension8` |
| `InventDimension9` | `CustomDimension9` |
| `InventDimension10` | `CustomDimension10` |
| `InventDimension11` | `CustomDimension11` |
| `InventDimension12` | `CustomDimension12` |

##### Physical measures configured for the fno data source

The following physical measures are configured for the `fno` data source:

- `Ordered`
- `Arrived`
- `AvailPhysical`
- `PhysicalInvent`
- `ReservPhysical`
- `ReservOrdered`
- `OnOrder`

#### Configuration of the pos data source

This section describes how the data source `pos` is configured.

##### Physical measures for the pos data source

The following physical measures are configured for the `pos` data source:

- `PosInbound`
- `PosOutbound`

##### Calculated measure for the pos data source

The calculated measure that is shown in the following table is configured for the `pos` data source. <!-- KFM: Are we missing a name for this calculated measure? -->

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `AvailPhysical` |
| Addition | `pos` | `PosInbound` |
| Subtraction | `pos` | `PosOutbound` |

#### Configuration of the iom data source

The following physical measures are configured for the `iom` (intelligent order management) data source:

- `OnOrder`
- `OnHand`

#### Configuration of the sap data source

The following physical measures are configured for the `sap` data source: <!-- KFM: Can we tell what `sap` stands for? -->

- `Unrestricted`
- `QualityInspection`

### Partition configuration

The following table shows the default partition configuration.

| Base dimension | Hierarchy |
|---|---|
| `SiteId` | 1 |
| `LocationId` | 2 |

### Index configuration

The following table shows the default index configuration.

| Set Number | Dimension | Hierarchy |
|---|---|---|
| 1 | `ColorId` | 1 |
| 1 | `SizeId` | 2 |
| 1 | `StyleId` | 3 |

### Reservation configuration

This section describes the default reservation configuration.

#### Reservation mapping

The following table shows the default reservation mapping.

| Physical measure data source | Physical measure | Available for reservation data source | Available for reservation calculated measure |
|---|---|---|---|
| `iv` | `SoftReservOrdered` | `iv` | `AvailableToReserve` |

#### Reservation hierarchy

The following table shows the default reservation hierarchy.

| Base dimension | Hierarchy |
|---|---|
| `SiteId` | 1 |
| `LocationId` | 2 |
| `ColorId` | 3 |
| `SizeId` | 4 |
| `StyleId` | 5 |
| `BatchId` | 6 |
| `SerialId` | 7 |
| `StatusId` | 8 |
| `LicensePlateId` | 9 |
| `WMSLocationId` | 10 |
| `WMSPalletId` | 11 |
| `ConfigId` | 12 |
| `VersionId` | 13 |
| `CustomDimension1` | 14 |
| `CustomDimension2` | 15 |
| `CustomDimension3` | 16 |
| `CustomDimension4` | 17 |
| `CustomDimension5` | 18 |
| `CustomDimension6` | 19 |
| `CustomDimension7` | 20 |
| `CustomDimension8` | 21 |
| `CustomDimension9` | 22 |
| `CustomDimension10` | 23 |
| `CustomDimension11` | 24 |
| `CustomDimension12` | 25 |
| `ExtendedDimension1` | 26 |
| `ExtendedDimension2` | 27 |
| `ExtendedDimension3` | 28 |
| `ExtendedDimension4` | 29 |
| `ExtendedDimension5` | 30 |
| `ExtendedDimension6` | 31 |
| `ExtendedDimension7` | 32 |
| `ExtendedDimension8` | 33 |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
