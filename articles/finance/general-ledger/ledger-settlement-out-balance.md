---
# required metadata
title: Out of balance ledger settlements
description: This topic explains how to use the Out of balance ledger settlements page to reverse settlements that aren't balanced in General ledger. 
author: JodiChristiansen
ms.date: 7/24/2025
ms.topic: article
# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2024-10-17
ms.dyn365.ops.version: 10.0.45

---

# Out of balance ledger settlements

[!include [banner](../includes/banner.md)]

If there are out of balance ledger settlements, the year-end close fails with an out of balance error. To address out of balance errors so the year can be closed successfully, any out of balance ledger settlements need to be reversed. This page helps find out of balance ledger settlements. 

Once these ledger settlements are reversed, they shouldn't be settled again in the same manner because they were out of balance. 

## Out of balance

To find settlements that are out of balance, follow these steps:
1. Go to **General ledger > Periodic tasks > Out of balance ledger settlements**.
2. Select the fiscal year, and select **Show ledger settlements**. Only open fiscal years can be selected in **Fiscal year**.
3. To see the detail of the ledger settlement, select **Settlement ID**. Out of balance ledger settlements for each settlement ID display all settled transactions for the settlement ID, including any outside of the target fiscal year that are involved with the selected settlement ID. 
For each settlement ID, the following are displayed:
 - **Settlement ID**
 - **Date settled**
 - **Automation rule** (if using process automation for ledger settlements)
 - **Total balance in accounting currency**
 - **Total balance in reporting currency**
If the ledger settlement can't be reversed from this page, the **Reversal blocked** column is marked.
4. To reverse a ledger settlement on this page, mark the settlement lines and then select **Unsettle marked records**.

### Reversal blocked
The **Reversal blocked** column indicates if an out of balance ledger settlement can be reversed. Out of balance ledger settlements with transactions posted in a closed fiscal year can't be reversed. To reverse them, the closed fiscal year must be reopened by reversing the year-end close voucher of the target fiscal year. Out of balance ledger settlements with realized gain/loss adjustment transactions can't be reversed on this page. The **Ledger settlements page** can be used for reversal. 

Out of balance ledger settlements aren't allowed when doing ledger settlements. There are instances when an out of balance ledger settlement has happened and needs to be reversed so the year-end close can run successfully. 

### Example
Some examples of ledger settlements that may appear on this page include: 
- Any cross-year ledger settlements when the **Enable advanced awareness option** is set to **Yes** in **General ledger parameters**, **Ledger settlements** tab.
When using the Advanced awareness options, cross-year settlements aren't supported. If the Advanced awareness feature was set to **Yes** after a cross-year settlement was done, cross-year settlements show on this page and must be unsettled.
- If a ledger settlement was done for transactions where a realized gain or loss should have been calculated and wasn't, it's considered out of balance.
- Select **Settlement ID** to see if the **Amount in transaction currency** is equal but the **Amount in accounting currency** and/or reporting currency isn't equal. The accounting currency and reporting currency won't balance with no gain or loss calculated. The **Enable post currency realized gain/losses for ledger settlements** needs to be set to **Yes** in **General ledger parameters**, **Ledger settlements** tab to calculate the gain/loss during ledger settlement. 

