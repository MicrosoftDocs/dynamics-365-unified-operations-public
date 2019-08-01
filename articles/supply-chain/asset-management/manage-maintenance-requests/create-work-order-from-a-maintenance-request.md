---
# required metadata

title: Create work order from a maintenance request
description: This topic explains how to create a work order from a maintenance request in Asset Management.
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
# Create work order from request



This topic explains how to create a work order from a request in Enterprise Asset Management. When you have created requests, you can easily convert the requests to work orders. The quickest way to work with requests, update several requests at a time, and subsequently create a work order for several requests at a time is described in this procedure. If required, you can also work with one request at a time and convert one request to one work order in the **Active requests** or **Active requests with no work order list**.

>[!NOTE]
>One request can only be related to one work order, but several requests can be included in one work order even if the requests have different objects.

1. Click **Enterprise asset management** > **Common** > **Requests** > **All requests**.
2. Before you can create a work order from a request, you must as a minimum select a job type and, if required, a job variant and a job trade for the requests for which you want to create a work order. In grid view, you can easily update data for a request.  
3. When you are ready to create a work order, select the requests you want to
include in one work order.

- If you multi-select several requests to be converted to one work order, the **Object** and **Job type** fields must be filled out before you start creating the work order. If you select one request to be converted to a work order, the **Object** field must be filled out before you start creating the work order, but **Job type** (and if relevant, related **Variant** and **Trade** fields) can be selected in the **Create work order** drop-down dialog box when you create the work order.  

4. Click the **Work order** button.
5. In the **Create work order** drop-down dialog, fill in the fields, and click **OK**.
6. A message may be shown that a new work order has been created.

- If you create a work order based on a request, and the object related to the request is included in a warranty agreement, a message informing you of the warranty agreement will be shown on the screen.  

7. Open the new work order in **Enterprise asset management** > **Common** > **Work orders** > **All work orders**.

![Figure 1](media/04-manage-requests.png)
