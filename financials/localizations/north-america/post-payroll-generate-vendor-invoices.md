---
# required metadata

title: Post payroll and generate vendor invoices | Microsoft Docs
description: This topic walks you through the process for posting payroll distributions and generating the required vendor invoices.
author: rschloma
manager: AnnBe
ms.date: 2016-10-31 15:31:19
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: PayrollPayStatement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 220964
ms.assetid: d9cd7f62-d110-4d9b-b3d5-f78449e556d9
ms.region: USA
# ms.industry: 
ms.author: brpotter

---

# Post payroll and generate vendor invoices

This topic walks you through the process for posting payroll distributions and generating the required vendor invoices.

When you post payroll, the accounting distributions that are specified on each pay statement line determine the offset accounts that are used. When each line has a balanced transaction, all transactions for the pay statement can be entered in the general ledger. **Note:** Offset accounts are determined by the posting definitions that are assigned to pay statements on the **Transaction posting definitions** page. When you post a pay statement, all lines must be successfully posted. Otherwise, no lines are posted. Similarly, when you post multiple pay statements, if one statement can't be posted, no pay statements are posted. After you post payroll, you should generate vendor invoices for the payables that were generated from the pay period that you posted. This process combines the amounts from all the pay statements that were posted for the period, and uses the benefit and tax setup information to create an invoice for each vendor. The totals and their corresponding accounting distributions from the original pay statement lines are used to create the invoices.

## How posting payroll fits into the overall payroll process
The following illustration shows how this topic fits into the larger picture of payroll processing. ![Basic steps for processing earnings](https://i-technet.sec.s-msft.com/dynimg/IC766976.gif "Basic steps for processing earnings")

## Prerequisites
The following table shows the prerequisites that must be in place before you start.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
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
After you review pay statement for a specific pay period, you post the pay statements to the general ledger and generate vendor invoices for that pay period. **Tip:** The posting process ignores any pay statements that must be recalculated. Therefore, before you complete this process, we recommend that you view the **Pay statements to recalculate** list page to verify that no pay statements must be recalculated. For more information, see “Modify pay statements” in [Work with pay statements](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/work-with-pay-statements). To post pay statements and generate vendor invoices for a pay period, follow these steps. **Post the pay statements**

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
3.  Select the **Submit for payment after posting** check box. For more information about this check box, see [Issue worker payments](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/issue-worker-payments).
4.  On the **Post the selected pay statement** page, click **Post**. You receive a message that states that the pay statement was posted successfully. You can’t delete or recalculate the invoice. **Tip:** To verify that the pay statement was posted, click the pay statement to show the **Pay statement** details. If the pay statement was posted successfully, **Posted** appears in the pay statement header.

## Generate vendor invoices for a specific benefit plan
After pay statements for a specific cycle and pay period have been posted to the general ledger, follow these steps to generate vendor invoices for a specific benefit plan for the pay period.

1.  On the **Generate vendor invoices** page, in the **Pay cycle** field, select the pay cycle to generate vendor invoices for.
2.  In the **Pay period** field, select the pay period to post pay statements for. The list includes only the pay periods that are available for the pay cycle. The default pay period is the first open pay period. However, you can select any open pay period in the list.
3.  Select **Benefit plan invoice**, select the benefit plan to generate invoices for, and then click **OK**.
4.  To verify that at least one vendor invoice was generated, click the pay statement to show the **Pay statement** details. Verify that the **Included in invoice** check box is selected on the line for the benefit plan statement. You can also verify that a new vendor invoice was created and posted for the vendor.

## Generate multiple invoices for the same vendor
After pay statements for a specific pay cycle and pay period have been posted to the general ledger, you generate all the vendor invoices for a specific vendor. These invoices include multiple invoices for several benefit plans. To generate multiple invoices for one vendor, follow these steps.

1.  On the **Generate vendor invoices** page, in the **Pay cycle** field, select the pay cycle to generate vendor invoices for.
2.  In the **Pay period** field, select the pay period to post pay statements for. The list includes only the pay periods that are available for the pay cycle. The default pay period is the first open pay period. However, you can select any open pay period in the list.
3.  Select **Vendor invoice**, select the vendor to generate invoices for, and then click **OK**.
4.  To verify that the vendor invoice was generated, click the pay statement to show the **Pay statement** details. Verify that the **Included in invoice** check box is selected on the pay statement lines for the benefits that are associated with the vendor. You can also verify that at least one vendor invoice was created for the vendor.


