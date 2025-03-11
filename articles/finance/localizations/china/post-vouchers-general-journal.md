---
title: Post vouchers from the general journal
description: This article describes how to post Chinese vouchers using the general journal for China in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 03/11/2025
ms.reviewer: johnmichalak
ms.search.region: China (PRC)
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransDaily, LedgerJournalTransDimension, DimensionLookup
ms.custom: 
  - bap-template
---

# Post vouchers from the general journal

[!include [banner](../../includes/banner.md)]

This article describes how to post Chinese vouchers using the general journal for China in Microsoft Dynamics 365 Finance.

The following procedure walks you through posting Chinese vouchers using the general journal. This procedure was created using the demo data company CNMF.

For the CNMF demo data, you must create fiscal years through the current year in the fiscal calendar **Fiscal_CN**.

Before you can complete this procedure, ensure that you've created all of the necessary fiscal calendars. 

## Post vouchers from general ledger journals

To post vouchers from general ledger journals, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Journal entries \> General journals**.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Name** field, enter or select a value.
1. In the list, select the link in the selected row.
1. In the **Voucher type** field, enter or select a value.
1. In the **Account** field, enter the desired values.
1. In the **Description** field, enter or select a value.
1. In the **Debit** field, enter a number.
1. In the **Offset account type** field, select an option.
1. In the **Offset account** field, enter the desired values.
1. Select **Financial dimensions**.
1. Select **Offset account**.
1. In the **Cashflow_CN** field, enter or select a value.
1. Select **OK**.
1. Select **Validate**. For this example, the criteria for the voucher of type Pay must be met. This means that one of the debit and credit accounts must be a bank account that is a cash account, otherwise the validation doesn't pass.  
1. Select **Validate**.
1. Select **Post**.
1. Select **Print**.
1. Select **Voucher**.
1. In the **Print layout code** field, enter or select a value.
1. Select the **Print account dimension** checkbox.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
