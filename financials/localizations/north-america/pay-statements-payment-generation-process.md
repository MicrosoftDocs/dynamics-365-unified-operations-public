---
# required metadata

title: Pay statements and generating payments FAQ
description: This topic answers questions that are related to activities that go beyond standard payroll processing. Examples include payments that are made to workers outside Payroll and final payments to terminated workers. 
author: rschloma
manager: AnnBe
ms.date: 2016-10-31 15 - 38 - 30
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
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 221054
ms.assetid: 0fd018c4-a786-4d36-97eb-7087521bb9f2
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.dyn365.ops.intro: 01-11-2016
ms.dyn365.ops.version: Version 1611

---

# Pay statements and generating payments FAQ

This topic answers questions that are related to activities that go beyond standard payroll processing. Examples include payments that are made to workers outside Payroll and final payments to terminated workers. 

This topic describes functionality that is available only if the **Payroll - USA** configuration key is selected.

## How do I record payments that were made outside Payroll?
In some cases, a worker payment is made and taxes are withheld outside the Payroll system. For example, when stock shares for an employee are vested, and a specific number of shares is withheld to cover the taxes, the vesting is a worker payment. Although the event occurs outside Payroll, you must record the event and all transactions that are associated with it in Payroll, so that statutory reporting and pay statement reporting are accurate. To record payments that were made outside Payroll, follow these steps.

1.  Enter the earnings for payments that were made outside Payroll. For instructions, see the "Manually enter worker earnings" section of the [Generate earnings](generate-earnings.md) topic. On the **Line details** FastTab, select the **Manual** check box. **Note:** The earning code for these earnings can’t be set up for a fringe benefit or a gross-up payment run type. The rate basis must be a flat amount.
2.  Release earnings. For instructions, see the "Release earnings for payment processing" section of the [Work with existing earnings](existing-earnings.md) topic.
3.  Generate the pay statement. For instructions, see the "Generate pay statements" section of the Work with existing earnings topic. The payment run type must be **Manual**. If you don’t want to record accounting-related information or post the pay statement to the general ledger, select **Disable accounting**.
4.  Add tax lines and benefit lines to the statement. For instructions, see the "Modify pay statements" section of the Work with existing earnings topic. You can add, remove, or change all tax lines and benefit lines on the pay statement, even lines that are usually locked. These lines include Federal Insurance Contributions Act (FICA) lines. When the pay statement is correct, click **Finalize** in the message bar.

## How do I issue the final payment to a terminated worker?
If you must issue a payment to a single worker, you don't use the periodic processes. Instead, generate the earnings statement and the pay statement from the **Payroll** tab on the Action Pane of the **Worker** page. Consider the following information when you issue the final payment to a terminated worker:

-   Verify that you entered earning codes to allow for payment of accrued benefits, as appropriate. Additionally, verify that any premiums, arrearages, tax levies, or garnishments have been handled according your organization’s policies, and according to any applicable laws or regulations.
-   If a worker is paid a salary, when you try to adjust the earnings statement lines on the final earnings statement, the values are automatically adjusted so that the worker still receives the expected amount for the pay period. To override this behavior, turn off the **Calculate Salary** functionality on the **Earnings statement** page.

## Why do the benefit lines and amounts on a pay statement differ from what I expect?
If arrearages were created when the pay statement was generated, the arrearage amounts appear in the **Generated Arrears** FactBox. The arrearages might cause the pay statement benefit lines to differ from the lines and amounts that you expect. If a benefit line seems to be missing, it might have been removed when the benefit was calculated, because the pay wasn’t enough to cover the amount. Likewise, if a benefit line or amount unexpectedly appears on the pay statement, it might have been added to recover arrears from previous pay statements. The pay statement itself doesn't indicate that an arrearage amount has been recovered. To determine whether arrears were recovered on the pay statement, you must use the **Worker arrears** page.

## Can I change the distributions for a pay statement line?
No. However, you can change distributions for earnings from the earnings statement line. For more information, see [Earnings and the earnings generation process FAQ](earnings-generation-process.md).

## Can I create a pay statement that has zero earnings?
Yes. For example, if you must create a pay statement just so that you can correct benefit and tax contributions or deductions, you can manually create the pay statement.

### Manually create a pay statement that has zero earnings

1.  On the **All pay statements** page, click **New**.
2.  Select the pay cycle, pay period, and payment date for the pay statement.
3.  Select the worker to update benefit and tax deductions or contributions for, and then click **OK**.
4.  Click the **Benefit deductions** tab to add benefit deduction lines, or click the **Benefit contributions** tab to add benefit contribution lines.
5.  Click the **Tax deductions** tab to add tax deduction lines, or click the **Tax** **contributions** tab to add tax contribution lines. Then click **Calculate**. **Important:** You must calculate the pay statement before you can submit it for payment or post it to the general ledger.


