--- 
title: Create and confirm a customer consolidated invoice
description: Learn how to consolidate customer invoices each month to calculate the due amount, including a step-by-step process using the JPMF demo company data.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 10/04/2021
ms.custom: 
ms.reviewer: johnmichalak   
audience: Application User 
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: CustConsInvoice_JP 
ms.dyn365.ops.version: Version 7.0.0 
---

# Create and confirm a customer consolidated invoice

[!include [banner](../../includes/banner.md)]

In Japan, sales and purchase invoices during the month are consolidated at the end of the month to calculate the due amount. 

Use this task to learn how to create and confirm a consolidated invoice. 

In order to complete this task, the sales or purchase invoices should have been posted before running this task.

This task uses the JPMF demo company data.

1. Go to Accounts receivable > Periodic tasks > Consolidated invoice.
2. Click New.
    * The default Execution date is the session date.  
    * Specify the Use consolidation date specified below slider to be 'Yes' if you want to override the consolidation date.  
    * Example: When the consolidation date is specified as the 25th, you can run the consolidation on the 24th if you set this slider to 'Yes'. You will have to manually specify a Consolidation date.  
3. Click OK.
    * Verify that the Consolidated invoice was generated.  
    * One Consolidated invoice will contain only one Customer account. When there are multiple Customer accounts to be consolidated, multiple consolidated invoices will be generated.  
4. In the list, click the link in the selected row.
    * Switch to the detail view of the Consolidated invoice page  by clicking on the Consolidation ID of the Consolidated invoice in the grid.  
    * Verify that invoiced sales orders are included in the consolidated invoice.  
5. Click Confirm.
    * The Status of the consolidated invoice changes to be 'Confirmed' after you click Confirm. When confirmed, the consolidated invoice will be locked and you cannot edit it.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
