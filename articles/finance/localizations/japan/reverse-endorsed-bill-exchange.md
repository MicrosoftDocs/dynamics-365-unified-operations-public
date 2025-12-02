---
title: Reverse an endorsed bill of exchange
description: Learn how to reverse an endorsed bill of exchange from the accounts payable option for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 05/02/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: CustBillOfExchangeEndorseListPage, CustBillOfExchangeEndorseReverse, LedgerTransVoucher
ms.custom: 
  - bap-template
---

# Reverse an endorsed bill of exchange

[!include [banner](../../includes/banner.md)]

This article explains how to reverse an endorsed bill of exchange from the accounts payable option for Japan in Microsoft Dynamics 365 Finance.

Before you can complete the following procedure, you must have at least one endorsed bill of exchange. 

The procedure uses the demo data company JPMF.

To reverse an endorsed bill of exchange, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Payments \> Endorse bills of exchange**.
1. In the list, find and select a bill of exchange with a status of **Endorsed**.

    > [!NOTE]
    > You can't reserve a bill of exchange if the vendor transaction is already settled. Before you reserve the endorsement, you must undo the settlement.  

1. Select  **Reverse endorsement** to open the drop dialog.
1. Select  **Reverse endorsement**. You can change the reverse date if necessary.  
1. Select  **Inquiry**.
1. Select  **Voucher**.
1. Verify that an accounting voucher was generated for the reversal.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
