--- 
# required metadata 
 
title: Create a requisition for consumption
description: This article describes the process of creating a requisition. 
author: GalynaFedorova
ms.date: 07/09/2019
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
# Create a requisition for consumption

[!include [banner](../../includes/banner.md)]

This article describes the process of creating a requisition. It shows you different ways to search for products in your procurement catalog and how to add a product that isn't in your catalog. Before you start this procedure, you must have a purchasing policy set up with Consumption as the default type of requisition. You can walk through this procedure in demo data company USMF, or using your own data. The procedure can only be carried out by a user profile that is set up as worker. This task would normally be carried out by an employee. The **Employee** employ security role will allow you to carry out the tasks, or if you're using USMF, you can log in as **Alicia**.


## Create a new requisition
1. Go to **Procurement and sourcing > Purchase requisitions > Purchase requisitions prepared by me**.
2. Select **New**.
3. In the **Name** field, give the requisition a name.
4. In the **Requested date** field, enter a date. By default, the requested date and accounting date are copied to the purchase requisition lines. They can be changed at the line level. The requested date is the requested delivery date.  
5. In the **Accounting date** field, enter a date. The accounting date is used to record the accounting entry in the general ledger, and to validate whether budget funds are available.  
6. Select **OK**.
7. In the **Reason** field, select an option from the drop-down menu. By default, the business justification reason that you select appears for the purchase requisition lines, but you can change it at the line level.  
8. Select the reason.
9. In the **details** field enter a more descriptive justification for the requisition.

## Add a line to the requisition
1. Select **Add line**. There are two ways of adding lines to the purchase requisition. If you already know the product number or you already know that you are requesting a product that is not in the product catalog, then you can add the line directly with **Add line**. The other way is to use **Add products** where you can use searching and filtering to find items in the product catalog.    
2. Select the row you just created.
    - The requester is the worker that has requested the requisition.   
    - By default the person preparing the requisition is the worker who has requested it. You have to be given permission to prepare a requisition line on behalf of another worker. If you have such permissions then the other workers will show up in this lookup.  
3. In the **Item number** field, type a value. The items that are available for you to choose are limited by the category access policy and the procurement catalog for the buying legal entity.   
4. In the **Quantity** field, enter a number.

## Add more products to the requisition
1. Select **Add products**. This is the option where you can search for products in the product catalog.    
2. In the **Find procurement category node** field, enter the first part of the name of the category that you are looking for, and then select **Enter**. For example, enter `comput`.  
3. Use the **InvokeDefaultButton** shortcut.
4. Use the **Filter** to filter the list of products in the selected category.
5. Select the product card that you want to add to the requisition.
6. Select **Add to lines**.
7. In the **Quantity** field, enter a number.
8. In the **Find procurement category node** field, type the first part of the name of the category that you are looking for, and then select **Enter**. For example, enter `High` (highlighters).  
9. Use the **InvokeDefaultButton** shortcut.
10. Select **Add unlisted product to lines** to add a product that's not listed in the procurement catalog.
11. In the **Product name** field, type a value.
12. In the **Unit** field, type a value.
13. Select **OK**.
14. In the **Item description** field, add a description of the product.
15. In the **Quantity** field, enter a number.
16. In the **Unit price** field, enter a number. If you know the price for a particular vendor (that you select in the vendor account field) then that price can be entered.   
17. In the **Vendor account** field, open the drop-down list to select an option. The vendors that are available in this field depend on the purchasing policies and the status that the vendor has for the current procurement category. As an alternative to selecting a vendor here, you can select **Suggest vendor**.    
18. In the list, select the vendor you want to use.
19. In the **External item number** field, type a value. This is a reference number for the product that is known by the vendor. For example, this could be the item number of the product in the vendor's own catalog.  
20. Select **OK**.

## Distribute amounts
1. Select **Financials**.
2. Select **Distribute amounts**. This process shows you how to distribute the cost for the first line between 2 accounts. This can also be done later when the requisition is in review.  
3. Select **Split** to create a new distribution line.
4. In the **Ledger account** field select the first cost center that should take part of the cost.
5. Select the other distribution line.
6. In the Ledger account field specify the other cost center.
7. Select **Distribute equally**.
8. Close the page.

## View line details
1. Toggle the expansion of the **Line details** section.

## Submit the requisition
1. Select **Workflow** to open the drop dialog.
2. Select **Submit**.
3. Close the page.
4. In the **Comment** field, type a note for the approver of the requisition.
5. Select **Submit**.
6. Close the page.
7. Refresh the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]