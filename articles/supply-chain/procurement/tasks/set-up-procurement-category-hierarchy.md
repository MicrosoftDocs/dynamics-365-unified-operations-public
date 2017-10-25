--- 
# required metadata 
 
title: Set up a procurement category hierarchy
description: This procedure shows you how to create new nodes in a procurement category hierarchy and how to configure a procurement category to be used in a procurement process. 
author: mkirknel
manager: AnnBe 
ms.date: 11/11/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up a procurement category hierarchy

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to create new nodes in a procurement category hierarchy and how to configure a procurement category to be used in a procurement process. These tasks would typically be carried out by a Purchasing manager. Before you can start this procedure, there must be a category hierarchy of type Procurement. If you're using a demo data company, you can run this procedure in the USMF company.


## Add a new procurement category
1. Go to Procurement and sourcing > .. > Procurement categories.
2. Click Edit category hierarchy.
    * The current procurement category hierarchy is displayed in the left side of the page. You  are about to modify the hierarchy.  
3. Click New category node.
    * The system selects the top node by default. If you are running this procedure as a task guide, you can click the Unlock button and select another parent node to insert your new node into. Once that is done, lock the task guide again and then click New category node.  
4. In the Name field, type a value.
5. In the Description field, type a value.
6. In the Friendly name field, type a value.
    * The friendly name is optional. It will be displayed in category lookups together with the category name.  
7. Click Save.

## Add products to your new procurement category
1. Go to Procurement and sourcing > .. > Procurement categories.
    * Select the node you just added. If you’re running this procedure as a task guide you might need to unlock the task guide to select the node.  
2. Toggle the expansion of the Products section.
3. Click Add to associate products with the procurement category.
4. Select the product you want to add to the procurement category.
5. Click the arrow to select the product.
6. Select another product to add to the procurement category.
7. Click the arrow to select the product.
8. Click OK.

## Add approved and preferred vendors
1. Toggle the expansion of the Vendors section.
2. Click Add.
    * You can add a vendor to a procurement category and specify whether a vendor is preferred or just approved for the category. When you delete a vendor from a category, the historical transactions with the vendor in the category are not deleted.   
3. Find the vendor you want to add to the category.
4. Click the arrow to select the vendor.
5. Click OK.
6. Select the vendor row that you want to modify.
7. In the Vendor status field, select an option.
    * The vendor selection setting in the Category policy rule governs whether preferred, approved, or all vendors are available on purchase requisitions.   

## Add additional information to the category
1. Toggle the expansion of the Vendor evaluation criterion groups section.
    * This tab allows you to define which criteria the vendors in the procurement category should be rated against. To do this you would click Add and then select a vendor evaluation group that contains the criteria you want.  
2. Toggle the expansion of the Questionnaires section.
    * This tab allows you to add questionnaires that will appear on the requisition, as long as you set the Activity type to "Requisition". The requester then has to fill out a questionnaire before they submit a requisition for the specific product or products in the procurement category.  
3. Toggle the expansion of the Item sales tax groups section.
4. In the Item sales tax group: field, click the drop-down button to open the lookup.
5. Select a sales tax group.
6. Toggle the expansion of the Category page section.
    * Category pages are created in the Category hierarchy page. They contain information about the procurement category such as information about the type of products in a category, images of products in a category, or announcements such as the discounts that are available in a category. The information in a category page is displayed on purchase requisitions.  
7. Close the page.

