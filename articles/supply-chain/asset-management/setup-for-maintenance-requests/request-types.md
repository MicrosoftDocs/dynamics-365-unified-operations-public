---
# required metadata

title: Request types
description: This topic explains how to set up a request type in Enterprise Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Request types



This topic explains how to set up a request type in Enterprise Asset Management. A request type is used to categorize requests, for example relating to preventive maintenance, corrective maintenance, or a special request type that manages repair of objects, which could be called "depot repair".

A request type defines the request stage group affiliation. **Request stage group** defines which stages can be set for a request, for example, "Created", "Active", and "Ended".

1. Click **Enterprise asset management** > **Setup** > **Request** > **Request Types**.
2. Click **New** to create a new request type.
3. Insert the request type ID in the **Request type** field and a name for the request type in the **Name** field.
4. Select a stage group in the **Request stage group** field.
5. Select a work order type in the **Work order type** field. When a request is converted to a work order, the work order automatically gets the work order type related to the request type.

The following figure shows a screenshot of the interface.

![Figure 1](media/07-setup-for-requests.png)
