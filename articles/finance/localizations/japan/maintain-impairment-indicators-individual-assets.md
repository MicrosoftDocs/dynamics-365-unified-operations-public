---
title: Maintain impairment indicators on individual assets
description: Learn how to maintain impairment indicators on individual assets for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 04/25/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetBook, AssetImpairmentIndicator_JP, AssetImpairmentReview_JP, SysQueryForm
ms.custom: 
  - bap-template
---

# Maintain impairment indicators on individual assets

[!include [banner](../../includes/banner.md)]

This article explains how to maintain impairment indicators on individual assets for Japan in Microsoft Dynamics 365 Finance.

The following procedures use the JPMF demo company data.

Before you complete the procedures, you must first set up the impairment accounting common parameters. Learn more in [Set up impairment accounting common parameters and posting profile](impairment-accounting.md).

## Update impairment indicator on a single fixed asset

To update the impairment indicator on a single fixed asset, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. In the list, find and select the desired record. For example, select **TOOLM-000006**.  
1. Select **Books**.
1. Select **Functions**.
1. Select **Update impairment indicators**.
1. Select **New**.
1. In the **Modify date** field, enter a date.
1. In the **Description** field, enter a value.
1. In the **Undiscounted cash flow** field, enter "3900000".  
1. In the **Recoverable amount** field, enter "3350226".  
1. Select **Save**.

## Update impairment indicator on the impairment management form

To update impairment indicator on the impairment management form, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets \> Impairment management**.
1. Select **Query**.
1. In the **Criteria** field of the fixed asset group row, select the drop-down button to open the lookup.
1. Select **OK**.
1. In the list, find and select **TOOLM-000007**.  
1. In the list, find and select **TOOLM-000008**. 
1. Select **Update impairment indicators**.
8. In the list, select the record with fixed asset number **TOOLM-000007**.  
9. In the **Modify date** field, enter a date.
1. In the **Description** field, enter a value.
1. In the **Undiscounted cash flow** field, enter "2500000.00".  
1. In the **Recoverable amount** field, enter "2000000.00".  
1. In the list, find and select the row with fixed asset number **TOOLM-000008**.  
1. In the **Modify date** field, enter a date.
1. In the **Description** field, enter a value.
1. In the **Undiscounted cash flow** field, enter "2000000.00".  
1. In the **Recoverable amount** field, enter "1500000.00".  
1. Select **Update indicator**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
