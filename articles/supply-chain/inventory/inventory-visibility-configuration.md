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

## <a id="introduction"></a>Introduction

Before playing around with the Inventory Visibility, you should complete the configurations following the listed sections:

- [Data Source Configuration](#data-source-configuration)
- [Partition Configuration](#partition-configuration)
- [Product Index Hierarchy Configuration](#index-configuration)
- [Reservation Configuration (optional)](#reservation-configuration)
- [Default Configuration Sample](#default-configuration-sample)

> [!NOTE]
> You can view and edit the Inventory Visibility Configurations in [Power Apps](./inventory-visibility-power-platform.md#configuration). After the editing is complete, select the **Update Configuration** button in the app.

## <a id="data-source-configuration"></a>Data source configuration

Data Source represents the system from which your data comes, such as _fno_ and _pos_. (_fno_ stands for Dynamics 365 Finance and Operations, _pos_ stands for point of sale)

The Data Source Configuration includes the following parts:

- Dimension (Dimension Mapping)
- Physical Measure
- Calculated Measure

> [!NOTE]
> Data source _fno_ is reserved for Dynamics 365 Supply Chain Management.

### <a id="data-source-configuration-dimension"></a>Dimension (dimension mapping)

The purpose of dimension configuration is to standardize the multi-system integration for the event posting and query based on dimension combinations.

The Inventory Visibility provides a list of general base dimensions:

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
| Inventory Status | `StatusId` |
| Warehouse Specific | `WMSLocationId` |
| Warehouse Specific | `WMSPalletId` |
| Warehouse Specific | `LicensePlateId` |
| Others | `VersionId` |
| Inventory (Custom) | InventDimension1 ~ InventDimension12 |
| Extension | ExtendedDimension1 ~ ExtendedDimension8 |

> [!NOTE]
> The dimension types listed in the table are for reference only. You don't need to define them in the Inventory Visibility.

> [!NOTE]
> Inventory (Custom) dimensions might be reserved for Dynamics 365 Suppply Chain Management usage. In this case, you can use extended dimensions instead.

External systems can access the Inventory Visibility through RESTful APIs. For the integration, the Inventory Visibility enables you to configure the _external data source_ and the mapping from the _external dimensions_ to the _base dimensions_. Here is an example of dimension mapping table:

| External Dimension | Base Dimension |
| --- | --- |
| `MyColorId` | `ColorId` |
| `MySizeId` | `SizeId` |
| `MyStyleId` | `StyleId` |
| `MyDimension1` | `ExtendedDimension1` |
| `MyDimension2` | `ExtendedDimension2` |

By configuring a dimension mapping, you can send the _external dimensions_ directly to the Inventory Visibility which will convert _external dimensions_ to _base dimensions_ automatically.

### Physical measure

Physical Measure modifies the quantity and reflects the inventory status. You can define your own physical measures based on your needs.

The Inventory Visibility provides a list of default physical measures which are linked to Dynamics 365 Finance and Operations (data source _fno_). Here is an example of physical measures:

| Physical Measure Name | Description |
| --- | --- |
| `NotSpecified` | Not Specified |
| `Arrived` | Arrived |
| `AvailOrdered` | Available Ordered |
| `AvailPhysical` | Available Physical |
| `Deducted` | Deducted |
| `OnOrder` | OnOrder |
| `Ordered` | Ordered |
| `PhysicalInvent` | Physical Inventory |
| `Picked` | Picked |
| `PostedQty` | Posted Quantity |
| `QuotationIssue` | Quotation Issue |
| `QuotationReceipt` | Quotation Receipt |
| `Received` | Received |
| `Registered` | Registered |
| `ReservOrdered` | Ordered Reserved |
| `ReservPhysical` | Physical Reserved |

### <a id="data-source-configuration-calculated-measure"></a>Calculated measure

Calculated Measure provides the customized computation formula which is made up of a combination of physical measures. This functionality simply allows you to define a set of physical measures that will be added, and/or a set of physical measures that will be subtracted, in order to form the customized measurement.

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

Then you configure the calculated measure as `MyCustomAvailableforReservation` to be consumed by the consumption system:

| Consumption system | Calculated Measure | Data Source | Physical Measure | Calculation Type |
| --- | --- | --- | --- | --- |
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `availphysical` | Addition |
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `orderedintotal` | Addition |
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `orderedreserved` | Subtraction |
| `CustomChannel` | `MyCustomAvailableforReservation` | `pos` | `inbound` | Addition |
| `CustomChannel` | `MyCustomAvailableforReservation` | `pos` | `outbound` | Subtraction |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `received` | Addition |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `scheduled` | Addition |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `issued` | Subtraction |
| `CustomChannel` | `MyCustomAvailableforReservation` | `externalchannel` | `reserved` | Subtraction |

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
 _100 + 50 + 80 + 90 + 30 &ndash; 10 &ndash; 20 &ndash; 60 &ndash; 40 = 220_

## <a id="partition-configuration"></a>Partition configuration

Partition Configuration consists of a combination of base dimensions and defines the data distribution pattern. Data operations in the same partition support high performance and do not cost too much. Therefore, good partition patterns contribute much benefits.

The Inventory Visibility provides a default partition configuration as follows:

| Base Dimension | Hierarchy |
| --- | --- |
| `SiteId` | 1 |
| `LocationId` | 2 |

> [!NOTE]
> The default partition configuration is for reference only. You don't need to define it in the Inventory Visibility. Currently, the partition configuration upgrade is not supported.

## <a id="index-configuration"></a>Product index hierarchy configuration

Most of the time, the inventory on-hand query will not only be at the highest "total" level, but you may want to see results aggregated based on the inventory dimensions.

The Inventory Visibility provides flexibility by allowing you to set up the _indexes_, which are based on the dimension or the combination of the dimensions. An _Index_ consists of Set Number, Dimension and Hierarchy. Here are the definitions:

| Name | Description |
| --- | --- |
| Set Number | Dimensions belonging to the same set (index) will be grouped together and allocated with the same set number. |
| Dimension | Base dimension that you want the query result is aggregated on. |
| Hierarchy | Hierarchy is used to define the supported dimension combinations that can be queried. For example, if you set up a dimension set with a hierarchy sequence of (_ColorId_, _SizeId_, _StyleId_), the system will support queries on 4 dimension combinations. The first combination is empty. The second combination is (_ColorId_). The third combination is (_ColorId_, _SizeId_). And the fourth combination is (_ColorId_, _SizeId_, _StyleId_). The other combinations are not supported. Please refer to the below example for details. |

Here is an example of how the hierarchy works. Below is a list of inventories.

| Item | ColorId | SizeId | StyleId | Quantity |
| --- | --- | --- | --- | --- |
| T-shirt | Black | Small | Wide | 1 |
| T-shirt | Black | Small | Regular | 2 |
| T-shirt | Black | Large | Wide | 3 |
| T-shirt | Black | Large | Regular | 4 |
| T-shirt | Red | Small | Wide | 5 |
| T-shirt | Red | Small | Regular | 6 |
| T-shirt | Red | Large | Regular | 7 |

Suppose the index is as follows:

| Set Number | Dimension | Hierarchy |
| --- | --- | --- |
| 1 | `ColorId` | 1 |
| 1 | `SizeId` | 2 |
| 1 | `StyleId` | 3 |

The index enables you to query the inventory on-hand in below ways:

- () - grouped by all
  - T-shirt, 28
- (_ColorId_) – grouped by _ColorId_
  - T-shirt, Black, 10
  - T-shirt, Red, 18
- (_ColorId_, _SizeId_) – grouped by the combination of _ColorId_ and _SizeId_
  - T-shirt, Black, Small, 3
  - T-shirt, Black, Large, 7
  - T-shirt, Red, Small, 11
  - T-shirt, Red, Large, 7
- (_ColorId_, _SizeId_, _StyleId_)- grouped by the combination of _ColorId_, _SizeId_ and _StyleId_
  - T-shirt, Black, Small, Wide, 1
  - T-shirt, Black, Small, Regular, 2
  - T-shirt, Black, Large, Wide, 3
  - T-shirt, Black, Large, Regular, 4
  - T-shirt, Red, Small, Wide, 5
  - T-shirt, Red, Small, Regular, 6
  - T-shirt, Red, Large, Regular, 7

> [!NOTE]
> Base dimensions defined in partition configuration should not be defined in index configurations.

## <a id="reservation-configuration"></a>Reservation configuration

Reservation Configuration is necessary if you want to experience the Soft Reservation feature. Basically, it contains 2 parts:

- Soft Reservation Mapping
- Soft Reservation Hierarchy

### Soft Reservation Mapping

When you do reservation, you may want to know if the current inventory on-hand is available for reservation. This validation is linked to a calculated measure which represents a computation formula of a combination of physical measures.

Suppose _SoftReservOrdered_ (physical measure) of _iv_ (data source) is the reservation measure. Afterwards, define a calculated measure _AvailableToReserve_ of _iv_ as follows:

| Calculation type | Data source | Physical measure |
| --- | --- | --- |
| Addition | `fno` | `AvailPhysical` |
| Addition | `pos` | `Inbound` |
| Subtraction | `pos` | `Outbound` |
| Subtraction | `iv` | `SoftReservOrdered` |

Then set up a soft reservation mapping from _SoftReservOrdered_ to _AvailableToReserve_:

| Physical Measure Data Source | Physical Measure | Available for Reservation Data Source | Available for Reservation Calculated Measure |
| --- | --- | --- | --- |
| `iv` | `SoftReservOrdered` | `iv` | `AvailableToReserve` |

This soft reservation mapping provides a mapping from the reservation measure _SoftReservOrdered_ to a calculated measure _AvailableToReserve_. When you do reservation on _SoftReservOrdered_, the Inventory Visibility will automatically find _AvailableToReserve_ and its related computation formula to do the reservation validation.

Suppose you have some on-hand in Inventory Visibility as follows:

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

In the sample, the _AvailableToReserve_ is _fno.availphysical_ + _pos.inbound_ - _pos.outbound_ - _iv.SoftReservOrdered_ (70 + 50 - 20 - 90 = 10). If you make reservations on _iv.SoftReservOrdered_ with quantity less than or equal to _AvailableToReserve_ (10), you are allowed to do the reservation.

### Soft Reservation Hierarchy

Reservation hierarchy describes the sequence of dimensions to specify when making reservations. It works the same way as product index hierarchy works for on-hand queries.

Reservation hierarchy is independent from product index hierarchy. This allows category management where users break down the dimensions into details to specify the needs for making more precise reservations.

Here is an example of Soft Reservation Hierarchy:

| Base Dimension | Hierarchy |
| --- | --- |
| `SiteId` | 1 |
| `LocationId` | 2 |
| `ColorId` | 3 |
| `SizeId` | 4 |
| `StyleId` | 5 |

In this sample, you can do reservation in the following dimension sequences:

- () - no dimension specified.
- (SiteId)
- (SiteId, LocationId)
- (SiteId, LocationId, ColorId)
- (SiteId, LocationId, ColorId, SizeId)
- (SiteId, LocationId, ColorId, SizeId, StyleId)

A valid dimension sequence should strictly follow the reservation hierarchy one by one. E.g., (SiteId, LocationId, SizeId) is invalid, because _ColorId_ is missing in the hierarchy sequence.

## <a id="default-configuration-sample"></a>Default Configuration Sample

The Inventory Visibility will set up a default configuration in initialization stage. You may modifiy the configuration and do the upgrade based on your needs.

### Data Source Configuration

Data Source _iv_ (Inventory Visibility):

- Physical Measure
  - _Ordered_
  - _SoftReservPhysical_
  - _SoftReservOrdered_
  - _ReservOrdered_
  - _ReservPhysical_
- Calculated Measure
  - _OrderedTotal_
  
 | Calculation Type | Data Source | Physical Measure |
 |---|---|---|
 | Addition | `fno` | `Ordered` |
 | Addition | `fno` | `Arrived` |
 | Addition | `iv` | `Ordered` |

  - _OnHand_
  
 | Calculation Type | Data Source | Physical Measure |
 |---|---|---|
 | Addition | `fno` | `PhysicalInvent` |
 | Addition | `iom` | `OnHand` |
 | Addition | `sap` | `Unrestricted` |
 | Addition | `sap` | `QualityInspection` |
 | Addition | `pos` | `PosInbound` |
 | Subtraction | `pos` | `PosOutbound` |

  - _ReservedTotal_
  
 | Calculation Type | Data Source | Physical Measure |
 |---|---|---|
 | Addition | `fno` | `ReservPhysical` |
 | Addition | `fno` | `ReservOrdered` |
 | Addition | `iv` | `SoftReservPhysical` |
 | Addition | `iv` | `SoftReservOrdered` |
 | Addition | `iv` | `ReservPhysical` |
 | Addition | `iv` | `ReservOrdered` |

  - _SoftReserved_
  
 | Calculation Type | Data Source | Physical Measure |
 |---|---|---|
 | Addition | `iv` | `SoftReservPhysical` |
 | Addition | `iv` | `SoftReservOrdered` |

  - _HardReserved_
  
 | Calculation Type | Data Source | Physical Measure |
 |---|---|---|
 | Addition | `fno` | `ReservPhysical` |
 | Addition | `fno` | `ReservOrdered` |
 | Addition | `iv` | `ReservPhysical` |
 | Addition | `iv` | `ReservOrdered` |

  - _OpenOrder_
  
 | Calculation Type | Data Source | Physical Measure |
 |---|---|---|
 | Addition | `fno` | `OnOrder` |
 | Addition | `iom` | `OnOrder` |

  - _OnHandAvailable_
  
 | Calculation Type | Data Source | Physical Measure |
 |---|---|---|
 | Addition | `fno` | `PhysicalInvent` |
 | Addition | `iom` | `OnHand` |
 | Addition | `sap` | `Unrestricted` |
 | Addition | `sap` | `QualityInspection` |
 | Addition | `pos` | `PosInbound` |
 | Subtraction | `fno` | `ReservPhysical` |
 | Subtraction | `iv` | `SoftReservPhysical` |
 | Subtraction | `pos` | `PosOutbound` |

  - _AvailableToReserve_
  
 | Calculation Type | Data Source | Physical Measure |
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

  - _InventorySupply_
  
 | Calculation Type | Data Source | Physical Measure |
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

  - _InventoryDemand_
  
 | Calculation Type | Data Source | Physical Measure |
 |---|---|---|
 | Addition | `fno` | `OnOrder` |
 | Addition | `iom` | `OnOrder` |
 | Addition | `iv` | `SoftReservPhysical` |
 | Addition | `iv` | `SoftReservOrdered` |
 | Addition | `fno` | `ReservPhysical` |
 | Addition | `fno` | `ReservOrdered` |
 | Addition | `iv` | `ReservPhysical` |
 | Addition | `iv` | `ReservOrdered` |

Data Source _fno_ (Dynamics 365 Finance and Operations):

- Dimension Mapping

 | External Dimension | Base Dimension |
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

- Physical Measure
  - _Ordered_
  - _Arrived_
  - _AvailPhysical_
  - _PhysicalInvent_
  - _ReservPhysical_
  - _ReservOrdered_
  - _OnOrder_

Data Source _pos_ (Point of Sale):

- Physical Measure
  - _PosInbound_
  - _PosOutbound_
- Calculated Measure

 | Calculation Type | Data Source | Physical Measure |
 |---|---|---|
 | Addition | `fno` | `AvailPhysical` |
 | Addition | `pos` | `PosInbound` |
 | Subtraction | `pos` | `PosOutbound` |

Data Source _iom_ (Intelligent Order Management):

- Physical Measure
  - _OnOrder_
  - _OnHand_

Data Source _sap_:

- Physical Measure
  - _Unrestricted_
  - _QualityInspection_

### Partition Configuration

| Base Dimension | Hierarchy |
| --- | --- |
| `SiteId` | 1 |
| `LocationId` | 2 |

### Index Configuration

| Set Number | Dimension | Hierarchy |
| --- | --- | --- |
| 1 | `ColorId` | 1 |
| 1 | `SizeId` | 2 |
| 1 | `StyleId` | 3 |

### Reservation Configuration

Reservation Mapping:

| Physical Measure Data Source | Physical Measure | Available for Reservation Data Source | Available for Reservation Calculated Measure |
| --- | --- | --- | --- |
| `iv` | `SoftReservOrdered` | `iv` | `AvailableToReserve` |

Reservation Hierarchy:

| Base Dimension | Hierarchy |
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