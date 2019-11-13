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

a. The business choses to rely on their warehouse operations to manage picking of quantities with batch/serial numbers after the said quantities have been located within the warehousing storage space. This model - referred to as &quot;Batch-below[location]&quot; - is common when product&#39;s batch/serial number identification is of no importance to the customers when placing the demand with the selling company.
b. When batch/serial numbers are part of the customer&#39;s order specification and are recorded on the demand order, the warehouse operations are constrained by the requested specific numbers when locating the quantities within the warehouse, and are not allowed to change them. This is a &quot;Batch-above[location]&quot; reservation hierarchy type.

The challenge with the above principle is that any given released product can have only one inventory reservation hierarchy assigned to it. This implies that in order for the warehouse management system to support handling of the tracked item, the decision on timing for when batch/serial number is reserved, i.e. at demand order taking or during the warehouse picking work, once taken by means of hierarchy assignment, cannot be changed ad-hoc.
