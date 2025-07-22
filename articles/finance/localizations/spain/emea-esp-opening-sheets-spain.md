---
title: Special entries and opening sheets
description: Learn how to work with special entries and opening sheets for Spain in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 07/11/2025
ms.reviewer: johnmichalak
ms.search.region: Spain
ms.search.validFrom: 2016-11-30
ms.search.form: LedgerOpeningSheet_ES
---

# Special entries and opening sheets

[!include [banner](../../includes/banner.md)]

This article explains how to work with special entries and opening sheets for Spain in Microsoft Dynamics 365 Finance.

Legal entities in Spain can post special entries as opening entries for the current period, while adapting accounts to changes in accounting rules.

By using opening sheets, you can indicate the following:
- Increase the value of specific financial fixed assets.
- Change the value of specific raw materials when the value has changed significantly during the year and when the material meets specific criteria.

When you close the entries for the previous fiscal year, you can create several lines by setting the **Type** field to **Opening**. This allows special opening entries for the current fiscal year to be posted. You can make adjustments to the opening sheet for the fiscal year on the **Opening sheets** page.

## Create a new opening sheet

To create a new opening sheet, follow these steps. 

1. In Dynamics 365 Finance, go to  on the **Opening sheets** page.
1. Select **New**.
1. Enter or select the following field values.

    |  Field           |  Description |
    |--------------------|----------------------------------|
    | **Opening sheets** | Enter a code for the opening sheet. You can create several opening sheets for each year, but each must have a unique identifier in the **Opening sheets** field.             |
    | **Name**           | Name for the opening sheet.        |
    | **Posting layer**  | Select the posting layer for the transactions.        |
    | **Type**           | Select **Opening** to make adjustments for the entire year that were maintained separately from the daily postings in the last period of the year. If you select **Opening**, you should use the **Opening fiscal period** field on the **General** tab to specify the opening period to post to. |
    | **From … To**      | Specify the period that the adjustments apply to.         |
    | **Post**           | Specify the posting date for the adjustments.         |

After you enter the general information about the opening sheet, you must specify the main accounts to include in the opening sheet.

To specify the main accounts to include in the opening sheet, follow these steps.

1. In Dynamics 365 Finance, go to the **Opening sheets** page.
1. Select **Opening accounts** \> **Load balances**.
1. To post all ledger account balances and adjustments to the opening sheet, select **Post**.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
