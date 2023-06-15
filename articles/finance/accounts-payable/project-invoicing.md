---
# required metadata

title: Project invoicing
description: This article provides an overview of project invoicing for Time and material projects and Fixed-price projects. It includes information about invoice proposals (preliminary invoices), invoice control, on-account invoicing, vendor invoicing, and credit notes.
author: TaylorVH
ms.date: 07/10/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ProjInvoiceCashFlow, ProjInvoiceControl, ProjInvoiceListPage, ProjInvoiceProposalDetail, ProjInvoiceProposalListPage
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: zezhangzhao
# ms.tgt_pltfrm: 
ms.assetid: 1812d6f2-8b34-4258-8f5f-dcf12281547f
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-07-06
ms.dyn365.ops.version: AX 10.0.13

---

# Project invoicing

[!include [banner](../includes/banner.md)]

This article provides an overview of project invoicing for Time and material projects and Fixed-price projects. It includes information about invoice proposals (preliminary invoices), invoice control, on-account invoicing, vendor invoicing, and credit notes.

The project type determines which invoicing procedure should be applied. Only the two external project types, Time and material and Fixed-price, can be invoiced. Time and material projects and Fixed-price projects are always attached to a project contract.

-   **Fixed-price projects** – The customer invoice amount is based on invoice billing schedules. Invoicing is done through an on-account setup, which is also referred to as a billing schedule. Fixed-price projects can be invoiced per project or per project contract.
-   **Time and material projects** – The customer invoice amount is based on transaction lines that are entered on projects. Transactions can be invoiced per project or per project contract.

There are three ways to attach Time and material projects and Fixed-price projects to the invoice projects:

-   **On-account invoicing** – Time and material projects and Fixed-price projects can be invoiced on account. Two types of on-account setup are required, one for each project type.
-   **Invoicing in the periodic section** – Through the periodic functions, transactions can be invoiced across projects. The periodic functions provide an overview of transactions that must be invoiced.
-   **By using credit notes in invoicing** – A credit note can be created for both Time and material projects and Fixed-price projects.

## Invoice proposals
Before you create a customer invoice for a project, you can create a preliminary invoice, or invoice proposal. In an invoice proposal, you can select project transactions to include in a project invoice. You can then review the invoice details before you post the project invoice and send it to the customer or other funding source.

### Creating invoice proposals

You can create invoice proposals by manually selecting a transaction from a list of available transactions for a specified project. You can also set up billing rules that specify when to create an invoice proposal automatically. For example, you can create a billing rule to create an invoice proposal when work on a project is 25-, 50-, 75-, and 100-percent complete. 

You can create invoice proposals for the following transactions:

-   Hours, expenses, and other project transactions
-   Amounts that are withheld by customers on previous project invoices
-   Credit notes
-   Amounts that a customer paid to you before a project is started

> [!NOTE]
> The **Enable sorting by resource during project invoice proposal creation** feature enables the project accountant to sort the project transactions available for billing by the resource when creating a new project invoice proposal. The grid displaying the available project transactions will have separate fields for **Resource ID** and **Resource**. These fields let you filter and sort on the resource name. This feature is turned off by default. It can be enabled using the **Feature management** page (**Workspaces > Feature management**). Contact your system administrator for assistance with enabling this feature.

You can create fee transactions in an invoice proposal. You can also modify the sales price on hour, expense, item, and fee transactions. When you post an invoice proposal, the updated prices and transactions are added to project reports, and the transaction history. 

To create multiple customer invoices for a project, you must create an invoice proposal for each invoice. For example, you can create invoices based on transaction type. To specify hours on one customer invoice and items on another invoice, you must create separate invoice proposals for hour transactions and fee transactions. 

If a project has more than one funding source, you can create a separate invoice proposal for each funding source. On the **Funding rule allocations** page, you can define the percentage of the transaction amount to allocate to each funding source, and the source to post rounding differences to.

### Creating customer invoices from invoice proposals

After you create and post an invoice proposal, a customer invoice is automatically created for the transactions that are included in the invoice proposal. 

Before you post an invoice proposal, you can add transactions to it or delete transactions from it. For example, you can remove expense transactions that were posted to a project, but are not chargeable to the customer. 

If your organization requires that invoice proposals be reviewed before they are posted, you might need to be approved it through the "Review project invoice proposals" workflow before posting it.

### View grant information on project invoice list pages

Public sector users can add the **Grant ID** and **Grant name** to the **Project invoice proposals** and **Project invoices** list pages. These columns are enabled using the **Add grant information to project invoice list pages** feature. This feature is turned off by default and can be enabled in **Workspaces > Feature management**. Contact your system administrator for assistance with enabling this feature.

## On-account invoicing
The amount that you enter for a project in an on-account invoice is based on the timing, percentage of completion, and other billing conditions that are specified in the related project contract. The amount is not calculated based on the hours, items, expenses, or fees that are posted to the project. 

You must create an on-account transaction for a time-and-material project or a fixed-price project before you can add that on-account transaction to a project invoice. On the on-account transaction, enter the amount to invoice a customer. To create a project invoice for the amount, create a preliminary invoice (invoice proposal). In the invoice proposal, select the on-account transaction. You can review the on-account information in the invoice proposal before you create a project invoice for it. 

### Fixed-price projects
For Fixed-price projects, on-account transactions are based on an agreed-upon milestone, unit of delivery, or progress billing arrangement that is specified in a project contract. One line is created for each payment that must be received from the project customer. No deductions are required.

### Time and material projects

For Time and material projects, you can bill a customer or other funding source for a prepayment amount by using an on-account invoice proposal. Enter on-account transactions as one line. You can optionally enter additional lines as deductions to offset any prepayments that the customer has already made. To create deduction lines, enter a minus sign before the amount.

## Invoice control
You can use invoice control to track both invoiced and non-invoiced transactions, and to analyze those transactions against quotations for an end-to-end view of your projects from the quotation stage to completion. You can see which transactions have been charged to a specific project and which lines have been invoiced. You can also view individual transactions, so that you can adjust them after they are posted.

## Invoicing Fixed-price projects
To invoice a Fixed-price project, you must define a billing schedule and complete the invoicing procedure.

### Billing schedule

You can invoice fixed-price projects on a billing schedule. The billing schedule is defined in terms of one or more milestones for the project. For each milestone, you can define a specific date, sales currency, sales price, and activity. 

For example, you can set up the following billing schedule:

-   20 percent when the project contract is signed
-   30 percent on first delivery
-   15 percent on second delivery
-   35 percent on final delivery

### Invoicing procedure

When the milestone payments are ready to be invoiced, you use the procedure for invoicing amounts on-account.

## Vendor invoicing
When you order an item from a vendor and assign the item to a project, the line property that you select for the purchase order line for that item determines whether the purchased item is invoiced to a customer. If you set up default line properties, they are displayed for the item on the purchase order line (**Line details > Project > Line property amounts**). There are two ways to modify the line property:

-   Invoice the project's customer for the item. To do this, set the line property for the item to a chargeable value on the purchase order, and then invoice the customer by using the correct project invoicing method.
-   Don’t invoice the project's customer for the item. To do this, do not select the **Chargeable** line property on the purchase order line for the item. You can then invoice the purchase order, and no further action is required.

> [!NOTE] 
> Release retention lines are non-chargeable by default. This means the ability to create an invoice proposal for the released retention is not enabled.

## Credit notes
When an amount on a customer invoice has a negative value, the invoice is classified as a credit note. When the document is printed, it has the title "Credit note." 

When you create a credit note to credit an amount that was previously invoiced, you must first select the invoiced amount for crediting. You then create a credit note by following the same procedure that's used to create an ordinary customer invoice. You select the transactions that were previously posted on a customer invoice, and then create and post a credit note proposal. 

The same document can include transactions that are selected for crediting, credit transactions, and transactions that have been posted. The document is classified as either an invoice or a credit note, depending on whether the total amount is positive or negative. 

To credit an invoiced amount, you first select the invoiced amount to credit and then create a credit note. You create a credit note by following the same procedure that you would use to generate a customer invoice. 

You can create an invoice that has a negative amount, which becomes an invoice that is classified as a credit note. To create and print a credit note, you must select the transactions that were previously posted for a customer invoice, and then modify the transactions. Unless the primary address of the legal entity is in Germany, the title of the invoice will be "Corrective invoice."





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
