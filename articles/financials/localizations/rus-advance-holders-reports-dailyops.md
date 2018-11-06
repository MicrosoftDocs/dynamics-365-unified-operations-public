---
# required metadata

title: Advance reports with budget control (Russia)
description: 
author: ShylaThompson
manager: AnnBe
ms.date: 10/04/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.dyn365.ops.version: 8.1
ms.search.validFrom: 2018-10-31

---

# Advance reports with budget control (Russia)

[!include [banner](../includes/banner.md)]

## Accounting distributions and subledger journals

Subledger journal lines are accounting entries that are posted to the general ledger by using the general journal. You can generate subledgers from source documents such as invoices, packing slips, and picking lists for customers and vendors. Before you post the voucher information to the general ledger, you can view or modify subledger journals by using the distribution method. This method lets you allocate posting amounts among multiple financial dimensions. Depending on your user permissions, you can also change the default ledger account number or financial dimension values. Distributions serve as an interface to the subledger journals and contain only one side of the accounting entry.

An advance report is used to report travel expenses that an employee incurs during a business trip. You can distribute the expense amount across ledger dimensions. You can view the ledger entries and verify the distribution of the expense amount. Advance report posting supports ledger line functions, exchange adjustments, and advance adjustments. If the advance report transactions are split by distribution, the canceled advance report supports the creation of a storno accounting transaction to account the distribution.

## Manually generate and post advance report lines

An advance report is used to report travel expenses that an employee incurs during a business trip. Use this procedure to manually generate and post advance report lines.

You can distribute the expense amount among different ledger dimensions. You can then view the ledger entries and verify the distribution of the expense amount.

1. Select **Accounts payable** \> **Advance holders** \> **Advance reports**.
2. Press Ctrl+N to create an advance report. For more information, see.
3. On the **Advance report lines** FastTab, select **Add line** to create a line.
4. In the **Disbursement date** field, enter the date of the document that describes the expense.
5. In the **Document number** field, enter the number of the confirming document.
6. In the **Document name** field, enter the name of the confirming document.
7. In the **Currency** field, select the currency that is used for the transaction.
8. In the **Amount** field, enter the amount that is spent for the transaction.
9. In the **Confirmed amount of advance report** field, enter the confirmed expense for the advance report.
10. In the **Ledger account** field, select the general ledger account that the expense belongs to.
11. Select **Distribute amounts** to open the **Accounting distributions** page.
12. In the **Distributed by** field, select whether to distribute amounts by extended price or discount percentage.
13. Create distributions:

    - To create multiple distributions that have the same quantity, percentage, or amount distribution, select **Split** for each distribution. Select a ledger account for each distribution, and then select **Distribute equally**.
    - To create one distribution at a time, select **Split**. Select the ledger account to distribute the invoice line to, and then enter the quantity, percentage, or amount to distribute. For example, if you selected **Percent** in the **Distributed by** field, enter a percentage in the **Percent** field.

    Repeat until you've finished creating distributions.

14. Close the **Accounting distributions** page.
15. On the **Line details** FastTab, on the **Setup** tab, in the **Sales tax group** field, select the code for the sales tax group for the advance report.
17. In the **Item sales tax group** field, select the code for the item sales tax group for the advance report.
18. Set the **Prices include sales tax** option to **Yes** to indicate that the amount on the advance report includes sales tax.
19. On the Action Pane, select **Post** to post the advance report. The status of the advance report changes to **Posted**.

## Generate an expense account line by using the Copy from sources function

1. Select **Accounts payable** \> **Advance holders** \> **Advance reports**.
2. Press Ctrl+N, and enter information in the required fields.
3. In the lower pane, on the **Lines** tab, select **Functions** \> **Copy from sources** to open the **Create lines** dialog box. This dialog box shows a list of credit transactions that the advance holder has posted.

    > [!NOTE]
    > In the upper pane, the **Source type** field shows the identification type of the original document. The source for the **Facture** type is the purchase order, and the source for the **Accounts payable** type is the vendor transaction. The **Amount currency**, **Currency**, and **Amount** fields indicate the total amount in the secondary currency of the transaction, the currency code, and the amount in the company's standard currency, respectively. In the lower pane, the **Number** field shows the number of the vendor's facture. The **Description** field shows the item name. The **Currency**, **Amount currency**, and **Sales tax amount in currency** fields show the voucher currency, the line amount, and the sales tax amount, respectively.

5. In the upper pane, select the **Mark** check box to confirm the documents to copy.
6. Select **OK** to transfer the expense data to the advance report.

    In the **Document number** field of the advance report, the number of the source facture is copied if the **Line type** field of the advance report is set to **Facture**. If the **Line type** field of the advance report is set to **Vendor**, the number of the transaction is copied.

    > [!NOTE]
    > You can't edit the **Amount**, **Currency**, and **Ledger account** fields.

7. On the Action Pane, select **Post** to post the report.
8. Press Ctrl+S, or close the page.

## Generate advance report lines by using the Copy from expends function

1. Select **Accounts payable** \> **Advance holders** \> **Advance reports**.
2. Press Ctrl+N, and enter the required details.
3. In the lower pane, on the **Lines** tab, enter the required details.
5. Select **Functions** \> **Copy from expends** to open the **Create advance report lines** dialog box.
6. Select an expense line.
7. In the **Date** field, enter the date of the transaction.
8. In the **Document number** field, enter the number of the confirmed disbursement voucher.

    > [!NOTE]
    > The entries in the **Document name**, **Rate**, and **Currency** fields are automatically filled in from the expense rate Help book.

9. In the **Quantity of days** field, enter the number of days of the business trip.
10. In the **To weekday** field, enter the daily expense amount.

    > [!NOTE]
    > The **Total amount** field shows the total expense amount. The **Rate** and **Over rate** fields show information about the expense type.

11. Select **Save** to transfer the entries from the **Create advance report lines** dialog box to the advance report.

    > [!NOTE]
    > The value in the **Ledger account** field is based on the setup of expense rate posting. If the actual expense is more than the established rates, a supplementary line for the excess amount is created when the expenses are transferred to the advance report. In this case, the **Over rate** check box is automatically selected. For an advance report that is generated by using the **Copy from expends** function, the **Line type** field is set to **Expense**.

12. On the Action Pane, select **Post** to post the report.
13. Press Ctrl+S, or close the page.

## Generate and post a facture for an advance report

The **Generate facture by expense account** function can be used to reflect value-added tax (VAT) in the purchase ledger for the personal expenses of advance holders, such as the standard part of per diem expenses.

1. Select **Accounts payable** \> **Advance holders** \> **Advance reports**.
2. On the Action Pane, select **Update facture** to open the **Update facture** page.
2. In the lower pane, on the **Advance report** tab, you can view the details of the advance report.
3. Select the **To facture** check box to include advance reports in the facture.
4. On the **Advance report lines** tab, clear the **To facture** check box to exclude advance report lines that aren't included in the facture.
6. On the **Records affected** tab, you can view the included lines of the advance report.
7. In the upper pane, on the **Overview** tab, in the **Date of the registration** field, enter the registration date of the facture.
9. In the **Facture date** field, enter the facture date.

    > [!NOTE]
    > You must set the **Same as** option to **No** to set the **Facture date** field.

10. On the Action Pane, select **Posting** \> **Update and print** to post the document.
11. Press Ctrl+S, or close the **Update facture** page.
12. Select **Inquiries** \> **Advance report facture** to view the factures that are generated.
13. Press Ctrl+S, or close the **Advance reports** page.

## Void an expense report

You can void expense reports that have been posted, if the advance report for them has a status of **Posted**. These reports should not have been settled. Factures aren't created for these reports.

1. Select **Accounts payable** \> **Advance holders** \> **Advance reports**.
2. Select the advance report to void.
3. On the Action Pane, select **Rejection**. The status of the advance report is set to **Rejected**.

    > [!NOTE]
    > When an advance report is rejected, reversed transactions are created for the advance holder. The **Reversed** check box is automatically selected on the **Advance holder transactions** page. The transactions are automatically settled and reversed.

4. Close the page.
5. Select **Accounts payable** \> **Advance holders** \> **Advance holders**.
6. On the Action Pane, select **Transactions** to open the **Advance holder transactions** page.
7. On the Action Pane, select **Voucher**, and verify that the **Correction** check box is selected.

    You can verify the distribution of expenses for the reversed transaction. Reversed or storno accounting transactions are distributed like the original transactions. However, the distributions for reversed or storno accounting transactions have a negative sign.

## Budget control for advance reports

By using budget control, you can make sure that sufficient funds are available for planned or actual purchases. After you set up basic budgeting, you can set up budget control. You can use budget control to confirm whether budget funds are available on source documents, such as purchase orders, expense reports, advance reports, and accounting journals. If the budget funds exceed the budget limit that is set, additional processing of the document can be prevented.

An advance report is primarily used to report travel expenses that an employee incurs during a business trip. If the expenses that are incurred on an advance report exceed the budget that is set, budget control indicates that the funds aren't available.

To enable budget control for advance reports, follow these steps.

1. On the **Budget control configuration** page, on the **Select source documents** tab, select **Advance reports** as a source document for budget control, and enable budget checks for advance report lines.
2. On the **Budget funds available** tab, define the calculation that determines whether budget funds for advance reports are available.

### Budget calculation

When you define the budget calculation for advance reports, you should consider actual expenditures and unposted actual expenditures.

**Example**

Budget funds available = (Original budget + Budget revisions + Budget transfers) – (Actual expenditures + Unposted actual expenditures)

You can view the actual expenditures and unposted actual expenditures for each advance report line on the **Actual expenditures** page.

### Budget checking

Budget checking for advance reports makes sure that budget funds are available for planned or future expenditures. The budget checking process runs automatically when an advance report line is saved, or when the report is posted.
