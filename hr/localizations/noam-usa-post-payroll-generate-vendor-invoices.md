---
# required metadata

title: Post payroll and generate vendor invoices
description: This topic walks you through the process for posting payroll distributions and generating the required vendor invoices.
author: rschloma
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: PayrollPayStatement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 220964
ms.assetid: c16043b0-ccdc-4d4d-bf18-67d4c7e3e5f0
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Post payroll and generate vendor invoices

This topic walks you through the process for posting payroll distributions and generating the required vendor invoices.

When you post payroll, the accounting distributions that are specified on each pay statement line determine the offset accounts that are used. When each line has a balanced transaction, all transactions for the pay statement can be entered in the general ledger. 

**Note:** Offset accounts are determined by the posting definitions that are assigned to pay statements on the **Transaction posting definitions** page. When you post a pay statement, all lines must be successfully posted. Otherwise, no lines are posted. Similarly, when you post multiple pay statements, if one statement can't be posted, no pay statements are posted. 

After you post payroll, you should generate vendor invoices for the payables that were generated from the pay period that you posted. This process combines the amounts from all the pay statements that were posted for the period, and uses the benefit and tax setup information to create an invoice for each vendor. The totals and their corresponding accounting distributions from the original pay statement lines are used to create the invoices.

## Prerequisites
The following table shows the prerequisites that must be in place before you start.

<table>
<thead>
<tr class="header">
<th>Category</th>
<th>Prerequisite</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Country/region</td>
<td>(USA) The primary address for the legal entity must be in the United States.</td>
</tr>
<tr class="even">
<td>Related configuration tasks</td>
<td>You must complete the following tasks before you can post payroll and generate vendor invoices:
<ul>
<li>On the <strong>Payroll parameters</strong> page, set the <strong>Payroll clearing account</strong> field.</li>
<li>On the <strong>Payroll parameters</strong> page, set the <strong>Procurement category</strong> field.</li>
<li>On the <strong>Transaction posting definitions</strong> page, make sure that transaction posting definitions are created for payroll.</li>
</ul></td>
</tr>
</tbody>
</table>

## Post pay statements and generate vendor invoices for a single pay period
After you review pay statement for a specific pay period, you post the pay statements to the general ledger and generate vendor invoices for that pay period. 

**Tip:** The posting process ignores any pay statements that must be recalculated. Therefore, before you complete this process, we recommend that you view the **Pay statements to recalculate** list page to verify that no pay statements must be recalculated. For more information, see “Modify pay statements” in [Work with pay statements](noam-usa-pay-statements.md). To post pay statements and generate vendor invoices for a pay period, follow these steps. 

**Post the pay statements**

1.  Click **Payroll** &gt; **Pay statement processing** &gt; **Post pay statements**.
2.  In the **Pay cycle** field, select the pay cycle to post pay statements for.
3.  In the **Pay period** field, select the pay period to post pay statements for. The list includes only the pay periods that are available for the pay cycle. The default pay period is the first open pay period. However, you can select any open pay period in the list, and then click **OK**.

**Generate the vendor invoices**

1.  Click **Payroll** &gt; **Pay statement processing** &gt; **Generate vendor invoices**.
2.  In the **Pay cycle** field, select the pay cycle to generate vendor invoices for.
3.  In the **Pay period** field, select the same pay period that you posted the pay statements for.
4.  Select **All invoices**, and then click **OK**. You can’t delete or recalculate the invoices.

**Verify the results of the posting the pay statements and generating vendor invoices**

1.  Click **Payroll** &gt; **Pay statements** &gt; **All pay statements**.
2.  Click the pay statement to show the **Pay statement** details, and then verify this information:
    -   If the pay statement was posted successfully, **Posted** appears in the pay statement header.
    -   If the vendor invoice was generated successfully, the **Included in invoice** check box is selected on some pay statement lines.

## Post a pay statement for an individual worker and submit it for payment
To post a pay statement for a specific worker to the general ledger, and then submit the pay statement for payment, follow these steps.

1.  On the **All pay statements** page, select the pay statement for the specific worker and pay period.
2.  On the **Financials** tab, in the **Accounting** group, click **Post**.
3.  Select the **Submit for payment after posting** check box. For more information about this check box, see [Issue worker payments](noam-usa-issue-worker-payments.md).
4.  On the **Post the selected pay statement** page, click **Post**. You receive a message that states that the pay statement was posted successfully. You can’t delete or recalculate the invoice. **Tip:** To verify that the pay statement was posted, click the pay statement to show the **Pay statement** details. If the pay statement was posted successfully, **Posted** appears in the pay statement header.

## Generate vendor invoices for a specific benefit plan
After pay statements for a specific cycle and pay period have been posted to the general ledger, follow these steps to generate vendor invoices for a specific benefit plan for the pay period.

1.  On the **Generate vendor invoices** page, in the **Pay cycle** field, select the pay cycle to generate vendor invoices for.
2.  In the **Pay period** field, select the pay period to post pay statements for. The list includes only the pay periods that are available for the pay cycle. The default pay period is the first open pay period. However, you can select any open pay period in the list.
3.  Select **Benefit plan invoice**, select the benefit plan to generate invoices for, and then click **OK**.
4.  To verify that at least one vendor invoice was generated, click the pay statement to show the **Pay statement** details. Verify that the **Included in invoice** check box is selected on the line for the benefit plan statement. You can also verify that a new vendor invoice was created and posted for the vendor.

## Generate multiple invoices for the same vendor
After pay statements for a specific pay cycle and pay period have been posted to the general ledger, you generate all the vendor invoices for a specific vendor. These invoices include multiple invoices for several benefit plans. 

To generate multiple invoices for one vendor, follow these steps.

1.  On the **Generate vendor invoices** page, in the **Pay cycle** field, select the pay cycle to generate vendor invoices for.
2.  In the **Pay period** field, select the pay period to post pay statements for. The list includes only the pay periods that are available for the pay cycle. The default pay period is the first open pay period. However, you can select any open pay period in the list.
3.  Select **Vendor invoice**, select the vendor to generate invoices for, and then click **OK**.
4.  To verify that the vendor invoice was generated, click the pay statement to show the **Pay statement** details. Verify that the **Included in invoice** check box is selected on the pay statement lines for the benefits that are associated with the vendor. You can also verify that at least one vendor invoice was created for the vendor.


