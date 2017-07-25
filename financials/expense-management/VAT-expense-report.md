---
# required metadata

title: Value Added Tax (VAT) recovery in Expense
description: To receive refunds on eligible VAT transactions, a company or organization must identify, collect, verify, and submit 
accurate information
author: saraschi2
manager: AnnBe
ms.date: 07/25/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi2
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: AX 7.0.0
---

# Value Added Tax (VAT) recovery in Travel and expense 

[!include[banner](../includes/banner.md)]

To receive refunds on eligible VAT transactions, a company or organization must identify, collect, verify, and submit accurate 
information. This process includes multiple tasks, and depending on the size of your company, can include several employees or roles.

To recover VAT by using **Expense management**, the following prerequisite tasks must be completed:

-   Tax codes must be created for countries/regions that are allocated to expense categories.

-   A sales tax group must be created for each tax code.

-   An item sales tax code must be created for each sales tax group.

After these prerequisites are in place, employees can complete the following steps that are required to request refunds on 
VAT transaction:

1.  In an expense report, enter tax information about credit card transactions to identify eligible VAT refunds.

2.  Ensure that all tax information is complete before posting an expense report.

3.  Process eligible expenses for international VAT recovery.

4.  Send VAT recovery data to the third-party vendor to file international recovery returns.

5.  Process expenses for domestic VAT recovery.

The following scenarios provide examples of how Fabrikam employees complete these steps.

**In an expense report, enter tax information about credit card transactions to identify eligible VAT refunds**

Nancy, a U.S.-based Fabrikam sales representative, recently returned from a sales trip to the United Kingdom. Nancy must create 
an expense report to reconcile her expenses. During her trip, she incurred some personal credit card expenses for meals. When Nancy 
is entering information in her expense report in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, in the 
**Country/region** field of the **Edit expense report** page, she selects United Kingdom. The list of sales tax group is filtered to 
display only the groups that apply to the United Kingdom. 

Nancy selects the United Kingdom 001 sales tax group and then selects the Meals item sales tax group. Nancy then adds a new transaction
for her lodging. Because there is only one sales tax group and item sales tax group for lodging in the United Kingdom, this information 
is automatically filled in on Nancy’s expense report. Because Fabrikam has created a policy that all expenses must have a matching
receipt, when Nancy saves her expense report, a message appears that states that she must attach a receipt for each transaction that
is listed on her expense report. Nancy verifies that she has attached a digital image of each transaction receipt to her expense report 
and submits her report for approval. She then sends the paper receipts to the back-office processing team, which sends the VAT recovery 
data to the third-party vendor that files international VAT returns for recovery for Fabrikam.

**Ensure that all tax information is complete before posting an expense report**

April, the account payable coordinator for Fabrikam, must enter any tax information that is missing in an expense report before 
the report can be posted. April opens the **Expense report details** page and sees Nancy’s approved expense report. April opens the
expense report to view the details of the transactions. April sees that Nancy did not enter an item sales tax group for one of the 
transactions. Because this information is not provided, April cannot post the expense report. April looks in the **Tax configurations** 
page in **Expense management** and locates the appropriate item sales tax group for the country/region and the transaction type. 
April can now post the expense report to the general ledger. When April posts the expense report, a VAT recoverable work item is created. 
This work item is assigned to a member of the back-office processing team. The expense report is posted and April receives a message 
that confirms the success of the posting and that lists the number of VAT transactions that are identified for recovery.

### Process eligible expenses for international VAT recovery

Arnie, a member of Fabrikam’s back-office processing team, is responsible for confirming that all of the required information for 
VAT recovery is included in expense reports. Arnie opens the **Expense tax recovery** page and selects the expense report that Nancy
submitted. Arnie verifies that all of the required receipts are attached and that the correct sales tax group and item sales tax
codes were entered. When Arnie receives the paper receipts from Nancy, he verifies the paper receipts against the digital receipts and
changes the status of the expense report to **Ready for recovery**.

## Send VAT recovery data to the third-party vendor to file international recovery returns

When Arnie is ready to send the expense report data to the third-party vendor that will file the VAT recovery returns, he opens the 
**Expense tax recovery** page. Arnie filters the form to show only the expense reports that are marked as **Ready for recovery**. 
Arnie then clicks **File** \> **Export to Excel**.

The VAT information from the expense reports is exported into a Microsoft Office Excel worksheet. Arnie submits this worksheet to the 
third-party vendor and includes a message that the paper receipts have been sent by courier.

### Process expenses for domestic VAT recovery

Arnie must verify that the expense report transactions are eligible for VAT recovery and that the digital receipts are attached to
the reports. To start to process eligible expenses for domestic recovery, Arnie opens the **Expense tax recovery** page and selects 
the expense report that needs verification. Arnie verifies that receipts are in the name of the company and not the employee,
which is required for VAT recovery. Arnie then confirms that the correct sales tax group and item sales tax codes were applied. 
When Arnie receives the paper receipts, he changes the status of the expense report to **Ready for recovery**, which allows him to 
file the return with the appropriate taxing authority. In this case, the appropriate taxing authority in the U.S. is the Internal Revenue
Service (IRS).
