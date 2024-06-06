---
title: Create and confirm a vendor consolidated invoice
description: Learn how to consolidate vendor invoices each month to calculate the due amount, including a step-by-step process using the JPMF demo data company.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 10/04/2021
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: VendConsInvoice_JP
ms.dyn365.ops.version: Version 7.0.0
---

# Create and confirm a vendor consolidated invoice

[!include [banner](../../includes/banner.md)]

In Japan, sales and purchase invoices during the month are consolidated at the end of the month to calculate the due amount. 

This task walks you through creating and confirming a vendor consolidated invoice.

Before you can complete this task, you must have posted purchase invoices. 

This task was created using the demo data company JPMF.

1. Go to **Accounts payable** > **Periodic tasks** > **Consolidated invoice**.
2. Select **New** and in the **Execution date** field, enter a date.
3. Select or clear the **Use consolidation date specified below** check box. If you want to override the consolidation date, set the **Use consolidation date** slider to **Yes**.  
4. In the **Consolidation date** field, enter a date. For example, when the consolidation date is the 25th, run the consolidation on the 24th if you set this slider to **Yes**. You will have to manually specify a consolidation date.  
5. Select **OK**. Verify the generated consolidate invoice.  
6. In the list, select the link in the selected row. Switch to the detail view of the **Consolidated invoice** page by selecting the Consolidation ID of the Consolidated invoice in the grid.  
7. Verify that the invoiced purchase orders are included in the consolidated invoice, and then select **Confirm**. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
