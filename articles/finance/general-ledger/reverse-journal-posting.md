---
title: Reverse journal posting
description: This article describes capabilities that allows you to reverse vouchers from the voucher transaction list or from financial journals.
author: twheeloc
ms.date: 02/21/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.form: LedgerTransVoucher, LedgerJournalTable
---

# Reverse journal posting

[!include [banner](../includes/banner.md)]

This article describes capabilities Microsoft Dynamics 365 Finance that allows you to reverse an entire journal, or reverse one or more vouchers from the voucher transaction list, regardless of their origin. 

Before you can use one of the features described in this article, it must be turned on. Administrators can use the **Feature management** workspace to check the status of the feature and turn it on if it's required. The feature is listed in the following way:
 - Module: General ledger
 - Feature name: **Mass reversals for multiple documents**

It's recommended to turn on **Automatic split of large financial journals** feature from feature management. It offers performance improvements during the journal posting and journal reversal. 
For more information, see [Automatic split of large financial journals](auto-split-journal.md) 
The feature is listed in the following way:
 - Module: General ledger
 - Feature name: **Automatic split of large financial journals**   

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

If the voucher contains more than 100 lines, the reversal process will run using the batch process. You can review the results by viewing the comments in the batch job. Any transactions that couldn't be reversed will be listed in the batch job history.

If the voucher contains 100 lines or fewer, the reversal process will run immediately. The results will be presented in a dialog box that shows any voucher that couldn't be reversed, along with the reason why it couldn't be reversed. Select **OK** to close the dialog box.

## Reversing vouchers from the voucher transaction list. 

You can also reverse vouchers from the **Voucher transaction list** across all subledgers. In addition, you can reverse more than one voucher at a time. 

To reverse one or more vouchers: 

- Select the **Reverse entire journal dropdown** menu at the top of the page.
- The total number of vouchers and voucher lines are displayed, as well as the total amount of the lines being reversed.
- Select **Yes** to use the existing transaction dates or **No** to enter a new one. In some cases, the period of the original transaction may be closed and you must enter a new transaction date to reverse it.
- If you select **No**, enter a transaction date for the reversal. 
- Enter a comment to describe the reversal transaction.
- Select the **Reverse** button.

The transactions will be reversed. 

If there are more than 100 voucher lines, the reversal process will run using the batch process. You can review the results by viewing the comments in the batch job. Any transactions that couldn't be reversed will be noted in the batch job history.

If the number of voucher lines is 100 lines or fewer, the reversal process will run immediately. The results will display in a dialog box that shows any voucher that couldn't be reversed, along with the reason why. Select **OK** to close the dialog box.

Transactions can be reversed only if they meet the business rules for reversing them. Vendor payments cannot be reversed using the capability described in this article. Vendor payments must be reversed by following the steps listed in [Reverse a vendor payment](../accounts-payable/reverse-vendor-payment.md).

### Reverse related journals with journals that have been automatically split  

When the **Automatic split of large financial journals** feature is enabled, large journals with more than 1000 lines are automatically be split into multiple journals. For more information, see [Automatic split of large financial journals](auto-split-journal.md). 

When a user reverses a journal that's split into multiple journals, all related journals are reversed. For example, a user selects a journal from the list and selects **Reverse entire journal**, any related journals are checked and will post the reversal for all related journals. Users are able to view the count of related journals and total number of lines impacted, when the reversal is initiated. 

Reversing related journals is only supported at journal level. Users can reverse individual lines without impacting other lines.  

Reversal of split journals is a background process. Users can review the results by viewing the message log in the batch job history. Any transactions that couldn't be reversed are noted in the batch job history.   

>[!Note]
> Reversing related journals isn't possible when reversing vouchers from the **Voucher transaction inquiry** page. You can only reverse selected vouchers.  

### Examples 
Below are a couple examples: 

When a large journal that has 1050 lines split into two journals and are related to each other. The first journal gets 1000 lines and the other related one will get 50 lines. Users can initiate the reversal from either of these related journals but depending on from which journal the reversal is initiated, the user experience might differ. 
 - When the reversal is starts from the journal having 1000 lines. Both journals are reversed in a batch process. Notifications appear and two batch jobs are created for the reversal process.
 - When the reversal is starts from the journal having 50 lines. The first journal that has 50 lines will reverse from the synchronous process and the other journal with 1000 lines will reverse using the batch process.  

### Additional considerations

 - If the batch process fails and the reversal process doesn't complete, users can find more information on the batch job history log.
 - If the reversal of a journal is in progress and users try to reverse again, users are prevented from doing that. A **Reversal is already in progress** message is displayed.  

 



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
