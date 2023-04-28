--- 
# required metadata 
 
title: Set up a mobile device menu item for completing work of type Purchase order
description: This article shows how to set up a Mobile device menu item. 
author: Mirzaab
ms.date: 08/02/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSRFMenuItem, WHSRFAutoConfirm, WHSRFMenu   
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
# Set up a mobile device menu item for completing work of type Purchase order

[!include [banner](../../includes/banner.md)]

This article shows how to set up a Mobile device menu item. In this example, the menu item is used for performing work of type Purchase order. The work class that's associated with the menu item determines which work is valid. You can use this guide in demo data company USMF. This procedure is typically carried out by a warehouse manager.


## Create a mobile device menu item
1. Go to **Mobile device menu items** by entering it in the search bar.
2. Select **New**.
3. In the **Menu item name** field, type a value. Enter a unique value. For example, you could type `POMove`. Remember the value, you'll need it later.  
4. In the **Title** field, type a value. This is the title which will be displayed on the mobile device. For example, you could type `PO Move`.  
5. In the **Mode** field, select **Work**.
6. Select **Yes** in the **Use existing work** field.
    - This mobile device menu item is used to perform existing work. Therefore you must set this value to **Yes**.  
    - The **Display inventory status** field determines whether the inventory status of the on-hand inventory will be displayed to the warehouse worker on the mobile device.  
7. In the **Directed by** field, select **System grouping**. When you select something in the **Directed by** field, additional fields appear in the **General** section on this page. The fields that appear depend on what you selected. When you select **System grouping**, two new fields are added. These are explained below.  
8. In the **System grouping** field, select **WorkPoolId**. When warehouse workers open this menu item, they'll be asked to scan a Work pool ID. All work orders with this Work pool ID and open work order lines with one of the work classes added to this menu item will be pushed to the user.  
9. In the **System grouping label** field, type a value. This is the text displayed to the user on the mobile device. For example, you could type **Work pool**.  
10. Select **Yes** in the **Override license plate during put** field. This option allows warehouse workers to override the target license plate when items are put down on a license plate controlled location.  
11. Select **Yes** in the **Group put away** field.
    - If all the Put lines on the work order share the same location, the user will receive one combined Put instruction for all lines. 
    - Audit template ID: A work audit template allows you to specify that the work process for a menu item should be interrupted so that another operation can be performed. For example, if this menu item is for inbound work, the audit template might require that the worker checks the temperature. The point at which the process is interrupted is specified on the audit template and can be, for example, when work is started or completed, or when its status changes.  
12. Expand the **Work classes** section.
13. Select **New**.
14. In the **Work class ID** field, type `Purchase`. The work pool restricts the work that the menu item can be used for. In this case it will be used for open work order lines that have the Purchase work class ID.  
15. Select **Save**.

## Set up work confirmation
1. Select **Work confirmation setup**.
2. In the **Work type** field, select **Pick**.
3. Select the **Auto confirm** check box. The work instruction with work type Pick will be auto-confirmed. This instruction will not be presented to the user.  
4. Select **New**.
5. In the **Work type** field, select 'Put'.
6. Select the **Location confirmation** check box. The warehouse worker will be asked to perform a confirmation scan of the location, when the item is put down.  
7. Select **Save**.

## Add the menu item to a mobile device menu
1. Go to **Mobile device** menu by entering it in the search bar.
2. Select **Edit**.
3. Use the Quick Filter to find records. For example, filter on the **Name** field with a value of **inbound**. You want to find the menu you use for inbound menu items. In USMF this is called **Inbound**.  
4. In the tree, select **a value**.
5. Select the arrow that points to the right.
6. Select **Save**.
7. Close the page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]