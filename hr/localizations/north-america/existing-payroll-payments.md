---
# required metadata

title: Work with existing payroll payments
description: This topic describes tasks such as reprinting pay statements, and replacing paychecks that have been lost or damaged. It also explains how to complete similar tasks after pay statements have been generated or payments have been issued to workers.
author: rschloma
manager: AnnBe
ms.date: 2016-10-31 15 - 31 - 05
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTransPayrollDisbursement, PayrollPayStatement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 220934
ms.assetid: b95ac219-fbea-48e6-b2c8-6f27853a7f6a
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Work with existing payroll payments

This topic describes tasks such as reprinting pay statements, and replacing paychecks that have been lost or damaged. It also explains how to complete similar tasks after pay statements have been generated or payments have been issued to workers.

Print or reprint pay statements for previously processed payments
-----------------------------------------------------------------

To print or reprint pay statements for payments that were previously processed, follow these steps.

1.  Open the **Pay statements report** page. You can also print pay statements from the **All Pay statements** page.
2.  In the **Pay cycle** field, select the pay cycle for the pay statements to print.
3.  In the **Pay period** field, select the pay period for the pay statements, and then click **OK**. The list includes only the pay periods that are available for the pay cycle.

## Reprint a check for a worker before the payment journal is posted
If a check was damaged when it was printed, you can follow these steps to reprint the check for a worker, provided that the payment journal hasn’t been posted. If you have permissions to change values on the **Cash and bank management parameters** page, and you want to use the same check number, on the **Cash and bank management parameters** page, in the **Check setup** section, select the **Allow check reuse** check box. If you don’t have permission to change values on the **Cash and bank management parameters** page, follow these steps.

1.  On the **Payment journal** page, select the payment journal, and then click **Lines**.
2.  On the **Journal voucher** page, select the check payment to reprint.
3.  Follow one of these steps:
    -   If you can change the parameter to reuse checks, click **Payment status**, and then select **Reuse** to remove the check number from the bank journal.
    -   If you can't change the parameter to reuse checks, click **Payment status**, and then select **Reuse** to remove the check number from the bank journal.

4.  Select **Functions**, and then select **Generate payments** to generate payments that have a status of **None**, and that match the method of payment and bank account that you selected.
5.  On the **Generate payments** page, select the bank account and the check method of payment, and then click **OK**.
6.  On the **Payroll check payment** page, verify the check number in the **From** field, verify the print destination, and then click **OK** to print the check.
7.  Verify that the check was printed correctly, and that the payment status is set to **Sent** on the **Journal voucher** page.

## Reissue a check to a worker after the payment journal is posted
Use this procedure when check payments were generated, and the payment journal was posted, but you want to reprint a check for a worker. For example, you might have to reprint a check that was lost. To issue another check for a worker, follow these steps.

1.  On the **Cash and bank management parameters** page, select the check, and then click **Payment reversal**. You can reverse only checks that have a payment status of **Paid**.
2.  On the **Payment reversal** page, complete the information, and then click **OK**.
3.  On the **Check reversals** page, select the journal that contains the reversal.
4.  On the **Post** menu, click **Post** to unsettle the original payment journal record from the invoice and create an offset transaction that will be settled to the original payment. The invoice will have an outstanding amount that hasn’t been settled. **Note:** This process occurs automatically if the **Use review process for payment reversals** check box is cleared on the **Cash and bank management parameters** page.
5.  On the **Issued pay statements** page, select the pay statement, and then click **Submit to reissue**. A new payment journal is created that has the new line. An invoice isn’t created.
6.  On the **Payment journal** page, select the payment journal that was just created, and then select **Lines**.
7.  On the **Journal voucher** page, select **Functions**, and then select **Generate payments** to generate payments that have a **None** status, and that match the method of payment and bank account that you selected.
8.  On the **Generate payments** page, select the bank account and the check method of payment, and then click **OK**.
9.  On the **Payroll check payment** page, verify the check number in the **From** field, verify the print destination, and then click **OK** to print the check.
10. On the **Journal voucher** page, verify that the payment status is set to **Sent**.

## Void a check payment and reverse a pay statement
Sometimes, you must void a check. For example, if the payment journal was already posted, you might have to void a check that was printed for a worker who should not have been paid. If the check or Automated Clearing House (ACH) file that contains the payment hasn’t been created, but the pay statement has been submitted or posted, you don’t have to void the payment. However, you do have to reverse the pay statement. On the **All pay statements**, follow the steps for reversing a payment. If the pay statement hasn’t been submitted or posted, you don't reverse the pay statement. Instead, delete it. For more information, see [Work with pay statements](pay-statements.md). To void a check and reverse the payment, follow these steps.

1.  On the **Checks** page, select the check, and then click **Payment reversal**. You can reverse only checks that have a payment status of **Paid**.
2.  On the **Payment reversal** page, complete the information, and then click **OK**.
3.  On the **Check reversals** page, select the journal that contains the reversal.
4.  On the **Post** menu, select **Post** to unsettle the original payment journal record from the invoice and create an offset transaction that will be settled to the original payment. The invoice will have an outstanding amount that hasn’t been settled. **Note:** This process occurs automatically if the **Use review process for payment reversals** check box is cleared on the **Cash and bank management parameters** page.
5.  On the **Issued pay statements** page, select the pay statement, and then click **Reverse**. **Important:** Arrearage amounts aren’t reversed when you reverse a pay statement. If arrearages were created or recovered on the pay statement that you reverse, you must manually adjust the worker’s arrearage balance on the **Worker arrears** page. If an arrearage was created, the amount of the arrearage appears in the **Arrears** FactBox. To determine whether an arrearage was recovered, use the **Worker arrears** page.
6.  When you're prompted to continue, click **Yes**. A new pay statement is created that has amounts that are the opposite of the amounts on the original pay statement. You also receive a message that shows the ID of the reversing pay statement. A message bar appears on the original pay statement to notify you that the pay statement was reversed. A message bar also appears on the new pay statement to notify you that this pay statement was created to reverse a pay statement. Additionally, the new pay statement shows the original pay statement ID and provides an option to open the reversed pay statement.
7.  If the original pay statement was submitted, on the **All pay statements** page, select the new reversed pay statement that was created, and then click **Submit for payment**. **Note:** If the original pay statement was posted but wasn't submitted, skip to step 10.
8.  Optional: Select the **Post the selected pay statement** check box. Skip this step if the original pay statement wasn’t posted.
9.  Click **Submit**. A new invoice is created that has opposite values. This invoice is then posted and settled with the original invoice. A payment journal isn’t created.
10. If the original pay statement was posted but wasn't submitted, select the new reversed pay statement that was created. Then, on the Action Pane, on the **Financials** tab, click **Post**.
11. Leave the **Submit for payment after posting** check box cleared, and click **Post**.

## Recreate an ACH file
To re-create an ACH file for a group of electronic payments when the payment journal hasn’t been posted, follow these steps.

1.  On the **Payment journal** page, select the payment journal that contains the lines to re-create the file for, and then click **Lines**.
2.  On the **Journal voucher** page, select the lines to re-create the file for.
3.  Select **Payment status**, and then click **None**.
4.  Select **Functions**, and then select **Generate payments** to generate payments that have a **None** status, and that match the method of payment and bank account that you selected.
5.  On the **Generate payments** page, select the bank account and the check method of payment, and then click **OK**.
6.  On the **Payroll electronic (Direct deposit)** page, enter the path (be sure to include the file name), enter an effective date, and optionally select the **Pay statement** check box to print the pay statements. Click **OK** to create the ACH file. A message shows the number of transactions and prenotes that were created.
7.  On the **Journal voucher** page, verify that the payment status is set to **Sent**.


