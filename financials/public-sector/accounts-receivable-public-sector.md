---
# required metadata

title: Accounts receivable in the public sector | Microsoft Docs
description: This topic describes the Accounts receivable functionality that is available for the public sector.
author: rschloma
manager: AnnBe
ms.date: 2015-12-12 23:44:39
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: CustInvoiceJournal, CustParameters, CustTradingPartnerCode
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 26281
ms.assetid: 9cfc8a87-abe9-42e6-98a5-c6e9fba9c81d
ms.region: Global
ms.industry: Public sector
ms.author: brpotter

---

# Accounts receivable in the public sector

This topic describes the Accounts receivable functionality that is available for the public sector.

How do I set Accounts receivable parameters for the public sector?
------------------------------------------------------------------

Most Accounts receivable parameters are set the same way whether you’re in the public sector or the private sector. However, the parameters that are required for billing classifications and billing codes are used only by the public sector. For more information, see [Billing classifications and billing codes in the public sector](https://docs.microsoft.com/en-us/dynamics365/operations/financials/public-sector/billing-classifications-and-billing-codes-in-the-public-sector).

-   To enable the use of billing classifications and billing codes, in the **General** section, on the **Sales setup** FastTab, select **Use billing classifications**.
-   To prioritize the settlement of free text invoices, see the required parameter settings in [Settlement priority in the public sector](https://docs.microsoft.com/en-us/dynamics365/operations/financials/public-sector/settlement-priority-in-the-public-sector) and [Free text invoices in the public sector](https://docs.microsoft.com/en-us/dynamics365/operations/financials/public-sector/free-text-invoices-in-the-public-sector).
-   To use billing codes with Project accounting, select the option to display project-related fields on free text invoices. When you do this, two things happen:
    -   Project-related fields are displayed both on free text invoices and on billing codes.
    -   The ledger account related to the project is automatically used on the free text invoice. To allow users to change the ledger account on the free text invoice and in the accounting distributions, select the option to allow the ledger account number to be changed.

## How do I control the settlement order for Accounts receivable transactions?
You can use billing classifications along with other billing attributes to control the order that your Accounts receivable transactions are settled in. For details, see [Settlement priority in the public sector](https://docs.microsoft.com/en-us/dynamics365/operations/financials/public-sector/settlement-priority-in-the-public-sector).

## Is there an easy way to review reimbursement transactions?
You can use billing classifications to create a separate reimbursement transaction for each billing classification. When you do this, reimbursement transactions are grouped by the unique customer balance posting type entry and billing classification. For details, see [Reimbursements in the public sector](https://docs.microsoft.com/en-us/dynamics365/operations/financials/public-sector/reimbursements-in-the-public-sector).

## Where are the trading partner codes that I need for GFRS and FACTS I reporting?
The trading partner codes required for GFRS and FACTS I reporting are established by the US Department of the Treasury. Any organization that follows U.S. governmental reporting rules for accounts receivables should add trading partner codes to their customer account information for the agencies they do business with. For example, if your agency does business with the Federal Trade Commission, you’d go to the **Trading partner codes** page and create trading partner code 29. Then, on the customer detail page for the FTC, you’d enter 29 in the **Trading partner code** field.

### I created default financial dimensions for a customer group, but one customer in the group needs a different value for one of the financial dimensions. What’s the easiest way to handle this?

You can keep the default financial dimensions for the customer group. Just go to the customer record for the customer that needs a different value, and enter default financial dimensions for the customer. The customer’s default financial dimensions will override the default financial dimensions that were set for the customer group.

## What can I use Accounts receivable posting definitions for?
You can use posting definitions to create subledger journal lines for originating transactions that meet selected criteria - for example, to generate multiple, balanced, ledger entries based on attributes such as transaction types and accounts. To learn more about posting definitions, see [Posting definitions in the public sector](https://docs.microsoft.com/en-us/dynamics365/operations/financials/public-sector/posting-definitions-in-the-public-sector).

See also
--------

[Accounts receivable](https://docs.microsoft.com/en-us/dynamics365/operations/financials/accounts-receivable/accounts-receivable)

