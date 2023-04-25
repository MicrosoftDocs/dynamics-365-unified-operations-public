---
title: Chinese voucher continuity check
description: Before you can close a fiscal period, the Chinese voucher numbers for each voucher type must start at 1 and be sequential.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: China (PRC)
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
  - LedgerCalendar, LedgerCheckList_CN
  - SysQueryForm, SysDateLookUp, LedgerTransVoucher, SrsReportViewerForm, LedgerVoucherRenumberLog_CN
---
# Chinese voucher continuity check

[!include [banner](../../includes/banner.md)]

Before you can close a fiscal period, the Chinese voucher numbers for each voucher type must start at 1 and be sequential.
This procedure shows how to check all posted vouchers in a fiscal period and renumber the Chinese voucher numbers to to be sequential. This process is part of the fiscal period closing process, so it can only be run for On hold fiscal periods. The first sub task walks you through stopping a fiscal period. 

This procedure was created using the demo data company CNMF. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Stop a fiscal period
1. Go to General ledger > Calendars > Ledger calendars.
2. In the Fiscal year field, enter or select a value.
3. In the list, find and select the desired record.
4. In the list, mark the selected row.
5. Click Edit.
6. Click Stop period.
7. Click Validate.
8. Click OK.
9. Click OK.

## Check whether posted vouchers have continuity voucher numbers
1. Go to General ledger > Inquiries and reports > Voucher transactions.
2. In the Criteria field, enter or select a value.
3. In the Criteria field, enter or select a value.
4. Click OK.

## Run the Chinese voucher continuity check process
1. Go to General ledger > Periodic tasks > Chinese voucher continuity check.
2. Select Yes in the Print out the result of renumbering field.
3. In the Period start field, enter a date.
4. Click OK.
5. Go to General ledger > Inquiries and reports > Voucher continuity check log.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
