---
# required metadata
title: Out of balance ledger settlements
description: This topic explains how to use the Out of balance ledger settlements page to reverse settlements that are not balanced in General ledger. 
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

If there are out of balance ledger settlements, the year-end close will fail with an out-of-balance error. To address these out of balance errors so the year can be closed successfully, any out of balance ledger settlements need to be reversed. This page will help find those out of balance ledger settlements. 

Once these ledger settlements have been reversed they should not be settled again in the same manner because they were out of balance. 

In **Out of balance ledger settlements** (**General ledger > Periodic tasks > Out of balance ledger settleents**) select the fiscal year and then select **Show ledger settlements**. Only open fiscal years, that have not been closed by the year-end process, can be selected in Fiscal year.

To see the detail of the ledger settlement select the Settlement ID hyperlink. The page with the out of balance ledger settlements for each settlement ID will show all settled transactions for the settlement ID, including any outside of the target fiscal year, that are involved with the selected settlement ID. 

The Settlement ID, Date settled, Automation rule (if using process automation for ledger settlements), Total balance in accounting currency and Total balance in reporting currency, display for each settlement ID. If the ledger settlement cannot be reversed from this page the **Reversal blocked** column is marked. To reverse a ledger settlement on this page, mark the settlement line(s) and then select **Unsettle marked records**.

The **Reversal blocked** column indicates whether an out of balance ledger settlement can be reversed. Out of balance ledger settlements with transactions posted in a closed fiscal year cannot be reversed. To reverse them, the closed fiscal year must be reopened by reversing the year-end close voucher of the target fiscal year. Out of balance ledger settlements with realized gain/loss adjustment transactions cannot be reversed on this page. Use the Ledger settlements page for reversal. 

Out of balance ledger settlements are not allowed when doing ledger settlements. However, we have found there are instances when an out-of-balance ledger settlement has happened, and it needs to be reversed so the year-end close can run successfully. Some examples of ledger settlements that may appear on this page include the following. 

- Any cross-year ledger settlements when the **Enable advanced awareness option** is set to **Yes** in **General ledger parameters**, **Ledger settlements** tab. When using the Advanced awareness options cross-year settlements are no longer supported so if the Advanced awareness feature was set to Yes after a cross-year settlement was done, cross-year settlements will show on this page and must be unsettled.
- If a ledger settlement was done for transactions where a realized gain or loss should have been calculated and was not, it will be considered out of balance. Select the Settlement ID hyperlink to see if the Amount in transaction currency is equal but the amount in accounting currency and/or reporting currency is not equal. The accounting currency and reporting currency will not balance with no gain or loss calculated. The **Enable post currency realized gain/losses for ledger settlements** needs to be set to **Yes** in **General ledger parameters**, **Ledger settlements** tab to calculate the gain/loss during ledger settlement. 

