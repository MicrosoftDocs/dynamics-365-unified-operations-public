---
# required metadata

title: Modeling a lean organization
description: The article provides information about the key concepts in modeling a lean organization. 
author: johanhoffmann
ms.date: 09/24/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LeanProductionFlow, PlanActivity, KanbanFlowSelection, KanbanFlow
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 4f272f2f-ec2c-4b0d-a652-00a63b719b9e
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Modeling a lean organization

[!include [banner](../includes/banner.md)]

The article provides information about the key concepts in modeling a lean organization. 

Typically, a lean manufacturing scenario is more than just a collection of unrelated kanban rules or material supply policies. The flow of material and products throughout work cells and locations for a specific production or supply scenario can be described as a sequence or small network of process or transfer activities. This sequence or network is known as a production flow.

## Production flows in lean manufacturing
In production scenarios that are based on production orders, material is issued to a specific production order. During a sequence of operations that is based on a bill of materials (BOM) and routes, products are created and are finally received at the supplied location. The throughput time of production orders varies from minutes to weeks. All related cost, material, and labor are accumulated on the production order. 

To reduce the delivery lead times and excess inventory between work centers that batch production causes, lean manufacturing introduces kanban replenishment and supermarkets in manufacturing and warehouse replenishment. Typically, these features disrupt the production of partially independent kanban cycles. The replenishment of a kanban for a semi-finished product is no longer triggered by an order for a finished product. 

To re-establish a production and cost context for the various kanban scenarios that are proposed, activity-based production flows have been introduced as the backbone of lean manufacturing. All kanban rules refer to this predefined structure. The activity-based model supports the setup of a wide range of scenarios. However, this model doesn't add complexity for the shop floor workers, because all scenarios use the same activity-based user interface.

## Semi-finished products (non-BOM levels)
Lean manufacturing integrates kanbans for inventoried products and semi-finished products in a single framework, and therefore offers a unified user experience for all cases. Because of this architecture, additional BOM levels no longer have to be introduced to enable kanbans to be used for semi-finished products. This architecture also helps reduce inventory transactions to a minimum.

## Products and material in work in progress
The reduction of batch sizes to the ideal state of a single piece flow in lean manufacturing can cause a dramatic increase in inventory transactions if each picking process or kanban registration causes transactions for the consumed items. The production flow architecture allows for the transfer of material to the production flow, together with the withdrawal kanbans in storage or transport handling unit sizes. The value of the issued material is added to the work in progress (WIP) account that is related to the production flow. This behavior resembles the behavior for material that is issued to a production order. The same principle can be applied to products and semi-finished products. Unless these products are created, transferred, or consumed within a production flow, inventory transactions are optional. After the products are posted to inventory, the WIP account for the production flow is reduced by deducting by the related standard cost.

## Value streams and value stream mapping
The architecture of Lean manufacturing is inspired by the five Lean principles that were formulated by Womack and Jones: Customer value, Value stream, flow, pull, and perfection. One approved method for implementing lean manufacturing solutions in the physical world of manufacturing is value stream mapping (VSM). This method was introduced by Rother and Shook in their publication “Learning to See” at the Lean Manufacturing Institute. 

The future-state value stream can be modeled as a production flow version. All processes of the value stream are modeled as process activities. Movements or transfers can be modeled as transfer activities if the transfer status must be registered, or if integration with inventory picking or consolidated shipments is required. 

The value stream itself is modeled as an operating unit. Therefore, the value stream can be used as a financial dimension.

For more information about operating units, see [Create an operating unit](../../fin-ops-core/fin-ops/organization-administration/tasks/create-operating-unit.md).

## Costing for lean manufacturing based on the production flow
The periodic consolidation of the cost for a production flow corrects the related WIP account and enables variances to be determined for the products that are supplied by the production flow.

## Continuous improvement
To better support continuous improvement, the production flows are implemented in time-effective versions. Therefore, an existing production flow version, together with all related kanban rules, can be copied to a future version of the production flow. In addition, the future-state production flow can be modeled before it's validated and activated for production. To help guarantee a seamless material flow on the transition date and beyond, existing kanbans from old production flow versions are automatically related to the new version.

## Simplicity
For the implementation of Lean manufacturing, we choose a production flow and activity approach that enables simple and complex production scenarios to be modeled in a single scalable architecture. A closer look at the activity concept reveals a new simplicity for those users who require it: the shop floor and logistics workers. By reporting against activity-based jobs instead of inventory transactions, a unified user interface for all lean manufacturing variants transfers the business complexity from the user interface to where it belongs: the production flow as the backbone of lean manufacturing.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]