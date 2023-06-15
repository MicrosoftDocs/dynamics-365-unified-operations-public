---
# required metadata

title: Enter payroll beginning balances
description: The article describes the steps for entering beginning balances for earning codes, deductions, benefits, and taxes.
author: twheeloc
ms.date: 11/20/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: PayrollEarningStatement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: b48b1cb2-6e66-467e-9c0e-09b6a4aeb9fe
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: AX 7.0.0

---

# Enter payroll beginning balances

[!include [banner](../../includes/banner.md)]

The article describes the steps for entering beginning balances for earning codes, deductions, benefits, and taxes. This information is valuable for partners who transfer data for a new Payroll implementation from another system. To prepare to enter beginning payroll balances, we verify the following information:

- Employee records are entered and available in the system
- The following data is set up and assigned to employees:

    - Pay cycles and pay periods
    - Earning codes
    - Taxes
    - Benefits and deductions

- The company should have chosen a date where payroll beginning balances can be set.
- Information was gathered on all earnings, benefits/deductions, benefit contributions, employee taxes, and employer taxes and their YTD amounts from the legacy system.

As you plan to enter beginning balances, consider how detailed the data needs to be. Most businesses enter a single, consolidated year-to-date amount. However if more detailed information is needed, balances can be entered in quarterly increments. Deciding the level of detail that's needed determines how many manual pay statements must be created for each worker. For a single year-to-date amount, only one manual statement is needed for each employee. To do this, use year-to-date amounts from the final pay statement from the previous system as the amount entered in the new payroll system.

The following example shows how you can enter employee payroll beginning balances, including earning codes, benefits/deductions, and taxes. In a real-world example you would have a line item for each earning code, benefit deduction, benefit contribution, employee tax and employer tax with the amount entered being the year-to-date amount. Using that list of codes and amounts, follow the steps for creating a manual earning and pay statement with accounting disabled to bring over beginning balances for payroll purposes. You disable accounting because you won't want to post this beginning balance pay statement to your general ledger. That was done in the legacy system and will come over to the new system when you set beginning balances in General ledger.

### A. How to set up earnings codes to be used on payroll beginning balances

When you enter payroll beginning balances, be sure the earning codes that you will be using are configured with the "Allow editing of earning statement rates" option enabled. This will allow you to manually key the amount from the legacy system. 

### B. Create earnings statement for an employee to have a beginning balance

This step manually creates an earnings statement for each worker for the last pay period of the legacy system, which creates the earning statement lines in the new payroll system. Enter one line per earning code and the YTD amount and hours. The sample steps are as follows:

1. Open the **All earnings statements** page and click **New**.

    Enter the following: 

    | Field      | Value                 |
    |------------|-----------------------|
    | Worker     | Michael Redmond       |
    | Pay cycle  | sm                    |
    | Pay period | 6/16/2017 - 6/30/2017 |

2. In the **Earnings statement line** tab, enter the following:

    Line 1: **Earning statement line** tab

    | Field            | Value       |
    |------------------|-------------|
    | Earnings code    | Regular pay |
    | Quantity         | 1.00        |
    | Rate             | 30,000      |
    | Line details tab |             |
    | Manual           | (marked)    |

    Line 2: **Earning statement line** tab

    | Field            | Value    |
    |------------------|----------|
    | Earnings code    | Bonus    |
    | Quantity         | 1.0000   |
    | Rate             | 4250.00  |
    | Line details tab |          |
    | Manual           | (marked) |

    Line 3: **Earning statement line** tab

    | Field           | Value      |
    |-----------------|------------|
    | Earnings code   | Commission |
    | Quantity        | 1.0000     |
    | Rate            | !,299.00   |
    | Rate            | 1,299.00   |
    | Line detail tab |            |
    | Manual          | (Marked)   |

    > [!NOTE]
    > Setting the **Manual** slider to **Yes** in the **Line Details** tab for each earnings statement line is key to have payroll beginning balances entered for each worker.

3. On the **Action** pane, click **Release earnings statement** USA-FED-ER-FICA.
4. On the **Action** pane click **Pay statement** to open the **Generate pay statements** page and set the following:

    | Field              | Value     |
    |--------------------|-----------|
    | Payment date       | 6/30/2017 |
    | Payment run type   | Manual    |
    | Disable accounting |   Yes     |

    > [!NOTE] 
    > This is only available when the payment run type is manual and wherein the user want to disable accounting on the pay run.

    Click **OK** and close the **Infolog**.

#### Why the Disable Accounting slider needs to set to Yes when generating pay statements?

Setting the slider to **Yes** prevents lines in the pay statement from being distributed to General ledger. General ledger amounts were updating earlier when account balances from the legacy system were entered. Entering beginning balances for Payroll lets you generate reports that include information from prior years, as well as for identifying limits for benefit and tax purposes.

### C. Create pay statements for employees

After you generate pay statements that have beginning balances, you must verify that the pay statements accurately reflect payroll data. You must also manually update the benefit and taxes information to match the values in the previous payroll system. After you verify that the amounts from the previous payroll system match the amounts on the current pay statements, you must finalize the pay statements.

1. Open the **All pay statements** page.
2. Highlight the last generated pay statement for Michael Redmond
3. Click **Edit** to open the **Pay statement** page.
4. Open the **Benefit deductions** tab and enter the following:

    | Field             | Value            |
    |-------------------|------------------|
    | Benefit           | Deduction amount |
    | 401K              | Participate      |
    | Dental            | SubSp            |
    | Dep care spending | Participate      |
    | Vision            | SupSp            |

5. In the **Benefit contributions** tab and enter the following:

    | Field   | Value               |
    |---------|---------------------|
    | Benefit | Contribution amount |
    | 401K    | Participate         |
    | Dental  | SubSp               |
    | Vision  | SubSp               |

6. In the **Tax deductions** tab, enter the following:

    | Field           | Value            |
    |-----------------|------------------|
    | Tax code        | Deduction amount |
    | USA-FED-ER-FICA | 1600.00          |
    | USA-FED-ER-MEDI | 825.75           |

7. In the **Tax contributions** tab enter the following:
8. Click **Calculate**.

    > [!IMPORTANT] 
    > Validate the totals of the pay statement that they match the YTD of the legacy system for the worker. You may want to hold off on finalizing in the next step to do some overall validating of all pay statements in aggregate. Once validated run through all the pay statements and finalize them.

The same process can be done in quarter increments if necessary for all prior quarters in each year. This is only needed if the customer needs to see the data by quarter without going back to the legacy system.

## If you make a mistake Entering Beginning Balances for an Employee

It is possible to reverse and reenter transactions. To reverse the transaction, all you have to do is to complete the follow steps on the **All pay statements** page.

1. Click **Reverse**.
2. Click **Yes** when the message "When you reverse this pay statement, a reversing pay statement will be created to offset this pay statement. Neither pay statement can be edited. Do you want to reverse this pay statement?" displays. 

After you reverse the pay statement, you can generate a new pay statement for the worker from the earnings statement that you created previously. Be sure to fix any incorrect lines on the earnings statement before you generate the new pay statement, and then generate new pay statements with the correct amounts. 


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
