---
title: Periodic settlement of over and under depreciation
description: Learn how to calculate and record depreciation expense for deductible expense in Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm, AssetDepPreTaxDedProcess_JP, AssetDepPreTaxDedProcessDetail_JP
ms.custom: 
  - bap-template
---

# Periodic settlement of over and under depreciation

[!include [banner](../../includes/banner.md)]

This article explains how to calculate and record depreciation expense for deductible expense in Japan with Microsoft Dynamics 365 Finance.

The following procedures use the JPMF demo company data.

## Fixed asset depreciation

To calculate and record fixed asset depreciation, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Depreciation proposal**.
1. In the **To date** field, enter a date. 
1. Select **Filter**.
1. In the **Criteria** field, enter a value. For example, enter "BUILM-000005".  
1. Select **OK**.
1. Select **OK**.
1. Verify that the depreciation journal is created.  
1. Select **Post**.

## Over and under depreciation settlements

To calculate and record over and under depreciation settlements, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Periodic tasks \> Settlement of over depreciation or under depreciation amount**.
1. Select **New**.
1. In the **To date** field, enter a date.
1. In the **Journal name** field, enter a value.
1. Expand the **Records to include** section.
1. Select **Filter**.
1. In the **Criteria** field, enter a value. For example, enter "BUILM-000005".  
1. Select **OK**.
1. Select **OK**.
1. Refresh the page to see if the result is created. The results might not appear instantly. 
1. In the list, find and select the new result with **Status** = **Draft**.  
1. Select **View settlement results**.
1. Verify that the correct result is created.  
1. Select **Post**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
