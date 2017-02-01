---
# required metadata

title: Work with pay statements | Microsoft Docs
description: This topic describes the process for generating pay statements. It also describes other tasks, such as reversing a pay statement, that you might have to complete after you generate pay statements.
author: rschloma
manager: AnnBe
ms.date: 2016-11-01 16:40:11
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
ms.custom: 233834
ms.assetid: 091b6418-3b8c-45bf-b642-13c0ab9d6c9c
ms.region: USA
# ms.industry: 
ms.author: brpotter

---

# Work with pay statements

This topic describes the process for generating pay statements. It also describes other tasks, such as reversing a pay statement, that you might have to complete after you generate pay statements.

When you generate pay statements, all worker deductions and employer contributions for benefits and taxes are calculated, benefit accruals are processed, and the worker’s net pay is determined. We recommend that you use batch processing mode when you generate pay statements, to improve performance. Completed pay statements are used to issue worker payments. For more information, see [Issue worker payments](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/issue-worker-payments).

## Where pay statements fit in the payroll process
The following illustration shows where the generation of pay statements fits into the larger picture of payroll processing. Other tasks that this topic describes aren't part of the end-to-end payroll process.   ![Basic steps for processing earnings](https://i-technet.sec.s-msft.com/dynimg/IC766964.gif "Basic steps for processing earnings")

## Prerequisites
Before you begin, make sure that the following parameters are set up on the **Payroll parameters** page.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Location on the Payroll parameters page</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Accounting date options Payroll clearing account</td>
<td><strong>Calculations</strong> tab</td>
</tr>
<tr class="even">
<td>Recovery of arrears in all payment run types</td>
<td><strong>Arrear threshold</strong> field</td>
</tr>
<tr class="odd">
<td>Methods of payment for check and electronic pay runs</td>
<td><strong>Payment issuance</strong> area</td>
</tr>
<tr class="even">
<td>Number sequence codes for the following items:
<ul>
<li>Earnings statements</li>
<li>Pay statements</li>
<li>Pay statement vouchers</li>
<li>Vendor invoice number</li>
<li>Batch number</li>
</ul></td>
<td><strong>Number sequences</strong> area</td>
</tr>
</tbody>
</table>

## Generate pay statements
Pay statements are generated for the pay cycle, pay period, and payment run type that you specify. When you generate pay statements, all released earnings that match the specified criteria are automatically collected. Before you generate a pay statement, you must generate and release the earnings for the pay cycle and pay period. For more information, see [Generate earnings](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/generate-earnings) and [Work with existing earnings](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/work-with-existing-earnings). **Note:** If a worker payment occurs outside Microsoft Dynamics 365 for Operations, see “Record payments made outside Payroll” in [Pay statements and the payment generation process FAQ](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/pay-statements-and-the-payment-generation-process). To generate pay statements, follow these steps.

1.  On the **Generate pay statements** page, enter information in the following fields. You can also generate a single pay statement from the **Payroll** tab on the **Worker** or **Position** page.
    | Field            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    |------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Pay cycle        | Select the pay cycle that includes the earnings to generate the pay statement for.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | Pay period       | Select the pay period that includes the earnings. The list includes only the pay periods that are available for the selected pay cycle. The default pay period is the first open pay period. However, you can select any open pay period in the list.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | Payment run type | Select the payment run type. The default payment run type, **Primary**, is used for regular pay runs. The **Manual** payment run type is used to enter payments, such as vested stock options, that are made outside payroll. If you select **Manual** in this field, the **Disable accounting** check box appears. When that check box is selected, accounting information isn’t recorded or posted to the general ledger. **Note:** If the earning code for a released earning isn’t set up for the selected payment run type, the earning isn’t included on the pay statement. Additionally, if the basis for the accrual rate for a benefit accrual plan is a fixed amount, earning lines that are related to the plan are processed only in primary pay runs. |

2.  When you've finished entering information, click **OK** to generate pay statements.
3.  When you're notified that the pay statements have been generated successfully, close the page.
4.  To verify that the batch job was completed successfully, on the **My batch jobs** page, click **Log**, and inspect the log for errors.

To post pay statements to the general ledger, see [Post payroll and generate vendor invoices](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/post-payroll-and-generate-vendor-invoices). To submit pay statements for payment, see [Issue worker payments](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/issue-worker-payments).

## Delete pay statements
You can delete pay statements only if they haven’t been posted or submitted to Accounts payable for payment, and if the payment hasn’t been issued. If pay statements have been posted, submitted, or paid, you can't delete them. Instead, you must reverse them. For more information, see [Work with existing payroll payments](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/work-with-existing-payroll-payments). When you delete a pay statement, the following events occur:

-   The earnings statement lines aren’t deleted, and you can include them when you generate a new pay statement.
-   Any arrearages that the pay statement created are deleted. If an amount that is in arrears is partially or fully recovered by a later pay statement, you must delete the pay statement that recovered the amount before you can delete the pay statement that created the arrearage.

To delete a pay statement, on the **All pay statements** page, select the pay statement to delete, and then click **Delete**.

## Modify earning lines on pay statements
You maintain earning lines on the **Earnings statement** page. You can remove earning lines from a pay statement, but you can’t add or change earning lines. To add or change earning lines, you must first delete the pay statement as described in the previous section.

### Add earning lines to a pay statement

1.  On the **All pay statements** page, select the pay statement to add earning lines to, and then click **Delete**.
2.  On the **All Earnings statements** page, open the earnings statement that contains the pay statement that you must add earning lines to.
3.  Review the lines that weren’t included on the deleted pay statement, and make any changes or corrections that are required. In most cases, missing lines were unintentionally deleted from the pay statement, or they haven’t been released. The lines might be in a different pay cycle or pay period, or the earning code for the earning line might not be set up for the selected payment run type.
4.  Generate a new pay statement.

### Remove earning lines from a pay statement

1.  On the **All pay statements** page, open the pay statement to remove earning lines from, and then click **Edit**.
2.  Select the earning lines to remove, and then click **Remove**. The earning lines that you remove aren’t deleted from Payroll, and you can include them on a future pay statement.
3.  In the message bar, click **Recalculate**. **Important:** You must recalculate the pay statement before you submit it for payment or post it to the general ledger.
4.  Close the page.

### Modify earning lines on a pay statement

1.  On the **All pay statements** page, select the pay statement to work with, and then click **Delete**.
2.  On the **All Earnings statements** page, put the earnings for the deleted pay statement on hold, change the earning lines as you require, and then release the earnings. For instructions, see [Work with existing earnings](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/work-with-existing-earnings).
3.  Generate a new pay statement.

## Modify benefit lines and tax lines on pay statements
You can add or remove benefit lines. You can also change benefit lines that a user added. If benefit lines were created automatically, you can change them if the benefit plan isn’t locked for pay statements. You can add, remove, and change tax lines, except tax lines for Medicare and Federal Insurance Contributions Act (FICA) tax.

1.  On the **All pay statements** page, open the pay statement to modify, and then click **Edit**.
2.  Click the **Benefit calculations** link, and change the benefit lines as you require. You can't change benefit lines that are marked by a red circle that has a line through it. Benefit lines that a user has already changed are marked by a pencil icon. **Caution:** If arrearages were created when the pay statement was generated, the arrearage amounts appear in the **Arrears** FactBox. The arrearages might cause the pay statement benefit lines to differ from the lines and amounts that you expect. For more information, see [Pay statements and the payment generation process Q&A](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/pay-statements-and-the-payment-generation-process).
3.  Click the **Tax calculations** link, and change the tax lines as you require. You can't change tax lines that are marked by a red circle that has a line through it. Tax lines that a user has already changed are marked by a pencil icon.
4.  In the message bar, click **Recalculate**. **Important:** You must recalculate the pay statement before you submit it for payment or post it to the general ledger.

## Modify benefit accrual lines on pay statements
Benefit accrual lines are created when you submit a pay statement for payment. You can’t add, remove, or change benefit accrual lines. If the benefit accrual lines on a pay statement create incorrect balances in a benefit accrual plan, you must change the plan balances. If you change the worker’s plan balances, the amounts on the pay statement aren’t updated. The change is reflected on the next pay statement that is processed. For more information, see [Benefit accrual plan tasks](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/benefit-accrual-plan-tasks).

## Reverse a pay statement
To reverse a pay statement that has been posted or submitted for payment, see [Work with existing payroll payments](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/north-america/work-with-existing-payroll-payments).

