---
title: Set up time and attendance information in Dynamics 365 Human Resources
description: Learn how to set up calculation and approval groups for time and attendance and set up absence information in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.date: 06/11/2026
ms.topic: how-to
f1_keywords:
- group
- approval
- calculation
- password
audience: Application User
ms.search.region: Global
---

# Set up time and attendance information in Dynamics 365 Human Resources

This article explains how to set up calculation and approval groups for time and attendance, and how to set up absence information through absence setups and absence groups.

## Set up calculation and approval groups for time and attendance

All workers who register in **Time and attendance**, or **Manufacturing execution** if you're using it with **Time and attendance**, must connect to a calculation group and to an approval group.

> [!NOTE]
> For security reasons, enter a password for the group on the **General** tab. The system requests the password before you can open the **Calculate** page.
> When you create approval groups, enter a password for the group on the **General** tab. The system requests the password before you can open the **Approve** page.

## Set up absence information

### Create absence setups

Some companies or groups of workers in the same company need multiple absence periods, multiple absence administrators, and different working times to track workers’ absences. To allow for this differentiation, create absence setups.

#### Create an absence setup

1. Select **Human resources** > **Setup** > **Absence** > **Absence setup**.
1. Select **New**.
1. Enter a name and description for the absence setup.
1. Select the length of the period in which you must register absences for workers who are assigned to the absence setup.

    For example, to track a worker’s absences on a monthly basis, select **Calendar month**. Any worker who is assigned to the absence setup must transfer their absence registrations monthly for approval.
    To use a flexible registration period, select **No period**. This option enables the person assigned to the absence setup to register absence, as needed, and reduces how often absence journals must be created.

1. Select the absence administrator for the absence setup. The absence administrator approves or rejects absences for workers who are assigned to the absence setup.
1. Select the period when you register absences from the following options:
    - **Days**
    - **Hours**
     For example, to track absences by the days that a worker missed, select **Days**.

1. Select **Close**.

### Create absence groups

Absence groups are logical groups of absence codes. For example, an absence group titled Personal might include the following absence codes:

- Dentist
- Doctor
- Funeral
- Wedding

#### Create an absence group

1. Select **Human resources** > **Setup** > **Absence** > **Absence groups**.
1. Select **New**.
1. Enter a name and description for the absence group.
1. If you use time and attendance, and you have workers with flexible work hours, select the **Reduce flex** checkbox to reduce the balance of flexible hours for workers who register an absence by using an absence code in the absence group.
1. If you use time and attendance, and you have workers who work overtime hours, select the **Deduct overtime** checkbox to reduce overtime hours for workers who register an absence by using an absence code in the absence group.
1. Select the **Registration** checkbox to enable workers to enter an absence registration by using the absence codes in the absence group.
1. Select **Close**.

### Create absence codes

Absence codes indicate the reasons for worker absences. For each absence code, you can also set up validation rules that indicate how often during a specific period that a worker can be absent for the same reason.

For example, you could create an absence code titled Doctor Visit for when a worker has to miss work to visit a doctor. By using validation rules, you could also specify that workers can only be absent from work for two doctor visits per month.

#### Create an absence code

1. Select **Human resources** > **Setup** > **Absence** > **Absence codes**.
1. Select **New**.
1. Enter a name and description for the absence code.
1. If you plan to use absence validation rules, select the text color and the background color for the absence code.

    The color codes that you specify are used in the **Absence administration** page, where you can view a list of the workers who violated absence validation rules.

1. Select the absence group to include this absence code in.

> [!NOTE]
> On the **Time and attendance** FastTab, in the **Icon** field, you can specify the identifier for an icon for the absence code. The icon is displayed for the absence code when a worker clocks in or clocks out at a time that is outside typical working hours. However, before you can enter the identifier, add the icon to the list of embedded resources. For assistance, contact your system administrator.

#### Add validation rules to an absence code

1. Select **Human resources** > **Setup** > **Absence** > **Absence codes**.
1. In the left pane, select the absence code to add validation rules to.
1. Expand the **Validations** FastTab.
1. To create a **Max. in series** validation rule, read the example, and then complete the following steps.

    **Example**

    The rule is that only three consecutive absence days are allowed in a two-month period.

    1. Select the **Active** check box to activate this rule.
    1. To indicate that the rule only applies to work days, select the **Work days** checkbox.
    1. Enter the number of consecutive absence days that are allowed. For the example rule, enter 3.
    1. Enter the number of period units. For the example rule, enter 2.
    1. Select the period code. For the example rule, select **Months**.

1. To create a **Max. days in a period** validation rule, read the example, and then complete the following steps.

    **Example**

    The rule is that a worker can only have 10 absences that span multiple days in a one-year period.

    1. Select the **Active** checkbox to activate this rule.
    1. Enter the number of multiple-day absences that are allowed. For the example rule, enter 10.
    1. Enter the number of period units. For the example rule, enter 1.
    1. Select the period code. For the example rule, select **Year**.

1. To create a **Max. series in a period** validation rule, read the example, and then complete the following steps.

    **Example**

    The rule is that a worker can only have five instances of multiple-day absences in a 52-week period.

    1. Select the **Active** checkbox to activate this rule.
    1. To indicate that the rule only applies to work days, select the **Work days** checkbox.
    1. Enter the number of occurrences of multiple-day absences that are allowed. For the example rule, enter 10.
    1. Enter the number of period units. For the example rule, enter 52.
    1. Select the period code. For the example rule, select **Weeks**.

### Specify a color for open absence transactions

To make it easier for workers and absence administrators to notice open absence transactions on the **Register absences** page, specify a color for open absence transactions. On the **Register absences** page, the rows in the grid that represent open absence transactions appear in the color that you select for open absence transactions.

1. Select **Human resources** > **Setup** > **Parameters** > **Human resources parameters**.
1. Select **General** to display the **Set up Human resources** page.
1. Select a color to apply to all open absence transactions.

## See also

[Time and attendance information in Dynamics 365 Human Resources](hr-about-time-and-attendance-information.md)

[Register time for workers in Dynamics 365 Human Resources](hr-register-time.md)
