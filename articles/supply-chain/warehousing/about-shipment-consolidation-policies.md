---
# required metadata

title: About shipment consolidation policies
description: This topic provides an overview of functionality that provides flexible configuration of shipment consolidation policies.
author: GarmMSFT
manager: tfehr
ms.date: 04/16/2019
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: v-olbara
ms.search.validFrom: 2020-04-16
ms.dyn365.ops.version: 10.0.3

---
# About shipment consolidation policies

The shipment consolidation process using shipment consolidation policies allows for automated shipment consolidation during automated and manual release to warehouse. Before introduction of this functionality, automated consolidation was available with hardcoded fields and based on the **Consolidate shipment at release to warehouse** field set on a warehouse.

Shipment consolidation policies are used at the following instances of functionality:

- Automated release to warehouse batch job
- The **Release to warehouse** command from a sales or transfer order
- The dedicated **Release to warehouse** page
- The **Release to warehouse** command from the **Load planning workbench** page
- The manual consolidation of shipments on the **Consolidate shipments** and **Shipment consolidation workbench** pages

Before shipment consolidation policies were introduced, the consolidation function existed as a setting at the warehouse level, where the application treated orders by all customers from a single warehouse as having the same consolidation requirements. Shipment consolidation policies add support for scenarios where different organizations can have different requirements for shipment consolidation.

The shipment consolidation policies follow a pattern (for example, of the wave templates) where queries are used to identify which policy applies, and then a modifiable set of fields drives how to group the load lines on the shipment level. In addition, a **Consolidate with existing shipments** setting has been added to each policy, which is able to find all open shipments that match the policy&mdash;in this case, an existing shipment/load will be selected instead of creating a new one.

The **Consolidate shipment at release to warehouse** setting previously available on the **Warehouses** setup page is now hidden. To help you transition to the new shipment consolidation feature, we've added a function on the **Shipment consolidation policies** page to create a default policy, which automatically includes the old setting for existing warehouses. After that, the **Consolidate shipment at release to warehouse** setting on the **Warehouses** setup page will no longer be taken into account.

Use the **Release to warehouse** page to manually override the applicable consolidation policy in the same way that you can override fulfillment policies.

Use the **Release > Release to warehouse** menu item on the **Load planning workbench** page to build outbound loads based on sales and transfer order lines before releasing to warehouse and use the same consolidation logic introduced with the consolidation of shipment policies.  

Use the **Shipment consolidation workbench** page to consolidate existing shipments that are not yet confirmed after they've been released to the warehouse. This functionality caters for  scenarios where the automated release process, with its own shipment consolidation, is run multiple times a day&mdash;but prior completing the shipment to carriers during the confirmation process, potential additional consolidations are identified manually. This functionality allows you to consolidate the outbound shipments created from sales or transfer order lines at any time after releasing to warehouse and before confirming the shipment. The page works similarly to the load building workbench, where you can assess multiple shipments at the same time and can choose to assign a non-consolidated order to a specific shipment. You can apply shipment consolidation templates to recurrently assess proposed consolidations and confirm them. Some rules are implemented to prevent unauthorized consolidation and to warn  of possible errors.

<!-- KFM: Maybe add a section on how to enable this in feature management -->

## Overview of new functionality

This section describes the pages, menu items, and features that are modified or added when you enable and use the *Shipment consolidation policies* feature.

### Shipment consolidation policies (page)

Policies are differentiated based on work order types (**Sales orders** to represent _Sales order_ shipments and **Transfer orders** to represent _Transfer issue_ shipments).

Each shipment consolidation policy has a query that defines when it applies and a sequence number to control the execution order. Consolidation is applied for each unique combination of the selected fields. An additional parameter is provided for consolidating with existing (open) shipments. The policies are evaluated and applied each time a new shipment is created (before wave processing).

If a policy is missing any mandatory fields, or includes any prohibited fields, in the **Selected** section, the policy is marked as invalid. The lists of mandatory and forbidden fields are hardcoded and can be extended.

This is the mandatory field list (shipments are always split by these fields, so you can't group several shipments that have different values for these fields):

- For sales orders:
  - **Account number**: _WHSShipmentTable.AccountNum_
  - **Delivery recipient**: _WHSShipmentTable.DeliveryName_
  - **Postal address** (RecId): _WHSShipmentTable.DeliveryPostalAddress_
  - **Warehouse**: _WHSShipmentTable.InventLocationId_

- For transfer orders:
  - **From warehouse**: _InventTransferTable.InventLocationIdFrom_
  - **To warehouse**: _InventTransferTable.InventLocationIdTo_

Following fields are unavailable for all document types (these fields aren't visible on the UI and can't be used for consolidation):

- **Shipment ID**: _WHSShipmentTable.ShipmentId_
- **Status**: _WHSShipmentTable.ShipmentStatus_
- **Shipment consolidation policy**: _WHSShipmentTable.ShipConsolidationPolicyName_
- **Work transaction type**: _WHSShipmentTable.WorkTransType_
- **Wave ID**: _WHSShipmentTable.WaveId_
- **Load ID**: _WHSShipmentTable.LoadId_
- **Shipment ID**: _WHSLoadLine.ShipmentId_
- **Load ID**: _WHSLoadLine.LoadId_

The consolidation fields default to the mandatory set of fields when you create a new policy, but you can modify the list using left and right arrows (similar to the way you select methods in **Wave templates**).

Values for these fields (as selected by a user) will be equal for newly created shipments, or added to existing shipments when consolidating with existing shipments. When the values of a field selected for consolidating two shipments match, the shipments are consolidated (as is the case for all subsequently selected consolidation fields). If the values differ, then the second shipment is discarded and will be selected for a new shipment. The automated-consolidation process consists of creating all the unique combinations of values for the consolidate-shipment fields and then assigning the shipment to the relevant combination.

Unselected fields are ignored during the consolidation process. If an unselected field has different values in two shipments, it will be cleared (set to blank). If a field was not selected but has the same values in both shipments, it will be filled in.

The list of consolidation fields (fields that will be cleared when they have different values) is hardcoded. The list contains all fields that are initialized from a sales line or transfer line when a new shipment is created. In other words, if a field isn't initialized from a sales line or transfer line, it is ignored when new data is added to an existing shipment.

### Release to warehouse (page)

- A new field was added to the lower grid to display the applied consolidation policy
- A new button was added to manually select and/or override the consolidation policy

### Release to warehouse (menu item) at Load planning workbench (page)

- Logic was adjusted to use applied consolidation policies
- Shipments are now consolidated only within a single load

### Consolidate shipments (page)

- Search for similar shipments (candidates for consolidation) was modified to use fields selected on shipment consolidation policy
- Fields that have different values in different shipments are now set to blank (previously the values from the selected "base" shipment were used)

### Shipment consolidation workbench (page)

- Added new functionality that replicates the process of manual consolidation on a larger scale
- You can now open this page from the **Release to warehouse** menu of the **Warehouse management** module
- The algorithm analyzes existing shipments (that are not yet shipped) and proposes consolidation based on fields selected in the consolidation policies

## Comparison of functionality

The following table summarizes how shipment consolidation works when you don't use shipment consolidation policies compared to when you do.

<!-- KFM there were issues with this table (caused by extra carriage returns, I think). I tried to sort it out, but please confirm. -->

| Without shipment consolidation policies | With shipment consolidation policies |
|---|----|
| N/A | Sales or transfer shipments chosen for consolidation must have the same consolidation policy as the shipment that is being created, or be assigned to an open shipment (when the **Consolidate with existing shipments** option is enabled). |
| The *Release to warehouse* procedure doesn't search for a shipment for consolidation among already existing ones. Only shipments created by a current instance of the *Release to warehouse* procedure are used to find a shipment to consolidate. | If the **Consolidate with existing shipments** option is enabled for a currently used consolidation policy, the *Release to warehouse* procedure searches for a shipment for consolidation among already existing ones that were created based on the same consolidation policy. A shipment being created based on a policy #2 will never be consolidated with a shipment created based on a policy #1. |
| N/A | If a consolidation policy field list is empty (or if a policy can't be found), a new shipment is created for each sales or transfer line. |
| Consolidation fields that define the unique combination of values to consolidate shipments for a *transfer line* are as follows (other fields are ignored): <br><br> - Order number (OrderNum) | Consolidation fields that define the unique combination of values to consolidate shipments for a *transfer line* are as follows (other fields are ignored):<br><br> - Order number (OrderNum) <br> - Delivery recipient (DeliveryName) <br> - Postal address (DeliveryPostalAddress) <br> - ISO country code (CountryRegionISOCode) <br> - Address (Address) <br> - Site (InventSiteId) <br> - Warehouse (InventLocationId) <br> - Shipping carrier (CarrierCode) <br> - Carrier service (CarrierServiceCode) <br> - Mode of delivery (ModeCode) <br> - Carrier group (CarrierGroupCode) <br> - Delivery terms (DlvTermId) <br><br> These are the only fields that are available and initialized when a new shipment is created. |
| Consolidation fields that define the unique combination of values to consolidate the shipments for a *sales line* are as follows (other fields are ignored):<br><br>- Order number (OrderNum) <br> - Customer reference (CustomerRef) <br> - Customer requisition (CustomerReq) <br> - Delivery terms (DlvTermId) | Consolidation fields that define the unique combination of values to consolidate the shipments for a *sales line* are as follows (other fields are ignored): <br><br> - Order number (OrderNum) <br> - Account number (AccountNum) <br> - Delivery recipient (DeliveryName) <br> - Postal address (DeliveryPostalAddress) <br> - ISO country code (CountryRegionISOCode) <br> - Address (Address) <br> - Site (InventSiteId) <br> - Warehouse (InventLocationId) <br> - Shipping carrier (CarrierCode) <br> - Carrier service (CarrierServiceCode) <br> - Mode of delivery (ModeCode) <br> - Carrier group (CarrierGroupCode) <br> - Broker ID (BrokerCode) <br> - Direction (LoadDirection) <br> - Delivery terms (DlvTermId) <br> - Customer reference (CustomerRef) <br> - Customer requisition (CustomerReq) <br><br> These are the only fields that are available and initialized when a new shipment is created. |
| N/A | The mandatory consolidation fields for a *sales line* are as follows (and can't be removed):<br><br>- Account number (AccountNum) <br> - Delivery recipient (DeliveryName) <br> - Postal address (DeliveryPostalAddress) <br> - Warehouse (InventLocationId) <br> <br> These fields will be assigned by default when a new policy is created and can't be removed. |
| The *Release of loads to warehouse* procedure on the **Load planning workbench** page uses its own separate code for creating shipments and waves. | Shipment consolidation policies are applied to decide which fields are evaluated for consolidation. Shipments are consolidated only within a single load. |
| You manually select **Consolidate shipments** on the **All shipments** page and then choose a target "base" shipment. The filter will suggest any other existing shipments that have matching values for several key fields. | You manually select **Consolidate shipments** on the **All shipments** page and then choose a target "base" shipment. Other existing shipments will be suggested by matching the values for several key fields configured for the relevant shipment consolidation policies. |
| You can only use the **Consolidate shipments** command on the **All shipments** page for a single shipment | The **Shipment consolidation workbench** helps you find a set of shipments that aren't yet in a shipped state. These shipments are analyzed based on several key fields configured on your shipment consolidation policies, and shipments where the values in these fields match are suggested for consolidation. <br> It is possible to maintain the consolidation manually by removing and/or adding some shipments from suggested consolidations. Any of several types of errors may occur, but you can override some of them. |
| **Design note:** The *Automatic release of sales orders to warehouse* procedure splits sales lines into groups. Each group has its own unique **ReleaseToWarehouseId** value and is processed by the *Release to warehouse* procedure separately, which creates new work regardless of work break setup. | **Design note:** The *Automatic release of sales orders to warehouse* procedure assigns the same **ReleaseToWarehouseId** value to all sales lines being processed. All sales lines are processed by the *Release to warehouse* procedure at once. Work break per shipment ID must be configured to ensure the legacy behavior. |

## Related articles and demo scripts

- [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
