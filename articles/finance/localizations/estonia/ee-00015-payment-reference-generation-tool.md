---
title: EE-00015 Payment reference generation tool
description: This article describes how to specify number sequences for payment references and create payment reference numbers in Estonia with Microsoft Dynamics 365 Finance.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/11/2025
ms.reviewer: johnmichalak
ms.search.region: Estonia
ms.search.validFrom: 2016-06-30
ms.search.form: MainAccount, LedgerJournalTable, LedgerJournalTransDaily
---
# EE-00015 Payment reference generation tool

[!include [banner](../../includes/banner.md)]

This article describes how to specify number sequences for payment references and create payment reference numbers in Estonia with Microsoft Dynamics 365 Finance.

The following procedures walk you through generating the payment references. The procedures were created using the demo data company DEMF with the country/region of legal entity primary address updated to be Estonia.

## Specify a number sequence for payment references

To specify a number sequence for payment references, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Select the **Number sequences** tab.
1. In the **Reference** column, find and select the **Payment reference** record.
1. In the **Number sequence code** field, enter or select a value. You may want to select a dedicated, newly created numeric and continuous number sequence. For demo purposes, you can use  "Acco_18".  
1. Select **Save**.

## Create payment reference numbers

To create payment reference numbers, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Periodic tasks \> Create payment reference numbers**.
2. in the **Create payment reference numbers** field, select **Yes**.
    > [!NOTE]
    > To remove reference numbers already assigned to customers, select **Delete payment reference numbers**. To limit the number of customers for which you want to remove or create reference numbers, go to the **Record to include** section and apply criteria for customers or customer groups.  
3. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
