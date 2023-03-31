--- 
# required metadata 
 
title: Create a procurement catalog
description: This article explains how to create a procurement catalog. 
author: GalynaFedorova
ms.date: 07/19/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ProcCategoryHierarchyManagement, CatProcureCatalogListPage, CatProcureCatalogCreate, CatProcureCatalogEdit, SysPolicyListPage, SysPolicy, CatCatalogPolicyRule, PurchReqTableListPage, PurchReqCreate, PurchReqTable, PurchReqAddItem   
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
# Create a procurement catalog

[!include [banner](../../includes/banner.md)]

This article explains how to create a procurement catalog. This task would typically be carried out by a procurement professional. You will also learn how employees can use the catalog when they create a requisition. Before you can create a catalog, there must be a procurement category hierarchy in your system. The hierarchy is inherited by the new catalog, along with all the products that are in the hierarchy. You can use this guide in demo data company USMF where the procurement category hierarchy is available, as well as the examples used in the procedure steps.


## Ensure that a procurement category hierarchy exists
1. Go to **Procurement and sourcing > Procurement categories**. A procurement category hierarchy is available in the USMF demo data company and products have been added to the **Office machines/Computers** category. If you're running this procedure as a task guide, you'll need to unlock the guide if you want to browse through the category. If a hierarchy was not available, you'd create it by clicking **New**. This can only be done once.  
2. Close the page.

## Create a catalog
1. Go to **Procurement and sourcing > Catalogs > Procurement catalogs**.
2. Select **New procurement catalog** to open the drop dialog.
3. In the **Name** field, type a value.
4. Select **OK**.
5. In the tree, expand **CORP PROCUREMENT CATEGORIES**.
6. In the tree, expand **OFFICE MACHINES**.
7. In the tree, select **Computers**.

  - The products from the procurement category are displayed in the list. If you want to add a product to the category you need to do this on the **Procurement category hierarchy** page or on the **Item details** page.  
  - The **Default** update type determines whether new products that have been added to the procurement category hierarchy are immediately visible in the catalog. If the update type is set to **Dynamic**, changes are visible immediately. If the update type is **Static**, new products are only visible to people using the catalog after the catalog has been re-published. The **Publish** action is available on the Action Pane at the top of the page. If products are removed from the procurement category hierarchy, the change is immediately visible, regardless of the value in the **Default** update type field.  

8. On the Action Pane, select **Category navigation** and ensure that **Enable** is selected.
9. Select **Activate catalog**.
10. Close the page.

## Make the catalog visible
1. Go to **Procurement and sourcing > Setup > Policies > Purchasing policies**.
2. Select **Procurement Policy USMF**. You need to select the purchasing policy for the legal entity that the worker connected to your user profile is allowed to order products in. In the USMF demo data, the Admin user is connected to the worker called **Julia Funderburk**, and orders products in USMF by default.  
3. Select the catalog that you've just created.
4. Select **OK**.

## Use the catalog
1. Go to **Procurement and sourcing > Purchase requisitions > All purchase requisitions**.
2. Select **New**.
3. In the **Name** field, type a value.
4. Select **OK**.
5. Select **Add products**.
6. In the list, find and select the desired record. You can use the category hierarchy on the left or the filter at the top of the list to filter the products.  
7. Select **Add to lines**.
8. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
