---
title: Shipment consolidation policies overview
description: Access an overview of the functionality that provides flexible configuration of shipment consolidation policies, including an overview of new functionality.
author: Mirzaab
ms.author: mirzaab
ms.topic: overview
ms.date: 01/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench, WHSShipConsolidationError, WHSShipConsolidationSetShipment, WHSShipConsolidationPolicySelect, WHSShipPlanningListPage, TMSCarrierGroup, WHSShipConsolidationTemplate, WHSShipConsolidationTemplateApply, WHSShipConsolidationTemplateCreate, WHSOutboundLoadPlanningWorkbench
---

# Shipment consolidation policies overview

[!include [banner](../includes/banner.md)]

The shipment consolidation process that uses shipment consolidation policies allows for automated shipment consolidation during automated and manual release to the warehouse. The automated consolidation that was available before this feature was introduced had hard-coded fields and was based on the **Consolidate shipment at release to warehouse** field that was set for a warehouse.

Shipment consolidation policies are used for the following functionality:

- The automated release-to-warehouse batch jobs
- The **Release to warehouse** command on a sales order, transfer order, or outbound shipment order
- The dedicated **Release to warehouse** pages
- The **Release to warehouse** command on the **Outbound load planning workbench** page
- The manual consolidation of shipments on the **Consolidate shipments** and **Shipment consolidation workbench** pages

Before shipment consolidation policies were introduced, the consolidation function existed as a setting at the warehouse level. All orders for all customers from a single warehouse were treated as though they had the same consolidation requirements. Shipment consolidation policies add support for scenarios where different organizations have different requirements for shipment consolidation.

Queries are used to identify the shipment consolidation policy that applies, and then an editable set of fields determines how the load lines are grouped at the shipment level. (This pattern resembles the pattern that wave templates follow.) In addition, a **Consolidate with existing shipments** option has been added to each policy. When this option is turned on, the *Release to warehouse* procedure finds shipments for consolidation by searching among existing shipments that were created based on the same consolidation policy. In this case, the system will select an existing shipment or load instead of creating a new one. However, the system will only consolidate with existing shipments that have a status of *Open*; shipments that belong to a wave release with a status of *Released* or higher won't be considered as targets for consolidation.

When the *Shipment consolidation policies* feature is turned on for your system, the **Consolidate shipment at release to warehouse** setting that was previously available on the **Warehouses** setup page is hidden. To help you transition to the new shipment consolidation feature, a function on the **Shipment consolidation policies** page lets you create a default policy that automatically includes the old setting for existing warehouses. After that default policy is created, the **Consolidate shipment at release to warehouse** setting on the **Warehouses** setup page will no longer be considered. Learn more in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md).

You can use the various **Release to warehouse** pages to manually override the applicable consolidation policy in the same way that you can override fulfillment policies.

You can use the **Release \> Release to warehouse** command on the **Outbound load planning workbench** page to build outbound loads that are based on sales, transfer, and outbound shipment order lines before you do the release to the warehouse. These loads use the same consolidation logic that was introduced together with the consolidation of shipment policies.

You can use the **Shipment consolidation workbench** page to consolidate existing shipments that haven't yet been confirmed but have already been released to the warehouse. This functionality supports scenarios where the automated release process, which has its own shipment consolidation, is run multiple times a day, but potential additional consolidations are manually identified before the shipment to carriers is completed during the confirmation process. This functionality lets you consolidate outbound shipments that are created from sales, transfer, or outbound shipment order lines at any time after the shipments are released to the warehouse but before they are confirmed.

The **Shipment consolidation workbench** page works like the load building workbench, where you can assess multiple shipments at the same time and assign a non-consolidated order to a specific shipment. You can apply shipment consolidation templates to assess proposed consolidations multiple times and confirm them. Some rules are implemented to prevent unauthorized consolidation and to warn you about possible errors.

## Overview of new functionality

This section describes the pages, commands, and features that are changed or added when you turn on and use the *Shipment consolidation policies* feature.

### Shipment consolidation policies page

Policies are differentiated by work order type. The **Sales orders** type represents *Sales order* shipments, the **Transfer orders** type represents *Transfer issue* shipments, and the **Outbound shipment order** type represents *Outbound shipment order* shipments.

Every shipment consolidation policy has a query that defines when it's applied and a sequence number that determines the execution order. Consolidation is applied for each unique combination of the selected fields. An additional parameter that is provided is used for consolidation with existing (open) shipments. The policies are evaluated and applied every time that a new shipment is created (before wave processing).

If a policy is missing any mandatory fields, or if it includes any prohibited fields, the policy is marked as not valid in the **Selected** section. The lists of mandatory and prohibited fields are hard-coded and can be extended.

The following list shows the mandatory fields. Because shipments are always split based on these fields, you can't group multiple shipments that have different values for these fields.

- For sales orders:

    - **Account number:** *WHSShipmentTable.AccountNum*
    - **Delivery recipient:** *WHSShipmentTable.DeliveryName*
    - **Postal address (RecId):** *WHSShipmentTable.DeliveryPostalAddress*
    - **Warehouse:** *WHSShipmentTable.InventLocationId*

- For transfer orders:

    - **From warehouse:** *InventTransferTable.InventLocationIdFrom*
    - **To warehouse:** *InventTransferTable.InventLocationIdTo*

- For outbound shipment orders:

    - **Account number:** *WHSShipmentTable.AccountNum*
    - **Delivery recipient:** *WHSShipmentTable.DeliveryName*
    - **Postal address (RecId):** *WHSShipmentTable.DeliveryPostalAddress*
    - **Warehouse:** *WHSShipmentTable.InventLocationId*
    - **Source system:** *WHSShipmentTable.SourceSystem*

The following fields are unavailable for all document types. These fields aren't visible in the user interface (UI), and they can't be used for consolidation.

- **Shipment ID:** *WHSShipmentTable.ShipmentId*
- **Status:** *WHSShipmentTable.ShipmentStatus*
- **Shipment consolidation policy:** *WHSShipmentTable.ShipConsolidationPolicyName*
- **Work transaction type:** *WHSShipmentTable.WorkTransType*
- **Wave ID:** *WHSShipmentTable.WaveId*
- **Load ID:** *WHSShipmentTable.LoadId*
- **Shipment ID:** *WHSLoadLine.ShipmentId*
- **Load ID:** *WHSLoadLine.LoadId*

By default, when you create a policy, the set of mandatory fields is used as the consolidation fields. However, you can modify the list by using left arrow and right arrow buttons. (The process resembles the process for selecting methods in wave templates.)

The values that users select for these fields will be used for all newly created shipments, or they will be added to existing shipments during consolidation with those shipments. When two shipments have the same value for a field that is selected for consolidation of those shipments, the shipments are consolidated. The same principle applies for all subsequent consolidation fields that are selected. If the values differ, the second shipment is discarded and will be selected for a new shipment. The automated consolidation process consists of creating all the unique combinations of values for the shipment consolidation fields and then assigning a shipment to the relevant combination.

Unselected fields are ignored during the consolidation process. If two shipments have different values for an unselected field, the field is cleared (that is, it's set to blank). If both shipments have the same value for an unselected field, the field is filled in.

The list of consolidation fields (that is, fields that will be cleared if they have different values) is hard-coded. The list contains all fields that are initialized from a sales order or transfer order line when a new shipment is created. In other words, if a field isn't initialized from a sales order or transfer order line, it's ignored when new data is added to an existing shipment.

### Release to warehouse page

- A new field in the lower grid shows the consolidation policy that was applied.
- A new button lets you manually select and/or override the consolidation policy.

### Release to warehouse command on the Outbound load planning workbench page

- The logic was adjusted so that it uses applied consolidation policies.
- Shipments are now consolidated only within a single load.

### Consolidate shipments page

- The search for similar shipments (that is, candidates for consolidation) was changed so that it uses fields that are selected in the shipment consolidation policy.
- Fields that have different values in different shipments are now set to blank. (Previously, the values from the selected "base" shipment were used.)

### Shipment consolidation workbench page

- New functionality replicates the process of manual consolidation on a larger scale.
- You can now open this page from the **Release to warehouse** menu in the **Warehouse management** module.
- The algorithm analyzes existing shipments that haven't yet been shipped. It then proposes consolidation, based on fields that are selected in the consolidation policies.

## Comparison of functionality

The following table summarizes how shipment consolidation works when you don't use shipment consolidation policies and when you do use them.

| Without shipment consolidation policies | With shipment consolidation policies |
|---|----|
| Not applicable | Sales or transfer shipments that are selected for consolidation must have the same consolidation policy as the shipment that is being created, or they must be assigned to an open shipment (when the **Consolidate with existing shipments** option is turned on). |
| The *Release to warehouse* procedure doesn't search among existing shipments to find a shipment for consolidation. Only shipments that are created by a current instance of the *Release to warehouse* procedure are used to find a shipment for consolidation. | If the **Consolidate with existing shipments** option is turned on for a consolidation policy that is currently being used, the *Release to warehouse* procedure searches among existing shipments that were created based on the same consolidation policy to find a shipment for consolidation. Therefore, if you have two policies, a shipment that is being created based on policy 2 will never be consolidated with a shipment that was created based on policy 1. |
| Not applicable | If a list of consolidation policy fields is empty, or if a policy can't be found, a new shipment is created for each sales order or transfer order line. |
| The following consolidation field defines the unique combination of values that is used to consolidate shipments for a *transfer line*. (All other fields are ignored.)<ul><li>Order number (OrderNum)</li></ul> | The following consolidation fields define the unique combination of values that is used to consolidate shipments for a *transfer line*. (All other fields are ignored.)<ul><li>Order number (OrderNum)</li><li>Delivery recipient (DeliveryName)</li><li>Postal address (DeliveryPostalAddress)</li><li>ISO country code (CountryRegionISOCode)</li><li>Address (Address)</li><li>Site (InventSiteId)</li><li>Warehouse (InventLocationId)</li><li>Shipping carrier (CarrierCode)</li><li>Carrier service (CarrierServiceCode)</li><li>Mode of delivery (ModeCode) \*</li><li>Carrier group (CarrierGroupCode)</li><li>Delivery terms (DlvTermId)</li></ul><p>These fields are the only fields that are available and initialized when a new shipment is created.</p><p>\* Note: The *ModeCode* is the **Mode** assigned to the **Shipping carrier** selected for a transfer line (not the **Mode of delivery** selected for a transfer line). If you choose to include *Mode of delivery (ModeCode)* among your consolidation criteria, then the system will only consolidate transfer lines with the same **Mode** value provided **Shipping carrier**, **Carrier service**, and **Mode of delivery** are all defined for the line (regardless of their values). In addition, the system will also consolidate all transfer lines where the **Mode** is blank.</p> |
| The following consolidation fields define the unique combination of values that is used to consolidate shipments for a *sales line*. (All other fields are ignored.)<ul><li>Order number (OrderNum)</li><li>Customer reference (CustomerRef)</li><li>Customer requisition (CustomerReq)</li><li>Delivery terms (DlvTermId)</li></ul> | The following consolidation fields define the unique combination of values that is used to consolidate shipments for a *sales line*. (All other fields are ignored.)<ul><li>Order number (OrderNum)</li><li>Account number (AccountNum)</li><li>Delivery recipient (DeliveryName)</li><li>Postal address (DeliveryPostalAddress)</li><li>ISO country code (CountryRegionISOCode)</li><li>Address (Address)</li><li>Site (InventSiteId)</li><li>Warehouse (InventLocationId)</li><li>Shipping carrier (CarrierCode)</li><li>Carrier service (CarrierServiceCode)</li><li>Mode of delivery (ModeCode) \*</li><li>Carrier group (CarrierGroupCode)</li><li>Broker ID (BrokerCode)</li><li>Direction (LoadDirection)</li><li>Delivery terms (DlvTermId)</li><li>Customer reference (CustomerRef)</li><li>Customer requisition (CustomerReq)</li></ul><p>These fields are the only fields that are available and initialized when a new shipment is created.</p><p>\* Note: The *ModeCode* is the **Mode** assigned to the **Shipping carrier** selected for a sales line (not the **Mode of delivery** selected for a sales line). If you choose to include *Mode of delivery (ModeCode)* among your consolidation criteria, then the system will only consolidate sales lines with the same **Mode** value provided **Shipping carrier**, **Carrier service**, and **Mode of delivery** are all defined for the line (regardless of their values). In addition, the system will also consolidate all sales lines where the **Mode** is blank.</p> |
| Not applicable | The following consolidation fields are mandatory for a *sales line* and can't be removed:<ul><li>Account number (AccountNum)</li><li>Delivery recipient (DeliveryName)</li><li>Postal address (DeliveryPostalAddress)</li><li>Warehouse (InventLocationId)</li></ul>By default, these fields will be assigned when a new policy is created. They can't be removed. |
| The *Release of loads to warehouse* procedure on the **Outbound load planning workbench** page uses its own separate code to create shipments and waves. | Shipment consolidation policies are applied to determine which fields should be evaluated for consolidation. Shipments are consolidated only within a single load. |
| You manually select **Consolidate shipments** on the **All shipments** page and then select a target "base" shipment. The filter will suggest any existing shipments that have matching values for several key fields. | You manually select **Consolidate shipments** on the **All shipments** page and then select a target "base" shipment. The system will suggest other existing shipments by matching the values of several key fields that are configured for the relevant shipment consolidation policies. |
| You can use the **Consolidate shipments** command on the **All shipments** page for only a single shipment. | The **Shipment consolidation workbench** page helps you find a set of shipments that aren't yet in a shipped state. These shipments are analyzed based on several key fields that are configured in your shipment consolidation policies. Any shipments where the values of these fields match are suggested for consolidation.<p>You can manually maintain the consolidation by removing shipments from suggested consolidations and/or by adding shipments to them. Several types of errors can occur, but you can override some of them.</p> |
| **Design note:** The *Automatic release of sales orders to warehouse* procedure splits sales lines into groups. Each group has its own unique **ReleaseToWarehouseId** value and is processed separately by the *Release to warehouse* procedure. This procedure creates new work regardless of the work break setup. | **Design note:** The *Automatic release of sales orders to warehouse* procedure assigns the same **ReleaseToWarehouseId** value to all sales lines that are being processed. All sales lines are processed by the *Release to warehouse* procedure at the same time. To ensure the earlier behavior, you must configure work break per shipment ID. |

## Related information

- [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]