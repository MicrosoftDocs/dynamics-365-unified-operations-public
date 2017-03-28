---
# required metadata

title: Special entries and opening sheets
description: Legal entities in Spain can post special entries as opening entries for the current period, while adapting accounts to changes in accounting rules.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-02 21 - 05 - 24
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 261334
ms.assetid: ee065203-20dc-4bbb-bc56-bb01d28a6576
ms.search.region: Spain
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Special entries and opening sheets

Legal entities in Spain can post special entries as opening entries for the current period, while adapting accounts to changes in accounting rules.

By using opening sheets, you can indicate the following:

-   Increase the value of specific financial fixed assets.
-   Change the value of specific raw materials when the value has changed significantly during the year and when the material meets specific criteria.

When you close the entries for the previous fiscal year, you can create several lines by setting the **Type** field to **Opening**. This allows special opening entries for the current fiscal year to be posted. You can make adjustments to the opening sheet for the fiscal year on the **Opening sheets** page.

## Create a new opening sheet
To create a new **Opening sheet,** click **New** on the **Opening sheets** page, and specify the following.

|                    |                                                                                                                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Field**          | **Description**                                                                                                                                                                                                                                                                                   |
| **Opening sheets** | Enter a code for the opening sheet. You can create several opening sheets for each year, but each must have a unique identifier in the **Opening sheets** field.                                                                                                                                  |
| **Name**           | Name for the opening sheet.                                                                                                                                                                                                                                                                       |
| **Posting layer**  | Select the posting layer for the transactions.                                                                                                                                                                                                                                                    |
| **Type**           | Select **Opening** to make adjustments for the entire year that were maintained separately from the daily postings in the last period of the year. If you select **Opening**, you should use the **Opening fiscal period** field on the **General** tab to specify the opening period to post to. |
| **From … To**      | Specify the period that the adjustments apply to.                                                                                                                                                                                                                                                 |
| **Post**           | Specify the posting date for the adjustments.                                                                                                                                                                                                                                                     |

After you enter the general information about the opening sheet, you'll need to specify the main accounts to include in the opening sheet. To do this, click **Opening accounts** &gt; **Load balances** on the **Opening sheets** page. To post all ledger account balances and adjustments to the opening sheet, click **Post**.

