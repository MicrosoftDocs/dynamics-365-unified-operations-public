---
title: Create a requisition for consumption
description: Learn about the process of creating a requisition for consumption, including a step-by-step process using the USMF demo data company. 
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 5/19/2026
ms.custom: 
  - bap-template
---

# Create a requisition for consumption

[!include [banner](../../includes/banner.md)]

his article describes the process of creating a requisition. It shows you different ways to search for products in your procurement catalog and how to add a product that isn't in your catalog. Before you start this procedure, you must have a purchasing policy set up with Consumption as the default type of requisition. You can walk through this procedure in demo data company USMF, or using your own data. The procedure can only be carried out by a user profile that is set up as worker. This task is normally be carried out by an employee. The **Employee** employ security role allows you to carry out the tasks, or if you're using USMF, you can sign in as *Alicia*.

## Create a new requisition

1. Go to **Procurement and sourcing > Purchase requisitions > Purchase requisitions prepared by me**.
1. Select **New**.
1. In the **Name** field, enter a name for the requisition.
1. In the **Requested date** field, enter a date. By default, the requested date and accounting date are copied to the purchase requisition lines. You can change them at the line level. The requested date is the requested receipt date.  
1. In the **Accounting date** field, enter a date. The accounting date records the accounting entry in the general ledger, and validates whether budget funds are available.  
1. Select **OK**.
1. In the **Reason** field, select an option from the drop-down menu. By default, the business justification reason that you select appears for the purchase requisition lines, but you can change it at the line level.  
1. Select the reason.
1. In the **Details** field, enter a more descriptive justification for the requisition.

## Add a line to the requisition

1. Select **Add line**. There are two ways to add lines to the purchase requisition. If you already know the product number or you already know that you're requesting a product that isn't in the product catalog, add the line directly by using **Add line**. The other way is to use **Add products** where you can use searching and filtering to find items in the product catalog.
1. Select the row you just created.
    - The requester is the worker that requests the requisition.
    - By default, the person preparing the requisition is the worker who requests it. You must be given permission to prepare a requisition line on behalf of another worker. If you have such permissions, the other workers appear in this lookup.  
1. In the **Item number** field, type a value. The items that you can choose from are limited by the category access policy and the procurement catalog for the buying legal entity.
1. In the **Quantity** field, enter a number.

## Add more products to the requisition

1. Select **Add products**. This option lets you search for products in the product catalog.
1. In the **Find procurement category node** field, enter the first part of the name of the category that you're looking for, and then select **Enter**. For example, enter *comput*.  
1. Use the **InvokeDefaultButton** shortcut.
1. Use the **Filter** to filter the list of products in the selected category.
1. Select the product card that you want to add to the requisition.
1. Select **Add to lines**.
1. In the **Quantity** field, enter a number.
1. In the **Find procurement category node** field, type the first part of the name of the category that you're looking for, and then select **Enter**. For example, enter *High* (highlighters).  
1. Use the **InvokeDefaultButton** shortcut.
1. Select **Add unlisted product to lines** to add a product that's not listed in the procurement catalog.
1. In the **Product name** field, type a value.
1. In the **Unit** field, type a value.
1. Select **OK**.
1. In the **Item description** field, add a description of the product.
1. In the **Quantity** field, enter a number.
1. In the **Unit price** field, enter a number. If you know the price for a particular vendor (that you select in the vendor account field) enter that price.
1. In the **Vendor account** field, open the drop-down list to select an option. The vendors that are available in this field depend on the purchasing policies and the status that the vendor has for the current procurement category. As an alternative to selecting a vendor here, you can select **Suggest vendor**.
1. In the list, select the vendor you want to use.
1. In the **External item number** field, type a value. This value is a reference number for the product that the vendor knows. For example, this value could be the item number of the product in the vendor's own catalog.  
1. Select **OK**.

## Distribute amounts

1. Select **Financials**.
1. Select **Distribute amounts**. This process shows you how to distribute the cost for the first line between two accounts. You can also distribute amounts later when the requisition is in review.  
1. Select **Split** to create a new distribution line.
1. In the **Ledger account** field, select the first cost center that should take part of the cost.
1. Select the other distribution line.
1. In the **Ledger account** field, specify the other cost center.
1. Select **Distribute equally**.
1. Close the page.

## View line details

1. Toggle the expansion of the **Line details** section.

## Submit the requisition

1. Select **Workflow** to open the drop dialog.
1. Select **Submit**.
1. Close the page.
1. In the **Comment** field, type a note for the approver of the requisition.
1. Select **Submit**.
1. Close the page.
1. Refresh the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
