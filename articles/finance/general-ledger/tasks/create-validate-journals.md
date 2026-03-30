--- 
title: Create and validate journals
description: Learn about the procedure for creating and validating journals and journal lines. 
author: panolte
ms.author: twheeloc
ms.topic: how-to
ms.date: 09/05/2025
ms.custom:
ms.reviewer: twheeloc    
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransDaily
ms.dyn365.ops.version: Version 7.0.0 
---

# Create and validate journals

[!include [banner](../../includes/banner.md)]

This procedure creates and validates journals and journal lines. You can try this procedure using the USMF demo company.  

1. Go to **General ledger > Journal entries > General journals**.
1. Click **New**.
1. In the **Name** field, click the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. Click **Lines**.
1. In the **Account** field enter an appropriate account based on the account type.
1. In the **Description** field, type a value.
1. Enter an amount for the account as either a **Debit** or **Credit**.
1. In the **Offset account** field, enter an appropriate account based on the **Offset account** type.
1. Click **Validate**.
1. Click **Validate**.
1. Click **Post**.
1. Click **Voucher**.

## Validate transaction data integrity

Dynamics F&O easily allows you to validate the data integrity of a financial dimension associated with a particular transaction.

After navigating to **General ledger > Journal entries > General journals**, selecting the desired journal and clicking **Lines** from the action pane, right click the dimension combination in the account of interest. Then, select **Validate data integrity** from the drop down menu.

:::image type="content" source="../media/validate-data-integrity.png" alt-text="Screenshot of the validate data integrity dialog.":::

If data integrity errors are found, reset the dimension value by renaming it. For example, rename "Cust-01" to "Cust-01_rename", then rename it back to "Cust-01".

As this rename process may take a few minutes, check its status on the **Misc** tab of the **System administration > Periodic tasks > Data maintenance** module. There you should see the **Dimension value rename and modify chart of accounts delimiter process** data maintenance action.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
