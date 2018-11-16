---
# required metadata

title: Advance reports with budget control (Russia)
description: This topic shows how to generate subledgers from source documents such as invoices, packing slips, and picking lists for customers and vendors. 
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

# Advance reports with budget control

[!include [banner](../includes/banner.md)]

## Accounting distributions and subledger journals
Subledger journal lines are accounting entries that are posted to the general ledger by using the general journal. You can generate subledgers from source documents such as invoices, packing slips, and picking lists for customers and vendors. Before you post the voucher information to the general ledger, you can view or modify subledger journals by using the distribution method. This method lets you allocate posting amounts between multiple financial dimensions, and change the default ledger account number or financial dimension values based on user permissions. Distributions serve as an interface to the subledger journals and only contain one side of the accounting entry.

An advance report is used to report travel expenses that are incurred by an employee during a business trip. You can distribute the expense amount across ledger dimensions. You can view the ledger entries and verify the distribution of the expense amount. Advance report posting supports ledger line functions, exchange adjustments, and advance adjustments. If the advance report transactions are split by distribution, the canceled advance report supports the creation of a storno accounting transaction to account the distribution.

## Generate and post advance report lines manually
An advance report is used to report travel expenses that are incurred by an employee during a business trip. Use this procedure to generate and post advance report lines manually.

You can distribute the expense amount between different ledger dimensions. You can then view the ledger entries and verify the distribution of the expense amount.

1.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance reports**.
2.  Press CTRL+N to create a new advance report. For more information, see.
3.  Click the **Advance report lines** FastTab, and then click **Add line** to create a new line.
4.  In the **Disbursement date** field, enter the date of the document that describes the expense.
5.  In the **Document number** field, enter the number of the confirming document.
6.  In the **Document name** field, enter the name of the confirming document.
7.  In the **Currency** field, select the currency that is used for the transaction.
8.  In the **Amount** field, enter the amount that is spent for the transaction.
9.  In the **Confirmed amount of advance report** field, enter the confirmed expense for the advance report.
10. In the **Ledger account** field, select the general ledger account that the expense belongs to.
11. Click **Distribute amounts**.
12. In the **Distributed by** field, select whether to distribute amounts by extended price or discount percentage.
13. You can create distributions in the following ways:
    
      - To create multiple distributions that have the same quantity, percentage, or amount distribution, click **Split** for each distribution. Select a ledger account for each distribution, and then click **Distribute equally**.
    
      - To create one distribution at a time, click **Split**. Select the ledger account to distribute the invoice line to, and then enter the quantity, percentage, or amount to distribute. For example, if you selected **Percent** in the **Distributed by** field, enter a percentage in the **Percent** field.
    
    Repeat until you have finished creating distributions.

14. Close the form.
15. Click the **Setup** tab.
16. In the **Sales tax group** field, select the code for the sales tax group for the advance report.
17. In the **Item sales tax group** field, select the code for the item sales tax group for the advance report.
18. Select the **Prices include sales tax** check box to indicate that the amount on the advance report includes sales tax.
19. On the **Action Pane**, click **Post** to post the advance report. The status of the advance report changes to **Posted**.

## Generate an expense account line using the Copy from sources function

1. Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance reports**.
2. Press CTRL+N and enter information in the required fields.
3. In the lower pane, click the **Lines** tab.
4. Click **Functions**, and then select **Copy from sources** to open the **Create lines - Advance report** form. The form displays a list of credit transactions posted by the advance holder.
    
    > [!NOTE]
    > <P>In the upper pane, the <STRONG>Source type</STRONG> field displays the identification type of the original document. The source for type <STRONG>Facture</STRONG> is the purchase order, and the source for type <STRONG>Accounts payable</STRONG> is the vendor transaction. The <STRONG>Amount currency</STRONG>, <STRONG>Currency</STRONG>, and <STRONG>Amount</STRONG> fields indicate the total amount in the secondary currency of the transaction, the currency code, and the amount in the company's standard currency. In the lower pane, the <STRONG>Number</STRONG> field displays the number of the vendor's facture. The <STRONG>Description</STRONG> field displays the item name. The <STRONG>Currency</STRONG>, <STRONG>Amount currency</STRONG>, and <STRONG>Sales tax amount in currency</STRONG> fields display the voucher currency, the line amount, and the sales tax amount respectively.</P>

5. In the upper pane, select the **Mark** check box to confirm the documents to be copied.
6. Click **OK** to transfer the expense data to the advance report.
    
    In the **Document number** field of the advance report, the number of the source facture is copied if the **Line Type** field of the advance report is set to **Facture**, or the number of the transaction is copied if the **Line Type** field of the advance report is set to **Vendor**.
    
    > [!NOTE]
    > <P>You cannot edit the <STRONG>Amount</STRONG>, <STRONG>Currency</STRONG>, and <STRONG>Ledger account</STRONG> fields.</P>

7.  Click **Post** to post the report.
8.  Press CTRL+S or close the form.

## Generate advance report lines using the Copy from expenses function

1.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance reports**.
2.  Press CTRL+N and enter the required details.
3.  In the lower pane, click the **Lines** tab.
4.  Enter the required details.
5.  Click **Functions**, and select **Copy from expends**.
6.  Select an expense line.
7.  In the **Date** field, enter the date of the transaction.
8.  In the **Document number** field, enter the number of the confirmed disbursement voucher. 

    > [!NOTE]
    > <P>The entries in the <STRONG>Document name</STRONG>, <STRONG>Rate</STRONG>, and <STRONG>Currency</STRONG> fields are automatically displayed from the expense rate Help book.</P>

9.  In the **Quantity of days** field, enter the number of days of the business trip.
10. In the **To weekday** field, enter the daily expense amount.

    > [!NOTE]
    > <P>The <STRONG>Total amount</STRONG> field displays the total expense amount. The <STRONG>Rate</STRONG> and <STRONG>Over rate</STRONG> fields display information about the expense type.</P>

11. Click **Save** to transfer the entries from the **Create lines** form to the **Advance report** form.  

    > [!NOTE]
    > <P>The entry in the <STRONG>Ledger account</STRONG> field is displayed according to the expense rate posting setup. If the actual expense is more than the established rates, then a supplementary line for the excess amount is created when the expenses are transferred to the advance report. In this situation, the <STRONG>Over rate</STRONG> check box is selected automatically. The <STRONG>Line type</STRONG> field of the advance report that is generated by using the <STRONG>Copy from expends</STRONG> function displays the value <STRONG>Expense</STRONG>.</P>

12. Click **Post** to post the report.
13. Press CTRL+S or close the form.

## Generate and post a facture for an advance report

The Generate facture by expense account function can be used to reflect VAT in the purchase ledger for the personal expenses of advance holders, such as the standard part of per diem expenses.

1.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance reports**. Click **Update facture** tab to open the **Update facture** form.
2.  Click the **Advance report** tab to view the details of the advance report.
3.  Select the **To facture** check box to include advance reports in the facture.
4.  Click the **Advance report lines** tab.
5.  Clear the **To facture** check box to exclude advance report lines that are not included in the facture.
6.  Click the **Records affected** tab to display the included lines of the **Advance report**.
7.  In the upper pane, click the **Overview** tab.
8.  In the **Date of the registration** field, enter the registration date of the facture.
9.  In the **Facture date** field, enter the facture date.
    
    > [!NOTE]
    > <P>You must clear the <STRONG>Same as</STRONG> check box to enter the <STRONG>Facture date</STRONG> field.</P>

10. Click **Posting**,and then click**Update and print** to post the document.
11. Press CTRL+S or close the **Update facture** form.
12. Click **Inquiries**, and then click **Advance report facture** to view the generated factures.
13. Press CTRL+S or close the **Advance reports** form.

## Void an expense report

You can void expense reports that have been posted, and for which the status of the advance report is **Posted**. These reports should not have been settled. Factures are not created for these reports.

1.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance reports**.
2.  Select the advance report to void.
3.  Click **Rejection**. The status of the advance report is set to **Rejected**.

    > [!NOTE]
    > <P>When an advance report is rejected, reversed transactions are created for the advance holder. The <STRONG>Reversed</STRONG> check box is automatically selected in the <STRONG>Advance holder transactions</STRONG> form. The transactions are settled and reversed automatically.</P>

4.  Close the form.
5.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance holders**. Click **Transactions** to open the **Advance holder transactions** form.
6.  Click **Voucher**, and verify that the **Correction** check box is selected
    
    You can verify the distribution of expenses for the reversed transaction. Reversed or storno accounting transactions are distributed like the original transactions. However, the distributions for reversed or storno accounting transactions have a negative sign.
    
## Budget control for advance reports

By using budget control, you can make sure that sufficient funds are available for planned or actual purchases. After you set up basic budgeting, you can set up budget control. You can use budget control to confirm whether budget funds are available on source documents, such as purchase orders, expense reports, advance reports, and accounting journals. If the budget funds exceed the budget limit that is set, additional processing of the document can be prevented.

An advance report is primarily used to report travel expenses that are incurred by an employee during a business trip. If the expenses that are incurred on an advance report exceed the budget that is set, budget control indicates that the funds are not available.

To enable budget control for advance reports, follow these steps.

  - In the **Budget control configuration** form, in the **Select source documents** area, select advance reports as a source document for budget control, and enable budget checks for advance report lines.

  - In the **Budget control configuration** form, in the **Budget funds available** area, define the calculation that determines whether budget funds for advance reports are available.

### Budget calculation

When you define the budget calculation for advance reports, you should take actual expenditures and unposted actual expenditures into account.

**Example**

Budget funds available = (**Original budget** + **Budget revisions** + **Budget transfers**) – (**Actual expenditures** + **Unposted actual expenditures**)

You can view the actual expenditures and unposted actual expenditures for each advance report line in the **Actual expenditures** form.

### Budget checking

Budget checking for advance reports makes sure that budget funds are available for planned or future expenditures. The budget checking process runs automatically when an advance report line is saved, or when the report is posted.
