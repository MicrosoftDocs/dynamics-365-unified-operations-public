---
# required metadata

title: Mass transaction reversals for multiple documents
description: 
author: Rcarlson
manager: AnnBe
ms.date: 10/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerChartofAccounts,DimensionDetails
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 14091
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2019-09-28
ms.dyn365.ops.version: 10.0.7

---

# Mass transaction reversals for multiple documents

[!include [banner](../includes/banner.md)]

This topic describes the process of reversing multiple voucher transactions at once. You can also reverse an entire journal without going to the subledger transaction form. When this feature is enabled, you can reverse one or more vouchers or reverse an entire journal by completing the following steps.

## Reverse one or more vouchers

Perform this action by opening the **Voucher transaction** page from any one of the possible entry points including **General Ledger > Inquiries and reports > Voucher transactions**. 

1.	From the **Voucher transactions** page, select one or more voucher records to reverse, and click the **Reverse transactions** button. 

2.	A dialog will appear as shown below with the choices to:
 >  a.	Use existing dates for reversal 
 >      i.	The default value of ‘No’ allows you to specify a new date for the reversal posting. 
 >      ii.	Setting the value of ‘Yes’ will keep the current transaction date for the reversal posting.
 >  b.	Reversal date – used when the above field for use existing dates for reversal is set to ‘No’
 >  c.	Reason Comment – The text value to be recorded on the reversed transaction generated from this process. 

3.	Click the **Reverse** button to initiate the reversal process. 

4.	The results window will appear with status of the reversal process.

[![Reverse transaction](./media/Reversal1_size.jpg)](./media/Reversal1_size.jpg)

## Reverse an entire journal
From a posted journal, opening the **Lines** page lets you select the “Reverse entire journal” button. The same options appear in the reversal form to select before clicking the **Reverse** button. 

[![Reverse Journal](./media/Reversal2.jpg)](./media/Reversal2.jpg)

### Batch processing 
Note that when you select more than 100 lines to reverse, the process will run as a batch process. The standard batch processing dialog will appear to let you schedule the reversal later, as appropriate for your organization. 

[![Reverse Batch](./media/Reversal3.jpg)](./media/Reversal3.jpg)

### Results
The results of the reversal process will display on the screen after it's completed when reversing fewer than 100 lines. When the batch processing is used for more than 100 lines, you can view the results and errors on the **View reversal failures** page, which you can open from the menu on the **Voucher inqiury** page. The result of each transaction reversal is displayed in the **Reason** column. 

[![Reverse Errors](./media/ReversalError.png)](./media/ReversalError.png)

## Known limitations

The selected transactions, journals or vouchers for reversal must be allowed for each transaction type. This feature uses the existing logic for what transactions are allowed/not allowed to be reversed, but simply allow multiple voucher transactions to be selected or an entire journal for reversal processing. For example, vendor payments must be reversed correctly and would fail the reversal process from this feature. Vendor payment reversal can be accomplished by following the steps in the related article. https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/accounts-payable/reverse-vendor-payment 
