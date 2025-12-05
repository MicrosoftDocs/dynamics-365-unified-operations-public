---
title: Chinese voucher continuity check
description: This article describes how to check all posted vouchers in a fiscal period and renumber the Chinese voucher numbers to be sequential in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/05/2025
ms.reviewer: johnmichalak
ms.search.region: China (PRC)
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - LedgerCalendar, LedgerCheckList_CN
  - SysQueryForm, SysDateLookUp, LedgerTransVoucher, SrsReportViewerForm, LedgerVoucherRenumberLog_CN
ms.custom: 
  - bap-template
---

# Chinese voucher continuity check

[!include [banner](../../includes/banner.md)]

This article describes how to check all posted vouchers in a fiscal period and renumber the Chinese voucher numbers to be sequential in Microsoft Dynamics 365 Finance.

Before you can close a fiscal period, the Chinese voucher numbers for each voucher type must start at "1" and be sequential.

The following procedures show how to check all posted vouchers in a fiscal period and renumber the Chinese voucher numbers to be sequential. This process is part of the fiscal period closing process, so you can only run it for "On hold" fiscal periods. This procedure uses the demo data company CNMF.

## Stop a fiscal period

To stop a fiscal period, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Calendars \> Ledger calendars**.
1. In the **Fiscal year** field, enter or select a value.
1. In the list, find and select the desired record.
1. In the list, mark the selected row.
1. Select **Edit**.
1. Select **Stop period**.
1. Select **Validate**.
1. Select **OK**.
1. Select **OK**.

## Check whether posted vouchers have continuity voucher numbers

To check whether posted vouchers have continuity voucher numbers, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Inquiries and reports \> Voucher transactions**.
1. In the **Criteria** field, enter or select a value.
1. Select **OK**.

## Run the Chinese voucher continuity check process

To run the Chinese voucher continuity check process, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Periodic tasks \> Chinese voucher continuity check**.
1. In the **Print out the result of renumbering** field, select **Yes**.
1. In the **Period start** field, enter a date.
1. Select **OK**.
1. Go to **General ledger \> Inquiries and reports \> Voucher continuity check log**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
