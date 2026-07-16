---
title: Process existing payroll payments
description: Learn about tasks such as reprinting pay statements, and replacing paychecks that have been lost or damaged, including step-by-step processes.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 06/25/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: USA
ms.search.validFrom: 2016-11-30
ms.search.form: LedgerJournalTransPayrollDisbursement, PayrollPayStatement
ms.dyn365.ops.version: Version 1611
ms.assetid: b95ac219-fbea-48e6-b2c8-6f27853a7f6a
---

# Process existing payroll payments

[!include [banner](../../../../../finance/includes/banner.md)]

This article describes tasks such as reprinting pay statements, and replacing paychecks that have been lost or damaged. It also explains how to complete similar tasks after pay statements have been generated or payments have been issued to workers.

## Print or reprint pay statements for previously processed payments

To print or reprint pay statements for payments that you previously processed, follow these steps:

1. Open the **Pay statements report** page. You can also print pay statements from the **All Pay statements** page.
1. In the **Pay cycle** field, select the pay cycle for the pay statements to print.
1. In the **Pay period** field, select the pay period for the pay statements, and then select **OK**. The list includes only the pay periods that are available for the pay cycle.

## Reprint a check for a worker before posting the payment journal

If a check is damaged during printing, you can reprint the check for a worker by following these steps, as long as you didn't post the payment journal.

If you have permissions to change values on the **Cash and bank management parameters** page, and you want to use the same check number, on the **Cash and bank management parameters** page, in the **Check setup** section, select the **Allow check reuse** check box.

If you don't have permission to change values on the **Cash and bank management parameters** page, follow these steps:

1. On the **Payment journal** page, select the payment journal, and then select **Lines**.
1. On the **Journal voucher** page, select the check payment to reprint.
1. Follow one of these steps:

    - If you can change the parameter to reuse checks, select **Payment status**, and then select **Reuse** to remove the check number from the bank journal.
    - If you can't change the parameter to reuse checks, select **Payment status**, and then select **Reuse** to remove the check number from the bank journal.

1. Select **Functions**, and then select **Generate payments** to generate payments that have a status of **None**, and that match the method of payment and bank account that you selected.
1. On the **Generate payments** page, select the bank account and the check method of payment, and then select **OK**.
1. On the **Payroll check payment** page, verify the check number in the **From** field, verify the print destination, and then select **OK** to print the check.
1. Verify that the check was printed correctly, and that the payment status is set to **Sent** on the **Journal voucher** page.

## Reissue a check to a worker after posting the payment journal

Use this procedure when you generate check payments and post the payment journal, but you want to reprint a check for a worker. For example, you might need to reprint a check that was lost. To issue another check for a worker, follow these steps:

1. On **Cash and bank management parameters**, select the check, and then select **Payment reversal**. You can reverse only checks that have a payment status of **Paid**.
1. On **Payment reversal**, enter the required information, and then select **OK**.
1. On **Check reversals**, select the journal that contains the reversal.
1. On the **Post** menu, select **Post** to unsettle the original payment journal record from the invoice and create an offset transaction that settles to the original payment. The invoice has an outstanding amount that isn't settled.

    > [!NOTE]
        > This process occurs automatically if you clear the **Use review process for payment reversals** checkbox on **Cash and bank management parameters**.

1. On **Issued pay statements**, select the pay statement, and then select **Submit to reissue**. A new payment journal is created that has the new line. An invoice isn't created.
1. On **Payment journal**, select the payment journal that you created, and then select **Lines**.
1. On **Journal voucher**, select **Functions**, and then select **Generate payments** to generate payments that have a **None** status, and that match the method of payment and bank account that you selected.
1. On **Generate payments**, select the bank account and the check method of payment, and then select **OK**.
1. On **Payroll check payment**, verify the check number in the **From** field, verify the print destination, and then select **OK** to print the check.
1. On the **Journal voucher** page, verify that the payment status is set to **Sent**.

## Void a check payment and reverse a pay statement

Sometimes, you need to void a check. For example, if you already posted the payment journal, you might need to void a check that you printed for a worker who shouldn't be paid.

If you didn't create the check or Automated Clearing House (ACH) file that contains the payment, but you submitted or posted the pay statement, you don't need to void the payment. However, you do need to reverse the pay statement. On **All pay statements**, follow the steps for reversing a payment.

If the pay statement hasn't been submitted or posted, you don't reverse the pay statement. Instead, delete it. For more information, see [Generate and work with pay statements](noam-usa-pay-statements.md).

To void a check and reverse the payment, follow these steps:

1. On **Checks**, select the check, and then select **Payment reversal**. You can reverse only checks that have a payment status of **Paid**.
1. On **Payment reversal**, enter the required information, and then select **OK**.
1. On **Check reversals**, select the journal that contains the reversal.
1. On the **Post** menu, select **Post** to unsettle the original payment journal record from the invoice and create an offset transaction that settles to the original payment. The invoice has an outstanding amount that isn't settled.

    > [!NOTE]
        > This process occurs automatically if you clear the **Use review process for payment reversals** checkbox on **Cash and bank management parameters**.

1. On the **Issued pay statements** page, select the pay statement, and then select **Reverse**.

    > [!IMPORTANT]
    > Arrearage amounts aren't reversed when you reverse a pay statement. If arrearages were created or recovered on the pay statement that you reverse, you must manually adjust the worker's arrearage balance on the **Worker arrears** page. If an arrearage was created, the amount of the arrearage appears in the **Arrears** FactBox. To determine whether an arrearage was recovered, use the **Worker arrears** page.

1. When you're prompted to continue, select **Yes**. A new pay statement is created that has amounts that are the opposite of the amounts on the original pay statement. You also receive a message that shows the ID of the reversing pay statement. A message bar appears on the original pay statement to notify you that the pay statement was reversed. A message bar also appears on the new pay statement to notify you that this pay statement was created to reverse a pay statement. Additionally, the new pay statement shows the original pay statement ID and provides an option to open the reversed pay statement.
1. If the original pay statement was submitted, on the **All pay statements** page, select the new reversed pay statement that was created, and then select **Submit for payment**.

    > [!NOTE]
    > If the original pay statement was posted but wasn't submitted, skip to step 10.

1. (Optional) Select the **Post the selected pay statement** check box. Skip this step if the original pay statement wasn't posted.
1. Select **Submit**. A new invoice is created that has opposite values. This invoice is then posted and settled with the original invoice. A payment journal isn't created.
1. If the original pay statement was posted but wasn't submitted, select the new reversed pay statement that you created. Then, on the Action Pane, on the **Financials** tab, select **Post**.
1. Leave the **Submit for payment after posting** check box cleared, and select **Post**.

## Recreate an ACH file

To recreate an ACH file for a group of electronic payments when the payment journal isn't posted, follow these steps:

1. On the **Payment journal** page, select the payment journal that contains the lines to re-create the file for, and then select **Lines**.
1. On **Journal voucher**, select the lines to recreate the file for.
1. Select **Payment status**, and then select **None**.
1. Select **Functions**, and then select **Generate payments** to generate payments that have a **None** status, and that match the method of payment and bank account that you selected.
1. On the **Generate payments** page, select the bank account and the check method of payment, and then select **OK**.
1. On the **Payroll electronic (Direct deposit)** page, enter the path (be sure to include the file name), enter an effective date, and optionally select the **Pay statement** check box to print the pay statements. Select **OK** to create the ACH file. A message shows the number of transactions and prenotes that were created.
1. On the **Journal voucher** page, verify that the payment status is set to **Sent**.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
