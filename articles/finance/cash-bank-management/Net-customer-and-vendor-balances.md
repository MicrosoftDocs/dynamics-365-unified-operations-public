---
# required metadata

title: Net customer and vendor balances 
description: This article explains customer and vendor balance netting in Microsoft Dynamics 365 Finance. 
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

Customer and vendor balance netting is a process where the balances for a vendor and a customer are netted against each other, because the vendor and customer are the same party. This approach minimizes the exchange of money between an organization and the customer or vendor party. It can also help a company avoid making unnecessary payments or receipts, and save on transaction fees, by consolidating the company's customer and vendor balances.

This article provides an overview of the customer and vendor balance netting process in Microsoft Dynamics 365 Finance. It also explains how to set up the netting agreement, manually net customer and vendor balances, and reverse posted netting transactions.

> [!NOTE]
> This feature is a preview feature in Dynamics 365 Finance version 10.0.38 and is available only in sandbox environment. The general availability date in production environments will be announced later.

## Set up a journal name and main account

When customer invoices and vendor invoices are selected for balance netting, a netting journal is automatically posted to settle the customer invoice balance and the vendor invoice balance. To post this netting journal, a journal name and main account must be defined in advance.

1. Create a journal name of the **Customer and vendor netting** journal type.
2. Create a main account as the bridging account for netting purposes.

## Set up a netting agreement

A netting agreement lets you maintain the pairs of customer accounts and vendor accounts for netting during an effective time period. The agreement must be configured and activated before you create the netting transactions.

1. Go to **Cash and bank management** \> **Netting** \> **Netting agreement**.
2. Create a record, and enter a name and description.
3. Select the journal name that you defined earlier.
4. Select the main account that you defined earlier.
5. Select the finance dimension values.
6. On the **Parties** FastTab, add a vendor account and a customer account as a pair.
7. Activate the netting agreement.

## Manual netting

You can manually net customer and vendor balances by selecting the open customer invoices and vendor invoices. The system automatically calculates the minimal amount between the customer invoice balance and the vendor invoice balance as the netting amount. A netting journal that has two journal lines is automatically posted. One journal line automatically settles the selected customer invoices, and the other line automatically settles the selected vendor invoices.

1. Go to **Cash and bank management** \> **Netting** \> **Customer and vendor balances netting**.
2. The page shows all the pairs of customer accounts and vendor accounts that are available for netting. Select a pair, and then select **Create Netting**.
3. Select the open customer invoices and open vendor invoices that you want to net, and then select **Post**.

## Automatic netting

You can automatically net customer and vendor balances by defining a netting rule and then running it through a batch job or the process automation framework.

### Set up a netting rule

1. Go to **Cash and bank management** \> **Netting** \> **Netting rule**.
2. Create a record, and enter a name and description.
3. Select a netting sequence. Four options are available:

    - By due date - From oldest to newest
    - By due date - From newest to oldest
    - By invoice balance - From largest to smallest
    - By invoice balance - From smallest to largest

4. Select the netting agreement scope. If you select **All**, all the active netting agreements are included in this rule. If you select **Selected**, define a netting agreement list.
5. In the automatic netting, in the **Include credit note and debit note** field, select **Yes** or **No**.
6. On the **Netting criteria** FastTab, define the criteria if users want to automatically net only specific vendor accounts, customer accounts, or invoice currency.
7. Activate the netting rule.

### Run automatic netting

There are three ways to run automatic netting.

- Trigger a one-time automatic netting by selecting **Automatic netting** on the **Customer and vendor balances netting** page.
- Trigger a one-time automatic netting by selecting **Automatic netting** on the **Netting** menu in the **Cash and bank management** module.
- Schedule periodic automatic netting by selecting **Process automation** on the **Netting** menu in the **Cash and bank management** module.

## Reverse netting

You can reverse posted netting transactions by selecting **Reverse netting** on the **Netting history** page. This function automatically unsettles the selected customer invoices, unsettles the selected vendor invoices, and reverses the posted netting journal.

1. Go to **Cash and bank management** \> **Netting** \> **Customer and vendor balances netting**.
2. Select **Netting history**.
3. Select the netting transaction, and then select **Reverse netting**.

## Print netting advice

You can print netting advice for selected customer invoices and vendor invoices. The advice can then be shared with the customer or vendor as a notification for netting.

1. Go to **Cash and bank management** \> **Netting** \> **Customer and vendor balances netting**.
2. Select **Netting history**.
3. Select the netting transaction, and then select **Print netting advice**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
