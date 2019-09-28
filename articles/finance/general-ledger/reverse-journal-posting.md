---
# required metadata

title: Reverse journal posting
description: This topic describes capabilities in Microsoft Dynamics 365 for Finance and Operations that allows you to reverse vouchers from the voucher transaction list or from financial journals.  
author: MikeFalkner
manager: AnnBe
ms.date: 08/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerTransVoucher, LedgerJournalTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 15721
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: mikefalkner
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Reverse journal posting

[!include [banner](../includes/banner.md)]

This topic describes capabilities in Microsoft Dynamics 365 for Finance and Operations that allows you to reverse an entire
journal or reverse one or more vouchers from the voucher transaction list regardless of their origin. 

## Reversing journals

You can reverse journal lines individually. With reverse journal posting, you can also reverse an entire financial journal. 
To reverse a journal: 
- Open the financial journal and filter on posted journals
- Click on the Reverse menu at the top of the page
- You will see the total number of vouchers and voucher lines as well as the total amount of the lines being reversed
- Select Yes to use the existing transaction dates or No to enter a new one. In some cases, the period of the original transaction 
may be closed and you want to enter a new transaction date for the reversal.
- If you selected No, enter a transaction date for the reversal. 
- Enter a comment that you want added to the reversal transaction
- Click the Reverse button

The transactions will be reversed. 

If the number of voucher lines exceeds 100 lines, the reversal process will be run using the batch process. You can review the results
of the reversal by viewing the comments in the batch job that was run. All failures will be noted in the batch job history.

If the number of voucher lines is 100 lines or less, the reversal process will run immediately. The results will be presented in a dialog that shows any voucher that could not be reversed and the reason why it could not be reversed. Click on Ok to close the dialog.

## Reversing vouchers from the voucher transaction list. 

You can also reverse vouchers from the **Voucher transaction list** across all subledgers. In addition, you can reverse more than one
voucher at a time. 

To reverse one or more vouchers: 
- Click on the Reverse menu at the top of the page
- You will see the total number of vouchers and voucher lines as well as the total amount of the lines being reversed
- Select Yes to use the existing transaction dates or No to enter a new one. In some cases, the period of the original transaction 
may be closed and you want to enter a new transaction date for the reversal.
- If you selected No, enter a transaction date for the reversal. 
- Enter a comment that you want added to the reversal transaction
- Click the Reverse button

The transactions will be reversed. 

If the number of voucher lines exceeds 100 lines, the reversal process will be run using the batch process. You can review the results
of the reversal by viewing the comments in the batch job that was run. All failures will be noted in the batch job history.

If the number of voucher lines is 100 lines or less, the reversal process will run immediately. The results will be presented in a dialog that shows any voucher that could not be reversed and the reason why it could not be reversed. Click on Ok to close the dialog.

