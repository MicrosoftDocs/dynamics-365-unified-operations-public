--- 
# required metadata 
 
title: Key invoice data into accounts payable using an approval journal
description: This article explains how to use the invoice register to create invoices and then use the approval journal to update the expense accounts. 
author: abruer
ms.date: 02/11/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerJournalTable, LedgerJournalTransInvoiceRegister, HcmWorkerLookUp, LedgerJournalTransApprove, LedgerJournalTransApproveFetchVouchers, LedgerTransVoucher   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Key invoice data into accounts payable using an approval journal

[!include [banner](../../includes/banner.md)]

This article explains how to use the invoice register to create invoices and then use the approval journal to update the expense accounts.

## Create and post and invoice
1. In the navigation pane, go to **Modules > Accounts payable > Invoices > Invoice register**.
2. Select **New**.
3. Select the name of the invoice register that you want to use.
4. Select **Lines** to open the register and enter expense lines.
5. Select a vendor. For example, enter or select `US-104`.
6. In the **Invoice** field, type a value.
7. In the **Description** field, type a value.
8. In the **Credit** field, enter a number.
9. In the **Approved by** field, select an approver from the drop-down menu.
10. Select **Post**.

## Approve an invoice
1. In the navigation pane, go to **Modules > Accounts payable > Invoices > Invoice approval**.
2. Select **New**.
3. Select the name of the invoice approval journal that you want to use.
4. Select **Lines** to display a page where you will be able to select the invoices that you want to approve.
5. Select **Find Vouchers** to display all of the invoices that are ready for approval.
6. Mark the invoice that you created, then click **Select**. The vouchers that you selected above are moved to this list after you select them.  
7. Select **OK**.
8. Select the **account number** field to add an expense account to the invoice.
9. Enter an account number and tab off of the field. For example, enter `600120`.
10. Select **Post**.
11. Select **Voucher** to view the entries that were posted. The Invoice Pending Approval account is reversed and replaced with the actual expense account.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
