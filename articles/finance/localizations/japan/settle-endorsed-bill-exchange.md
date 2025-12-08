---
title: Settle an endorsed bill of exchange
description: Learn how to settle an endorsed bill of exchange for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: CustBillOfExchangeEndorseListPage, VendOpenTrans, CustBillOfExchangeEndorseSettle
ms.custom: 
  - bap-template
---

# Settle an endorsed bill of exchange

[!include [banner](../../includes/banner.md)]

This article explains how to settle an endorsed bill of exchange for Japan in Microsoft Dynamics 365 Finance.

Before you can complete the following procedures, you must have an endorsed bill of exchange and an open vendor transaction.

The procedures use the demo data company JPMF.

## Settle a vendor transaction that an endorsement generates

To settle a vendor transaction that an endorsement generates, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Payments \> Endorse bills of exchange**.
1. In the list, find and select a bill of exchange with a status of **Endorsed**.  
1. Select **Settle transactions**.
1. In the list, find and select the transaction that the endorsement of the bill of exchange generates.  
1. Select the **Mark** checkbox.
1. In the list, find and select the corresponding vendor transaction to settle with.  
1. Select the **Mark** checkbox.
1. Select **Post**.

## Settle an endorsed bill of exchange

To settle an endorsed bill of exchange, follow these steps.

1. Select **Settle endorsed bill of exchange** to open the dialog.
1. Select **Settle endorsed bill of exchange**.
1. Change the settlement date if necessary.  
1. Verify that the status is updated to **Endorsement settled**.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
