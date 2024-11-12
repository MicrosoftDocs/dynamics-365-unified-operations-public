---
title: Voyage creation entities
description: Learn about voyage creation data entities, which group the data entities that are required to create a working voyage with a table providing mappings for names.
author: lisascholz91
ms.author: lisascholz
ms.topic: article
ms.date: 05/27/2022
ms.reviewer: kamaybac
ms.search.form:
---

# Voyage creation entities

[!include [banner](../includes/banner.md)]

The voyage creation data entities group together the data entities that are required to create a working voyage. You or your freight forwarder can use these data entities to create voyage, shipping container, folio, and voyage line records that reference existing purchaser order or transfer order lines.

## Voyages (ITMTableEntity)

The voyage represents the journey of inbound goods and serves as the highest-level cost area in Landed cost. It contains header-level information that is related to the vessel, port of origin, and destination port. This functionality is supported by the `ITMTableEntity` entity. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Mode of delivery | ITMTable.DlvModeId | Nvarchar(10) | No | No |
| Broker advised | ITMTable.ITMBrokerAdvised | Datetime | No | No |
| Customer appointment | ITMTable.ITMCustomerAppointment | Datetime | No | No |
| Delivered at warehouse | ITMTable.ITMDelAtWarehouse | Datetime | No | No |
| Delivery instructions | ITMTable.ITMDeliveryInstructions | Datetime | No | No |
| Departure date | ITMTable.ITMDepartureDate | Datetime | No | No |
| Goods released | ITMTable.ITMGoodsReleased | Datetime | No | No |
| Local transport date | ITMTable.ITMLocalTransportDate | Datetime | No | No |
| Local transport time | ITMTable.ITMLocalTransportTime | Int | No | No |
| Original bill of landing sent | ITMTable.ITMOriginalBOLSebt | Datetime | No | No |
| Original documents received | ITMTable.ITMOriginalDocsReceived | Datetime | No | No |
| Purchase order status | ITMTable.ITMPurchStatus | Int | No | No |
| Verification date | ITMTable.ITMVerificationDate | Datetime | No | No |
| Customs entry identifier | ITMTable.ShipCustomsEntryId | Nvarchar(20) | No | No |
| Ship date | ITMTable.ShipDate | Datetime | No | No |
| Description | ITMTable.ShipDescription | Nvarchar(60) | No | No |
| Documents received | ITMTable.ShipDocReceived | Int | No | No |
| Estimated delivery date | ITMTable.ShipEstDlvDate | Datetime | No | No |
| ETA at shipping port | ITMTable.ShipEstPortDate | Datetime | No | No |
| From port | ITMTable.ShipFromPort | Nvarchar(20) | No | No |
| House air way/Bill of lading | ITMTable.ShipHAWB | Nvarchar(20) | No | No |
| Voyage | ITMTable.ShipId | Nvarchar(20) | **Yes** | **Yes** |
| Booking reference | ITMTable.ShipIdExternal | Nvarchar(20) | No | No |
| Journey template | ITMTable.ShipJourneyId | Nvarchar(20) | No | No |
| Local forwarder | ITMTable.ShipLocalForwarder | Nvarchar(20) | No | No |
| Master air way/Bill of lading | ITMTable.ShipMAWB | Nvarchar(20) | No | No |
| Measurement | ITMTable.ShipMeasurement | Numeric(32, 6) | No | No |
| Measurement unit | ITMTable.ShipMeasurementUnit | Int | No | No |
| Number of pallets | ITMTable.ShipNoOfPallets | Int | No | No |
| Pending voyage | ITMTable.ShipPending | Int | No | No |
| Remarks | ITMTable.ShipRemarks | Nvarchar(MAX) | No | No |
| Rental | ITMTable.ShipRental | Int | No | No |
| Voyage status | ITMTable.ShipStatusId | Nvarchar(20) | No | No |
| Tally in number | ITMTable.ShipTallyInNumber | Nvarchar(20) | No | No |
| To port | ITMTable.ShipToPort | Nvarchar(20) | No | No |
| Valuation date | ITMTable.ShipValuationDate | Datetime | No | No |
| Shipping company | ITMTable.ShipVendAccount | Nvarchar(20) | No | No |
| Vessel | ITMTable.ShipVesselId | Nvarchar(20) | No | **Yes** |
| External voyage ID | ITMTable.ShipVoyage | Nvarchar(20) | No | No |

### Number sequences for voyages

The shared number sequence for voyages controls the allocation of voyage IDs.

The value that is passed to the data entity as the **Voyage ID** (`ShipId`) value is used to identify an existing record for update. If that record doesn't exist, the behavior depends on whether the assigned number sequence is configured to allow for manual entry:

- If manual entry is enabled, a new record is created that uses the passed value.
- If manual entry isn't enabled, the next number in the assigned number sequence is used instead of the passed value.

During the import session, the placeholder value that is imported as the voyage ID is retained. This behavior ensures that shipping container and voyage lines that reference the placeholder are included in the voyage, and that they are updated to reflect the value that is assigned from the number sequence.

### Automatic cost transactions

Automatic costs can be added to a voyage from the **Auto costs** page in Microsoft Dynamics 365 Supply Chain Management (**Landed cost \> Costing setup \> Auto costs**). Records for automatic costs can also be created by using cost transaction data entities for each cost area that Landed cost supports.

Automatic costs that are configured in Supply Chain Management are applied to the voyage when a voyage line is created. No costs will be visible against the record until the header record is associated with line information.

## Shipping containers (ITMContainersEntity)

A shipping container represents a physical container that goods are transported in. This physical container might be a freight container for ocean freight or a single pallet for air freight. The shipping container includes header-level information that is related to the shipping container ID, seal number, and shipping container type. (The shipping container type provides dimension information.) This functionality is supported by the `ITMContainersEntity` entity. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Departure date | ITMContainers.ITMDepartureDate | Datetime | No | No |
| Local transport date | ITMContainers.ITMLocalTransportDate | Datetime | No | No |
| Local transport time | ITMContainers.ITMLocalTransportTime | Int | No | No |
| Original voyage | ITMContainers.OrigShipId | Nvarchar(20) | No | No |
| Actual weight | ITMContainers.ShipActualWeight | Numeric(32, 6) | No | No |
| Broker advised | ITMContainers.ShipBrokerAdvised | Datetime | No | No |
| Shipping container | ITMContainers.ShipContainerId | Nvarchar(20) | **Yes** | **Yes** |
| Shipping container type | ITMContainers.ShipContainerTypeId | Nvarchar(20) | No | No |
| Unit type | ITMContainers.ShipContainerUnitTypeId | Nvarchar(10) | No | No |
| Converted to rental | ITMContainers.ShipConvertedToRental | Int | No | No |
| Customer appointment | ITMContainers.ShipCustomerAppointment | Datetime | No | No |
| Ship date | ITMContainers.ShipDate | Datetime | No | No |
| Delivered at warehouse | ITMContainers.ShipDelAtWarehouse | Datetime | No | No |
| Delivery instructions | ITMContainers.ShipDeliveryInstructions | Datetime | No | No |
| Examination certificate applied date | ITMContainers.ShipECAppliedDate | Datetime | No | No |
| Examination certificate expiry date | ITMContainers.ShipECExpiryDate | Datetime | No | No |
| Examination certificate number | ITMContainers.ShipECNum | Nvarchar(20) | No | No |
| Examination certificate received date | ITMContainers.ShipECReceivedDate | Datetime | No | No |
| Estimated delivery date | ITMContainers.ShipEstDlvDate | Datetime | No | No |
| ETA at shipping port | ITMContainers.ShipEstPortDate | Datetime | No | No |
| Expected loading date | ITMContainers.ShipExpectedLoadingDate | Datetime | No | No |
| From port | ITMContainers.ShipFromPort | Nvarchar(20) | No | No |
| Description of goods | ITMContainers.ShipGoodsDesc | Nvarchar(60) | No | No |
| Goods released | ITMContainers.ShipGoodsReleased | Datetime | No | No |
| GPS tracker unit | ITMContainers.ShipGPSUnit | Nvarchar(30) | No | No |
| House air way/Bill of lading | ITMContainers.ShipHAWB | Nvarchar(20) | No | No |
| Voyage | ITMContainers.ShipId | Nvarchar(20) | **Yes** | **Yes** |
| Journey template | ITMContainers.ShipJourneyId | Nvarchar(20) | No | No |
| Local forwarder | ITMContainers.ShipLocalForwarder | Nvarchar(20) | No | No |
| Measurement | ITMContainers.ShipMeasurement | Numeric(32, 6) | No | No |
| Measurement unit | ITMContainers.ShipMeasurementUnit | Int | No | No |
| Number of cartons | ITMContainers.ShipNoOfCartons | Numeric(32, 6) | No | No |
| Original bill of landing sent | ITMContainers.ShipOriginalBOLSebt | Datetime | No | No |
| Original documents received | ITMContainers.ShipOriginalDocsReceived | Datetime | No | No |
| Our seal number | ITMContainers.ShipOurSealNum | Nvarchar(20) | No | No |
| Used | ITMContainers.ShipPendingUsed | Int | No | No |
| Purchase order status | ITMContainers.ShipPurchStatus | Int | No | No |
| Refrigeration type | ITMContainers.ShipRefrigerationTypeId | Nvarchar(10) | No | No |
| Remarks | ITMContainers.ShipRemarks | Nvarchar(MAX) | No | No |
| Rental | ITMContainers.ShipRental | Int | No | No |
| Returnable | ITMContainers.ShipReturnable | Int | No | No |
| Voyage status | ITMContainers.ShipStatusId | Nvarchar(20) | No | No |
| Shipping company seal number | ITMContainers.ShipTheirSealNum | Nvarchar(20) | No | No |
| To port | ITMContainers.ShipToPort | Nvarchar(20) | No | No |
| Verification date | ITMContainers.ShipVerificationDate | Datetime | No | No |
| Vessel | ITMContainers.ShipVesselId | Nvarchar(20) | No | **Yes** |

### Voyage ID validation

The shipping container ID isn't controlled by a number sequence. It's unique only in the context of the voyage that it's used on.

If the shipping container entity (`ITMContainersEntity`) is used independently of the voyage entity (`ITMTableEntity`), the **Voyage ID** (`ShipId`) value must match an existing record in the voyage table. Otherwise, the import will fail.

If the shipping container entity (`ITMContainersEntity`) and the voyage entity (`ITMTableEntity`) are used as part of the same import session, the voyage entity must precede the creation of a shipping container. Otherwise, the **Voyage ID** (`ShipId`) value can't be successfully validated. If a placeholder value is used for the **Voyage ID** (`ShipId`) value, the association can be created only if the same placeholder is used as the **Voyage ID** (`ShipId`) value in the shipping container entity.

### Other field validations

The following table shows the fields in the shipping container table (`ITMContainers`) that are validated against Landed cost setup tables. It also shows the Landed cost data entities that a freight forwarder can use to read the existing values and ensure that valid values are received in your environment.

| Field in the ITMContainers table | Landed cost data entity |
|---|---|
| Shipping container type | ITMShippingContainerTypeEntity |
| Description of goods | ITMGoodsDescriptionEntity |
| Refrigeration type | ITMShippingContainerRefrigerationTypeEntity |

## Folios (ITMFolioEntity)

A folio represents a grouping of items in a shipping container for the purposes of customs declarations. The folio includes header-level information that is related to the customs broker and a description of the goods. This functionality is supported by the `ITMFolioEntity` entity. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Broker advised | ITMFolioTable.ShipBrokerAdvised | Datetime | No | No |
| Cargo control number | ITMFolioTable.ShipCargoControlNumber | Nvarchar(20) | No | No |
| Customer appointment | ITMFolioTable.ShipCustomerAppointment | Datetime | No | No |
| Customs broker | ITMFolioTable.ShipCustomsBroker | Nvarchar(20) | No | No |
| Customs ID | ITMFolioTable.ShipCustomsId | Nvarchar(60) | No | No |
| Company | ITMFolioTable.ShipDataArea | Nvarchar(4) | No | **Yes** |
| Delivered at warehouse | ITMFolioTable.ShipDelAtWarehouse | Datetime | No | No |
| Delivery instructions | ITMFolioTable.ShipDeliveryInstructions | Datetime | No | No |
| Documents received | ITMFolioTable.ShipDocReceived | Int | No | No |
| Estimated delivery date | ITMFolioTable.ShipEstDlvDate | Datetime | No | No |
| ETA at shipping port | ITMFolioTable.ShipEstPortDate | Datetime | No | No |
| Exporter | ITMFolioTable.ShipExporterId | Nvarchar(20) | No | No |
| Name | ITMFolioTable.ShipExporterName | Nvarchar(60) | No | No |
| Folio date | ITMFolioTable.ShipFolioDate | Datetime | No | No |
| Folio | ITMFolioTable.ShipFolioId | Nvarchar(20) | **Yes** | **Yes** |
| From port | ITMFolioTable.ShipFromPort | Nvarchar(20) | No | No |
| Description of goods | ITMFolioTable.ShipGoodsDesc | Nvarchar(60) | No | No |
| Goods released | ITMFolioTable.ShipGoodsReleased | Datetime | No | No |
| House air way/Bill of lading | ITMFolioTable.ShipHAWB | Nvarchar(20) | No | No |
| Voyage | ITMFolioTable.ShipId | Nvarchar(20) | No | **Yes** |
| Measurement | ITMFolioTable.ShipMeasurement | Numeric(32, 6) | No | No |
| Measurement unit | ITMFolioTable.ShipMeasurementUnit | Int | No | No |
| Number of cartons | ITMFolioTable.ShipNoOfCartons | Numeric(32, 6) | No | No |
| Original bill of landing sent | ITMFolioTable.ShipOriginalBOLSebt | Datetime | No | No |
| Original documents received | ITMFolioTable.ShipOriginalDocsReceived | Datetime | No | No |
| Purchase order status | ITMFolioTable.ShipPurchStatus | Int | No | No |
| Remarks | ITMFolioTable.ShipRemarks | Nvarchar(MAX) | No | No |
| Voyage status | ITMFolioTable.ShipStatusId | Nvarchar(20) | No | No |
| Tariff code | ITMFolioTable.ShipTariffCode | Nvarchar(10) | No | No |
| To port | ITMFolioTable.ShipToPort | Nvarchar(20) | No | No |
| Valuation date | ITMFolioTable.ShipValuationDate | Datetime | No | No |
| Verification date | ITMFolioTable.ShipVerificationDate | Datetime | No | No |
| Vendor account | ITMFolioTable.VendAccount | Nvarchar(20) | No | No |

### Number sequences for folios

The number sequence for folios controls the allocation of folio IDs.

The value that is passed to the data entity as the **Folio ID** (`FolioId`) value is used to identify an existing record for update. If that record doesn't exist, the behavior depends on whether the assigned number sequence is configured to allow for manual entry:

- If manual entry is enabled, a new record is created that uses the passed value.
- If manual entry isn't enabled, the next number in the assigned number sequence is used instead of the passed value.

During the import session, the placeholder value that is imported as the folio ID is retained. This behavior ensures that voyage lines that reference the placeholder are correctly associated, and that they are updated to reflect the value that is assigned from the number sequence.

### Field validations

The **Description of goods** field in the folio table (`ITMFolioTable`) is validated against the Landed cost setup table of the same name. A freight forwarder can use the `ITMGoodsDescriptionEntity` Landed cost data entity to read the existing values and ensure that valid values are received in your environment.

## Voyage lines for purchase orders (ITMPurchaseLineEntity)

The voyage line represents a single purchase order line that is included in the voyage. This relationship is established through the **Purchase order number** and **Purchase line number** fields. The voyage line references each previous record that was created for the voyage, shipping container, and folio. This functionality is supported by the `ITMPurchaseLineEntity` entity. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Currency | ITMLine.CurrencyCode | Nvarchar(3) | No | No |
| Net amount | ITMLine.LineAmountMST | Numeric(32, 6) | No | No |
| Purchase line number | ITMLine.RefRecId | Numeric(32, 6) | **Yes** | No |
| Shipping container | ITMLine.ShipContainerId | Int | No | No |
| Company | ITMLine.ShipDataArea | Nvarchar(20) | **Yes** | No |
| Declared quantity | ITMLine.ShipDeclaredQty | Nvarchar(4) | No | No |
| Folio | ITMLine.ShipFolioId | Numeric(32, 6) | No | No |
| Voyage | ITMLine.ShipId | Nvarchar(20) | **Yes** | No |
| Item number | ITMLine.ShipItemId | Nvarchar(20) | No | No |
| Measurement | ITMLine.ShipMeasurement | Nvarchar(20) | No | No |
| Measurement unit | ITMLine.ShipMeasurementUnit | Numeric(32, 6) | No | No |
| Number of cartons | ITMLine.ShipNoOfCartons | Int | No | No |
| Position | ITMLine.ShipPosition | Numeric(32, 6) | No | No |
| Quantity | ITMLine.ShipQty | Int | No | No |
| Purchase order number | ITMLine.TransRefId | Numeric(32, 6) | **Yes** | No |
| Unit | ITMLine.UnitId | Int | No | No |
| Volume | ITMLine.Volume | Nvarchar(10) | No | No |
| Weight | ITMLine.Weight | Numeric(32, 6) | No | No |

## Voyage lines for transfer orders (ITMTransferLineEntity)

The voyage line represents a single transfer order line that is included in the voyage. This relationship is established through the **Transfer order number** and **Transfer line number** fields. The voyage line references each previous record that was created for the voyage, shipping container, and folio. This functionality is supported by the `ITMTransferLineEntity` entity. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Currency | ITMLine.CurrencyCode | Nvarchar(3) | No | No |
| Net amount | ITMLine.LineAmountMST | Numeric(32, 6) | No | No |
| Shipping container | ITMLine.ShipContainerId | Int | No | No |
| Company | ITMLine.ShipDataArea | Nvarchar(20) | **Yes** | No |
| Declared quantity | ITMLine.ShipDeclaredQty | Nvarchar(4) | No | No |
| Folio | ITMLine.ShipFolioId | Numeric(32, 6) | No | No |
| Voyage | ITMLine.ShipId | Nvarchar(20) | **Yes** | No |
| Item number | ITMLine.ShipItemId | Nvarchar(20) | No | No |
| Measurement | ITMLine.ShipMeasurement | Nvarchar(20) | No | No |
| Measurement unit | ITMLine.ShipMeasurementUnit | Numeric(32, 6) | No | No |
| Number of cartons | ITMLine.ShipNoOfCartons | Int | No | No |
| Position | ITMLine.ShipPosition | Numeric(32, 6) | No | No |
| Quantity | ITMLine.ShipQty | Int | No | No |
| Transfer line number | ITMLine.TransferLineNumber | Numeric(32, 6) | **Yes** | No |
| Transfer order number | ITMLine.TransRefId | Numeric(32, 6) | **Yes** | No |
| Unit | ITMLine.UnitId | Int | No | No |
| Volume | ITMLine.Volume | Nvarchar(10) | No | No |
| Weight | ITMLine.Weight | Numeric(32, 6) | No | No |

### Reference table

Voyage lines are created through an association with an open inbound order line. This line can be on a purchase order, or it can be the receive transaction on a transfer order. The `RefTableId` field in the voyage line table (`ITMLine`) specifies which order type the line is related to by referencing the table number. If specific table numbers are referenced in the table where the data is being created, the entities are split based on those values.

The values for the reference table (`RefTableId`) and the transaction type (`TransType`) are implicit in the selection of either the Landed cost purchase line entity or the Landed cost transfer line entity.

### Validation

A voyage line directly references a voyage record, a shipping container record, and a folio record. If the purchase line entity (`ITMPurchaseLinesEntity`) or transfer line entity (`ITMPurchaseLinesEntity`) is used independently of the entities that are used to create these reference records, the **Voyage ID** (`ShipId`), **Shipping container** (`ShipContainerId`), and **Folio** (`ShipFolioId`) values must match an existing record in the corresponding tables. Otherwise, the import will fail.

If either line entity is used as part of the same import session, those other entities must precede the creation of a voyage line. Otherwise, the values can't be successfully validated. If a placeholder value is used for the voyage or folio number, the association can be created only if the same placeholder is used for the voyage or folio number in the voyage line entity.

If the purchase order or transfer order line is already assigned to an existing voyage line, the new voyage line won't be created. Before the order line can be assigned to a new voyage, it must be removed from its current voyage.

### Order line identification

Voyage lines directly reference the reference **Record ID** (`RefRecId`), **Inventory dimension ID** (`InventDimId`), and **Inventory transaction ID** (`InventTransId`) values. These values no longer have to be included when the data entity is used. Instead, the order line number must now be included. Together, the order line number and the order number enable each of those reference values to be identified.

### Voyage line quantity

Because a voyage line is directly associated with an order line, the **Quantity** (`ShipQty`) value that is entered by using the entity requires that the values match. Validation is run against the quantity on either the purchase order line or the transfer line. If the validation fails, the record won't be processed.

### Calculated fields

The **Weight** and **Volume** calculated fields accept the values that are received through the data entity. If no values are provided, the system values are used to update these fields, if system values are available. For Landed cost, the values are calculated in the following way:

- *Weight* = *Quantity* × *Item gross weight*
- *Volume* = *Quantity* × (*Item gross depth* × *Item gross height* × *Item gross width*)

## Sequencing

Because of dependencies between the tables, the voyage record must be created first. The voyage line can be created only after the voyage, shipping container, and folios have been created.

To create a voyage without validation warnings, the system must process the entities in the following order:

1. Voyages (`ITMTableEntity`)
1. Shipping containers (`ITMContainersEntity`)
1. Folios (`ITMFolioTableEntity`)
1. Voyage lines (`ITMPurchaseLinesEntity` or `ITMTransferLinesEntity`)
