---
# required metadata

title: Configure shipment consolidation policies
description: This topic provides an overview of functionality that provides flexible configuration of shipment consolidation policies.
author: GarmMSFT
manager: PJacobse
ms.date: 12/31/2019
ms.topic: configure-shipment-consolidation-policies
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: PJacobse
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: v-olbara
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.3

---
# About shipment consolidation policies

# Released in version 10.0.3

# About

The shipment consolidation process using shipment consolidation policies allows for automated shipment consolidation during automated and manual release to warehouse. Prior the introduction of this functionality the consolidation functionality allowed automated consolidation with hardcoded fields and based on the “Consolidate shipment at release to warehouse” filed at warehouse level.

The shipment consolidation policies are used at following instances of functionality: 1) automated release to warehouse batch job, 2) release to warehouse function from the sales or transfer order, 3) separate release to warehouse form, 4) release to warehouse function from the Load planning workbench, and 5) the manual consolidation of shipment workbench .

Prior the introduction of this functionality the consolidation function was a setting at the warehouse level, where the application treated all customers from a single warehouse with the same consolidation requirement. This represented a limitation. The consolidation of shipment policies caters for scenarios where different end customers can have different requirements for shipment consolidation.

The shipment consolidation policies follow the pattern of e.g. the wave templates, where queries are used for identifying the applicability of the specific policy and then a modifiable set of fields drives how to group the load lines on shipment level. In addition, a setting “consolidate with existing shipments” is added to each policy allowing the policy to consult all open shipments that match the policy – in this case the load will not be created but the existing one will be used.

The “Consolidate shipment at release to warehouse” field, present prior introducing this feature at the warehouse setup form, will be hidden from the interface. As an assistance while transitioning, a function is added on Shipment consolidation policies form to create a default policy and include the warehouses with the old setting into it automatically. After that, the checkbox on “consolidate shipment at release to warehouse” at the warehouse setup will no longer be taken into account.

“Release to warehouse form” can be used to manually override the applicable consolidation policy, in a similar fashion that it is possible to override the fulfilment policies.

“Release to warehouse from Load planning workbench “ - the functionality allows to build the outbound loads based on sales and transfer order lines before releasing to warehouse and use the same consolidation logic introduced with the consolidation of shipment policies.  

The “Shipment consolidation workbench“ allows for consolidation of existing shipments after release to warehouse for shipments that are not yet confirmed. The functionality caters for the scenario where the automated release process with its own shipment consolidation are ran multiple time during a day – but prior completing the shipment to carriers during the confirmation process, a manual process can be undertaken that identifies potential additional consolidations. The shipment consolidation workbench and the downstream manual confirmation of proposed consolidated shipment functionality allows to consolidate the outbound shipments created from sales or transfer order lines at any point after release to warehouse and before confirming the shipment. The user interaction of the form is similar to the one achieved with the load building workbench, where you can assess multiple shipment at the time and have the ability to assigned non-consolidated order to a specific shipment. Shipment consolidation templates are available for the user to apply in order to have proposed consolidations to assess, and confirm by manually creating the shipment. Some rules are implemented to prevent unauthorized consolidation as well as provide functionality to warn user of possible errors.

# Overview of new functionality

## Shipment consolidation policies (form)

The policies are differentiated based on work order types (Sales orders to Sales orders shipments, Transfer orders to Transfer issue shipments).

Each shipment consolidation policy has a query used for defining the applicability and a sequence number in which it will be applied. The consolidation is applied for each unique combination of the selected fields. An additional parameter to consolidate with existing (open) shipments is included. The policies are evaluated and applied when new shipments are created which is before wave processing.

If a Policy either doesn’t have any mandatory field or has any prohibited field in the “Selected” section, the Policy is marked as invalid. The lists of mandatory/forbidden fields are hardcoded and can be extended.

The mandatory field list (the shipments are always split by these fields, or in other words you cannot group several shipments with different values on these fields):

For sales orders:

- WHSShipmentTable. AccountNum
- WHSShipmentTable. DeliveryName
- WHSShipmentTable. DeliveryPostalAddress
- WHSShipmentTable. InventLocationId

For transfer orders:

- InventTransferTable. InventLocationIdFrom
- InventTransferTable. InventLocationIdTo

Following fields are unavailable to the user for all document types (these fields are not visible on the UI and cannot be used for consolidation):

- WHSShipmentTable.ShipmentId
- WHSShipmentTable.ShipmentStatus
- WHSShipmentTable.ShipConsolidationPolicyName
- WHSShipmentTable.WorkTransType
- WHSShipmentTable.WaveId
- WHSShipmentTable.LoadId
- WHSLoadLine.ShipmentId
- WHSLoadLine.LoadId

The consolidation fields defaults to the mandatory set of fields when a new policy is created, but can be modified with left-right arrows (similar user interaction pattern as for methods in “Wave templates”).

Values of these fields, selected by a user, will be equal in a new shipment being created or added to an existing shipment (consolidate with existing shipment). When the values of a field selected for consolidation of two shipments is the same the shipment are consolidated (if this remain the case for all the subsequent selected consolidation fields), if they differ then the second shipment is discarded and will be selected for a new shipment. The process during the automated consolidation consists of creating all the unique combination of values of the consolidate shipment fields and assign the shipment to the relevant combination.

Values in not-selected fields are ignored during the consoldation process. If not selected field has different values in two shipments, it will be cleared (set to blank). If a field was not selected but has the same values in both shipments, it will be filled in.

The list of consolidation fields (fields which will be cleared when they have different values) is hardcoded. The list contains all fields which are initialized from a sales line or transfer line when a new shipment is created. I.e. if a field is not initialized from a sales line or transfer line, it is ignored when new data is being added into existing shipment.

## Release to warehouse (form)

- A new field was added to the lower grid to display currently applied consolidation policy
- A new button was added to manually select the consolidation policy and override

## Release to warehouse (menu item) at Load planning workbench (form)

- Logic was adjusted to use applied consolidation policies
- Shipments are consolidated only within a single load

## Consolidate shipments (form)

- Search for similar shipments (candidates for consolidation) modified to use fields selected on shipment consolidation policy
- Fields that have different values in different shipments are now set to blank (previously the values from the selected “base” shipment were used)

## Shipment consolidation workbench (form)

- New functionality that replicates the process of manual consolidation on a larger scale
- Can be open from the Release to warehouse menu of Warehouse management module
- The algorithm analyzes existing shipments (not Shipped yet) and proposes consolidation based on fields selected in consolidation policies

## Comparison of functionality before and after (table TODO)

# Related articles and demo scripts

- [Configure shipment consolidation policies](../configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../consolidate-shipments.md)

