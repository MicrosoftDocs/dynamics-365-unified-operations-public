---
title: Issue worker payments
description: Learn about how to submit pay statements, generate checks or electronic payments, generate a positive pay file for payroll, and post the payment journal.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 06/25/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: USA
ms.search.validFrom: 2016-11-30
ms.search.form: PayrollPayStatement
ms.dyn365.ops.version: Version 1611
ms.assetid: 64c9c810-23ff-4af6-a282-a4db4c60c0d5
---

# Issue worker payments

[!include [banner](../../../../../finance/includes/banner.md)]

This article explains how to submit pay statements, generate checks or electronic payments, generate a positive pay file for payroll, and post the payment journal.

You can pay workers by check or by electronic payment. When you submit pay statements, you create and post an invoice to the general ledger for the sum of the worker's net pay for the payroll vendor that you set up on the **Payroll parameters** page. You create a payment journal with lines so that you can generate and post payments. When you submit payments, you can optionally post the payroll costs that are associated with workers to the general journal.

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

| Category | Prerequisite |
|---|---|
| Country/region | (USA) The primary address for the legal entity must be in the United States. |
| Related configuration tasks | You must complete these tasks before you can post payroll and generate vendor invoices:<ul><li>Set the **Payroll clearing account** field on the **Calculation settings** tab on the **Payroll parameters** page.</li><li>Set the **Check method of payment**, **Vendor account for worker payments**, **Payment journal name**, and **Procurement category** fields on the **Payment issuance** tab on the **Payroll parameters** page.</li><li>Before you can generate a positive pay file for payroll, you must set up positive pay.</li><li>If you generate electronic payments, make sure that the **Electronic method of payment** field is set on the on the **Payment issuance** tab on the **Payroll parameters** page. Additionally, make sure that you've entered the bank account disbursements for each worker.</li></ul> |

For more information, see [Set up and generate positive pay files](../../../../../finance/accounts-payable/set-up-generate-positive-pay-files.md).

## Submit pay statements for multiple workers in a pay period

Use this procedure to create a payment journal for multiple pay statements at the same time. Before you generate pay statements, you must generate and release earnings. For more information, see [Generate earnings for workers](noam-usa-generate-earnings.md).

To submit pay statements for multiple workers at the same time, follow these steps:

1. Generate pay statements, so that earnings, benefits, and taxes are calculated. For more information, see [Generate and work with pay statements](noam-usa-pay-statements.md).

    > [!TIP]
    > Before you generate pay statements, view the **Pay statements to recalculate** list page to verify that no pay statements must be recalculated. For more information, see "Modify pay statements" in [Generate and work with pay statements](noam-usa-pay-statements.md).

1. On the **Submit pay statements** page, in the **Pay cycle** field, select the same pay cycle that you selected when you generated and released earnings.
1. In the **Pay period** field, select the same pay period that you selected when you generated and released earnings. The list includes only the pay periods that are available for the pay cycle. The default pay period is the first open pay period, but you can select any open pay period in the list.
1. Select **OK** to submit the pay statements. A vendor invoice for the sum of the net pay for all pay statements is created and posted. A payment journal that has lines is also created and posted, so that you can generate and post payments.
1. When you receive a message that states that the payment journal was successfully generated, and that a voucher and invoice details were created, close the message. The **Submitted pay statements** page shows a list of submitted statements. An icon in the first column of the **Pay statement** grid indicates that the payment was submitted.
1. View the payment journal, and then generate checks and electronic payments by using the **Payment journal** page.

## Submit individual pay statements

To create a payment journal for an individual pay statement, follow these steps:

1. Generate pay statements, so that earnings, benefits, and taxes are calculated. For more information, see [Generate and work with pay statements](noam-usa-pay-statements.md).
1. On the **Calculated pay statements** page, select the worker pay statement to create the payment journal for, and then select **Submit for payment**. The **Submit for payment** button is also available on the **Pay statement** page.
1. (Optional) Select the **Post the selected pay statement** check box to post the pay statement. You can post the pay statements as a separate step at any time by using the **Post pay statements** page.
1. Select **Submit** to submit the pay statements. A vendor invoice for the net pay of the pay statement is created and posted. A payment journal that has lines is also created, so that you can generate and post the payment.
1. When you receive a message that states that the payment journal was successfully generated, and that a voucher and invoice details were created, close the message. On the **Submitted pay statements** page, an icon in the first column of the **Pay statement** grid indicates that the payment was submitted.
1. View the payment journal, and then generate checks and electronic payments by using the **Payment journal** page.

Continue with the next section, "Generate checks or electronic payments for a payment journal."

## Generate checks or electronic payments for a payment journal

To generate checks and electronic payments for workers, follow these steps after you submit the pay statements and generate the payment journal.

> [!IMPORTANT]
> If you don't finish the bank account disbursements before the pay statements are generated, the workers are paid by check.

1. On the **Payment journal** page, select the payment journal. On the Action Pane, select **Lines** to open the **Journal voucher** page.
1. Verify that the number of vouchers is correct. There's one journal voucher line for each check pay statement, and one or more journal voucher lines for each electronic pay statement.
1. On the **Functions** menu, select **Generate payments**.

    > [!NOTE]
    > You must generate electronic payments and check payments separately. Therefore, if you're generating both electronic payments and check payments, you must complete this step two times.

1. On the **Generate payments** page, select the method of payment and the bank account.
1. Select **OK** to generate the payment for the records that match the method of payment and the bank account.

    - If you selected the check method of payment, the **Payroll check payment** page opens. In the **From** field, verify the starting check number, verify the printing destination, and then select **OK** to print the checks.
    - If you selected the electronic method of payment, the **Payroll electronic (Direct deposit)** page opens. Enter the path where the ACH file should be created. The path that you enter must include the file name. Enter an effective date and the printing destination, and optionally select the **Pay statement** check box to print the pay statements. Select **OK** to create the ACH file.

    > [!TIP]
    > You can print pay statements later, from the **Reports** menu.

    The payment status is set to **Sent** for every payment that you generated.

## Generate a positive pay file for payroll

You can generate an electronic list of payroll checks that you provide to the bank. When you present a payroll check to the bank, the bank compares it to the list. If the check matches a check in the list, the bank clears the check. Otherwise, the bank holds the check for review.

To generate a positive pay file for payroll, follow these steps:

1. On **Payroll positive pay**, in the **Cut-off date** field, enter the last check date to include in the positive pay file. The file includes all checks that aren't included in a positive pay file through this check date.
1. Select **OK**.

## Confirm a positive pay file for payroll

After you pay the checks that are listed in a payroll positive pay file, you receive a confirmation number from the bank. You can then confirm the positive pay file in your organization's data. When you confirm a positive pay file, you record the confirmation number that you received from the bank.

To confirm a positive pay file, follow these steps:

1. On the **Payroll positive pay file summary** page, select a payroll positive pay file that has a status of **Created**.
1. Select **Confirmation**.
1. Enter the confirmation number that you received from the bank, and then select **OK**.

## If necessary: Recall a positive pay file

If you must change a payroll positive pay file, you can recall it. When you recall a positive pay file, the field that indicates whether each check is included in a positive pay file is reset. You can then create a new positive pay file.

To recall a positive pay file, follow these steps:

1. On the **Payroll positive pay file summary** page, select a payroll positive pay file that has a status of **Created**.
1. Select **Recall**. You receive a message that states that the recall process was successful.

## Post a payment journal

You can post a payment journal after you generate checks and electronic payments as described earlier in this article.

To post a payment journal, follow these steps:

1. On the **Payment journal** page, select the payment journal. On the Action Pane, select **Lines** to open the **Journal voucher** page.
1. On the **Post** menu, select **Post**. The payment journal lines settle to the vendor invoice that you created and posted. You receive a message that indicates the number of vouchers that were posted.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
