---
title: Create POS permission groups
description: This article explains how to create a POS permission group in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/10/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: anvenkat
ms.search.validFrom: 2016-06-30
ms.search.form: RetailPosPermissionGroup, HcmJob
ms.custom: 
  - bap-template
---
# Create POS permission groups

[!include [banner](../includes/banner.md)]

This article explains how to create a POS permission group in Microsoft Dynamics 365 Commerce.

The demo data company used to create this task is USRT. This task is intended for the Commerce operations manager role.

To create a POS permission group in Commerce headquarters, follow these steps:

1. In Commerce headquarters, go to **Modules \> Retail and Commerce \> Employees \> Permission groups**.
1. Select **New**.
1. In the **POS permission group ID** field, enter a value.
1. In the **Description** field, enter a value.
1. Select **Yes** in the **View time clock entries** field. You can now enable or disable various permissions for your POS Permission group. For some permissions, you can set a value that the system uses to evaluate if the POS user can perform the action.
1. In the **Allow create order** field, select **Yes**.
1. In the **Allow edit order** field, select **Yes**.
1. In the **Allow retrieve order** field, select **Yes**.
1. In the **Allow password change** field, select **Yes**.
1. In the **Allow blind close** field, select **Yes**.
1. Select **Save**. After you save your changes, run the Staff distribution schedule to push the changes to commerce channels.
1. In the navigation pane, go to **Modules \> Human resources \> Jobs \> Jobs**.
1. Next, assign the POS permission group to a Job. In the list, find and select the desired record.
1. Select **Edit**.
1. Expand the **Job classification** section.
1. In the POS permission group field, enter or select a value. All Workers in Positions for this Job use this POS permission group's settings unless the workers POS permissions are overridden at their Position level.  
1. Select **Save**. After you save your changes, run the Staff distribution schedule to push the changes to channels.  

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
