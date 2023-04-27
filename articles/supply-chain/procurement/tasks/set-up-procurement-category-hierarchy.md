--- 
# required metadata 
 
title: Set up a procurement category hierarchy
description: This procedure shows you how to create new nodes in a procurement category hierarchy and how to configure a procurement category to be used in a procurement process. 
author: GalynaFedorova
ms.date: 06/21/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up a procurement category hierarchy

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create new nodes in a procurement category hierarchy and how to configure a procurement category to be used in a procurement process. These tasks would typically be carried out by a Purchasing manager. Before you can start this procedure, there must be a category hierarchy of type Procurement. If you're using a demo data company, you can run this procedure in the USMF company.


## Add a new procurement category
1. Go to **Procurement and sourcing > Procurement categories**.
2. On the Action Pane, select **Edit category hierarchy**. The current procurement category hierarchy is displayed in the left side of the page. You  are about to modify the hierarchy.  
3. On the Action Pane, select **New category node**. The system selects the top node by default. If you're running this procedure as a task guide, you can click the Unlock button and select another parent node to insert your new node into. Once that is done, lock the task guide again and then click New category node.  
4. In the **Name** field, type a value.
5. In the **Description** field, type a value.
6. In the **Friendly name** field, type a value. The friendly name is optional. It will be displayed in category lookups together with the category name.  
7. Select **Save**.

## Add products to your new procurement category
1. Go to **Procurement and sourcing > Consignment > Procurement categories**. Select the node you just added. If you're running this procedure as a task guide you might need to unlock the task guide to select the node.  
2. Toggle the expansion of the **Products** section.
3. Select **Add** to associate products with the procurement category.
4. Select the products you want to add to the procurement category.
5. Select the arrow to add the products to the **Selected** table.
6. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
