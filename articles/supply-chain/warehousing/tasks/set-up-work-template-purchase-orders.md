--- 
# required metadata 
 
title: Set up a work template for purchase orders
description: This article describes how to set up a simple work template to be used when putting away received items. 
author: Mirzaab
ms.date: 08/08/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSWorkTemplateTable, SysQueryForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up a work template for purchase orders

[!include [banner](../../includes/banner.md)]

This article describes how to set up a simple work template to be used when putting away received items. Work templates determine the set of instructions presented to the warehouse worker on a mobile device when moving items from the receiving area. You can use this procedure with the data mentioned in demo data company USMF. Before you start this guide, create a work pool ID. In this example, a work pool ID called in Inbound is used. This procedure is intended for the warehouse manager.

1. Go to **Warehouse management > Setup > Work > Work templates**.
2. In the **Work order type** field, select **Purchase orders**.

## Create a work template header
1. Select **New**.
2. In the **Sequence number** field, enter a number. This is the sequence in which the work templates are evaluated. You can modify the sequence, if needed.  
3. In the **Work template** field, type a value. This is the unique identifier for this template.  
4. In the **Work template description** field, type a value.
    - The **Valid** option will not be checked until you've completed all the information that's needed by the template and have then selected **Save**.  
    - A work order of type **Purchase order** cannot be automatically processed, so leave the **Automatically process** option set to **No**.  
5. In the **Work pool ID** field, type a value. Work pool IDs allow you to organize work into groups. The value that you set here will be the default value for any work that's created using this template.  
6. In the **Work priority** field, enter `1`. This indicates the importance of the work, and the value that you set here will be the default for any work created using this template.  
7. Select **Save**. You must save the work template header before the **Edit Query** button becomes available.  

## Set up the query for the work template
1. Select **Edit query**. We'll set a limitation that the template can only be used within a specific warehouse.  
2. Select **Add**.
3. In the **Field** field of the new row, type `warehouse`.
4. In the **Criteria** field, type a value.
5. Select **OK**.
6. Select **Yes**.

## Set work template details
1. Select **New**.
2. In the **Work type** field, select **Pick**.
3. In the **Work class ID** field, type `purchase`. The work class that you set here will be the default on all work lines of type Pick that are created using this template. The work class cannot be overridden from the work order lines. Work classes are used to direct and/or limit the type of work order lines a warehouse worker can process on a mobile device.  
4. Select **New**.
5. In the **Work type** field, select **Put**.
6. In the **Work class ID** field, type a value. The pick and put instructions are a set. Each pick/put set must have the same work class. Use the same work class that you provided for the pick instruction.  
7. Select **Save**. Note that the **Valid** checkbox is now checked.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]