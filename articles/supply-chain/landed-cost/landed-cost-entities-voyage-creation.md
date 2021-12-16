---
title: Voyage creation entities
description: The voyage creation data entities group together the data entities that are necessary for the creation of a working voyage.
author: yufeihuang
ms.date: 12/16/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2021-12-16
ms.dyn365.ops.version: 10.0.25
---

# Voyage creation entities

[!include [banner](../includes/banner.md)]

The voyage creation data entities group together the data entities that are necessary for the creation of a working voyage. You, or your freight forwarder, can use these data entities to create voyage, shipping container, folio and voyage line records that reference existing purchaser order or transfer order lines.

## Voyages

The voyage represents the journey of the inbound goods and serves as the highest level cost area within Landed cost. The voyage contains header level information related to the **vessel**, port of origin and destination port. This functionality is supported by the entity *ITMTableEntity*. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data Type | Key | Mandatory |
|---|---|---|---|---|
| Mode of delivery | ITMTable.DlvModeId | nvarchar(10) | No | No |
| Broker advised | ITMTable.ITMBrokerAdvised | datetime | No | No |
| Customer appointment | ITMTable.ITMCustomerAppointment | datetime | No | No |
| Delivered at warehouse | ITMTable.ITMDelAtWarehouse | datetime | No | No |
| Delivery instructions | ITMTable.ITMDeliveryInstructions | datetime | No | No |
| Departure date | ITMTable.ITMDepartureDate | datetime | No | No |
| Goods released | ITMTable.ITMGoodsReleased | datetime | No | No |
| Local transport date | ITMTable.ITMLocalTransportDate | datetime | No | No |
| Local transport time | ITMTable.ITMLocalTransportTime | int | No | No |
| Original bill of landing sent | ITMTable.ITMOriginalBOLSebt | datetime | No | No |
| Original documents received | ITMTable.ITMOriginalDocsReceived | datetime | No | No |
| Purchase order status | ITMTable.ITMPurchStatus | int | No | No |
| Verification date | ITMTable.ITMVerificationDate | datetime | No | No |
| Customs entry identifier | ITMTable.ShipCustomsEntryId | nvarchar(20) | No | No |
| Ship date | ITMTable.ShipDate | datetime | No | No |
| Description | ITMTable.ShipDescription | nvarchar(60) | No | No |
| Documents received | ITMTable.ShipDocReceived | int | No | No |
| Estimated delivery date | ITMTable.ShipEstDlvDate | datetime | No | No |
| ETA at shipping port | ITMTable.ShipEstPortDate | datetime | No | No |
| From port | ITMTable.ShipFromPort | nvarchar(20) | No | No |
| House air way/Bill of lading | ITMTable.ShipHAWB | nvarchar(20) | No | No |
| Voyage | ITMTable.ShipId | nvarchar(20) | **Yes** | **Yes** |
| Booking reference | ITMTable.ShipIdExternal | nvarchar(20) | No | No |
| Journey template | ITMTable.ShipJourneyId | nvarchar(20) | No | No |
| Local forwarder | ITMTable.ShipLocalForwarder | nvarchar(20) | No | No |
| Master air way/Bill of lading | ITMTable.ShipMAWB | nvarchar(20) | No | No |
| Measurement | ITMTable.ShipMeasurement | numeric(32, 6) | No | No |
| Measurement unit | ITMTable.ShipMeasurementUnit | int | No | No |
| Number of pallets | ITMTable.ShipNoOfPallets | int | No | No |
| Pending voyage | ITMTable.ShipPending | int | No | No |
| Remarks | ITMTable.ShipRemarks | nvarchar(MAX) | No | No |
| Rental | ITMTable.ShipRental | int | No | No |
| Voyage status | ITMTable.ShipStatusId | nvarchar(20) | No | No |
| Tally in number | ITMTable.ShipTallyInNumber | nvarchar(20) | No | No |
| To port | ITMTable.ShipToPort | nvarchar(20) | No | No |
| Valuation date | ITMTable.ShipValuationDate | datetime | No | No |
| Shipping company | ITMTable.ShipVendAccount | nvarchar(20) | No | No |
| Vessel | ITMTable.ShipVesselId | nvarchar(20) | No | **Yes** |
| External voyage ID | ITMTable.ShipVoyage | nvarchar(20) | No | No |

### Number sequences for voyages

The shared number sequence for voyages controls the allocation of voyage IDs. Where the assigned number is configured to allow for manual entry, the value passed to the data entity as the voyage ID (**ShipId**) will be used to identify an existing record for update or will result in the creation of a new record using that value.

If the assigned number sequence does not allow for manual entry, the value used for the voyage ID (**ShipId**) will first be used to identify an existing record for update. If this does not exist, the next number assigned to the number sequence will be used in place of the value entered.

Within the import session, the placeholder value imported as the voyage ID is retained to ensure shipping container and voyage lines referencing the placeholder are included within the voyage and are also updated to reflect the value assigned from the number sequence.

### Automatic cost transactions

Automatic costs can be added to a voyage through the configuration of the automatic costs form available under Setup &gt; Auto Costs. These records can also be created through the use of cost transaction data entities for each of the cost areas supported by Landed cost.

Automatic costs configured within Supply Chain Management are applied to the voyage on the creation of a voyage line. No costs will be visible against the record until this header record is associated with line information.

## Shipping Containers

The shipping container represents the physical container the goods are transported in. This may represent a freight container for ocean freight or could be a single pallet for air freight. The shipping container includes header level information related to the **shipping container id, seal number** and **shipping container type**, which provides dimension information. This functionality is supported by the entity *ITMContainersEntity*. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data Type | Key | Mandatory |
|---|---|---|---|---|
| Departure date | ITMContainers.ITMDepartureDate | datetime | No | No |
| Local transport date | ITMContainers.ITMLocalTransportDate | datetime | No | No |
| Local transport time | ITMContainers.ITMLocalTransportTime | int | No | No |
| Original voyage | ITMContainers.OrigShipId | nvarchar(20) | No | No |
| Actual weight | ITMContainers.ShipActualWeight | numeric(32, 6) | No | No |
| Broker advised | ITMContainers.ShipBrokerAdvised | datetime | No | No |
| Shipping container | ITMContainers.ShipContainerId | nvarchar(20) | **Yes** | **Yes** |
| Shipping container type | ITMContainers.ShipContainerTypeId | nvarchar(20) | No | No |
| Unit type | ITMContainers.ShipContainerUnitTypeId | nvarchar(10) | No | No |
| Converted to rental | ITMContainers.ShipConvertedToRental | int | No | No |
| Customer appointment | ITMContainers.ShipCustomerAppointment | datetime | No | No |
| Ship date | ITMContainers.ShipDate | datetime | No | No |
| Delivered at warehouse | ITMContainers.ShipDelAtWarehouse | datetime | No | No |
| Delivery instructions | ITMContainers.ShipDeliveryInstructions | datetime | No | No |
| Examination certificate applied date | ITMContainers.ShipECAppliedDate | datetime | No | No |
| Examination certificate expiry date | ITMContainers.ShipECExpiryDate | datetime | No | No |
| Examination certificate number | ITMContainers.ShipECNum | nvarchar(20) | No | No |
| Examination certificate received date | ITMContainers.ShipECReceivedDate | datetime | No | No |
| Estimated delivery date | ITMContainers.ShipEstDlvDate | datetime | No | No |
| ETA at shipping port | ITMContainers.ShipEstPortDate | datetime | No | No |
| Expected loading date | ITMContainers.ShipExpectedLoadingDate | datetime | No | No |
| From port | ITMContainers.ShipFromPort | nvarchar(20) | No | No |
| Description of goods | ITMContainers.ShipGoodsDesc | nvarchar(60) | No | No |
| Goods released | ITMContainers.ShipGoodsReleased | datetime | No | No |
| GPS tracker unit | ITMContainers.ShipGPSUnit | nvarchar(30) | No | No |
| House air way/Bill of lading | ITMContainers.ShipHAWB | nvarchar(20) | No | No |
| Voyage | ITMContainers.ShipId | nvarchar(20) | **Yes** | **Yes** |
| Journey template | ITMContainers.ShipJourneyId | nvarchar(20) | No | No |
| Local forwarder | ITMContainers.ShipLocalForwarder | nvarchar(20) | No | No |
| Measurement | ITMContainers.ShipMeasurement | numeric(32, 6) | No | No |
| Measurement unit | ITMContainers.ShipMeasurementUnit | int | No | No |
| Number of cartons | ITMContainers.ShipNoOfCartons | numeric(32, 6) | No | No |
| Original bill of landing sent | ITMContainers.ShipOriginalBOLSebt | datetime | No | No |
| Original documents received | ITMContainers.ShipOriginalDocsReceived | datetime | No | No |
| Our seal number | ITMContainers.ShipOurSealNum | nvarchar(20) | No | No |
| Used | ITMContainers.ShipPendingUsed | int | No | No |
| Purchase order status | ITMContainers.ShipPurchStatus | int | No | No |
| Refrigeration type | ITMContainers.ShipRefrigerationTypeId | nvarchar(10) | No | No |
| Remarks | ITMContainers.ShipRemarks | nvarchar(MAX) | No | No |
| Rental | ITMContainers.ShipRental | int | No | No |
| Returnable | ITMContainers.ShipReturnable | int | No | No |
| Voyage status | ITMContainers.ShipStatusId | nvarchar(20) | No | No |
| Shipping company seal number | ITMContainers.ShipTheirSealNum | nvarchar(20) | No | No |
| To port | ITMContainers.ShipToPort | nvarchar(20) | No | No |
| Verification date | ITMContainers.ShipVerificationDate | datetime | No | No |
| Vessel | ITMContainers.ShipVesselId | nvarchar(20) | No | **Yes** |

### Voyage ID validation

The shipping container ID is not controlled by a number sequence and is unique only in the context of the voyage it is on. If the shipping container entity (ITMContainersEntity) is used independently of the voyage entity (ITMTableEntity), the **voyage** (ShipId) must match an existing record within the voyage table, else the import will fail.

If the two entities are used as part of the same import session, the voyage entity (ITMTableEntity) must precede the creation of a shipping container so that the **voyage** (ShipId) can be successfully validated. If a placeholder value is used for the **voyage** (ShipId), the same placeholder must be used for the **voyage** (ShipId) in the shipping container entity to create the association.

### Further field validations

The following fields found on the shipping container table (ITMContainers) are validated against Landed cost setup tables. A freight forwarder can use the Landed Cost data entities listed below to read the existing values and ensure valid values are received into your environment.

- **Shipping container type** - ITMShippingContainerTypeEntity
- **Description of goods** - ITMGoodsDescriptionEntity
- **Refrigeration type** - ITMShippingContainerRefrigerationTypeEntity

## Folios

The folio represents a grouping of items within a shipping container, for the purposes of customs declarations. The folio includes header level information related to the **customs broker** and **description of goods**. This functionality is supported by the entity *ITMFolioEntity*. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data Type | Key | Mandatory |
|---|---|---|---|---|
| Broker advised | ITMFolioTable.ShipBrokerAdvised | datetime | No | No |
| Cargo control number | ITMFolioTable.ShipCargoControlNumber | nvarchar(20) | No | No |
| Customer appointment | ITMFolioTable.ShipCustomerAppointment | datetime | No | No |
| Customs broker | ITMFolioTable.ShipCustomsBroker | nvarchar(20) | No | No |
| Customs ID | ITMFolioTable.ShipCustomsId | nvarchar(60) | No | No |
| Company | ITMFolioTable.ShipDataArea | nvarchar(4) | No | **Yes** |
| Delivered at warehouse | ITMFolioTable.ShipDelAtWarehouse | datetime | No | No |
| Delivery instructions | ITMFolioTable.ShipDeliveryInstructions | datetime | No | No |
| Documents received | ITMFolioTable.ShipDocReceived | int | No | No |
| Estimated delivery date | ITMFolioTable.ShipEstDlvDate | datetime | No | No |
| ETA at shipping port | ITMFolioTable.ShipEstPortDate | datetime | No | No |
| Exporter | ITMFolioTable.ShipExporterId | nvarchar(20) | No | No |
| Name | ITMFolioTable.ShipExporterName | nvarchar(60) | No | No |
| Folio date | ITMFolioTable.ShipFolioDate | datetime | No | No |
| Folio | ITMFolioTable.ShipFolioId | nvarchar(20) | **Yes** | **Yes** |
| From port | ITMFolioTable.ShipFromPort | nvarchar(20) | No | No |
| Description of goods | ITMFolioTable.ShipGoodsDesc | nvarchar(60) | No | No |
| Goods released | ITMFolioTable.ShipGoodsReleased | datetime | No | No |
| House air way/Bill of lading | ITMFolioTable.ShipHAWB | nvarchar(20) | No | No |
| Voyage | ITMFolioTable.ShipId | nvarchar(20) | No | **Yes** |
| Measurement | ITMFolioTable.ShipMeasurement | numeric(32, 6) | No | No |
| Measurement unit | ITMFolioTable.ShipMeasurementUnit | int | No | No |
| Number of cartons | ITMFolioTable.ShipNoOfCartons | numeric(32, 6) | No | No |
| Original bill of landing sent | ITMFolioTable.ShipOriginalBOLSebt | datetime | No | No |
| Original documents received | ITMFolioTable.ShipOriginalDocsReceived | datetime | No | No |
| Purchase order status | ITMFolioTable.ShipPurchStatus | int | No | No |
| Remarks | ITMFolioTable.ShipRemarks | nvarchar(MAX) | No | No |
| Voyage status | ITMFolioTable.ShipStatusId | nvarchar(20) | No | No |
| Tariff code | ITMFolioTable.ShipTariffCode | nvarchar(10) | No | No |
| To port | ITMFolioTable.ShipToPort | nvarchar(20) | No | No |
| Valuation date | ITMFolioTable.ShipValuationDate | datetime | No | No |
| Verification date | ITMFolioTable.ShipVerificationDate | datetime | No | No |
| Vendor account | ITMFolioTable.VendAccount | nvarchar(20) | No | No |

### Number sequences for folios

The number sequence for folios controls the allocation of folio IDs. Where the assigned number is configured to allow for manual entry, the value passed to the data entity as the folio ID (**FolioId**) will be used to identify an existing record for update or will result in the creation of a new record using that value.

If the assigned number sequence does not allow for manual entry, the value used for the folio ID (**FolioId**) will first be used to identify an existing record for update. If this does not exist, the next number assigned to the number sequence will be used in place of the value entered.

Within the import session, the placeholder value imported as the folio ID is retained to ensure voyage lines referencing the placeholder are correctly associated and are updated to reflect the value assigned from the number sequence.

### Field validations

The description of goods field on the folio table (ITMFolioTable) is validated against the setup table of the same name. A freight forwarder can use the Landed Cost data entity below to read the existing values and ensure valid values are received into your environment.

- **Description of goods** - ITMGoodsDescriptionEntity

## Voyage Lines (purchase order)

The voyage line represents a single purchase order line which has been included within the Voyage, this relationship is established through the **purchase order number** and **purchase line number** fields. The voyage line references each of the previous records created for voyage, shipping container and folio. This functionality is supported by the entity *ITMPurchaseLineEntity*. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data Type | Key | Mandatory |
|---|---|---|---|---|
| Currency | ITMLine.CurrencyCode | nvarchar(3) | No | No |
| Net amount | ITMLine.LineAmountMST | numeric(32, 6) | No | No |
| Purchase line number | ITMLine.RefRecId | numeric(32, 6) | **Yes** | No |
| Shipping container | ITMLine.ShipContainerId | int | No | No |
| Company | ITMLine.ShipDataArea | nvarchar(20) | **Yes** | No |
| Declared quantity | ITMLine.ShipDeclaredQty | nvarchar(4) | No | No |
| Folio | ITMLine.ShipFolioId | numeric(32, 6) | No | No |
| Voyage | ITMLine.ShipId | nvarchar(20) | **Yes** | No |
| Item number | ITMLine.ShipItemId | nvarchar(20) | No | No |
| Measurement | ITMLine.ShipMeasurement | nvarchar(20) | No | No |
| Measurement unit | ITMLine.ShipMeasurementUnit | numeric(32, 6) | No | No |
| Number of cartons | ITMLine.ShipNoOfCartons | int | No | No |
| Position | ITMLine.ShipPosition | numeric(32, 6) | No | No |
| Quantity | ITMLine.ShipQty | int | No | No |
| Purchase order number | ITMLine.TransRefId | numeric(32, 6) | **Yes** | No |
| Unit | ITMLine.UnitId | int | No | No |
| Volume | ITMLine.Volume | nvarchar(10) | No | No |
| Weight | ITMLine.Weight | numeric(32, 6) | No | No |

## Voyage Lines (transfer order)

The voyage line represents a single transfer order line which has been included within the Voyage, this relationship is established through the **transfer order number** and **transfer line number** fields. The voyage line references each of the previous records created for voyage, shipping container and folio. This functionality is supported by the entity *ITMTransferLineEntity*. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data Type | Key | Mandatory |
|---|---|---|---|---|
| Currency | ITMLine.CurrencyCode | nvarchar(3) | No | No |
| Net amount | ITMLine.LineAmountMST | numeric(32, 6) | No | No |
| Shipping container | ITMLine.ShipContainerId | int | No | No |
| Company | ITMLine.ShipDataArea | nvarchar(20) | **Yes** | No |
| Declared quantity | ITMLine.ShipDeclaredQty | nvarchar(4) | No | No |
| Folio | ITMLine.ShipFolioId | numeric(32, 6) | No | No |
| Voyage | ITMLine.ShipId | nvarchar(20) | **Yes** | No |
| Item number | ITMLine.ShipItemId | nvarchar(20) | No | No |
| Measurement | ITMLine.ShipMeasurement | nvarchar(20) | No | No |
| Measurement unit | ITMLine.ShipMeasurementUnit | numeric(32, 6) | No | No |
| Number of cartons | ITMLine.ShipNoOfCartons | int | No | No |
| Position | ITMLine.ShipPosition | numeric(32, 6) | No | No |
| Quantity | ITMLine.ShipQty | int | No | No |
| Transfer line number | ITMLine.TransferLineNumber | numeric(32, 6) | **Yes** | No |
| Transfer order number | ITMLine.TransRefId | numeric(32, 6) | **Yes** | No |
| Unit | ITMLine.UnitId | int | No | No |
| Volume | ITMLine.Volume | nvarchar(10) | No | No |
| Weight | ITMLine.Weight | numeric(32, 6) | No | No |

### Reference table

Voyage lines are created through an association with an open inbound order line. This can either be on a purchase order or as the receive transaction on a transfer order. The field **RefTableId** found on voyage line table (ITMLine) is used to reference which of the two order types the line relates to by referencing the table number. Where specific table numbers are referenced in the table where the data is being created, the entities are split based on these values.

The values for the reference table (RefTableId) and the transaction type (TransType) are implicit in the selection of either the Landed cost purchase line or Landed cost transfer line entity.

### Validation

A voyage line directly references a voyage, shipping container and folio record. If the purchase line entity (ITMPurchaseLinesEntity) or transfer line entity (ITMPurchaseLinesEntity) is used independently of the entities used to create these reference records, the Voyage ID (**ShipId**), Shipping container (**ShipContainerId**) and Folio (**ShipFolioId**) must match an existing record within their respective tables, else the import will fail.

If either line entity is used as part of the same import session, these other entities must precede the creation of a voyage line so that the values can be successfully validated. If a placeholder value is used for the voyage or folio number, the same placeholder must be used for the voyage or folio number in the voyage line entity to create the association.

Where the purchase or transfer order line is already assigned to an existing voyage line, the new voyage line will not be created. To assign this order line to a new voyage it must first be removed from its current voyage.

### Order line identification

Voyage lines directly reference the reference record ID (**RefRecId**), inventory dimension ID (**InventDimId**) and inventory transaction ID (**InventTransId**). The requirement to include these values when using the data entity has been replaced with the need to include the order line number. The order line number along with the order number allow for the identification of each of these reference values.

### Voyage line quantity

As a voyage line is directly associated with an order line, the quantity (**ShipQty**) value entered through use of the entity requires that the values match. A validation against either the purchase order line quantity or transfer line quantity will be run. Where the validation fails the record will not be processed.

### Calculated fields

The calculated fields volume and weight will accept the values received through the data entity. If no value is provided, these will be updated using the system values if available. For Landed cost, the values are determined as;

- **Weight** = Quantity \* Item gross weight
- **Volume** = Quantity \* (Item gross depth \* Item gross height \* Item gross width)

## Sequencing

Due to dependencies between the tables, the Voyage record must be created first and the Voyage line can only be created once the Voyage, Shipping container, and Folios have been created.

To create a voyage without validation warnings, the system must process the entities in the following order;

1. Voyages – ITMTableEntity
1. Shipping containers – ITMContainersEntity
1. Folios – ITMFolioTableEntity
1. Voyage lines – ITMPurchaseLinesEntity or ITMTransferLinesEntity
