---
title: Define asset idle period and validate depreciation process
description: Learn how to define the fixed asset idle period and validate depreciation process for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetParameters, AssetIdlePeriodAssign_JP, AssetTable, AssetBook, AssetIdlePeriodUpdate_JP, AssetProfile, LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm
ms.custom: 
  - bap-template
---

# Define asset idle period and validate depreciation process

[!include [banner](../../includes/banner.md)]

Learn how to define the fixed asset idle period and validate depreciation process for Japan in Microsoft Dynamics 365 Finance.

The following procedures use the JPMF demo company data.

Before you complete the procedures, select the **Fixed Asset** configuration key.

## Assign a fixed assets number sequence

To assign a fixed assets number sequence, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Fixed assets parameters**.
1. Select the **Number sequences** tab.
1. In the list, find and select the fixed asset record.
1. In the **Number sequence code** field, enter or select a value.
1. Select **Save**.
1. Close the page.

## Assign an idle period for a fixed asset

To assign an idle period for a fixed asset, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Periodic tasks \> Assign idle period to a fixed asset**.
1. Select **New**.
1. In the **Description** field, enter a value.
1. Expand the **General** section.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. In the **Reason** field, enter a value.
1. Expand the **Idle Periods** section.
1. Select **New**.
1. In the **Fixed asset group** field, enter "EQUP-M".  
1. In the **Fixed asset number** field, enter "EQUPM-000024".  
1. In the **Book** field, enter "200NDB_CUR".  
1. Select **Save**.
1. Select **Confirm**.
1. Close the page.

## Validate a fixed asset book

To validate a fixed asset book, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. In the list, find and select the **EQUPM-000024** record.  
1. Select **Books**.
1. In the list, find and select the **200NDB_CUR** record.
1. Select **Functions**.
1. Select **Update idle periods**. Check that the idle period created for the fixed asset book is listed.
1. Close the page.
1. Select **Profile**. Check that the profile displays zero depreciation for the idle period.  
1. Close the page.

## Execute a depreciation proposal

To execute a depreciation proposal, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter or select a name.
1. Select **Save**.
1. Select **Lines**.
1. Select **Proposals**.
1. Select **Depreciation proposal**.
1. In the **To date** field, enter a date.
1. Expand the **Records to include** section.
1. Select **Filter**.
1. Select **Reset**.
1. In the list, mark the selected row.
1. In the **Criteria** field, enter "EQUPM-000024".  
1. In the list, find and select the desired record.
1. In the **Criteria** field, enter "200NDB_CUR".  
1. Select **OK**.
1. Select **OK**. Validate that no depreciation journal is created for the idle period. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
