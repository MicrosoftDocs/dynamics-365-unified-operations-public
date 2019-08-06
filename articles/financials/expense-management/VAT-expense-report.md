---
# required metadata

title: VAT recovery in Expense management
description: This topic explains how to receive refunds on eligible value-added tax (VAT) transactions.
author: saraschi2
manager: AnnBe
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  TrvPerDiems
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# VAT recovery in Expense management

[!include [banner](../includes/banner.md)]

To receive refunds on eligible value-added tax (VAT) transactions, a company or organization must identify, collect, verify, and submit accurate information. This process includes multiple tasks and, depending on the size of your company, can include several employees or roles.

To recover VAT by using Expense management, the following prerequisites must be completed:

- Tax codes must be created for countries/regions that are allocated to expense categories.
- A sales tax group must be created for each tax code.
- An item sales tax code must be created for each sales tax group.

After the prerequisites are completed, employees follow these steps to request refunds for VAT transactions.

1. On an expense report, enter tax information about credit card transactions to identify eligible VAT refunds.
2. Make sure that all tax information is complete, and then post the expense report.
3. Process expenses that are eligible for international VAT recovery.
4. Send VAT recovery data to the third-party vendor to file international recovery returns.
5. Process expenses for domestic VAT recovery.

The following sections provide examples that show how Contoso employees complete each step.

## On an expense report, enter tax information about credit card transactions to identify eligible VAT refunds

Nancy, a Contoso sales representative who is based in the US, recently returned from a sales trip to the United Kingdom. During her trip, she incurred some personal credit card expenses for meals. Nancy must now create an expense report to reconcile her expenses.

When Nancy enters information on her expense report, she selects **United Kingdom** in the **Country/region** field on the **Edit expense report** page. The list of sales tax groups is then filtered so that it shows only the groups that apply to the United Kingdom. Nancy selects the **United Kingdom 001** sales tax group and then selects the **Meals** item sales tax group. She then adds a new transaction for her lodging. Because there is only one sales tax group and item sales tax group for lodging in the United Kingdom, this information is automatically filled in on Nancy's expense report.

Per Contoso policy, all expenses must have a matching receipt. Therefore, when Nancy saves her expense report, she receives a message that states that she must attach a receipt for each transaction that she listed on her expense report. Nancy verifies that she has attached a digital image of each transaction receipt to her expense report and then submits her report for approval. She then sends the paper receipts to the back-office processing team. This team will send the VAT recovery data to the third-party vendor that files international VAT recovery returns for Contoso.

## Make sure that all tax information is complete, and then post the expense report

April, the Accounts payable coordinator for Contoso, must enter any tax information that is missing from an expense report before the report can be posted. She opens the **Expense report details** page and sees Nancy's approved expense report. April then opens the expense report to view the details of the transactions. She sees that Nancy didn't enter an item sales tax group for one of the transactions. Because this information isn't provided, April can't post the expense report. Therefore, April looks on the **Tax configurations** page in Expense management, and finds the appropriate item sales tax group for the country/region and the transaction type. April can now post the expense report to the general ledger.

When April posts the expense report, a VAT recoverable work item is created. This work item is assigned to a member of the back-office processing team. April receives a message that confirms that posting was successful. This message also lists the number of VAT transactions that were identified for recovery.

## Process expenses that are eligible for international VAT recovery

Arnie, a member of Contoso's back-office processing team, is responsible for confirming that all the required information for VAT recovery is included on expense reports. He opens the **Expense tax recovery** page and selects the expense report that Nancy submitted. Arnie verifies that all the required receipts are attached, and that the correct sales tax group and item sales tax codes were entered.

When Arnie receives the paper receipts from Nancy, he verifies the paper receipts against the digital receipts and then changes the status of the expense report to **Ready for recovery**.

## Send VAT recovery data to the third-party vendor to file international recovery returns

When Arnie is ready to send the expense report data to the third-party vendor that will file the VAT recovery returns, he opens the **Expense tax recovery** page. He filters the page so that it shows only the expense reports that are marked as **Ready for recovery**. Arnie then selects **File** &gt; **Export to Excel**. The VAT information from the expense reports is exported to a Microsoft Excel worksheet. Arnie submits this worksheet to the third-party vendor and includes a message that states that the paper receipts have been sent by courier.

## Process expenses for domestic VAT recovery

Arnie must verify that the expense report transactions are eligible for VAT recovery, and that the digital receipts are attached to the reports. To start to process eligible expenses for domestic recovery, Arnie opens the **Expense tax recovery** page and selects the expense report that requires verification. He verifies that receipts are in the name of the company instead of the employee. For VAT recovery, receipts must be in the name of the company. Arnie then confirms that the correct sales tax group and item sales tax codes were applied.

When Arnie receives the paper receipts, he changes the status of the expense report to **Ready for recovery**. He can then file the return with the appropriate tax authority. In this case, the appropriate tax authority in the US is the Internal Revenue Service (IRS).
