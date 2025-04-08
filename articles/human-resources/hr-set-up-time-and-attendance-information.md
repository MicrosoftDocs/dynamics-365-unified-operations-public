---
title: Set up time and attendance information in Dynamics 365 Human Resources
description: Learn how to set up calculation and approval groups for time and attendance and set up absence information in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.date: 01/24/2024
ms.topic: article
f1_keywords:
- group
- approval
- calculation
- password
audience: Application User
ms.search.region: Global
---

# Set up time and attendance information in Dynamics 365 Human Resources

This article discusses how to set up calculation and approval groups for time and attendance and how to set up absence information through absences setups and absence groups.

## Set up calculation and approval groups for time and attendance 

All workers who make registrations in **Time and attendance**, or **Manufacturing execution** if you're using it with **Time and attendance**, must be connected to a calculation group, and to an approval group.

> [!NOTE]
> For security reasons, it is recommended that you insert a password for the group on the **General** tab. The password will be requested before you can open the **Calculate** page.
> When creating approval groups, it's recommended that you insert a password for the group on the **General** tab. The password will be requested before you can open the **Approve** page.

## Set up absence information

### Create absence setups

For some companies, or for groups of workers in the same company, it's necessary to have multiple absence periods, multiple absence administrators, and different working times to track workers’ absences. To allow for this differentiation, you can create absence setups.

#### Create an absence setup

1.  Click **Human resources** \> **Setup** \> **Absence** \> **Absence setup**.
2.  Click **New**.
3.  Enter a name and description for the absence setup.
4.  Select the length of the period in which absences must be registered for workers who will be assigned to the absence setup.
    
    For example, to track a worker’s absences on a monthly basis, select **Calendar month**. Any worker who is assigned to the absence setup must transfer their absence registrations monthly for approval.
    To use a flexible registration period, select **No period**. This enables the person assigned to the absence setup to register absence, as needed, and reduces how often absence journals must be created.

5.  Select the absence administrator for the absence setup. The absence administrator approves or rejects absences for workers who are assigned to the absence setup.
6.  Select the period when absences are registered from the following options:
    - **Days**
    - **Hours**
     For example, to track absences by the days that a worker missed, select **Days**.

7.  Click **Close**.

### Create absence groups

Absence groups are logical groups of absence codes. For example, an absence group titled Personal might include the following absence codes:

  - Dentist
  - Doctor
  - Funeral
  - Wedding

#### Create an absence group

1.  Click **Human resources** \> **Setup** \> **Absence** \> **Absence groups**.
2.  Click **New**.
3.  Enter a name and description for the absence group.
4.  If you use time and attendance, and you have workers with flexible work hours, select the **Reduce flex** checkbox to reduce the balance of flexible hours for workers who register an absence by using an absence code in the absence group.
5.  If you use time and attendance, and you have workers who work overtime hours, select the **Deduct overtime** checkbox to reduce overtime hours for workers who register an absence by using an absence code in the absence group.
6.  Select the **Registration** checkbox to enable workers to enter an absence registration by using the absence codes in the absence group.
7.  Click **Close**.

### Create absence codes

Absence codes indicate the reasons for worker absences. For each absence code, you can also set up validation rules that indicate how often during a specific period that a worker can be absent for the same reason.

For example, you could create an absence code titled Doctor Visit for when a worker has to miss work to visit a doctor. By using validation rules, you could also specify that workers can only be absent from work for two doctor visits per month.

#### Create an absence code

1.  Click **Human resources** \> **Setup** \> **Absence** \> **Absence codes**.
2.  Click **New**.
3.  Enter a name and description for the absence code.
4.  If you plan to use absence validation rules, select the text color and the background color for the absence code.
    
    The color codes that you specify are used in the **Absence administration** page, where you can view a list of the workers who have violated absence validation rules.

5.  Select the absence group to include this absence code in.

> [!NOTE]
> On the **Time and attendance** FastTab, in the **Icon** field, you can specify the identifier for an icon for the absence code. The icon is displayed for the absence code when a worker clocks in or clocks out at a time that is outside typical working hours. However, before you can enter the identifier, the icon must be added to the list of embedded resources. For assistance, contact your system administrator.

#### Add validation rules to an absence code

1.  Click **Human resources** \> **Setup** \> **Absence** \> **Absence codes**.
2.  In the left pane, select the absence code to add validation rules to.
3.  Expand the **Validations** FastTab.
4.  To create a **Max. in series** validation rule, read the example, and then complete the following steps.
    
    **Example**
    
    The rule is that only three consecutive absence days are allowed in a two-month period.
    
    1.  Select the **Active** check box to activate this rule.
    2.  To indicate that the rule only applies to work days, select the **Work days** checkbox.
    3.  Enter the number of consecutive absence days that are allowed. For the example rule, you would enter 3.
    4.  Enter the number of period units. For the example rule, you would enter 2.
    5.  Select the period code. For the example rule, you would select **Months**.

5.  To create a **Max. days in a period** validation rule, read the example, and then complete the following steps.
    
    **Example**
    
    The rule is that a worker can only have 10 absences that span multiple days in a one-year period.
    
    1.  Select the **Active** checkbox to activate this rule.
    2.  Enter the number of multiple-day absences that are allowed. For the example rule, you would enter 10.
    3.  Enter the number of period units. For the example rule, you would enter 1.
    4.  Select the period code. For the example rule, you would select **Year**.

6.  To create a **Max. series in a period** validation rule, read the example, and then complete the following steps.
    
    **Example**
    
    The rule is that a worker can only have five instances of multiple-day absences in a 52-week period.
    
    1.  Select the **Active** checkbox to activate this rule.
    2.  To indicate that the rule only applies to work days, select the **Work days** checkbox.
    3.  Enter the number of occurrences of multiple-day absences that are allowed. For the example rule, you would enter 10.
    4.  Enter the number of period units. For the example rule, you would enter 52.
    5.  Select the period code. For the example rule, you would select **Weeks**.

### Specify a color for open absence transactions

To make it easier for workers and absence administrators to notice open absence transactions on the **Register absences** page, you can specify a color for open absence transactions. On the **Register absences** page, the rows in the grid that represent open absence transactions are displayed in the color that you select for open absence transactions.

1.  Click **Human resources** \> **Setup** \> **Parameters** \> **Human resources parameters**.
2.  Click **General** to display the **Set up Human resources** page.
3.  Select a color to apply to all open absence transactions.

## See also

[Time and attendance information in Dynamics 365 Human Resources](hr-about-time-and-attendance-information.md)

[Register time for workers in Dynamics 365 Human Resources](hr-register-time.md)
