---
# required metadata

title: Procurement
description: This topic explains procurement in Enterprise Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/27/2019
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

# Procurement



This topic explains procurement in Enterprise Asset Management. In Enterprise Asset Management, you can get an overview of purchase requisitions and purchase orders related to work orders. It is also possible to create a purchase order or a purchase requisition from a work order.

In the **Work order purchase requisition** list (**Enterprise asset management** > **Common** > **Procurement** > **Work order purchase requisition**), you see a list of purchase requisitions related to work orders.

- Select a work order line in the **Work order purchase requisition** list, and click the **Purchase requisition** button to open the related purchase requisition.  
- Select a work order line in the **Work order purchase requisition** list, and click the **Work order** button to open the related work order.  
- Select a work order line in the **Work order purchase requisition** list, and click the **Item where used** button if you want to get an overview of where the item on the selected line is used in Enterprise Asset Management in relation to objects, job type setup, spare parts, and work orders. Read more about this overview in the [Items where used](../controlling-and-reporting/items-where-used.md) section.

The following figure shows a screenshot of the interface.

![Figure 1](media/07-work-orders.png)

In the **Work order purchase** list (**Enterprise asset management** > **Common** > **Procurement** > **Work order purchase**), you can see a list of purchase orders related to work orders.

- Select a work order line in the **Work order purchase** list, and click the **Purchase order** button to open the related purchase order.  
- Select a work order line in the **Work order purchase** list, and click the **Work order** button to open the related work order.  
- Select a work order line in the **Work order** purchase list, and click the **Item where used** button if you want to get an overview of where the item on the selected line is used in Enterprise Asset Management in relation to objects, job type setup, spare parts, and work orders. Read more about this overview in the [Items where used](../controlling-and-reporting/items-where-used.md) section.

The figure below shows a screenshot of the interface.

![Figure 2](media/08-work-orders.png)

In the lists shown above, an icon regarding delivery date control is placed to the right on each line. If the icon shows an exclamation mark in a red circle, it means that delivery on the related purchase requisition or purchase order may be delayed.

On a purchase requisition, the date used to calculate possible delay is found in the **Purchase requisitions** form > **Purchase requisition header** FastTab > **Requested date** field. That date is compared with the available date on the work order or work order line in the same way as the purchase order date.

On a purchase order, the date used to calculate possible delay is the date related to the purchase order line, which shown in the **Purchase order** form > select purchase order line > **Line details** FastTab > **Setup** tab > **Confirmed delivery date** field. If that field is not filled out, the date in the **Delivery date** field on the **Purchase order header** FastTab is used. One of those dates is compared with the available date on the work order or work order line in the following order:

- Actual start date on the work order, or  

- Scheduled start date on the related work order line, or  

- Scheduled start date on the work order, or  

- Expected start date on the work order  

## Create purchase order from a work order

In **All Work orders**, you select a work order line and create a related purchase order or a purchase requisition. This is done to ensure project relations between the purchase order or purchase requisition and the work order.

Click **Enterprise asset management** > **Common** > **Work orders** > **All work orders** or **Active work orders**.

In the **All work orders** or **Active work orders** list, select the work order for which you want to create a purchase order, and click **Edit**.

1. In the **Work order** form > **Work order lines** FastTab, select the work order line for which you want to create the purchase order.

2. Click **Item tasks** > **Purchase orders**.

3. In the **Project purchase orders** list page, click **Purchase order**.

4. Create the purchase order.

>[!NOTE]
>Creating a purchase requisition is almost identical to creating a purchase order. The only difference is that in the above procedure, you click **Item tasks** > **Project purchase requisitions** in step 4, and in the **Project purchase requisitions** list page, you click **Purchase requisition** and create the requisition.

## Project relation between work order and purchase order / purchase requisition

A purchase order line or purchase requisition line is related to a work order line via the work order project and the related project activity number. When you create a purchase order or purchase requisition from a work order line, the related project activity number is mandatory. The project activity number is automatically inserted on a purchase order or purchase requisition if the related work order contains work order lines that all use the same job type. If the work order lines contain different job types, the project activity number must be inserted manually.

To see or insert the activity number related to a purchase order line, open **Work order purchase** > select the purchase order record > click on the purchase order in the **Purchase order** column > **Line details** FastTab > **Project** tab > **Activity number** field.

The figure below shows a screenshot of the interface.

![Figure 3](media/09-work-orders.png)

Likewise, to see or insert the activity number related to a work order purchase requisition line, open **Work order purchase requisition** > select the purchase requisition record > click on the purchase requisition in the **Purchase requisition** column > **Line details** FastTab > **Project** tab > **Activity number** field.
