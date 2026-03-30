---
title: Create a credit note against a sales invoice
description: Learn how to create a credit note against a sales invoice in Microsoft Dynamics 365 Finance.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/10/2025
ms.reviewer: johnmichalak  
ms.search.region: India
ms.search.validFrom: 2019-06-01
---

# Create a credit note against a sales invoice

[!include [banner](../../includes/banner.md)]

This article explains how to create a credit note against a sales invoice in Microsoft Dynamics 365 Finance.

## Create a sales order

To create a sales order, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Sales orders \> All sales orders**.
1. Create a sales credit note for a taxable item.
1. In the **Original invoice number** field, select a value.
1. Verify that the **Original invoice date** field is automatically set based on the original invoice number that you selected, and then save the record.
1. Select **Tax information**.
1. Select the **GST** tab.
1. Select the **Customer tax information** tab.
1. Select **OK**.
1. On the Action Pane, on the **Sell** tab, in the **Tax** group, select **Tax document**. You should see something that resembles the following example:

    - **Taxable amount:** -5,000
    - **IGST:** 20 percent
    - **CESS:** 1 percent

1. Select **Close**.

## Post the invoice

To post the invoice, follow these steps:

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Quantity** field, select **All**.
1. On the **Others** tab, verify that the **Invoice type** field is set to **Original**.

    > [!NOTE]
    > You can post a revised credit note by selecting **Revised** in the **Invoice type** field and then adding a reference to the original credit note.

1. Select **OK**, and then select **Yes** to acknowledge the warning message that you receive.

## Validate the voucher

To validate the voucher, follow these steps:

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. Select **Voucher**.

> [!NOTE]
> You can create a sales credit note through the general ledger and a free text invoice.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
