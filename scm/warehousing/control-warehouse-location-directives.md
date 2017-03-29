---
# required metadata

title: Control warehouse work by using work templates and location directives
description: This article describes how to use work templates and location directives to determine how and where work is carried out in the warehouse.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-03-30 13 - 17 - 44
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: WHSLocDirFailure, WHSLocDirHint, WHSLocDirTable, WHSLocDirTableUOM, WHSRFMenuItem, WHSWork, WHSWorkClass, WHSWorkPool, WHSWorkTemplateTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 72921
ms.assetid: 377ab8af-5b0c-4b5e-a387-06ac1e1820c0
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Control warehouse work by using work templates and location directives

This article describes how to use work templates and location directives to determine how and where work is carried out in the warehouse.

The instructions that warehouse workers receive on a mobile device are determined by the work templates that you set up in Microsoft Dynamics 365 for Operations to define the various warehouse processes and tasks. Work templates determine how the work is performed for each warehouse process. By linking a location directive to work templates, you can help guarantee that work occurs in specific physical areas of the warehouses.

## Work templates
The **Work templates** page lets you define the work operations that must be performed in the warehouse. Typically, warehouse work operations consist of a pair of actions: a warehouse worker picks up on-hand inventory in one location and then puts the picked inventory down in another location. 

Work templates consists of a header and associated lines. Each work template is for a specific *work order type*. Many work order types are associated with source documents, such as purchase or sales orders. However, other work order types represent separate warehouse processes, such as cycle counting. The *work pool ID* lets you organize work into groups. 

The settings in the work header definition can be used to determine when a new piece of work should be created. For example, you can set a maximum number of pick lines and a maximum expected pick time. Then, if the work for a sales order picking process exceeds either of those values, that work is split into two pieces of work. 

The work lines represent the physical tasks that are required in order to process the work. For example, for an outbound warehouse process, there might be a work line for picking up the items within the warehouse and another line for putting those items into a staging area. There can then be an additional line for picking the items from staging, and another line for putting the items into a truck as part of the loading process. You can set a *directive code* on work template lines. A directive code is linked to a location directive and therefore helps guarantee that the warehouse work is processed in the correct location in the warehouse. 

You can set up a query to control when a particular work template is used. For example, you can set a limitation so that a particular template can be used for work only in a specific warehouse. Alternatively, you might have several templates that are used to create work for outbound sales order processing, depending on the sales origin. The system uses the **Sequence number** field to determine the order that the available work templates are assessed in. Therefore, if you have a very specific query for a particular work template, you should give it a low sequence number. That query will then be evaluated before other, more general queries. 

To stop or pause a work process, you can use the **Stop work** setting on the work line. In that case, the worker who is performing the work won't be asked to perform the next work line step. To move on to the next step, that worker or another worker must select the work again. You can also separate the tasks within a piece of work by using a different *work class ID* on the work template lines.

## Location directives
Location directives are rules that help identify pick and put locations for inventory movement. For example, in a sales order transaction, a location directive determines where the items will be picked, and where the picked items will be put. Location directives consist of a header and associated lines, and you create them on the **Location directives** page. 

On the header, each location directive must be associated with a *work order type* that specifies the type of inventory transaction that the directive will be used for, such as sales orders, replenishment, or raw material picking. The *work type* specifies whether the location directive will be used for picking or putting work, or for some other warehouse process, such as counting or inventory status changes. You must also specify a *site* and a *warehouse*. A *directive code* that you specify on the header can be used to link the location directive to one or more work templates. 

As for work templates, you can set up a query to determine when a particular location directive is used. For example, you can specify that when e-commerce is the origin of a sales order, the inventory must be picked up from a dedicated area in the warehouse. The system uses the **Sequence number** field to determine the order that the available location directives are assessed in. 

The location directive lines set additional restrictions on the application of the location finding rules. You can specify a minimum quantity and a maximum quantity that the directive should apply to, and you can specify that the directive should be for a specific inventory unit. For example, if the unit of measure is pallets, the items in pallets can be put in a specific location. You can also specify whether the quantity can be split across multiple locations. Like the location directive header, each location directive line has a sequence number that determines the order that the lines are assessed in. 

Location directives have one additional level of detail: *location directive actions*. You can define multiple location directive actions for each line. Once again, a sequence number is used to determine the order that the actions are assessed in. On this level, you can set up a query to define how to find the best location in the warehouse. You can also use predefined **Strategy** settings to find an optimal location.

### Example of the use of location directives

For this example, we will consider a purchase order process where the location directive must find free capacity within a warehouse for inventory items that have just been registered at the receiving dock. First, we want to try to find free capacity within the warehouse by consolidating with existing on-hand inventory. If consolidation isn't possible, we then want to find an empty location. 

For this scenario, we must define two location directive actions. The first action in the sequence must use the **Consolidate** strategy, and the second should use the **Empty location with no incoming work** strategy. Unless we define a third action to handle an overflow scenario, two outcomes are possible when there is no more capacity in the warehouse: work can be created even though no locations are defined, or the work creation process can fail. The outcome is determined by the setup on the **Location directive failures** page, where you can decide whether to select the **Stop work on location directive failure** option for each work order type.

