---
# required metadata

title: Process existing earnings
description: This topic describes tasks, such as releasing or holding earnings, that you can complete after you generate an earnings statement. You must release earnings statement lines before you generate pay statements.
author: rschloma
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: PayrollEarningStatement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 233764
ms.assetid: 233c40f6-3e9e-4ed4-b42c-4643a68946e1
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Process existing earnings

[!include[banner](../includes/banner.md)]


This topic describes tasks, such as releasing or holding earnings, that you can complete after you generate an earnings statement. You must release earnings statement lines before you generate pay statements.

This topic doesn't discuss retroactive earnings. For information about retroactive earnings, see [Generate earnings](noam-usa-generate-earnings.md).

## If required: Hold earnings from payment processing
You can put one or more earnings statement lines on hold so that you can change information or correct errors. However, you can't put a line on hold if it's already included on a pay statement. You can use this procedure even if some or all of the earnings statement lines have been released. 

To put earnings statement lines on hold, follow these steps.

1.  Click **Payroll** &gt; **Earnings statements** &gt; **All Earnings statements**.
2.  Follow one of these steps:
    -   To put all the lines for an earnings statement on hold, select one or more earnings statements, and then click **Hold earnings statement**. The payment status is set to **On hold**, and the lines won’t be included on any pay statement until you release them for processing.
    -   To put individual lines on hold, so that the rest of the earnings statement can be processed, open the earnings statement, select the lines to put on hold, and then click **Hold lines for payment**.

## Release earnings for payment processing
Use this procedure to change the status of all earnings statement lines from **None** to **Released**. You must release earnings statement lines before you generate pay statements. If an earnings statement line is on hold, this procedure releases it only if you select the **Release lines on hold** check box. 

To release earnings statement lines, follow these steps.

1.  Click **Payroll** &gt; **Earnings statements** &gt; **All Earnings statements**, and select **Release earnings statement**.
2.  In the **Pay cycle** field, select the pay cycle of the worker positions to process.
3.  In the **Pay period** field, select the pay period for the worker position earnings. The list includes only the pay periods that are available for the pay cycle. The default pay period is the first open pay period. However, you can select any open pay period in the list.
4.  Optional: Select the **Release lines on hold** check box to release any lines that are on hold on the earnings statements.
5.  Click **OK** to change all the earnings statement lines that have a payment status of **None** to **Released**, so that they can be processed. **Note:** When you release an earnings statement line for an accrued benefit, such as sick time or vacation time, the number of hours on the line is verified against the minimum balance that the benefit accrual plan requires. If the balance is less than the number of hours on the line, the line isn’t released. For more information, see [Benefit accrual plan tasks](noam-usa-benefit-accrual-plan-tasks.md).

## If required: Change earnings statements
After you generate an earnings statement, you can add lines to it. You can also change existing lines, provided that they haven’t been released or processed. You can delete released lines but not processed lines.

1.  Click **Payroll** &gt; **Earnings statements** &gt; **All Earnings statements**, and select the earnings statement to change.
2.  Make the required changes. Keep the following information in mind:
    -   **Salaried workers** – If you change or add a line for a salaried worker, lines that have a source of **Salary** are calculated and re-created, unless you click **Calculate Salary**. This functionality helps guarantee that salaried workers don't receive more or less than their usual amount for the pay period. We recommend that you keep the **Calculate Salary** functionality turned on unless you're terminating a worker’s employment.
    -   **Overtime premiums** – Earnings statement lines that have a rate basis of **Regular rate of pay** are used to create overtime premiums. These lines are calculated based on all other earnings statement lines for nondiscretionary earnings. Therefore, after you change any earnings statement line, you must delete all lines that have a rate basis of **Regular rate of pay** and then add those lines again. Otherwise, the **Regular rate of pay** lines might not be correct.
    -   **Retroactive earnings** – You can change retroactive earning lines, but you can’t change the original retroactive rate that the earnings statement line originated from. For more information, see [Earning code and earning code group tasks](noam-usa-earning-code-group-tasks.md).

## Next step
After you finalize all the earnings, you’re ready to generate pay statements. For more information, see [Work with pay statements](noam-usa-pay-statements.md).

See also
--------

[Earnings and the earnings generation process Q&A](noam-usa-earnings-generation-process.md)



