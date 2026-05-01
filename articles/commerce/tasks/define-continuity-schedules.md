--- 
title: Define continuity schedules
description: Learn how to define continuity schedules in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/10/2026
ms.topic: how-to 
ms.author: josaw
ms.search.form: MCRContinuitySchedule, EcoResProductDetailsExtended   
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template
---
# Define continuity schedules

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to define continuity schedules in Microsoft Dynamics 365 Commerce.

The following procedures walk through setting up a continuity program (otherwise known as recurring orders). The procedures use company USRT in the demo data.

To create a continuity program, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** > **Continuity** > **Continuity programs**.
1. Select **New**.
1. In the **Schedule ID** field, enter the continuity schedule ID.
1. In the **Order start** field, select **First event**. If a customer places a new order for the continuity program, two options determine which product ships:
    - **First event**: The first product in the continuity program ships.
    - **Current event**: The current product ships. For example, three months into the program, the customer receives the third in the program.  
1. Select **Yes** to prompt for the order start date.
1. Select **Add line**.
1. In the **Item number** field, enter the item number for the first product ("0013").
1. Enter **CP**.
1. Enter the date when the first product is available for order.
1. Select **Add line**.
1. In the **Item number** field, enter **0014**.
1. In the **Date interval code** field, clear the value so the field is empty. For this procedure, clear the date interval. You set the date as incremental from the start date of the first item.  
1. Enter the interval at which the products ship. Enter **30**. For a monthly program, enter 30 days for the interval.  
1. Select **Add line**.
1. In the **Item number** field, enter **0015**.
1. Enter **End**.
1. Select **Save**.

To assign a continuity program to a continuity item, follow these steps:

1. In headquarters, go to **Product information management** > **Products** > **Released products**.
1. Select item **0016**. For this procedure, select item number 0016. Normally, you create a released product that has more continuity business logic applied when placed on a sales order in call center.  
1. In the list, select the link in the selected row.
1. Select **Edit**.
1. Expand or collapse the **Sell** section.
1. Enter the continuity program that this item represents. Enter the **Schedule ID** you created earlier. When you sell this item in a call center, additional business logic is applied from the selected continuity program.  
1. Select **Save**.

[!INCLUDE [footer-include](../../includes/footer-banner.md)]