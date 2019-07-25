---
# required metadata

title: Maintenance request types
description: This topic explains how to set up a request type in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 07/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
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

A maintenance request type is used to categorize maintenance requests, for example relating to preventive maintenance, corrective maintenance, or a special request type that manages repair of assets, which could be called "depot repair".

A maintenance request type defines the request stage group affiliation. **Request stage group** defines which stages can be set for a request, for example, "Created", "Active", and "Ended".


1. Click **Asset management** > **Setup** > **Maintenance request** > **Maintenance request types**.
2. Click **New** to create a new request type.
3. Insert the maintenance request type key in the **Maintenance request type** field and a name for the request type in the **Name** field.
4. Select a lifecycle model in the **Maintenance request lifecycle model** field.
5. Select a work order type in the **Work order type** field. When a request is converted to a work order, the work order automatically gets the work order type related to the request type.

The following figure shows a screenshot of the interface.

![Figure 1](media/07-setup-for-requests.png)
