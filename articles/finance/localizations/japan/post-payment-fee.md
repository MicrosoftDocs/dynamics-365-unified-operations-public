---
title: Generate and post payment fee
description: Learn how to generate and post a payment fee for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransVendPaym, VendTableLookup
ms.custom: 
  - bap-template
---

# Generate and post payment fee

[!include [banner](../../includes/banner.md)]

This article explains how to generate and post a payment fee for Japan in Microsoft Dynamics 365 Finance.

The following procedure uses the demo data company JPMF.

To generate and post a payment fee, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Payments \> Payment journal**.
1. Select **New**.
1. In the **Name** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Lines**.
1. In the **Account** field, enter a value. For example, enter "JPMF-000001".  
1. In the **Debit** field, enter a number.
1. Select **Save**.
1. Select the **Payment fee** tab.
1. Verify that the payment fee is generated correctly. You can also try to change the amount of payment, third party bank account, or the bank account to check if different combinations of these fields result in a different payment fee amount.  
1. Select **Post**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
