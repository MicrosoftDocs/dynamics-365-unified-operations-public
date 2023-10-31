---
# required metadata

title: Net customer and vendor balances 
description: This article explains customer and vendor balance netting in Dynamics 365 Finance. 
author: wangchen
ms.date: 10/26/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2019-03-08
ms.dyn365.ops.version: 10.0

---
# Net customer and vendor balances

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

Customer and vendor balance netting is a process where the balances for a vendor and customer are netted against each other because the vendor and customer are the same party. This approach minimizes the exchange of money between an organization and the customer or vendor party. It can also help a company avoid making unnecessary payments or receipts, and save on transaction fees, by consolidating the company’s customer and vendor balances.

This article provides an overview of the customer and vendor balances netting process in Dynamics 365 Finance. This article also explains how to set up the netting agreement, manual net customer and vendor balances, automatic net customer and vendor balances, and reverse posted netting transactions.

> [!NOTE]
> This is a preview feature in Dynamics 365 Finance 10.0.38. The feature is available in sandbox only and general availability date in Production environment will be announced later.

## Set up journal name and main account

When customer invoices and vendor invoices are selected for balances netting, a netting journal is automatically posted to settle the customer invoices balance and vendor invoices balance. To post this netting journal, a journal name and main account must be defined in advance.

1. Create a journal name with the journal type, **Customer and vendor netting**.
2. Create a main account as the bridging account for netting purpose.

## Set up netting agreement

A netting agreement lets you to maintain the pairs of customer account and vendor account for netting within an effective time period. The agreement must be configured and activated before you create the netting transactions. 

1. Go to **Accounts payable** > **Payments** > **Netting** > **Netting agreement** , or **Accounts receivable** > **Payments** > **Netting** > **Netting agreement**
2. Create a new record, and enter a name and description.
3. Select the journal name that you defined earlier.
4. Select the main account defined earlier.
5. Select the finance dimension values.
6. On the **Parties** FastTab, add a vendor account and a customer account as a pair.
7. Activate the netting agreement.

## Manual netting

You can manually net customer and vendor balances by selecting the open customer invoices and vendor invoices. The system automatically calculates the minimal amount between selected customer invoices balance and vendor invoice balance as the netting amount. A netting journal is posted automatically with two journal lines. One journal line automatically settles the selected customer invoices, and the other line automatically settles the selected vendor invoices.

1. Go to **Accounts payable** > **Payments** > **Netting** > **Customer and vendor balances netting**, or **Accounts receivable** > **Payments** > **Netting** > **Customer and vendor balances netting**.
2. All the pairs of customer account and vendor account available for netting are displayed on this page. Select one of the pairs, and then select **Create Netting**.
3. Select the open customer invoices and open vendor invoices that you want to net, and select **Post**.

## Reverse netting

You can reverse posted netting transactions by selecting **Reverse netting** on the **Netting history** page. This function automatically unsettles the selected customer invoices, unsettles the selected vendor invoices, and reverses the posted netting journal.

1. Go to **Accounts payable** > **Payments** > **Netting** > **Customer and vendor balances netting**, or **Accounts receivable** > **Payments** > **Netting** > **Customer and vendor balances netting**.
2. Select **Netting history**
3. Select the netting transaction, and then select **Reverse netting**.

## Print netting advice

You can print netting advice for selected customer invoices and vendor invoices. The advice can be shared with the customer or the vendor as a notification for netting.

1. Go to **Accounts payable** > **Payments** > **Netting** > **Customer and vendor balances netting**, or **Accounts receivable** > **Payments** > **Netting** > **Customer and vendor balances netting**.
2. Select **Netting history**
3. Select the netting transaction and then select **Print netting advice**.




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
