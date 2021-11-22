---
# required metadata

title: Generate earnings for workers
description: This topic describes the various ways that you can generate earnings for workers.
author: andreabichsel
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmPosition, HcmWorker, PayrollEarningStatement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.tgt_pltfrm: 
ms.custom: 220864
ms.assetid: 87aac2bd-fcdb-4f97-a55f-7f25659d6940
ms.search.region: USA
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Generate earnings for workers

[!include [banner](../../includes/banner.md)]

This topic describes the various ways that you can generate earnings for workers. You can automatically generate earnings for salaried positions, for positions that use a schedule, and for recurring earnings, premium earnings, and retroactive earnings. You can also enter earnings manually.

You can automatically generate earnings for salaried positions, for positions that use a schedule, and for recurring earnings, premium earnings, and retroactive earnings. You can also enter earnings manually.

When you automatically generate earnings, we recommend that you use the batch processing mode to improve performance. You must manually enter some earnings, such as sick time and paid time off. You can enter these earnings either before or after you use the automated process to generate the standard earning lines. If you use the automated process first, you must manually add and remove earning lines until the earnings statement is correct.

> [!NOTE]
> This topic describes how to generate earnings for a worker pay period for the first time. If you've already generated earnings, and you want to change them or take additional action on them, see [Process existing earnings](noam-usa-existing-earnings.md).

## Automatically generate earnings

Earnings that are automatically generated use settings for the position to identify the pay cycle, legal entity, and whether the earnings should be generated as a salary amount or based on a schedule. During this process, recurring earnings that are assigned to a specific worker are automatically generated if they are due in the specified pay period and pay cycle.

> [!NOTE]
> When you generate earnings for workers, you specify only the pay cycle and pay period to use. You don't specify the type of earning to generate. Recurring earnings, salary, leave, and schedule-based earnings are all created in the same process. Premium earnings, such as overtime premiums, and retroactive earnings are created separately.

To automatically generate worker earnings, follow these steps.

1. Click **Payroll** &gt; **Earnings statement processing** &gt; **Generate earnings**.

    > [!NOTE]
    > To generate earnings from the **Workers** or **Positions** page, click the **Payroll** tab.

2. Specify the following information for the worker positions to generate earnings for.

    | Field      | Description |
    |------------|-------------|
    | Pay cycle  | Select the pay cycle. |
    | Pay period | Select the pay period. The list includes only the pay periods that are available for the pay cycle. The first open pay period is the default pay period, but you can select any open pay period in the list. |

3. Click **OK** to generate earnings statements. You receive a message that states that the earnings statements were generated successfully.

    > [!NOTE]
    > Recurring earnings and the earnings from schedules are created first, because salary amounts might be affected by other earnings that are automatically generated.

4. To view the earnings statements that were created or updated, open the **All Earnings statements** list page.
5. Verify that the batch job was completed correctly. (Click **Common** &gt; **Inquiries** &gt; **Batch Jobs** &gt; **My batch jobs**. On the **Batch job** tab, click **Log**, and then inspect the log for any errors that occurred.)

## Manually enter earnings

To manually enter earnings that are based on pieces and earnings for exceptions, such as sick time or vacation time, follow these steps.

1. Click **Payroll** &gt; **Earnings statements** &gt; **All Earnings statements**.
2. Open an earnings statement, and then click **Edit**.
3. Click **Add line**, and then enter the following information:

    1. Modify the earnings date if it isn't the end date of the pay period.
    2. Select the position that the worker earned the earnings in.
    3. Select the tax region.
    4. Select the earning code that represents the type of earning. When you select the earning code, the default description, quantity, unit type, and rate are entered from the earning code. Enter a quantity that is appropriate for the unit type. You can also change the rate. However, the that you enter must be a flat rate and must not be calculated by the system.

4. If you didn't use the automated process to generate earnings before you began to enter lines manually, you can click **Generate earnings** to use the default values on the remaining lines of the worker's earnings statement. The lines that you entered manually aren't affected. You can also automatically generate earnings statements by using the process that is described earlier in this topic. In that case, the lines that you entered manually *are* affected.

    > [!NOTE]
    > You can complete this step regardless of whether the worker is paid a salary or paid hourly.

5. Close the page to save the earnings statement.

## If required: Generate premium earnings

You can manually enter premium earnings, or you can generate them by using an automated process. When you use the automated process, the system adds premium lines to existing pay statements that have the selected pay cycle. The automated process doesn't create new earnings statements.

If a worker should receive a premium for a pay period that the worker has no other earnings in, manually create an earnings statement for that worker, and then generate the premium earnings.

To generate premium earnings for workers, follow these steps.

1. Determine whether there are dependencies between any premiums that you offer. For example, if you offer a premium that is paid in addition to a shift differential, the additional premium can't be calculated unless the earnings for the shift differential are already on the earnings statement.
2. Click **Payroll** &gt; **Periodic** &gt; **Earnings statement processing** &gt; **Generate premium earnings**.

    > [!NOTE]
    > You can generate premium earnings for a single worker from the worker's earnings statement, but not from the **Workers** or **Positions** page.

3. Specify the following information for the worker positions to generate premium earnings for.

    <table>
    <thead>
    <tr>
    <th>Field</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>Pay cycle</td>
    <td>Select the pay cycle.</td>
    </tr>
    <tr>
    <td>Pay period</td>
    <td>Select the pay period. The list includes only the pay periods that are available for the pay cycle. The first open pay period is the default pay period, but you can select any open pay period in the list.</td>
    </tr>
    <tr>
    <td>Replace premium earnings</td>
    <td>Select this check box if you must replace existing premium earning lines. Often, when you select this check box, you also select the <strong>Generate earnings for specified codes only</strong> option in the <strong>Generate</strong> field.</td>
    </tr>
    <tr>
    <td>Generate</td>
    <td>Select one of the following options:
    <ul>
    <li><strong>Generate earnings for all premium codes</strong> – Select this option if there are no dependencies between premium codes.</li>
    <li><strong>Generate earnings for specified codes only</strong> – Select this option if there are dependencies between premium codes. After you select this option, select the premium codes to generate earnings for.</li>
    </ul>
    </td>
    </tr>
    </tbody>
    </table>

4. Click **OK** to generate premium earnings for all earnings statements. You receive a message that states that the premium earnings were generated successfully.
5. Repeat this task for any additional premium codes that you must generate premiums for.
6. To view the earnings statements that were updated, open the **All Earnings statements** list page.
7. Verify that the batch job was completed correctly. (Click **Common** &gt; **Inquiries** &gt; **Batch Jobs** &gt; **My batch jobs**. On the **Batch job** tab, click **Log**, and then inspect the log for any errors that occurred.)

## If required: Manually add overtime premiums

To create overtime premiums, manually add earning lines that have a rate basis of **Regular rate of pay**. For example, a worker worked 48 hours in a work period. Therefore, this worker's earnings statement includes 48 hours at the regular rate. You add a line that uses the earning code that you created for overtime premiums. The line calculates the full overtime premium by using the multiplier on the earning code to determine the worker's regular earnings plus any adjustments that are required by the Fair Labor Standards Act (FLSA).

> [!IMPORTANT]
> To help guarantee that the calculations are correct, you must enter overtime lines after all other earnings for the pay period have been entered. If you change any earnings on the earnings statement, you must delete and re-create the overtime premium lines.

To add overtime premiums for workers, follow these steps.

1. Click **Payroll** &gt; **Earnings statements** &gt; **All Earnings statements**.
2. Open an earnings statement, and then click **Edit**.
3. Click **Add line**, and then enter the following information:

    1. Change the earnings date if it isn't in the work period that the overtime line applies to.
    2. Select the position that the worker earned the earnings in.
    3. Select the tax region.
    4. Select the earning code for the overtime premium. When you select the earning code, the default description, quantity, unit type, and rate are entered from the earning code.

4. Close the page to save the earnings statement.

## If required: Generate retroactive earnings

When an hourly worker or a worker who is paid by the piece is entitled to back pay, you can automatically calculate the difference between the previous rate of pay and the new rate of pay. This amount appears as retroactive pay on its own earnings statement line, and the original retroactive rate is listed as the source.

You can also calculate retroactive pay for salaried workers. The salary-based earnings statement lines are adjusted to reflect the new rate.

> [!NOTE]
> If you generate earnings from the **Payroll** tab of the **Workers** or **Positions** page, retroactive earnings are included, and a separate process isn't required.

1. Click **Payroll** &gt; **Earnings statement processing** &gt; **Retroactive earnings** &gt; **Generate retroactive earnings**.
2. Enter the following information.

    | Field               | Description |
    |---------------------|-------------|
    | Pay cycle           | The pay cycle to evaluate for retroactive earnings. Only earnings that were processed in a pay period that is associated with the selected pay cycle are evaluated for retroactive earnings. |
    | Start date End date | The first and last dates in the range of dates to evaluate for retroactive earnings. Retroactive pay calculations ignore the start and end dates of the pay period. All earnings that are by the hour or by the piece, and that occur in the selected date range, are evaluated to determine whether retroactive earnings should be generated. For salary-based earnings, the start date must be the first date of a pay period, and the end date must be the last day of a pay period. Retroactive pay calculations that affect part of a pay period might not be accurate. |
    | Accounting date     | The accounting date that is assigned to the retroactive earning lines. |

3. Click **OK** to generate retroactive earnings and add them to earnings statements. You receive a message that indicates the number of earnings statements that were updated.
4. To view the earnings statements that were updated, open the **All Earnings statements** list page. For earnings that are based on hours or pieces, the retroactive earnings appear on a separate line, together with the retroactive earning code. For salary-based earnings, the amounts have been adjusted, but they don't appear on separate lines. To view all the retroactive earnings that you generated, open the **Review retroactive earnings lines** page. (Click **Payroll** &gt; **Earnings statement processing** &gt; **Retroactive earnings** &gt; **Review retroactive earning lines**.)
5. Verify that the batch job was completed correctly. (Click **Common** &gt; **Inquiries** &gt; **Batch Jobs** &gt; **My batch jobs**. On the **Batch job** tab, click **Log**, and then inspect the log for any errors that occurred.)

## Next step

After you generate earnings, you must release them before you can create pay statements. You might also have to change the earnings or put certain earnings on hold. For more information, see [Process existing earnings](noam-usa-existing-earnings.md).

## Additional resources

[Process existing earnings](noam-usa-existing-earnings.md)

[Generate and work with pay statements](noam-usa-pay-statements.md)

[Issue worker payments](noam-usa-issue-worker-payments.md)

[Post payroll distributions and generate vendor invoices](noam-usa-post-payroll-generate-vendor-invoices.md)

[Process existing payroll payments](noam-usa-existing-payroll-payments.md)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]