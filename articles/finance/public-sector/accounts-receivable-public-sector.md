---
# required metadata

title: Accounts receivable in the public sector overview
description: This article describes the Accounts receivable functionality that is available for the public sector.
author: v-kiarnd
ms.date: 07/25/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustInvoiceJournal, CustParameters, CustTradingPartnerCode
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: a411ec87-a209-471c-a141-5f5a92f2e45e
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Accounts receivable in the public sector overview

[!include [banner](../includes/banner.md)]

This article describes the Accounts receivable functionality that is available for the public sector.

## How do I set Accounts receivable parameters for the public sector?

Most Accounts receivable parameters are set the same way whether you’re in the public sector or the private sector. However, the parameters that are required for billing classifications and billing codes are used only by the public sector. For more information, see [Billing classifications and billing codes in the public sector](billing-classifications-billing-codes-public-sector.md).

-   To enable the use of billing classifications and billing codes, in the **General** section, on the **Sales setup** FastTab, select **Use billing classifications**.
-   To prioritize the settlement of free text invoices, see the required parameter settings in [Settlement priority in the public sector](settlement-priority-public-sector.md) and [Free text invoices in the public sector](free-text-invoices-public-sector.md).
-   To use billing codes with Project accounting, select the option to display project-related fields on free text invoices. When you do this, two things happen:
    -   Project-related fields are displayed both on free text invoices and on billing codes.
    -   The ledger account related to the project is automatically used on the free text invoice. To allow users to change the ledger account on the free text invoice and in the accounting distributions, select the option to allow the ledger account number to be changed.

## How do I control the settlement order for Accounts receivable transactions?
You can use billing classifications along with other billing attributes to control the order that your Accounts receivable transactions are settled in. For details, see [Settlement priority in the public sector](settlement-priority-public-sector.md).

## Is there an easy way to review reimbursement transactions?
You can use billing classifications to create a separate reimbursement transaction for each billing classification. When you do this, reimbursement transactions are grouped by the unique customer balance posting type entry and billing classification. For details, see [Reimbursements in the public sector](reimbursements-public-sector.md).

## Where are the trading partner codes that I need for GFRS and FACTS I reporting?
The trading partner codes required for GFRS and FACTS I reporting are established by the U.S. Department of the Treasury. Any organization that follows U.S. governmental reporting rules for accounts receivables should add trading partner codes to their customer account information for the agencies they do business with. For example, if your agency does business with the Federal Trade Commission, you’d go to the **Trading partner codes** page and create trading partner code 29. Then, on the customer detail page for the FTC, you’d enter 29 in the **Trading partner code** field.

### I created default financial dimensions for a customer group, but one customer in the group needs a different value for one of the financial dimensions. What’s the easiest way to handle this?

You can keep the default financial dimensions for the customer group. Just go to the customer record for the customer that needs a different value, and enter default financial dimensions for the customer. The customer’s default financial dimensions will override the default financial dimensions that were set for the customer group.

## What can I use Accounts receivable posting definitions for?
You can use posting definitions to create subledger journal lines for originating transactions that meet selected criteria - for example, to generate multiple, balanced, ledger entries based on attributes such as transaction types and accounts. To learn more about posting definitions, see [Posting definitions in the public sector](posting-definitions-public-sector.md).

## Additional resources

[Accounts receivable](../accounts-receivable/accounts-receivable.md)

[Create a billing code](tasks/create-billing-code-public-sector.md)

[Create a billing classification](tasks/create-billing-classification-public-sector.md)

[Create and assign a trading partner code](tasks/create-assign-trading-partner-code-public-sector.md)




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
