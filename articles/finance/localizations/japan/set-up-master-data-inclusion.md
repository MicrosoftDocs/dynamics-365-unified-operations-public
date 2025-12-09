---
title: Set up master data for inclusion of deductible expenses for multiple posting layers
description: Learn how to create fixed asset rules with required master data for inclusion of deductible expenses for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - AssetAdvancedRule_JP, AssetAdvancedRuleCreateEdit_JP
  - AssetBookTable
ms.custom: 
  - bap-template
---

# Set up master data for inclusion of deductible expenses for multiple posting layers

[!include [banner](../../includes/banner.md)]

This article explains how to create fixed asset rules with required master data for inclusion of deductible expenses  for multiple posting layers for Japan in Microsoft Dynamics 365 Finance.

Before you complete the following procedures, select the **Fixed Asset** configuration key.

The procedures use the demo data company JPMF.

## Set up depreciation settlement rules

To set up depreciation settlement rules, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Depreciation settlement rules**.
1. Optionally, if the settlement rule table is empty, you're asked if you want to import the default set of rules. Select **OK** to import the default set of rules.  
1. Select **New**.
1. In the **Over depreciation** field, select **Over depreciation = Ordinary depreciation**.  
1. In the **Under depreciation** field, select **Under depreciation = Additional depreciation (reserve)**.  
1. Select **OK**.
1. In the **Filter by rule type** field, select **Filter by rule type = Carry forward of over depreciation or under depreciation amount**.  
1. Select **Edit rule**.
1. In the **Periods to carry forward (years)** field, enter a number.
1. Select **OK**.

## Set up a book

To set up a book, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Books**.
1. Select **New**.
1. In the **Book** field, enter a value.
1. In the **Description** field, enter a value.
1. Expand the **General** section.
1. Configure the parameters according to the core fixed asset features.  
1. Expand the **Derived books** section.
1. Select the book on the tax layer that references this book. If you add a derived book for the acquisition type, the system simplifies the operation by automatically acquiring the tax layer book.
1. Select **Save**.
1. Use the Quick Filter to search for the tax layer book that you want to run settlement with the current layer book.  
1. Expand the **General** section.
1. In the **Referenced book** field, enter the book that you created.  
1. Select **Save**.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
