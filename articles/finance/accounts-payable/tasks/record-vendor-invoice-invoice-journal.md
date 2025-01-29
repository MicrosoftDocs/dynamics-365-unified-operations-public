--- 
title: Record a vendor invoice in the invoice journal
description: Learn about how to record vendor invoices that are not associated with purchase orders. 
author: sunfzam
ms.author: Raynezou
ms.topic: how-to
ms.date: 06/18/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: VendInvoiceWorkspace, LedgerJournalTable, LedgerJournalTransVendInvoice
ms.dyn365.ops.version: Version 7.0.0 
---

# Record a vendor invoice in the invoice journal

[!include [banner](../../includes/banner.md)]

This task guide shows how to record vendor invoices that aren't associated with purchase orders. Examples of this type of invoice include expenses for supplies or services. This recording uses the USMF demo company.

1. Go to **Accounts payable > Workspaces > Vendor invoice entry**.
2. On the **Action pane**, click **New invoice journal**.
3. Click **New**.
4. In the **Name** field, enter the journal name or click the drop down button to open the lookup.
5. In the **Description** field, type a value.
6. On the **Action pane**, click **Lines**. In the **Date** field, enter the posting date that will update General ledger.  
7. In the **Account** field, specify the **Vendor account**.
8. In the **Invoice** field, enter the invoice number.
9. In the **Description** field, type a value.
10. In the **Credit** field, enter a number.
11. In the **Offset account** field, enter the account number or click the drop down button to open the lookup.
    * The **Sales tax group** defaults from the vendor account.  
    * The **Item sales tax group** defaults from the main account specified in the **Offset account** field.  
    * The **Due date** is calculated based on the **Terms of payment**.  
    * The **Cash discount** defaults from the **Vendor account**.
12. If you have enabled the Vendor invoice journal workflow, click **Workflow > Submit**.
    * When your submission is approved and the transaction posting date falls within a period that's **On hold** or **Closed** for ledger posting, the date is advanced to the first day of the next open period.
13. Click **Post**.
14. Close the page.

## Validation and simulation posting in vendor invoice journal

On the **Vendor invoice** journal, the **Validate** and **Simulate posting** options are available on the **Validate** menu. 
 - **Validate** -  The journal is tested for specific error conditions. The validation returns only successful or error messages. 
 - **Simulate posting** - The posting process is run without posting the journal and the details of voucher transactions are diplayed. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
