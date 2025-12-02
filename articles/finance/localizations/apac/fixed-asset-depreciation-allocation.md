---
title: Set up fixed asset depreciation allocation
description: This article describes how to create a fixed asset allocation rule and assign a fixed asset allocation rule to a posting profile in Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 03/11/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: China (PRC), Japan
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
  - AssetAllocationRuleSetup_CN
  - AssetPosting
---

# Set up fixed asset depreciation allocation

[!include [banner](../../includes/banner.md)]

This article describes how to create a fixed asset allocation rule and assign a fixed asset allocation rule to a posting profile in Japan with Microsoft Dynamics 365 Finance.

In Japan, the depreciation expenses of a particular fixed asset can be shared among multiple departments. The following procedures were created using the demo data company JPMF. 

## Create a fixed asset depreciation allocation rule

To create a fixed asset depreciation allocation rule, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Depreciation allocation rules**.
1. Select **New**.
1. In the **Rule ID** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Dimension name** field, enter a value.
1. Select **Add**.
1. In the **BusinessUnit** field, enter a value for the first allocation target.  
1. In the **Percentage** field, enter a number. The total percentage of all the allocation targets must be 100.  
1. In the **Offset account** field, enter a value.
1. Select **Add**.
1. In the **BusinessUnit** field, enter a value.
1. In the **Percentage** field, enter a number. The total percentage of all the allocation targets must be 100.  
1. In the **Offset account** field, enter a value.
1. Select **Save**.

## Assign a fixed asset allocation rule to a posting profile

To assign a fixed asset allocation rule to a posting profile, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Fixed asset posting profiles**.
1. Select **Edit**.
1. In the **Transaction type** field, select **Depreciation**.
1. In the list, find and select the desired record to which you want to link the allocation rule.  
1. Expand the **Depreciation allocation rules** section.
1. In the **Asset allocation rule for depreciation** field, enter a value.
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
