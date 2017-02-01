---
# required metadata

title: Add a recommendations control to the transaction page on a POS device | Microsoft Docs
description: This topic describes how to add a recommendations control to the transaction screen on a point of sale (POS) device using the screen layout designer in Microsoft Dynamics 365 for Operations.
author: josaw1
manager: AnnBe
ms.date: 2016-11-30 21:58:46
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 41
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 260624
ms.assetid: 60e46a7c-d6b2-46f8-a51b-3b4cf85e0a34
ms.region: global
ms.industry: Retail
ms.author: asharchw

---

# Add a recommendations control to the transaction page on a POS device

This topic describes how to add a recommendations control to the transaction screen on a point of sale (POS) device using the screen layout designer in Microsoft Dynamics 365 for Operations.

You can display product recommendations on your POS device when you use Microsoft Dynamics 365 for Operations. *Recommendations* are items that your customer might be interested in based on their purchase history, items in their wish list, and items that other customers purchased online and in brick-and-mortar stores. To display product recommendations, you need to add a control to the transaction screen using the screen layout designer.

## Open Layout designer
1.  Go to **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS** &gt; **Screen layouts**.
2.  Use the Quick Filter to find the screen that you want to add the control to. For example, filter on the **Screen layout ID** field using a value of ‘F2CP16:9M’.
3.  In the list, find and select the desired record. For example, select ‘Name: F2CP16:9M Screen Layout ID: F2CP16:9M’.
4.  Click **Layout designer**.
5.  Follow the prompts to launch the layout designer. When prompted for credentials, enter the same credentials that were in use when the Layout designer was launched from **Screen layouts** page.
6.  When you log in, a page similar to the one below appears. The layout will be different depending on the customizations that were made for your store.

[![screenlayout-pic-1](./media/screenlayout-pic-1.png)](./media/screenlayout-pic-1.png)
Choose a display option
-----------------------

There are two configurations options available. Choose the option that works best for your store, and follow the remaining instructions to finish setting up the control. The two options are:
-   Recommendations are always visible.
-   A **Recommendations** tab appears in the grid on the right side of the screen.

#### To make recommendations always visible

1.  Reduce the height of the transaction lines details area so that it is the same height as the customer panel to its left.[](./media/pic-2.png)[![screenlayout-pic-2](./media/screenlayout-pic-2.png)](./media/screenlayout-pic-2.png)
2.  From the menu on the left, drag and drop the recommendations control to between the transaction line details area and the button grid in the center bottom of the transaction screen. Resize the control so it fits in that space.[](./media/pic-3.png)[![screenlayout-pic-3](./media/screenlayout-pic-3.png)](./media/screenlayout-pic-3.png)
3.  Click the **X** to save and exit Layout designer.
4.  In Dynamics 365 for Operations, go to **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedules**.
5.  In the list, select **1090 Registers**.
6.  Click **Run now**.

#### To add a Recommendations tab to the button grid on the right side of the screen

1.  Right-click in the empty space below the last tab on the button grid located on the right side of the page.
2.  Click **Customize**.[![pic-5](./media/pic-5.png)](./media/pic-5.png)
3.  Click **New tab**.
4.  Find the new tab that you just added. You may need to scroll down.
5.  In the **Contents** drop-down, select **Recommended products**. [![pic-6](./media/pic-6.png)](./media/pic-6.png)
6.  In the **Label** field, type a name for the recommendations tab. For example, type ‘Recommended products’.
7.  In the **Image** field, select the image to appear on the tab.
8.  Click **OK**. The new tab appears in the button grid.
9.  Click the **X** to save and exit Layout designer.
10. In Dynamics 365 for Operations, go to **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedules**.
11. In the list, select **1090 Registers**.
12. Click **Run now**.


See also
--------

[Personalized product recommendations overview](https://docs.microsoft.com/en-us/dynamics365/operations/retail/personalized-product-recommendations-powered-by-cognitive-services-and-azure-machine-learning)

