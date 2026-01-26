---
title: Create and confirm a vendor consolidated invoice
description: Learn how to consolidate vendor invoices each month to calculate the due amount, including a step-by-step process using the JPMF demo data company.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: VendConsInvoice_JP
ms.dyn365.ops.version: Version 7.0.0
---

# Create and confirm a vendor consolidated invoice

[!include [banner](../../includes/banner.md)]

In Japan, you consolidate sales and purchase invoices during the month at the end of the month to calculate the due amount.

This task shows you how to create and confirm a vendor consolidated invoice.

Before you can complete this task, you must post purchase invoices.

This task uses the demo data company JPMF.

1. Go to **Accounts payable** > **Periodic tasks** > **Consolidated invoice**.
1. Select **New** and in the **Execution date** field, enter a date.
1. Select or clear the **Use consolidation date specified below** check box. If you want to override the consolidation date, set the **Use consolidation date** slider to **Yes**.  
1. In the **Consolidation date** field, enter a date. For example, when the consolidation date is the 25th, run the consolidation on the 24th if you set this slider to **Yes**. You must manually specify a consolidation date.  
1. Select **OK**. Verify the generated consolidated invoice.  
1. In the list, select the link in the selected row. Switch to the detail view of the **Consolidated invoice** page by selecting the Consolidation ID of the Consolidated invoice in the grid.  
1. Verify that the invoiced purchase orders are included in the consolidated invoice, then select **Confirm**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
