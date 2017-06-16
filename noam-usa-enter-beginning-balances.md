---
# required metadata

title: Enter payroll beginning balances
description: The topic describes the steps for entering beginning balances for earning codes, deductions, benefits, and taxes. This information is valuable for Partners to migrate or transfer data for a new Payroll implementation from another system.
author: kherr
manager: AnnBe
ms.date: 07/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 20931
ms.assetid: b48b1cb2-6e66-467e-9c0e-09b6a4aeb9fe
ms.search.region: Global
# ms.search.industry: 
ms.author: kherr
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: AX 7.0.0

---

# Enter payroll beginning balances

[!include[banner](includes/banner.md)]

The topic describes the steps for entering beginning balances for earning codes, deductions, benefits, and taxes. This information is valuable for Partners to migrate or transfer data for a new Payroll implementation from another system. As a pre-requisite before entering beginning balances for Payroll, we suggest verifying the following:

> 1. Workers or Employees are all available in the system
> 2. The following are setup and assigned to workers or employees in the system:

> > * Pay cycles and pay periods
> > * Earning codes
> > * Taxes
> > * Benefits and Deductions

3. The company should have chosen a date where payroll beginning balances can be set.

4. Information were gathered on all earnings, benefits/deductions, benefit contributions, employee taxes, and employer taxes and their YTD amounts from the legacy system.

When planning your beginning balance transition, you will want to determine how granular you need your data.  Most customers decide to bring the pay statement data over as a consolidated year-to-date value, however in some cases they may want to bring it over in quarter increments.  Identifying this will determine how many manual pay statements will need to be created for each worker.  If you are doing YTD transition, then only one manual statement is needed per worker. To do this you will use the YTD amounts from the final pay statement of the legacy system as the amounts you enter into the manual pay statement in AX.

The example below shows how this can be accomplished in entering employee payroll beginning balances - earning codes, benefits/deductions, and taxes.  In a real world example you would have a line item for each earning code, benefit deduction, benefit contribution, employee tax and employer tax with the amount entered being the YTD amount.  Using that list of codes and amounts, follow the steps for creating a manual earning and pay statement with accounting disabled to bring over beginning balances for payroll purposes.  You disable accounting as you do not want to post this beginning balance pay statement to the GL.  That was done in the legacy system and will come over to AX in your General Ledger beginning balance load.

> [!NOTE] 
> If you want to reproduce the same steps below, you can use the Demo data. The Demo data can be downloaded on PartnerSource

> A. How to setup Earnings Code to be used on Payroll Beginning Balances
When you enter Payroll Beginning Balances, be sure the earning codes that you will be using are configured with the "Allow editing of earning statement rates" option enabled.  This will allow you to manually key the amount from the legacy system. 

> B. Create Earnings statement for an employee to have a Beginning Balance

This step creates earnings statement for the last pay period of the legacy system for each worker manually creating the earning statement lines in AX.  Enter one line per earning code and the YTD amount and hours. Below are sample steps:

1. Open the **All earnings statements** page and click **New**.  

Enter the following: 

| Field      | Value                 |
|------------|-----------------------|
| Worker     | Michael Redmond       |
| Pay cycle  | sm                    |
| Pay period | 6/16/2017 - 6/30/2017 |

2. Go to: Earnings Statement Line Tab. Enter the following:

Line 1: **Earning statement line** tab

| Field            | Value       |
|------------------|-------------|
| Earnings code    | Regular pay |
| Quantity         | 1.00        |
| Rage             | 30,000      |
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
> Marking Manual checkbox setting in the Line Details tab for each Earnings statement line is key to have payroll beginning balances entered in the system for each worker.

3. On the Action pane, click Release Earnings statement USA-FED-ER-FICA.

4. On the Action pane click Pay Statement to open Generate pat statements page and set the following:

| Field              | Value     |
|--------------------|-----------|
| Payment date       | 6/30/2017 |
| Payment run type   | Manual    |
| Disable accounting | (marked)  |

> [!NOTE] This is only available when the payment run type is manual and wherein the user want to disable accounting on the pay run.

Click **OK** and close the **Infolog**.

### Why Disable Accounting checkbox needs to be turned on when generating pay statements?
This prevents any lines in the pay statement from being distributed and posted to the General Ledger. You do not want to post this beginning balance pay statement as its values are already in the GL from the legacy system.  This balance loading is used for reporting and limiting purposes only.

### C. Create pay statements for employees
After you generate pay statements that have beginning balances, you must verify that the pay statements accurately reflect payroll data. You must also manually update the benefit and taxes information to match the values in the previous payroll system. After you verify that the amounts from the previous payroll system match the amounts on the current pay statements, you must finalize the pay statements.

1. Open the **All pay statements** page.

2. Highlight the last generated pay statement for Michael Redmond

3. Click **Edit** to open the **Pay statement** page.

4. Open the **Benefit deductions** tab and enter the following:

| Field                           | Value            |
|---------------------------------|------------------|
| Benefit                         | Deduction amount |
| 401K | Participate              | 3000.00          |
| Dental | SubSp                  | 495.00           |
| Dep care spending | Participate | 2500.00          |
| Vision | SupSp                  | 500.00           |

5. In the **Benefit deductions** tab enter the following: 

| Field                           | Value            |
|---------------------------------|------------------|
| Benefit                         | Deduction amount |
| 401K | Participate              | 3000.00          |
| Dental | SubSp                  | 495.00           |
| Dep care spending | Participate | 2500.00          |
| Vision | SupSp                  | 500.00           |

6. In the **Benefit contributions** tab and enter the following:

| Field              | Value               |
|--------------------|---------------------|
| Benefit            | Contribution amount |
| 401K | Participate | 3000,00             |
| Dental | SubSp     | 495.00              |
| Vision | SubSp     | 500.00              |

7. In the **Tax deductions** tab, enter the following:

| Field           | Value            |
|-----------------|------------------|
| Tax code        | Deduction amount |
| USA-FED-ER-FICA | 1600.00          |
| USA-FED-ER-MEDI | 825.75           |

8. In the **Tax contributions** tab enter the following:

9. Click Calculate.
> [!IMPORTANT] 
> Validate the totals of the pay statement that they match the YTD of the legacy system for the worker. You may want to hold off on finalizing in the next step to do some overall validating of all pay statements in aggregate. Once validated run through all the pay statements and finalize them.

The same process can be done in quarter increments if necessary for all prior quarters in each year. This is only needed if the customer needs to see the data by quarter without going back to the legacy system.

## If you make a mistake Entering Beginning Balances for an Employee
It is possible to reverse and re-enter transactions. To reverse the transaction, all you have to do is to complete the  follow steps on the **All pay statements** page.

1. Click **Reverse**.

2. Click **Yes** when the message "When you reverse this pay statement, a reversing pay statement will be created to offset this pay statement. Neither pay statement can be edited. Do you want to reverse this pay statement?" displays. 

After you reverse the pay statement, you can generate a new pay statement for the worker from the earnings statement that you created previously in the “Generate earnings statements and pay statements that have beginning balances” procedure earlier in this topic. Be sure to fix any incorrect lines on the earnings statement before you generate the new pay statement, and then repeat the “Update pay statements that have beginning balances for benefits and taxes” procedure in this topic.
