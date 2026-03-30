---
title: Create CGU groups and cash generating units
description: Learn how to create cash generating unit (CGU) groups and CGUs for Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetImpairmentCashGenUnitGroup_JP, SysQueryForm, AssetImpairmentCashGenUnit_JP
ms.custom: 
  - bap-template
---

# Create CGU groups and cash generating units

[!include [banner](../../includes/banner.md)]

This article explains how to create cash generating unit (CGU) groups and CGUs for Japan with Microsoft Dynamics 365 Finance.

In Japan, an impairment on fixed assets can be based on either individual fixed assets or CGUs. When you measure impairment based on CGUs, the first step is to group the fixed assets into CGUs. You can have multiple sets of CGUs so you can choose the most appropriate CGU. You create CGU groups to achieve this goal. 

The following procedures walk you through how to create CGU groups and CGUs, assign fixed assets to CGUs, and assign shared assets and goodwill to CGU groups. The procedures use the demo data company JPMF.

Before you complete the procedures, you must first select the **Fixed Asset** configuration key.

## Create a CGU group

To create a CGU group, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Impairment \> CGU groups**.
1. Select **New**. You can create multiple CGU groups for testing if you're not sure about the appropriate combinations of fixed assets and CGUs.  
1. In the **CGU group** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Impairment of goodwill and shared asset** field, select an option. Select the method according to your corporate policy.  
1. Select **Save**.

## Create CGUs under the CGU group

To create CGUs under the CGU group, follow these steps:

1. Select **New**.
1. In the **Name** field, enter a value.
1. Note the value in the **Cash generating unit number** field for reference later. You need this value when you configure the cash generating unit.  
1. Select **New**.
1. In the **Name** field, enter a value.
1. Note the value in the **Cash generating unit number** field to reference later. You need this value when you configure the cash generating unit.  

## Assign shared assets and goodwill to the CGU group

To assign shared assets and goodwill to the CGU group, follow these steps:

1. Expand the **Shared assets and goodwill** section.
1. Select **Massive import**. Microsoft recommends that you specify a condition that adds all the assets that meet the condition at once. You can also enter assets one at a time in the grid.  
1. In the **Criteria** field, enter a value.
1. Select **OK**.

## Configure CGUs

To configure CGUs, follow these steps:

1. Select **Assign fixed assets**.
1. Use the Quick Filter to find the CGU to edit. Enter the first CGU that you noted previously.  
1. Select **Massive import**. Microsoft recommends that you specify a condition that adds all the assets that meet the condition at once. You can also enter assets one at a time in the grid.
1. In the **Criteria** field, enter a value. For example, "Location = FUKUOKA".  
1. Select **OK**.
1. In the **Undiscounted cash flow** field, enter a number.
1. In the **Recoverable value** field, enter a number.
1. Select **Save**.
1. Use the Quick Filter to find the cash generating unit to edit. Enter the second cash generating unit number that you noted previously.  
1. Select **Massive import**.
1. In the **Criteria** field, enter a value. For example: "Location = OSAKA".  
1. Select **OK**.
1. In the **Undiscounted cash flow** field, enter a number.
1. In the **Recoverable value** field, enter a number.
1. Select **Save**.

## Activate the CGU group

To activate the CGU group, follow these steps:

1. Select **Activate**. Only active CGU groups can run recognition tests.  
1. Select **Yes**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
