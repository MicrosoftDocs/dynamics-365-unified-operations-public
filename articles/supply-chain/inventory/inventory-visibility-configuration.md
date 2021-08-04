---
title: Inventory Visibility Configurations
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

Before you begin to work with Inventory Visibility, you must complete the following configurations, which are described in this topic:

- [Data Source Configuration](#data-source-configuration)
- [Partition Configuration](#partition-configuration)
- [Product Index Hierarchy Configuration](#index-configuration)
- [Reservation Configuration (optional)](#reservation-configuration)
- [Default Configuration Sample](#default-configuration-sample)

> [!NOTE]
> You can view and edit Inventory Visibility configurations in [Power Apps](./inventory-visibility-power-platform.md#configuration). After the configuration is complete, select the **Update Configuration** button in the app.

## <a name="data-source-configuration"></a>Data source configuration

The data source represents the system from which your data comes, such as `fno` or `pos`. (`fno` stands for Dynamics 365 Finance and Operations, `pos` stands for point of sale)

The data source configuration includes the following parts:

- Dimension (dimension mapping)
- Physical measure
- Calculated measure

> [!NOTE]
> Data source `fno` is reserved for Dynamics 365 Supply Chain Management.

### <a name="data-source-configuration-dimension"></a>Dimension (dimension mapping)

The purpose of the dimension configuration is to standardize the multi-system integration for posting events and queries based on dimension combinations.

Inventory Visibility supports the following list of general base dimensions:

| Dimension type | Base dimension |
| --- | --- |
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
| Inventory (custom) | `InventDimension1` ~ `InventDimension12` |
| Extension | `ExtendedDimension1` ~ `ExtendedDimension8` |

> [!NOTE]
> The dimension types listed in the table are for reference only. You don't need to define them in Inventory Visibility.

> [!NOTE]
> Inventory (custom) dimensions might be reserved for Dynamics 365 Supply Chain Management. In this case, you can use the extended dimensions instead.

External systems can access Inventory Visibility through its RESTful APIs. For the integration, Inventory Visibility enables you to configure the _external data source_ and the mapping from the _external dimensions_ to the _base dimensions_. Here is an example of a dimension mapping table:

| External dimension | Base dimension |
| --- | --- |
| `MyColorId` | `ColorId` |
| `MySizeId` | `SizeId` |
| `MyStyleId` | `StyleId` |
| `MyDimension1` | `ExtendedDimension1` |
| `MyDimension2` | `ExtendedDimension2` |

By configuring a dimension mapping, you can send the _external dimensions_ directly to Inventory Visibility, which will convert _external dimensions_ to _base dimensions_ automatically.

### Physical measures

Physical measures modify the quantity and reflect the inventory status. You can define your own physical measures based on your needs.

Inventory Visibility provides a list of default physical measures, which are linked to Dynamics 365 Supply Chain Management (data source `fno`). The following table provides an example of physical measures:

| Physical measure name | Description |
| --- | --- |
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

Calculated measures provide a customized computation formula that is made up of a combination of physical measures. This functionality lets you define a set of physical measures that will be added, and/or a set of physical measures that will be subtracted, in order to form the customized measurement.

For example, suppose you have the following query result:

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

Then you configure a calculated measure called `MyCustomAvailableforReservation` (to be consumed by the consumption system) as follows:

| Consumption system | Calculated measure | Data source | Physical measure | Calculation type |
| --- | --- | --- | --- | --- |
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `availphysical` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `orderedintotal` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `orderedreserved` | `Subtraction` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `pos` | `inbound` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `pos` | `outbound` | `Subtraction` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `received` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `scheduled` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `issued` | `Subtraction` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `reserved` | `Subtraction` |

With this computation formula, the new query result will include the customized measurement.

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

The `MyCustomAvailableforReservation` output is based on the calculation setting in the custom measurements as:  
 _100 + 50 + 80 + 90 + 30 – 10 – 20 – 60 – 40 = 220_

## <a name="partition-configuration"></a>Partition configuration

The partition configuration consists of a combination of base dimensions and defines the data distribution pattern. Data operations in the same partition support high performance and do not cost too much. Therefore, good partition patterns contribute significant benefits.

Inventory Visibility provides a default partition configuration as follows:

| Base Dimension | Hierarchy |
| --- | --- |
| `SiteId` | 1 |
| `LocationId` | 2 |

> [!NOTE]
> The default partition configuration is for reference only. You don't need to define it in Inventory Visibility. Currently, the partition configuration upgrade is not supported.

## <a name="index-configuration"></a>Product index hierarchy configuration

Most of the time, the inventory on-hand query will not only be at the highest "total" level, but you may also want to see results aggregated based on the inventory dimensions.

Inventory Visibility provides flexibility by allowing you to set up the _indexes_, which are based on a dimension or a combination of dimensions. An index consists of a *Set number*, *Dimension*, and *Hierarchy*, as defined in the following table.

| Name | Description |
| --- | --- |
| Set number | Dimensions belonging to the same set (index) will be grouped together and allocated with the same set number. |
| Dimension | Base dimensions that the query result is aggregated on. |
| Hierarchy | Hierarchy is used to define the supported dimension combinations that can be queried. For example, if you set up a dimension set with a hierarchy sequence of (`ColorId`, `SizeId`, `StyleId`), the system will support queries on 4 dimension combinations. The first combination is empty. The second combination is (`ColorId`). The third combination is (`ColorId`, `SizeId`). And the fourth combination is (`ColorId`, `SizeId`, `StyleId`). The other combinations are not supported. Please refer to the following example for details. |

### Example

This section provides an example of how the hierarchy works.

Suppose you have the following items in your inventory:

| Item | ColorId | SizeId | StyleId | Quantity |
| --- | --- | --- | --- | --- |
| T-shirt | Black | Small | Wide | 1 |
| T-shirt | Black | Small | Regular | 2 |
| T-shirt | Black | Large | Wide | 3 |
| T-shirt | Black | Large | Regular | 4 |
| T-shirt | Red | Small | Wide | 5 |
| T-shirt | Red | Small | Regular | 6 |
| T-shirt | Red | Large | Regular | 7 |

And suppose the index is as follows:

| Set Number | Dimension | Hierarchy |
| --- | --- | --- |
| 1 | `ColorId` | 1 |
| 1 | `SizeId` | 2 |
| 1 | `StyleId` | 3 |

The index enables you to query the on-hand inventory in the following ways:

- `()` - grouped by all
  - T-shirt, 28
- `(ColorId)` – grouped by `ColorId`
  - T-shirt, Black, 10
  - T-shirt, Red, 18
- `(ColorId, SizeId)` – grouped by the combination of `ColorId` and `SizeId`
  - T-shirt, Black, Small, 3
  - T-shirt, Black, Large, 7
  - T-shirt, Red, Small, 11
  - T-shirt, Red, Large, 7
- `(ColorId, SizeId, StyleId)` – grouped by the combination of `ColorId`, `SizeId` and `StyleId`
  - T-shirt, Black, Small, Wide, 1
  - T-shirt, Black, Small, Regular, 2
  - T-shirt, Black, Large, Wide, 3
  - T-shirt, Black, Large, Regular, 4
  - T-shirt, Red, Small, Wide, 5
  - T-shirt, Red, Small, Regular, 6
  - T-shirt, Red, Large, Regular, 7

> [!NOTE]
> Base dimensions defined in the partition configuration shouldn't be defined in index configurations.

## <a name="reservation-configuration"></a>Reservation configuration

Reservation configuration is necessary if you want to use the soft reservation feature. It is made up of two fundamental parts:

- Soft reservation mapping
- Soft reservation hierarchy

### Soft reservation mapping

When you make a reservation, you may want to know if on-hand inventory is currently available for reservation. This validation is linked to a calculated measure that represents a computation formula of a combination of physical measures.

Suppose a reservation measure is based on the physical measure `SoftReservOrdered` from data source `iv`. You could then set up the calculated measure `AvailableToReserve` of `iv` as follows:

| Calculation type | Data source | Physical measure |
| --- | --- | --- |
| Addition | `fno` | `AvailPhysical` |
| Addition | `pos` | `Inbound` |
| Subtraction | `pos` | `Outbound` |
| Subtraction | `iv` | `SoftReservOrdered` |

Then set up a soft reservation mapping from `SoftReservOrdered` to `AvailableToReserve`:

| Physical Measure Data Source | Physical Measure | Available for Reservation Data Source | Available for Reservation Calculated Measure |
| --- | --- | --- | --- |
| `iv` | `SoftReservOrdered` | `iv` | `AvailableToReserve` |

This soft reservation mapping provides a mapping from the reservation measure `SoftReservOrdered` to a calculated measure `AvailableToReserve`. When you do reservation on `SoftReservOrdered`, Inventory Visibility will automatically find `AvailableToReserve` and its related computation formula to do the reservation validation.

Suppose you have on-hand inventory in Inventory Visibility as follows:

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

In the sample, the following calculation applies:

`AvailableToReserve` = `fno.availphysical` + `pos.inbound` – `pos.outbound` – `iv.SoftReservOrdered`  
= 70 + 50 – 20 – 90  
= 10

Therefore, if you make reservations on `iv.SoftReservOrdered` with a quantity less than or equal to `AvailableToReserve` (10), you are allowed to do the reservation.

### Soft reservation hierarchy

The reservation hierarchy describes the sequence of dimensions that must be specified when making reservations. It works the same way as the product index hierarchy works for on-hand queries.

Reservation hierarchy is independent from product index hierarchy. This allows category management where users break down the dimensions into details to specify the requirements for making precise reservations.

Here is an example of a soft reservation hierarchy:

| Base dimension | Hierarchy |
| --- | --- |
| `SiteId` | 1 |
| `LocationId` | 2 |
| `ColorId` | 3 |
| `SizeId` | 4 |
| `StyleId` | 5 |

In this example, you can do reservation in the following dimension sequences:

- `()` - no dimension specified.
- `(SiteId)`
- `(SiteId, LocationId)`
- `(SiteId, LocationId, ColorId)`
- `(SiteId, LocationId, ColorId, SizeId)`
- `(SiteId, LocationId, ColorId, SizeId, StyleId)`

A valid dimension sequence should strictly follow the reservation hierarchy one-by-one. For example, the hierarchy sequence `(SiteId, LocationId, SizeId)` isn't valid, because `ColorId` is missing.

## <a name="default-configuration-sample"></a>The default configuration

Inventory Visibility sets up a default configuration during its initialization stage. You can modify the configuration as needed.

### Data source configuration

#### Data source _iv_ configuration

This section describes how the data source `iv` (Inventory Visibility) is configured.

##### Physical measures configured for the _iv_ data source

The following physical measures are configured for the `iv` data source:

- `Ordered`
- `SoftReservPhysical`
- `SoftReservOrdered`
- `ReservOrdered`
- `ReservPhysical`

##### Calculated measure _OrderedTotal_

The calculated measure `OrderedTotal` is configured for the `iv` data source as shown in the following table.
  
| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `Ordered` |
| Addition | `fno` | `Arrived` |
| Addition | `iv` | `Ordered` |

##### Calculated measure _OnHand_

The calculated measure `OnHand` is configured for the `iv` data source as shown in the following table.
  
| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `PhysicalInvent` |
| Addition | `iom` | `OnHand` |
| Addition | `sap` | `Unrestricted` |
| Addition | `sap` | `QualityInspection` |
| Addition | `pos` | `PosInbound` |
| Subtraction | `pos` | `PosOutbound` |

##### Calculated measure _ReservedTotal_

The calculated measure `ReservedTotal` is configured for the `iv` data source as shown in the following table.
  
| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `ReservPhysical` |
| Addition | `fno` | `ReservOrdered` |
| Addition | `iv` | `SoftReservPhysical` |
| Addition | `iv` | `SoftReservOrdered` |
| Addition | `iv` | `ReservPhysical` |
| Addition | `iv` | `ReservOrdered` |

##### Calculated measure _SoftReserved_

The calculated measure `SoftReserved` is configured for the `iv` data source as shown in the following table.
  
| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `iv` | `SoftReservPhysical` |
| Addition | `iv` | `SoftReservOrdered` |

##### Calculated measure _HardReserved_

The calculated measure `HardReserved` is configured for the `iv` data source as shown in the following table.
  
| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `ReservPhysical` |
| Addition | `fno` | `ReservOrdered` |
| Addition | `iv` | `ReservPhysical` |
| Addition | `iv` | `ReservOrdered` |

##### Calculated measure _OpenOrder_

The calculated measure `OpenOrder` is configured for the `iv` data source as shown in the following table.
  
| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `OnOrder` |
| Addition | `iom` | `OnOrder` |

##### Calculated measure _OnHandAvailable_

The calculated measure `OnHandAvailable` is configured for the `iv` data source as shown in the following table.
  
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

##### Calculated measure _AvailableToReserve_

The calculated measure `AvailableToReserve` is configured for the `iv` data source as shown in the following table.
  
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

##### Calculated measure _InventorySupply_

The calculated measure `InventorySupply` is configured for the `iv` data source as shown in the following table.
  
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

##### Calculated measure _InventoryDemand_

The calculated measure `InventoryDemand` is configured for the `iv` data source as shown in the following table.
  
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

#### Data source _fno_ configuration

This section describes how the data source `fno` (Dynamics 365 Supply Chain Management) is configured.

##### Dimension mappings for the _fno_ data source

The dimension mappings listed in the following table are configured for the `fno` data source.

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

##### Physical measures configured for the _fno_ data source

The following physical measures are configured for the `fno` data source:

- `Ordered`
- `Arrived`
- `AvailPhysical`
- `PhysicalInvent`
- `ReservPhysical`
- `ReservOrdered`
- `OnOrder`

#### Data source _pos_ configuration

This section describes how the data source `pos` (point of sale) is configured.

##### Physical measures for the _pos_ data source

The following physical measures are configured for the `pos` data source:

- `PosInbound`
- `PosOutbound`

##### Calculated measure for the _pos_ data source

The calculated measure shown in the following table is configured for the `pos` data source. <!-- KFM: Are we missing a name for this calculated measure? -->

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | `fno` | `AvailPhysical` |
| Addition | `pos` | `PosInbound` |
| Subtraction | `pos` | `PosOutbound` |

#### Data source _iom_ configuration

The following physical measures are configured for the `iom` (intelligent order management) data source:

- `OnOrder`
- `OnHand`

#### Data source _sap_ configuration

The following physical measures are configured for the `sap` data source: <!-- KFM: Can we tell what `sap` stands for? -->

- `Unrestricted`
- `QualityInspection`

### Partition configuration

The following table shows the default partition configuration:

| Base dimension | Hierarchy |
| --- | --- |
| `SiteId` | 1 |
| `LocationId` | 2 |

### Index configuration

The following table shows the default index configuration:

| Set Number | Dimension | Hierarchy |
| --- | --- | --- |
| 1 | `ColorId` | 1 |
| 1 | `SizeId` | 2 |
| 1 | `StyleId` | 3 |

### Reservation configuration

This section describes the default reservation configuration.

#### Reservation mapping

The following table shows the default reservation mapping:

| Physical measure data source | Physical measure | Available for reservation data source | Available for reservation calculated measure |
| --- | --- | --- | --- |
| `iv` | `SoftReservOrdered` | `iv` | `AvailableToReserve` |

#### Reservation hierarchy

The following table shows the default reservation hierarchy:

| Base dimension | Hierarchy |
| --- | --- |
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