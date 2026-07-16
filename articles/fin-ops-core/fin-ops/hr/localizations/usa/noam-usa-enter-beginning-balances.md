---
title: Enter payroll beginning balances
description: Learn about the steps for entering beginning balances for earning codes, deductions, benefits, and taxes, including an overview on what to do in case of mistakes.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 06/25/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.search.form: PayrollEarningStatement
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: b48b1cb2-6e66-467e-9c0e-09b6a4aeb9fe
---

# Enter payroll beginning balances

[!include [banner](../../../../../finance/includes/banner.md)]

This article describes the steps for entering beginning balances for earning codes, deductions, benefits, and taxes. This information is valuable for partners who transfer data for a new Payroll implementation from another system. To prepare to enter beginning payroll balances, verify the following information:

- Employee records are entered and available in the system.
- The following data is set up and assigned to employees:

  - Pay cycles and pay periods
  - Earning codes
  - Taxes
  - Benefits and deductions

- The company chooses a date for setting payroll beginning balances.
- You gather information on all earnings, benefits and deductions, benefit contributions, employee taxes, and employer taxes and their year-to-date amounts from the legacy system.

As you plan to enter beginning balances, consider how detailed the data needs to be. Most businesses enter a single, consolidated year-to-date amount. However if more detailed information is needed, balances can be entered in quarterly increments. Deciding the level of detail that's needed determines how many manual pay statements must be created for each worker. For a single year-to-date amount, only one manual statement is needed for each employee. To do this, use year-to-date amounts from the final pay statement from the previous system as the amount entered in the new payroll system.

The following example shows how you can enter employee payroll beginning balances, including earning codes, benefits/deductions, and taxes. In a real-world example you would have a line item for each earning code, benefit deduction, benefit contribution, employee tax, and employer tax with the amount entered being the year-to-date amount. Using that list of codes and amounts, follow the steps for creating a manual earning and pay statement with accounting disabled to bring over beginning balances for payroll purposes. You disable accounting because you won't want to post this beginning balance pay statement to your general ledger. That was done in the legacy system and will come over to the new system when you set beginning balances in General ledger.

### A. How to set up earnings codes to be used on payroll beginning balances

When you enter payroll beginning balances, be sure the earning codes that you use are configured with the **Allow editing of earning statement rates** option enabled. This option allows you to manually key the amount from the legacy system.

### B. Create earnings statement for an employee to have a beginning balance

This step manually creates an earnings statement for each worker for the last pay period of the legacy system, which creates the earning statement lines in the new payroll system. Enter one line per earning code and the YTD amount and hours. The sample steps are as follows:

1. Open the **All earnings statements** page and select **New**.

    Enter the following values:

    | Field      | Value                 |
    |------------|-----------------------|
    | Worker     | Michael Redmond       |
    | Pay cycle  | sm                    |
    | Pay period | 6/16/2025 - 6/30/2025 |

1. In the **Earnings statement line** tab, enter the following values:

    Line 1: **Earnings statement line** tab

    | Field            | Value       |
    |------------------|-------------|
    | Earnings code    | Regular pay |
    | Quantity         | 1.00        |
    | Rate             | 30,000      |
    | Line details tab |             |
    | Manual           | (marked)    |

    Line 2: **Earnings statement line** tab

    | Field            | Value    |
    |------------------|----------|
    | Earnings code    | Bonus    |
    | Quantity         | 1.0000   |
    | Rate             | 4250.00  |
    | Line details tab |          |
    | Manual           | (marked) |

    Line 3: **Earnings statement line** tab

    | Field           | Value      |
    |-----------------|------------|
    | Earnings code   | Commission |
    | Quantity        | 1.0000     |
    | Rate            | 1,299.00   |
    | Rate            | 1,299.00   |
    | Line detail tab |            |
    | Manual          | (Marked)   |

    > [!NOTE]
    > Set the **Manual** slider to **Yes** in the **Line Details** tab for each earnings statement line to enter payroll beginning balances for each worker.

1. On the **Action** pane, select **Release earnings statement** USA-FED-ER-FICA.
1. On the Action pane, select **Pay statement** to open the **Generate pay statements** page and set the following values:

    | Field              | Value     |
    |--------------------|-----------|
    | Payment date       | 6/30/2025 |
    | Payment run type   | Manual    |
    | Disable accounting |   Yes     |

    > [!NOTE]
    > This option is available only when the payment run type is manual and you want to disable accounting on the pay run.

    Select **OK** and close the **Infolog**.

#### Why the Disable Accounting slider needs to set to Yes when generating pay statements?

Set the slider to **Yes** to prevent lines in the pay statement from being distributed to General ledger. General ledger amounts update earlier when you enter account balances from the legacy system. When you enter beginning balances for Payroll, you can generate reports that include information from prior years, and for identifying limits for benefit and tax purposes.

### C. Create pay statements for employees

After you generate pay statements that have beginning balances, you must verify that the pay statements accurately reflect payroll data. You must also manually update the benefit and taxes information to match the values in the previous payroll system. After you verify that the amounts from the previous payroll system match the amounts on the current pay statements, you must finalize the pay statements.

1. Open the **All pay statements** page.
1. Highlight the last generated pay statement for Michael Redmond.
1. Select **Edit** to open the **Pay statement** page.
1. Open the **Benefit deductions** tab and enter the following values:

    | Field             | Value            |
    |-------------------|------------------|
    | Benefit           | Deduction amount |
    | 401K              | Participate      |
    | Dental            | SubSp            |
    | Dep care spending | Participate      |
    | Vision            | SupSp            |

1. In the **Benefit contributions** tab, enter the following values:

    | Field   | Value               |
    |---------|---------------------|
    | Benefit | Contribution amount |
    | 401K    | Participate         |
    | Dental  | SubSp               |
    | Vision  | SubSp               |

1. In the **Tax deductions** tab, enter the following values:

    | Field           | Value            |
    |-----------------|------------------|
    | Tax code        | Deduction amount |
    | USA-FED-ER-FICA | 1600.00          |
    | USA-FED-ER-MEDI | 825.75           |

1. In the **Tax contributions** tab, enter the following values:
1. Select **Calculate**.

    > [!IMPORTANT]
    > Validate the totals of the pay statement that they match the YTD of the legacy system for the worker. You might want to hold off on finalizing in the next step to do some overall validating of all pay statements in aggregate. Once validated, run through all the pay statements and finalize them.

You can use the same process in quarter increments if necessary for all prior quarters in each year. This step is only needed if the customer needs to see the data by quarter without going back to the legacy system.

## If you make a mistake entering beginning balances for an employee

You can reverse and reenter transactions. To reverse the transaction, complete the following steps on the **All pay statements** page.

1. Select **Reverse**.
1. Select **Yes** when the message "When you reverse this pay statement, a reversing pay statement is created to offset this pay statement. Neither pay statement can be edited. Do you want to reverse this pay statement?" displays.

After you reverse the pay statement, you can generate a new pay statement for the worker from the earnings statement that you created previously. Be sure to fix any incorrect lines on the earnings statement before you generate the new pay statement. Then, generate new pay statements with the correct amounts.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
