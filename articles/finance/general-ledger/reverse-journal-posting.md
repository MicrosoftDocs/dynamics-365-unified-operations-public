---
title: Reverse journal posting
description: Learn about capabilities that let you reverse vouchers from the voucher transaction list or from financial journals, including on outline on reversing journals.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 02/21/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerTransVoucher, LedgerJournalTable
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
---

# Reverse journal posting

[!include [banner](../includes/banner.md)]

This article describes the capabilities in Microsoft Dynamics 365 Finance for reversing either an entire journal, or one or more vouchers from the voucher transaction list, regardless of their origin.

Before you can use one of the features that are described in this article, it must be turned on. Administrators can use the **Feature management** workspace to check the status of the feature.

The feature is listed in the following way:

- **Module:** General ledger
- **Feature name:** Mass reversals for multiple documents

We recommend that you turn on the **Automatic split of large financial journals** feature from Feature management. This feature offers performance improvements during journal posting and journal reversal. For more information, see [Automatic split of large financial journals](auto-split-journal.md).

The feature is listed in the following way:

- **Module:** General ledger
- **Feature name:** Automatic split of large financial journals

## Reversing journals

You can reverse journal lines individually. With reverse journal posting, you can also reverse an entire financial journal.

To reverse a journal:

1. Filter on the posted journals and open the **Lines** view on the journal.
1. Select the **Reverse entire journal** menu at the top of the page.

    The total number of vouchers and voucher lines is shown, together with the total amount of the lines that are being reversed.

1. Select **Yes** to use the existing transaction dates or **No** to enter a new one. In some cases, the period of the original transaction might be closed, and you must enter a new transaction date for the reversal.
1. If you selected **No**, enter a transaction date for the reversal.
1. Enter a comment that you want added to the reversal transaction.
1. Select the **Reverse** button.

The transactions are reversed.

If the voucher contains more than 100 lines, the reversal process runs by using the batch process. You can review the results by viewing the comments in the batch job. Any transactions that couldn't be reversed are noted in the batch job history.

If the voucher contains 100 lines or fewer, the reversal process runs immediately. The results are displayed in a dialog box that shows any voucher that couldn't be reversed and the reason why it couldn't be reversed. Select **OK** to close the dialog box.

## Reversing vouchers from the voucher transaction list

You can also reverse vouchers from the voucher transaction list across all subledgers. In addition, you can reverse more than one voucher at a time.

To reverse one or more vouchers:

1. Select the **Reverse entire journal** dropdown menu at the top of the page.

    The total number of vouchers and voucher lines is shown, together with the total amount of the lines that are being reversed.

1. Select **Yes** to use the existing transaction dates or **No** to enter a new one. In some cases, the period of the original transaction might be closed, and you must enter a new transaction date to reverse it.
1. If you selected **No**, enter a transaction date for the reversal.
1. Enter a comment to describe the reversal transaction.
1. Select the **Reverse** button.

The transactions are reversed.

If there are more than 100 voucher lines, the reversal process runs by using the batch process. You can review the results by viewing the comments in the batch job. Any transactions that couldn't be reversed are noted in the batch job history.

If there are 100 or fewer voucher lines, the reversal process runs immediately. The results are displayed in a dialog box that shows any voucher that couldn't be reversed and the reason why it couldn't be reversed. Select **OK** to close the dialog box.

Transactions can be reversed only if they meet the business rules for reversing them. Vendor payments can't be reversed by using the capability that's described in this article. To reverse them, you must follow the steps in [Reverse a vendor payment](../accounts-payable/reverse-vendor-payment.md).

### Reverse related journals with journals that were automatically split

When the **Automatic split of large financial journals** feature is enabled, large journals that contain more than 1,000 lines are automatically split into multiple journals. For more information, see [Automatic split of large financial journals](auto-split-journal.md).

When a user reverses a journal that's split into multiple journals, all related journals are reversed. For example, a user selects a journal in the list and then selects **Reverse entire journal**. Any related journals are checked, and the reversal is posted for all related journals. Users can view the count of related journals and the total number of lines that are affected.

The reversal of related journals is supported only at the journal level. Users can reverse individual lines without affecting other lines.

The reversal of split journals is a background process. Users can review the results by viewing the message log in the batch job history. Any transactions that couldn't be reversed are noted in the batch job history.

> [!NOTE]
> The reversal of related journals isn't possible when vouchers are reversed from the **Voucher transaction inquiry** page. You can reverse only selected vouchers.

### Example

A large journal that contains 1,050 lines is split into two journals that are related to each other. The first journal contains 1,000 lines, and the other related journal contains 50 lines. Users can initiate the reversal from either of the related journals. However, the user experience varies, depending on the journal that the reversal is initiated from.

- If the reversal is initiated from the journal that contains 1,000 lines, both journals are reversed in a batch process. Notifications appear, and two batch jobs are created for the reversal process.
- If the reversal is initiated from the journal that contains 50 lines, the first journal (the journal that contains 50 lines) is reversed from the synchronous process. The other journal (the journal that contains 1,000 lines) is reversed by using the batch process.

### More considerations

- If the batch process fails, and the reversal process isn't completed, users can find more information in the batch job history log.
- If the reversal of a journal is in progress, and users try to reverse that journal again, they're prevented from doing so and receive the following message: "Reversal is already in progress."

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
