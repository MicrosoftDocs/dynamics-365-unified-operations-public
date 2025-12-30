---
title: Settle vendor consolidated invoices by using settle transactions
description: Learn how to settle vendor consolidated invoices for Japan by using settle transactions functionality in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: VendConsInvoice_JP, VendTable, VendOpenTrans
ms.custom: 
  - bap-template
---

# Settle vendor consolidated invoices by using settle transactions

[!include [banner](../../includes/banner.md)]

This article explains how to settle vendor consolidated invoices for Japan by using the settle transactions functionality in Microsoft Dynamics 365 Finance.

In Japan, you make payments and settle them against a consolidated invoice.

Before running the following procedures, ensure that you create and confirm a consolidated invoice and post a payment.

The procedures use the demo data company JPMF.

## Confirm the consolidation invoice to settle

To confirm the consolidation invoice to settle, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Periodic tasks \> Consolidated invoice**.
1. In the **Consolidation ID** field, copy the value to use later.
1. Confirm that the consolidated invoice to settle has a status of **Confirmed**.

## Settle a consolidation invoice

To settle a consolidation invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Vendors \> All vendors**.
1. In the list, find and select the vendor for whom you want to settle the consolidated invoice. For example, select **JPMF-000002**.  
1. On the Action Pane, select **Invoice**.
1. Select **Settle transactions**.
1. In the list, find and select the record with a consolidation ID of **JPMF-000004**.  
1. Select or clear the **Mark** checkbox.
1. In the list, find and select the payment transaction that is valued more than the invoice amount.  
1. Select or clear the **Mark** checkbox.
1. Select **Post**.

## Validate that a consolidation invoice status is settled

To validate that a consolidation invoice status is settled, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Periodic tasks \> Consolidated invoice**.
1. Confirm that the status of the consolidated invoice is **Settled**.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
