---
# required metadata

title: Net customer and vendor balances 
description: This article provides an overview of the process of customer and vendor balances netting in Dynamics 365 Finance. It explains how to set up the netting agreement, manual net customer and vendor balances, automatic net customer and vendor balances, and reverse posted netting transactions.
author: wangchen
ms.date: 09/06/2023
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



Customer and vendor balance netting is a process where the balances for a vendor and customer are netted against each other because the vendor and customer are the same party. This approach minimizes the exchange of money between an organization and the customer/vendor party. It can help a company avoid making unnecessary payments or receipts, and save on transaction fees, by consolidating the company’s customer and vendor balances.

This article provides an overview of the process of customer and vendor balances netting in Dynamics 365 Finance. It explains how to set up the netting agreement, manual net customer and vendor balances, automatic net customer and vendor balances, and reverse posted netting transactions.

> [!NOTE]
> This is a preview feature in Dynamics 365 Finance 10.0.38. The feature is available in sandbox only and general availability date in Production environment will be announced later.

## Set up journal name and main account

When customer invoices and vendor invoices are selected for balances netting, a netting journal will be posted automatically to settle the customer invoices balance and vendor invoices balance. To post this netting journal, a journal name and main account must be defined in advance.

1. Create a journal name with Journal Type **Customer and vendor netting**.

2. Create a main account as the bridging account for netting purpose.

## Set up netting agreement

Netting agreement allows users to maintain the pairs of customer account and vendor account for netting within an effective time period. It must be configured and activated before creating the netting transactions. 

1. Go to **Accounts payable** > **Payments** > **Netting** > **Netting agreement** , or **Accounts receivable** > **Payments** > **Netting** > **Netting agreement**
2. Create a record, and enter **Name** and **Description**
3. Select the journal name defined in the previous section.
4. Select the main account defined in the previous section.
5. Select the finance dimension values
6. Add **vendor account** and **customer account** as a pair in the **Parties** fast tab.
7. **Activate** the netting agreement.



## Manual netting

Users can manually net customer and vendor balances by selecting the open customer invoices and vendor invoices. System will automatically calculate the minimal amount between selected customer invoices balance and vendor invoice balance as the netting amount. A netting journal will be posted automatically with two journal lines. One journal line will automatically settle the selected customer invoices, and the other line will automatically settle the selected vendor invoices.

1. Go to **Accounts payable** > **Payments** > **Netting** > **Customer and vendor balances netting**, or **Accounts receivable** > **Payments** > **Netting** > **Customer and vendor balances netting**.

2. All the pairs of customer account and vendor account available for netting will be displayed in this page. Select one of the pairs, and click **Create Netting**.

3. Select the open customer invoices and open vendor invoices which you want to net, and click **Post**.

   

## Automatic netting

Users can automatically net customer and vendor balances by defining a netting rule first, and then run it through batch job or process automation framework.

### Set up netting rule

1. Go to **Accounts payable** > **Payments** > **Netting** > **Netting rule** , or **Accounts receivable** > **Payments** > **Netting** > **Netting rule**

2. Create a record, and enter **Name** and **Description**

3. Select a **Netting sequence**. There are four options available:

- By due date - from oldest to newest
- Bu due date - from newest to oldest
- By invoice balance - from largest to smallest
- By invoice balance - from smallest to largest

4. Select **Netting agreement** scope. If **All** is selected, then all the active netting agreement will be included in this rule; If **Selected** is selected, then user should define a netting agreement list in the following fast tab.\

5. Select **Yes** or **No** in the **Include credit not and debit note** parameter in the automatic netting.

6. In **Netting criteria** fast tab, define the criteria if users only want to automatically net certain vendor accounts, customer accounts, or invoice currency.

7. **Activate** the netting rule.

### Run automatic netting

There are three ways for users to run automatic netting.

- Users can trigger one time automatic netting by clicking **Automatic netting** on **Customer and vendor balances netting** form.
- Users can trigger one time automatic netting by the **Automatic netting** function in **Periodical tasks** menu in **Accounts payable** or **Accounts receivable** modules.
- Users can schedule periodical automatic netting by the **Process automation** function in the **Setup** menu in **Accounts payable** or **Accounts receivable** modules.

> [!NOTE]
> Automatic netting  will be available in Dynamics 365 Finance release version 10.0.39. Please monitor the [What's new or changed in Dynamics 365 Finance](https://learn.microsoft.com/en-us/dynamics365/finance/get-started/whats-new-home-page) for detail release information.

## Reverse netting

Users can reverse posted netting transactions by clicking the **Reverse netting** button on netting history form. This function will automatically unsettle the selected customer invoices, unsettle the selected vendor invoices, reverse the posted netting journal.

1. Go to **Accounts payable** > **Payments** > **Netting** > **Customer and vendor balances netting**, or **Accounts receivable** > **Payments** > **Netting** > **Customer and vendor balances netting**.
2. Click **Netting history**
3. Select the netting transaction and then click **Reverse netting**.



## Print netting advice

Users can print netting advice for the selected customer invoices and vendor invoices. The advice can be shared with the customer or the vendor as a notification for netting.

1. Go to **Accounts payable** > **Payments** > **Netting** > **Customer and vendor balances netting**, or **Accounts receivable** > **Payments** > **Netting** > **Customer and vendor balances netting**.
2. Click **Netting history**
3. Select the netting transaction and then click **Print netting advice**.