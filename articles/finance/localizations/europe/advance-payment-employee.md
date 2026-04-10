---
title: EEU-00047 Advance payment to employee
description: This article describes how to set up and register transactions for an advance holder in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/05/2025
ms.reviewer: johnmichalak
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.search.validFrom: 2016-06-30
ms.search.form: RCashTable, LedgerJournalSetup, HcmWorkerGroup_RU, EmplPosting_RU, VendParameters, RCashPosting, BankParameters, PaymTerm, HcmWorker, HcmWorkerNewWorker, HcmWorkerAdvHolderTableListPage_RU, HcmWorkerAdvHolderTable_RU, PurchTable, PurchCreateOrder, HcmAdvHolderLookup_RU, InventItemIdLookupPurchase, VendEditInvoice, VendEditInvoiceDefaultQuantityForLinesDropDialog, EmplTrans_RU, EmplBalance_RU
ms.custom: 
  - bap-template
---

# EEU-00047 Advance payment to employee

[!include [banner](../../includes/banner.md)]

This article describes how to set up and register transactions for an advance holder in Microsoft Dynamics 365 Finance.

The following procedures demonstrate how to set up and register transactions for an advance holder. The procedures use the demo data company DEMF with a primary address in Lithuania, and only work for legal entities with a primary address in Poland, Lithuania, Latvia, Estonia, Czech Republic, or Hungary.

## Create a new cash account

To create a new cash account, follow these steps:

1. In Dynamics 365 Finance, go to **Cash and bank management \> Bank accounts \> Cash accounts**.
1. Select **New**.
1. In the **Cash** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Number sequence group** field, enter or select a value.
1. Expand the **Validation** section.
1. In the **Currency** field, enter or select a value.
1. In the **Negative cash** field, select **Yes**.
1. Select **Save**.

## Create a new journal

To create a new journal, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger \> Journal setup \> Journal names**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. In the **Voucher series** field, enter or select a value.
1. Select **Save**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. In the **Journal type** field, select an option.
1. In the **Voucher series** field, enter or select a value.
1. Select **Save**.

## Create an advance holder group

To create an advance holder group, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Setup \> Advance holders \> Advance holder groups**.
1. Select **New**.
1. In the **Group** field, enter a value.
1. In the **Description** field, enter a value.
1. Select **Save**.

## Create an employee posting profile

To create an employee posting profile, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Setup \> Advance holders \> Employee posting profiles**.
1. Select **New**.
1. In the **Posting profile** field, enter a value.
1. In the **Description** field, enter a value.
1. In the list, mark the selected row.
1. In the **Valid for** field, select an option.
1. In the **Summary account** field, enter a value.
1. Select **Save**.

## Set up advance holder parameters

To set up advance holder parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Setup \> Accounts payable parameters**.
1. Select the **Advance holders** tab.
1. In the **Posting profile** field, enter or select a value.
1. In the **Name** field, enter or select a value.
1. In the **Cash** field, enter or select a value.
1. In the **Account type** field, select an option.
1. In the **Main account** field, enter a value.
1. Select the **Number sequences** tab.
1. Select **Save**.

## Set up a cash posting profile

To set up a cash posting profile, follow these steps:

1. In Dynamics 365 Finance, go to **Cash and bank management \> Setup \> Cash posting profiles**.
1. Select **New**.
1. In the **Cash posting** field, enter a value.
1. In the **Description** field, enter a value.
1. In the list, mark the selected row.
1. In the **Valid for** field, select an option.
1. In the **Main account** field, enter a value.
1. Select **Save**.

## Set up cash and bank parameters

To set up cash and bank parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Cash and bank management \> Setup \> Cash and bank management parameters**.
1. Select the **Cash** tab.
1. In the **Cash** field, enter or select a value.
1. In the **Cash posting** field, enter or select a value.
1. Select **Save**.
1. Select the **Number sequences** tab.
1. In the list, find and select the desired record.
1. In the **Number sequence code** field, enter or select a value.
1. In the list, find and select the desired record.
1. In the **Number sequence code** field, enter or select a value.
1. Select **Save**.

## Set up terms of payment

To set up terms of payment, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Payment setup \> Terms of payment**.
1. Select **Edit**.
1. In the **From advance holder** field, select **Yes**.
1. Select **Save**.

## Create a new worker

To create a new worker, follow these steps:

1. In Dynamics 365 Finance, go to **Human resources \> Workers \> Workers**.
1. Select **New**.
1. In the **First name** field, enter a value.
1. In the **Last name** field, enter a value.
1. In the **Worker ID** field, enter a value.
1. Select **Hire new worker**.
1. Select **Save**.

## Set up a worker as an advance holder

To set up a worker as an advance holder, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Advance holders \> Advance holders**.
1. Select **Edit**.
1. In the **Group** field, enter or select a value.
1. In the **Advance holder** field, select **Yes**.
1. Select **Save**.

## Create and post a purchase order invoice

To create and post a purchase order invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, enter or select a value.
1. Select **OK**.
1. In the **Lines or header** field, select an option.
1. Expand the **Price and discount** section.
1. In the **Terms of payment** field, enter or select a value.
1. In the **Advance holder** field, enter or select a value.
1. In the **Lines or header** field, select an option.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Unit price** field, enter a number.
1. Select **Save**.
1. On the Action Pane, select **Purchase**.
1. Select **Confirm**.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. Select **Default from: Product receipt quantity** to open the drop dialog.
1. In the **Default quantity for lines** field, select an option.
1. Select **OK**.
1. In the **Number** field, enter a value.
1. In the **Invoice description** field, enter a value.
1. In the **Invoice date** field, enter a date.
1. In the **Date of VAT register** field, enter a date.
1. In the **Receive document date** field, enter a date.
1. Select **Post**.

## Balance and close advance holders transactions

To balance and close advance holders transactions, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Advance holders \> Advance holders**.
1. Select **Transactions**.
1. Close the page.
1. Select **Balance**.
1. Select **Close via bank**.
1. In the **Automatic** field, select **Yes**.
1. In the **Amount to be transferred** field, enter a number.
1. Select **OK**.
1. Select **Close via cash**.
1. In the **Automatic** field, select **Yes**.
1. Select **OK**.
1. Close the page.
1. Select **Transactions**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
