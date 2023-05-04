--- 
# required metadata 
 
title: Record a vendor invoice in the invoice journal
description: This task guide will show how to record vendor invoices that are not associated with purchase orders. 
author: abruer
ms.date: 02/08/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendInvoiceWorkspace, LedgerJournalTable, LedgerJournalTransVendInvoice   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Record a vendor invoice in the invoice journal

[!include [banner](../../includes/banner.md)]

This task guide will show how to record vendor invoices that are not associated with purchase orders. Examples of this type of invoice include expenses for supplies or services.  This recording uses the USMF demo company.

1. Go to **Navigation pane > Modules > Accounts payable > Workspaces > Vendor invoice entry**.
2. On the **Action pane**, click **New invoice journal**.
3. Click **New**.
4. In the **Name** field, enter the journal name or click the drop down button to open the lookup.
5. In the **Description** field, type a value.
6. On the **Action pane**, click **Lines**. In the **Date** field, enter the posting date that will update General ledger.  
7. In the **Account** field, specify the **Vendor account**.
8. In the **Invoice** field, enter the invoice number.
9. In the **Description** field, type a value.
10. In the **Credit** field, enter a number.
11. In the **Offset account** field, enter the account number or click the drop down button to open the lookup
    * The **Sales tax group** will be default from the vendor account.  
    * The **Item sales tax group** will be default from the main account specified in the **Offset account** field.  
    * The **Due date** will be calculated based on the Terms of payment.  
    * The **Cash discount** will default from the Vendor account.
12. If you have enabled Vendor invoice journal workflow, click **Workflow > Submit**.
    * When your submission is approved, the date will be advanced to the first day of the next open period, if the transaction posting date falls within a period that is **On hold** or **Closed** for ledger posting.
13. Click **Post**.
14. Close the page.

## Validation and simulation posting in vendor invoice journal

On the Vendor invoice journal, the **Validation** and **Simulate posting** options are available on the **Validate** menu. 
 - **Validate** -  The journal is tested for specific error conditions. The validation will return only successful or error messages. 
 - **Simulate posting** - The posting process is run without posting the journal and the details of voucher transactions will be diplayed. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
