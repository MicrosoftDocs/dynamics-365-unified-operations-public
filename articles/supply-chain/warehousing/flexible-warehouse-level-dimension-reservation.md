---
# required metadata

title: Flexible warehouse-level dimension reservation 
description: This topic describes an enhancement to the inventory reservation policy that allows businesses, who sell batch-tracked products and run their logistics as WMS-enabled operations, to reserve specific batches for their customers’ sales orders even though the reservation hierarchy associated with such products disallows this (by being of a type that is commonly referred to as “Batch-below[location]”.)
author: omulvad
manager: AnnBe
ms.date: 11/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSReservationHierarchy 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2020-01-15
ms.dyn365.ops.version: 10.0.9

---

# Flexible warehouse-level dimension reservation

[!include [banner](../includes/banner.md)]

This topic describes an enhancement to the inventory reservation policy that allows businesses, who sell batch-tracked products and run their logistics as WMS-enabled operations, to reserve specific batches for their customers’ sales orders even though the reservation hierarchy associated with such products disallows this (by being of a type that is commonly referred to as “Batch-below[location]”.)

## Inventory reservation hierarchy

Below is a summary of the existing inventory reservation hierarchy with focus on handing the batch- and serial-tracked items. Inventory reservation hierarchy concept is described in more details [insert link].

Inventory reservation hierarchy dictates that as far as storage dimensions are concerned, it is the demand order that carries the mandatory dimensions of site, warehouse, and inventory status, while it is the warehouse logic that is responsible for assigning and reserving a location to the requested quantities. In other words, in the interactions between the demand order and the warehouse operations, the demand order is expected to say from where - site and warehouse - the order must be shipped, and the warehouse then relies on its logic to locate the required quantity within the warehouse premises.

Tracking dimensions - batch and/or serial numbers - are, however, a subject to more flexibility, that is meant to reflect the business&#39;s operational model. Here, an inventory reservation hierarchy can accommodate scenarios where:

1. The business choses to rely on their warehouse operations to manage picking of quantities with batch/serial numbers after the said quantities have been located within the warehousing storage space. This model - referred to as &quot;Batch-below[location]&quot; - is common when product&#39;s batch/serial number identification is of no importance to the customers when placing the demand with the selling company.
2. When batch/serial numbers are part of the customer&#39;s order specification and are recorded on the demand order, the warehouse operations are constrained by the requested specific numbers when locating the quantities within the warehouse, and are not allowed to change them. This is a &quot;Batch-above[location]&quot; reservation hierarchy type.

The challenge with the above principle is that any given released product can have only one inventory reservation hierarchy assigned to it. This implies that in order for the warehouse management system to support handling of the tracked item, the decision on timing for when batch/serial number is reserved, i.e. at demand order taking or during the warehouse picking work, once taken by means of hierarchy assignment, cannot be changed ad-hoc.

## Flexible reservation for batch-tracked items

### Business scenario

Due to the nature of its manufactured products, a company employs an inventory strategy of tracking its finished goods by batch numbers. As the said company also uses the D365F&amp;O Warehouse Management System workload, that has a well-equipped logic for planning and executing warehouse pick and ship operations for batch-enabled items, most of the finished items are associated with a &quot;Batch-below[Location]&quot; inventory reservation hierarchy. The advantage behind such an operational setup is that decisions (that are effectively, reservation decisions) about which batches to pick and where to locate them within the warehouse are postponed until the warehouse picking operations start as opposed to when the customer&#39;s order is placed.

While the &quot;Batch\_below[location]&quot; inventory reservation hierarchy serves the company&#39;s business goals well, there are multiple of its established customers that when reordering products require the same batch as previously purchased. In essence, the company is looking for flexibility in handling the batch reservation rules, where depending on the customers&#39; demand for the same item:

- a batch number can be recorded and reserved at the order taking time by the sales processor, with no possibility to be changed during warehouse operations and/or being taken by other demands, hence ensuring the ordered batch number is shipped to the customer
- when irrelevant to the customer, a batch number(s) can be decided beyond the sales order registration and reservation by the warehouse operations during picking work

### Allowing specific batch reservation on the sales order

To accommodate the desired flexibility in the batch reservation behaviour for items that are associated with a &quot;Batch\_below[location]&quot; inventory reservation hierarchy, inventory managers must enable the **Allow reservation on demand order** field for the Batch number level.

Be aware that when **Batch number** level in the hierarchy is selected, all other dimensions that are above and up to the location will be selected automatically. This behaviour is meant to convey the logic according to which, once you reserve a specific batch number on the order line, all dimensions in the range between the batch number and location are also automatically reserved (see more details in the sections below).

 > [!NOTE]
 > The **Allow reservation on demand order** option only applies to reservation hierarchy levels that are below the warehouse location dimension.
 
 > In the current implementation, Batch number is the only level in the hierarchy that is open for flexible reservation policy. That means that you cannot set checkmark in the **Allow reservation on demand order** field for Location, License plate or Serial number.
 
 > If your reservation hierarchy includes Serial number dimension (which must always be placed below the Batch number level) and you have enabled batch-specific reservation for the Batch number, the program will continue handling serial number reservation and picking operations based on rules applicable to &quot;Serial\_below[location]&quot; reservation policy.
 
You can allow batch-specific reservation for an existing &quot;Batch\_below[location]&quot; hierarchy at any point of time in your deployment. This will not affect any reservations or open warehouse work that have been created prior to this change. However, removal of the **Allow reservation on demand order** option is disallowed when there are existing inventory transactions of issue type Reserved ordered, Reserved physical, or Ordered for one or more items that are associated with that reservation hierarchy.

 > [!NOTE]
 > You can also change item&#39;s existing reservation hierarchy from the one that does not allow batch specification on the order to the one that does, provided the hierarchy level structure is identical in both hierarchies. Use the standard **Change reservation hierarchy for items** function to perform the desired reassignment. This may be relevant when you wish to disallow flexible batch reservation for a subset of batch-tracked items and allow it for the rest of the product portfolio.

