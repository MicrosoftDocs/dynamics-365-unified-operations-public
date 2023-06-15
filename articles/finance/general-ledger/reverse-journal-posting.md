---
title: Reverse journal posting
description: This article describes capabilities that allows you to reverse vouchers from the voucher transaction list or from financial journals.
author: kweekley
ms.date: 10/08/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.form: LedgerTransVoucher, LedgerJournalTable
---

# Reverse journal posting

[!include [banner](../includes/banner.md)]

This article describes capabilities Microsoft Dynamics 365 Finance that allows you to reverse an entire journal, or reverse one or more vouchers from the voucher transaction list, regardless of their origin. 

Before you can use one of the features described in this article, it must be turned on in your system. Admins can use the **Feature management** workspace to check the status of the feature and turn it on if it's required. There, the feature is listed in the following way:
 - Module: General ledger
 - Feature name: **Mass reversals for multiple documents**

## Reversing journals

You can reverse journal lines individually. With reverse journal posting, you can also reverse an entire financial journal. 
To reverse a journal: 

- Filter on the posted journals and open the **Lines** view on the journal.
- Select the **Reverse entire journal** menu at the top of the page.
- You will see the total number of vouchers and voucher lines as well as the total amount of the lines being reversed.
- Select **Yes** to use the existing transaction dates or **No** to enter a new one. In some cases, the period of the original transaction may be closed and you must enter a new transaction date for the reversal.
- If you select **No**, enter a transaction date for the reversal. 
- Enter a comment that you want added to the reversal transaction.
- Select the **Reverse** button.

The transactions will be reversed. 

If the voucher contains more than 100 lines, the reversal process will run using the batch process. You can review the results
by viewing the comments in the batch job. Any transactions that couldn't be reversed will be listed in the batch job history.

If the voucher contains 100 lines or fewer, the reversal process will run immediately. The results will be presented in a dialog box that shows any voucher that could not be reversed, along with the reason why it could not be reversed. Select **OK** to close the dialog box.

## Reversing vouchers from the voucher transaction list. 

You can also reverse vouchers from the **Voucher transaction list** across all subledgers. In addition, you can reverse more than one
voucher at a time. 

To reverse one or more vouchers: 

- Select the **Reverse entire journal dropdown** menu at the top of the page.
- The total number of vouchers and voucher lines are displayed, as well as the total amount of the lines being reversed.
- Select **Yes** to use the existing transaction dates or **No** to enter a new one. In some cases, the period of the original transaction may be closed and you must enter a new transaction date to reverse it.
- If you select **No**, enter a transaction date for the reversal. 
- Enter a comment to describe the reversal transaction.
- Select the **Reverse** button.

The transactions will be reversed. 

If there are more than 100 voucher lines, the reversal process will run using the batch process. You can review the results
by viewing the comments in the batch job. Any transactions that couldn't be reversed will be noted in the batch job history.

If the number of voucher lines is 100 lines or fewer, the reversal process will run immediately. The results will display in a dialog box that shows any voucher that couldn't be reversed, along with the reason why. Select **OK** to close the dialog box.

Transactions can be reversed only if they meet the business rules for reversing them. Vendor payments cannot be reversed using the capability described in this article. Vendor payments must be reversed by following the steps listed in [Reverse a vendor payment](../accounts-payable/reverse-vendor-payment.md).



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
