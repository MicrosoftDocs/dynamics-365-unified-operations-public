--- 
# required metadata 
 
title: Create a procurement catalog
description: This guide shows you how to create a procurement catalog. 
author: mkirknel
manager: AnnBe 
ms.date: 08/23/2016
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
# Create a procurement catalog

[!include[task guide banner](../../includes/task-guide-banner.md)]

This guide shows you how to create a procurement catalog. This task would typically be carried out by a procurement professional. You will also learn how employees can use the catalog when they create a requisition. Before you can create a catalog, there must be a procurement category hierarchy in your system. The hierarchy is inherited by the new catalog, along with all the products that are in the hierarchy. You can use this guide in demo data company USMF where the procurement category hierarchy is available, as well as the examples used in the procedure steps.


## Ensure that a procurement category hierarchy exists
1. Go to Procurement and sourcing > Procurement categories.
    * A procurement category hierarchy is available in the USMF demo data company and products have been added to the Office machines/Computers category. If you’re running this procedure as a task guide, you’ll need to unlock the guide if you want to browse through the category. If a hierarchy was not available, you’d create it by clicking New. This can only be done once.  
2. Close the page.

## Create a catalog
1. Go to Procurement and sourcing > Catalogs > Procurement catalogs.
2. Click New procurement catalog to open the drop dialog.
3. In the Name field, type a value.
4. Click OK.
5. In the tree, expand 'CORP PROCUREMENT CATEGORIES'.
6. In the tree, expand 'OFFICE MACHINES'.
7. In the tree, select 'Computers'.
    * The products from the procurement category are displayed in the list. If you want to add a product to the category you need to do this on the Procurement category hierarchy page or on the Item details page.  
    * The Default update type determines whether new products that have been added to the procurement category hierarchy are immediately visible in the catalog. If the update type is set to Dynamic, changes are visible immediately. If the update type is Static, new products are only visible to people using the catalog after the catalog has been re-published. The Publish action is available on the Action Pane at the top of the page. If products are removed from the procurement category hierarchy, the change is immediately visible, regardless of the value in the Default update type field.  
8. In the list, find and select the desired record.
9. Click Hide.
10. On the Action Pane, click Category navigation.
11. Click Disable.
12. On the Action Pane, click Category navigation.
13. Click Enable.
14. Click Activate catalog.
15. Close the page.

## Make the catalog visible
1. Go to Procurement and sourcing > Setup > Policies > Purchasing policies.
2. Select Procurement Policy USMF.
    * You need to select the purchasing policy for the legal entity that the worker connected to your user profile is allowed to order products in. In the USMF demo data, the Admin user is connected to the worker called Julia Funderburk, and she orders products in USMF by default.  
3. In the list, click the link in the selected row.
4. Select the catalog that you’ve just created.
5. Click OK.
6. Close the page.
7. Close the page.

## Use the catalog
1. Go to Procurement and sourcing > Purchase requisitions > All purchase requisitions.
2. Click New.
3. In the Name field, type a value.
4. Click OK.
5. Click Add products.
6. In the list, find and select the desired record.
    * You can use the category hierarchy on the left or the filter at the top of the list to filter the products.  
7. Click Add to lines.
8. In the list, find and select the desired record.
9. Click Add to lines.
10. Click OK.

