---
# required metadata

title: Maintenance request types
description: This topic explains how to set up a maintenance request types in Asset Management.
author: josaw1
manager: tfehr
ms.date: 07/26/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2019-07-30
ms.dyn365.ops.version: AX 7.0.0

---

# Maintenance request types

[!include [banner](../../includes/banner.md)]

 

Maintenance request types are used to categorize maintenance requests. For example, you might have maintenance request types that are related to preventive maintenance and corrective maintenance. Or you might have a special maintenance request type that is used to manage repair of assets (depot repair).

A maintenance request type defines the affiliation with a maintenance request lifecycle state group (maintenance lifecycle model). Maintenance request lifecycle models define the lifecycle states that can be set for a maintenance request. (Examples of maintenance request lifecycle states include **Created**, **Active**, and **Ended**.)

1. Select **Asset management** \> **Setup** \> **Maintenance requests** \> **Maintenance request types**.
2. Select **New** to create a maintenance request type.
3. In the **Maintenance request type** field, enter an ID for the maintenance request type.
4. In the **Name** field, enter a name.
5. On the **General** FastTab, in the **Maintenance request lifecycle model** field, select a maintenance request lifecycle model.
6. In the **Work order type** field, select a work order type. When a maintenance request is converted to a work order, the work order automatically gets the work order type that is related to the maintenance request type.

The following illustration shows an example of the **Maintenance request types** page.

![Maintenance request types page](media/07-setup-for-requests.png)
