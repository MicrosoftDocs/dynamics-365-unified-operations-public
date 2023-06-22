--- 
# required metadata 
 
title: Configure access rights for a cost object controller
description: Use this procedure to configure access rights for a cost object controller. 
author: twheeloc
ms.date: 03/27/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure access rights for a cost object controller

[!include [banner](../../includes/banner.md)]

Use this procedure to configure access rights for a cost object controller. This recording uses the USP2 demo data company.


## Assign the cost object controller role
1. Go to **System administration > Users > Users**.
2. Use the Quick Filter to find records. For example, filter on the **User name** field with a value of 'alicia'.
3. In the list, click the link in the selected row.
4. Click **Assign roles**.
5. In the list, find and select the desired record.
6. Click **OK**.

## Enable access list security
1. Go to **Cost accounting > Dimensions > Dimension hierarchies**.
2. In the list, find and select the desired record.
    * Select **Organization**.  
3. Click **Edit**.
4. Select **Yes** in the **Access list hierarchy** field.
5. Click **View hierarchy**.

## Assign access rights to user
1. Click **New**.
2. In the list, mark the selected row.
3. In the **User ID** field, enter or select a value.
    * Select **Admin**.  
4. In the tree, select 'Organization\CEO\CFO\FIM'.
5. Click **New**.
6. In the list, mark the selected row.
7. In the **User ID** field, enter or select a value.
    * Select Alicia.  
8. Click **Save**.

## Enable access rights in Cost accounting
1. Go to **Cost accounting > Setup > Parameters**.
2. Click the **General** tab.
3. Select **Yes** in the **Enable view access for cost object dimension members** field.
4. Click **Save**.
5. Close the page.
6. Go to **Cost accounting > Setup > Cost control workspace configuration**.
7. Click **Edit**.
8. Select **Yes** in the **Published** field.
    * If you select **Yes**, a user who is assigned one of the following four roles can see the reports in the **Cost control** workspace: cost accounting manager, cost accountant, cost accountant clerk, and cost object controller. If you select No, only a user who is assigned one of the following roles can see the reports: cost accounting manager, cost accountant, and cost accountant clerk.    
9. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
