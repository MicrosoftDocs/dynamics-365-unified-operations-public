---
# required metadata

title: Pay based on registrations
description: This article explains how pay is calculated based on worker registrations.
author: johanhoffmann
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: JmgCalcApproveWeekView, JmgProdStatusListPagePayrollCostDetails, JmgPayCountTable, JmgPayStatConfig, JmgOvertimeSlize, JmgPayAgreementOverride, JmgPayCountSum, JmgPayAdjustSetup, JmgPayAdjustCostType, JmgPayEmployee, JmgMESBreak, JmgPayAddTable, JmgPayAddTransSelectTransId, JmgPayrollCostDetailsPart, jmgProdStatusListPagePayrollCosts, JmgPayrollCostPart, JmgPayEvents, JmgTermRegPayStatSetup, JmgPayStatGroup, JmgPayAddTrans, JmgPayStatTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 1705903
ms.assetid: 427e01b3-4968-4cff-9b85-1717530f72e4
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2018-03-20
ms.dyn365.ops.version: AX 8.0.0
---

# Pay based on registrations

[!include [banner](../includes/banner.md)]

This article explains, in detail, how pay is calculated based on worker registrations. It includes examples that show how the various combinations of setup options that are available for the calculation affect the result. Here are some of the areas that will be covered:

- Flex time
- Overtime
- Breaks
- Switch codes
- Pay items
- Pay agreements
- Time and attendance calculation parameters
- Absence

## The use of flex time

Periods of flex time are set up in the time profiles that are used in Time and attendance. There are two flex profile types: **Flex+** and **Flex-**. When a worker registers time in a Flex+ period, the worker's flex balance is increased by the hours that were worked. The worker doesn't receive any compensation for the hours that were worked during the Flex+ period. However, the worker can take time off during the Flex- periods and be compensated with the hours from their flex balance. Therefore, time off during the flex periods is considered an absence by the system.

## Scenarios based on flex periods

The two scenarios that follow are based on a flex profile that represents a workday. For both scenarios, pay is calculated according to the flex period where the worker clocks in and out.

### Flex profile for one workday

| Profile type  | Start    | End      | Day     |
|---------------|----------|----------|---------|
| Over time     | 00:00 AM | 06:00 AM | Monday  |
| Flex+         | 06:00 AM | 07:00 AM | Monday  |
| Clock in      | 07:00 AM | 07:00 AM | Monday  |
| Standard time | 07:00 AM | 02:30 PM | Monday  |
| Flex-         | 02:30 PM | 03:30 PM | Monday  |
| Clock out     | 03:30 PM | 03:30 PM | Monday  |
| Over time     | 03:30 PM | 06:00 AM | Tuesday |

### Scenario 1: A worker registers clock-in during a Flex+ period and clock-out during a Flex- period

The worker's registrations for the day looks like this.

| Journal registration type | Start    | End      |
|---------------------------|----------|----------|
| Clock in                  | 06:30 AM | 06:30 AM |
| Production job            | 06:30 AM | 02:45 PM |
| Clock out                 | 02:45 PM | 02:45 PM |

The worker's registrations for the day are calculated and transferred to pay on the **Approve** page (**Time and attendance** &gt; **Review and approve** &gt; **Approve**). After the registrations have been calculated, the result of the calculation can be viewed on the **Times** tab. 

To understand this scenario, see the following fields.

| Flex + | Flex - | Time | Pay time |
|--------|--------|------|----------|
| 0.50   | 0.75   | 8.25 | 8.50     |

#### Calculation of Flex+

According to the flex profile, the time between 06:00 AM and 07:00 AM is a Flex+ period. Therefore, if the worker clocks in at 06:30 AM, they earn 0.5 hours. This amount of time is added to the worker's flex account.

#### Calculation of Flex-

According to the flex profile, the Flex- period starts at 02:30 PM and ends at 03:30 PM. Therefore, if the worker clocks out at 02:45 PM, the 45 minutes (0.75 hours) that remain in the Flex- period are registered as pay time, and the same amount of time is deducted from the worker's flex account. The 45 minutes are included in pay time because the worker will be granted pay for the remaining 45 minutes in the Flex- period. If the worker is absent during the Flex- period, the 45 minutes will be deducted from their flex account.

#### Calculation of Time

Time is calculated as the time between clock-in and clock-out, that is, 06:30 AM to 14:45 PM with equals 8.25 hours.

#### Calculation of Pay time

Pay time is the time that a worker is granted pay during. In this scenario, the worker is at work for 8.25 hours (**Time**). However, **Pay time** is calculated as 8.50 hours because the worker is granted pay during the Flex- period after they clocked out. The pay time equals the planned work hours because Flex+ time is added to the worker's flex account, not to the pay time. The absence time during the Flex- period is compensated for by the pay time and deducted from the worker's flex account.

| Time              | Registration type | Pay time (hours)      |
|-------------------|-------------------|-----------------------|
| 6:30 AM - 7:00 AM | Flex+             | 0                     |
| 7:00 AM – 2:45 PM | Standard time     | 7.75                  |
| 2:45 PM – 3:30 PM | Flex-             | 0.75 (Absence period) |
|                   | Total             | 8.50                  |

### Scenario 2: A worker works during the whole Flex- period and also works overtime

The worker's registrations for the day look like this.

| Journal registration type | Start    | End      |
|---------------------------|----------|----------|
| Clock in                  | 06:30 AM | 06:30 AM |
| Production job            | 06:30 AM | 05:00 PM |
| Clock out                 | 05:00 PM | 05:00 PM |

After you've calculated the journal registrations on the **Approve** page, you can view the calculation result on the **Times** tab. To understand this scenario, see the following fields.

| Flex + | Flex - | Time  | Pay time | Pay overtime |
|--------|--------|-------|----------|--------------|
| 0.50   | 0.00   | 10.50 | 10.00    | 1.50         |

#### Calculation of Flex+

According to the flex profile, the time between 06:00 AM and 07:00 AM is a Flex+ period. Therefore, if the worker clocks in at 06:30 AM, they earn 0.5 hours of Flex+ time on their flex balance.

#### Calculation of Flex-

Because the worker is working during the Flex- period, Flex- isn't calculated. Flex- is calculated only if the worker is absent during the Flex- period. From a payment perspective, if the worker works during the Flex- period, they are granted the pay rate that is defined for standard time. If the worker if is absent during the Flex- period, the 45 minutes are deducted from their flex account.

#### Calculation of Time

Time is calculated as the time between clock-in at 06:30 AM and clock-out at 05:00 PM, or 10.50 hours.

#### Calculation of Pay time

In this scenario, the worker works 10.50 hours (**Time**). However, **Pay time** is calculated as 10.00 hours because the worker isn't granted pay during the Flex+ period.

#### Calculation of Pay overtime

| Time               | Registration type | Pay time (hours) |
|--------------------|-------------------|------------------|
| 6:30 AM - 7:00 AM  | Flex+             | 0                |
| 7:00 AM – 2:30 PM  | Standard time     | 7.50             |
| 2:30 PM – 3:30 PM  | Flex-             | 1.00             |
| 3:30 PM – 05:00 PM | Overtime          | 1.50             |
|                    | Total             | 10.00            |

### Generation of pay items

Worker registrations for the day can be transferred from the **Approve** page. During the transfer process, pay items and transferred registrations are generated. Pay items represent a breakdown of pay time into standard time, overtime, paid break time, and so on.

To open the list of pay items, select **Time and attendance** &gt; **Review and approve** &gt; **Approve**. Then select **Inquiry** &gt; **Transferred registrations**.

The pay items are the basis for a worker's pay. You can generate a file that includes the information from the pay items and transfer that file to a payroll system.

As part of the transfer process, time and cost from production and project activities are transferred to production and project journals to account for the time and cost spend. The transferred registrations are the basis for time and cost price per hour for production orders and projects. You can open the transferred registrations by using the **Inquiry** menu on the **Approve** page.

For example, for scenario 2, the following pay items are generated.

| Wage type     | Pay type | Pay units | Rate  | Total cost |
|---------------|----------|-----------|-------|------------|
| Standard time | 1201     | 10.0      | 10    | 100        |
| Overtime      | 1301     | 1.50      | 5     | 7.50       |
|               |          |           | Total | 107.50     |

The pay item for standard time has a pay unit of 10 hours that covers standard time, Flex- time, and overtime. Standard time, Flex- time, and overtime are consolidated into one pay item because all the types are calculated as standard time, based on the default setting of a parameter on the **Calculation parameters** page (**Time and attendance** &gt; **Setup** &gt; **Calculation parameters**). The overtime is calculated on top of the standard time by using an additional rate of 5.

If you want to clearly distinguish standard time and overtime, so that the pay units for the pay types cover only the actual time spend on standard time and overtime, the pay units for standard time must be calculated as 8.50, and the pay units for overtime must be calculated as 1.50.

To configure the system to clearly distinguish standard time and overtime, you must exclude overtime from the standard time. You must also change the setup of the pay type for overtime so that the pay rate for overtime covers all payments for the hours that were spent on overtime.

### Exclude overtime from the standard time

On the **Calculation parameters** page, select **Overtime** as the profile specification type, and set the **Pay time** option to **No**, as shown here.

| Reg. specification | Profile specification type | Calculation   | Setting | Paid         | Setting |
|--------------------|----------------------------|---------------|-----|--------------|-----|
| Working time       | Overtime                   | Standard time | Yes | Pay time     | No  |
|                    |                            | Pay time      | Yes | Pay overtime | Yes |

After you adjust the calculation parameters, the following pay items are generated.

| Wage type     | Pay type | Pay units | Rate  | Total cost |
|---------------|----------|-----------|-------|------------|
| Standard time | 1201     | 8.50      | 10    | 85.0       |
| Overtime      | 1301     | 1.50      | 15    | 22.50      |
|               |          |           | Total | 107.50     |

> [!NOTE]
> The calculation parameters have a recommended standard setting. In general, you should be careful when you change these parameters. To restore the recommended standard settings, on the **Calculation parameters** page, select **Restore values**.

### Allow a deviation from the standard pay profiles

On the **Profiles** page (**Time and attendance** &gt; **Setup** &gt; **Time profiles** &gt; **Profiles**), you can set up profile types that include switch codes and breaks.

### Switch codes

You can use switch codes to allow workers to deviate from their profile type by changing a different profile type. For example, you can allow a worker to change from Flex+ time to overtime. A worker can add a switch code during registration, or you can assign the task of adding a switch code to the approver of the registrations.

Before a switch code can be used, you must define it as a type of indirect activity. You must then add the switch code to the time profile for the period where you want to allow a change of profile type. For example, follow these steps to create a switch code that allows the Flex+ period to be changed from 06:00 AM to 07:00 AM to overtime.

1. Create a switch code that is named **OTBCI (Convert flex to overtime before clock-in)**. Select **Time and attendance** &gt; **Manage indirect activities** &gt; **Indirect activities**.
2. In the **Switch code** column, add OTBCI to the Flex+ line in the time profile.
3. In the **Secondary** column, add the **Overtime** profile type.

Consider the following flex profile that represents a workday.

| Profile type  | Start    | End      | Day     |
|---------------|----------|----------|---------|
| Over time     | 00:00 AM | 06:00 AM | Monday  |
| Flex+         | 06:00 AM | 07:00 AM | Monday  |
| Clock in      | 07:00 AM | 07:00 AM | Monday  |
| Standard time | 07:00 AM | 02:30 PM | Monday  |
| Flex-         | 02:30 PM | 03:30 PM | Monday  |
| Clock out     | 03:30 PM | 03:30 PM | Monday  |
| Over time     | 03:30 PM | 06:00 AM | Tuesday |

Here are the worker's registrations for the day.

| Journal registration type | Start    | End      |
|---------------------------|----------|----------|
| Clock in                  | 06:30 AM | 06:30 AM |
| Production job            | 06:30 AM | 02:45 PM |
| Clock out                 | 05:00 PM | 05:00 PM |

The following pay items are generated after the transfer.

| Wage type     | Pay type | Pay units | Rate  | Total cost |
|---------------|----------|-----------|-------|------------|
| Standard time | 1201     | 8.50      | 10    | 85.0       |
| Overtime      | 1305     | 1.50      | 15    | 22.50      |
|               |          |           | Total | 107.50     |

On the **Approve** page, undo the transfer, and then use the **Switch code** menu to apply the **OTBCI** switch code. When you transfer the registrations a second time, the following pay items are generated.

| Wage type     | Pay type | Pay units | Rate  | Total cost |
|---------------|----------|-----------|-------|------------|
| Standard time | 1201     | 8.50      | 10    | 80.0       |
| Overtime      | 1305     | 2.00      | 15    | 30.0       |
|               |          |           | Total | 107.50     |

> [!NOTE]
> When you apply the switch code, overtime is increased by 0.5 hour, from 1.50 to 2.00. The 0.5 hour is the conversion of the Flex+ time that is registered, from 6:30 AM to 07:00 to overtime.

### Breaks

Breaks from work affect the calculation of worker pay. Breaks are defined as a type of indirect activity. They can be defined as either **Paid**, to allow the break to add to the worker's pay, or **Unpaid**, to prevent the break from adding to the worker's pay. A break can also be defined as either **Planned** or **Registered**.

#### Planned breaks

If a company has a fixed break time, such as a fixed break for lunch, the break can be predefined in the time profile. In this case, the worker doesn't have to register the break on the job card pages. Instead, the break is automatically accounted for when the worker's registrations are calculated on the **Approve** page.

#### Registered breaks

If a company doesn't use planned breaks, workers can register breaks during the workday. Registered breaks can be used, for example, if a worker is working against a flex time profile that has no defined clock-in and clock-out times. Registered breaks are a type of indirect activity. The worker registers the break on the **Job card** terminal page or on the **Job card** device page. On both these pages, the user can select the type of break in a list of predefined break activities.

#### Paid and unpaid breaks

Break activities can be set up as **Paid** or **Unpaid**. A paid break is included in the calculation of pay time, and the system uses the pay type that is defined in the pay agreement for the **Break** registration type.

### Example of a planned break

Consider the following time profile that includes an unpaid break for lunch.

| Profile type  | Start    | End      | Day     |
|---------------|----------|----------|---------|
| Over time     | 00:00 AM | 06:00 AM | Monday  |
| Flex+         | 06:00 AM | 07:00 AM | Monday  |
| Clock in      | 07:00 AM | 07:00 AM | Monday  |
| Standard time | 07:00 AM | 12:00 PM | Monday  |
| Break         | 12:00 PM | 12:30 PM | Monday  |
| Standard time | 12:30 PM | 02:30 PM | Monday  |
| Flex-         | 02:30 PM | 03:30 PM | Monday  |
| Clock out     | 03:30 PM | 03:30 PM | Monday  |
| Over time     | 03:30 PM | 06:00 AM | Tuesday |

Here are the worker's registrations for the day.

| Journal registration type | Start    | End      |
|---------------------------|----------|----------|
| Clock in                  | 06:30 AM | 06:30 AM |
| Production job            | 06:30 AM | 02:45 PM |
| Clock out                 | 05:00 PM | 05:00 PM |

After you've calculated the journal registrations on the **Approve** page, you can view the calculation result on the **Times** tab. To understand this scenario, see the following fields.

| Flex + | Flex - | Time  | Pay time | Non-paid break time | Pay overtime |
|--------|--------|-------|----------|---------------------|--------------|
| 0.50   | 0.00   | 10.50 | 9.50     | 0.5                 | 1.50         |

> [!NOTE] 
> The system calculated 0.5 hours of unpaid break time, and that time isn't part of the pay time.

### Example of a registered break

Consider the following time profile that doesn't include planned breaks.

| Profile type  | Start    | End      | Day     |
|---------------|----------|----------|---------|
| Over time     | 00:00 AM | 06:00 AM | Monday  |
| Flex+         | 06:00 AM | 07:00 AM | Monday  |
| Clock in      | 07:00 AM | 07:00 AM | Monday  |
| Standard time | 07:00 AM | 02:30 PM | Monday  |
| Flex-         | 02:30 PM | 03:30 PM | Monday  |
| Clock out     | 03:30 PM | 03:30 PM | Monday  |
| Over time     | 03:30 PM | 06:00 AM | Tuesday |

Here are the worker's registrations for the day.

| Journal registration type | Start    | End      |
|---------------------------|----------|----------|
| Clock in                  | 06:30 AM | 06:30 AM |
| Production job            | 06:30 AM | 05:00 PM |
| Break                     | 12:03 PM | 12:32 PM |
| Clock out                 | 05:00 PM | 05:00 PM |

When the registrations are calculated, the time for the activities is calculated.

| Journal registration type | Start    | End      | Time  |
|---------------------------|----------|----------|-------|
| Clock in                  | 06:30 AM | 06:30 AM |       |
| Production job            | 06:30 AM | 05:00 PM | 10.00 |
| Break                     | 12:03 PM | 12:32 PM | 0.50  |
| Clock out                 | 05:00 PM | 05:00 PM |       |

> [!NOTE]
> The time for the break runs in parallel with the time for the activity (a production job, in this example). This behavior is always used for break activities. When the registrations are calculated, the break time is subtracted from the activity time. In this case, the production job has a duration of 10.50 hours, but the time is calculated as 10 because 0.5 hours of break time are subtracted from the activity time.

After you've calculated the journal registrations on the **Approve** page, you can view the calculation result on the **Times** tab. To understand this scenario, see the following fields.

| Flex + | Flex - | Time  | Pay time | Non-paid break time | Pay overtime |
|--------|--------|-------|----------|---------------------|--------------|
| 0.50   | 0.00   | 10.50 | 9.50     | 0.5                 | 1.50         |

If the planned break had been paid instead of unpaid, the calculation result would look like this.

| Flex + | Flex - | Time  | Pay time | Paid break time | Pay overtime |
|--------|--------|-------|----------|-----------------|--------------|
| 0.50   | 0.00   | 10.50 | 10.00    | 0.5             | 1.50         |

### Pay items and paid breaks

When you transfer registrations on the **Approve** page, pay items are generated. A separate pay item is generated for paid breaks.

The pay rate for a paid break is determined by the pay type that is set up in the pay agreements for the break. Instead of using a pay type, you can set up the cost price per hour on the break for a defined date interval.

Consider the following time profile.

| Profile type  | Start    | End      | Day     |
|---------------|----------|----------|---------|
| Over time     | 00:00 AM | 06:00 AM | Monday  |
| Flex+         | 06:00 AM | 07:00 AM | Monday  |
| Clock in      | 07:00 AM | 07:00 AM | Monday  |
| Standard time | 07:00 AM | 02:30 PM | Monday  |
| Flex-         | 02:30 PM | 03:30 PM | Monday  |
| Clock out     | 03:30 PM | 03:30 PM | Monday  |
| Over time     | 03:30 PM | 06:00 AM | Tuesday |

Here are the worker's registrations for the day.

| Journal registration type | Start    | End      | Time |
|---------------------------|----------|----------|------|
| Clock in                  | 07:00 AM | 07:00 AM |      |
| Production job            | 07:00 AM | 03:00 PM | 7.5  |
| Break (Paid)              | 12:00 PM | 12:30 PM | 0.5  |
| Clock out                 | 03:00 PM | 03:00 PM |      |

For this example, the pay type for standard time is set to **1201**, and a pay rate of **10** is set up in the pay agreement. The paid break has a pay type of **1301** and a pay rate of **8**. When the registrations are transferred, the following pay items are generated.

| Wage type     | Pay type | Pay units | Rate |
|---------------|----------|-----------|------|
| Standard time | 1201     | 7.50      | 10   |
| Flex-         | 1201     | 0.50      | 10   |
| Break (Paid)  | 1301     | 0.50      | 8    |

## How the cost of paid breaks is allocated to projects and production orders

The hourly cost on project activities and production jobs can be set up so that it's determined either by the pay rates that are calculated in Time and attendance or by the cost categories that are defined for the activities.

To set up the cost category, select **Production control** &gt; **Setup** &gt; **Manufacturing execution** &gt; **Production order defaults**, and set the **Cost category** field to either **Yes** or **No**.

- **No** – Cost is calculated based on pay rates that are defined for Time and attendance registration types.
- **Yes** – Cost is calculated based on cost categories for production and project activities.

### Cost calculation based on pay rates that are calculated in Time and attendance

The following example shows how the hourly cost is calculated when the cost is set up so that it's calculated based on pay rates.

The hourly cost rate that is used for production orders and projects is calculated during the transfer process. To view the hourly rate per activity, open the **Approve** page in Time and attendance, and then select **Inquiry** &gt; **Transferred registrations**. You can find the hourly cost rate per registration on the **Cost prices** tab.

Consider the following registrations that use the same time profile as the previous example.

| Journal registration type | Start    | End      | Time |
|---------------------------|----------|----------|------|
| Clock in                  | 07:00 AM | 07:00 AM |      |
| Process (Order: 4711)     | 07:00 AM | 11:00 AM | 4    |
| Process (Order: 4712)     | 11:00 AM | 03:00 PM | 3.50 |
| Break (Paid)              | 12:00 PM | 12:30 PM | 0.50 |
| Clock out                 | 03:00 PM | 03:00 PM |      |

After the registrations are transferred, the following transferred registrations are generated.

| Registration type     | Time | Cost price per hour |
|-----------------------|------|---------------------|
| Clock-in              | 0.00 | 0.00                |
| Process (Order: 4711) | 4.00 | 10.00               |
| Process (Order: 4712) | 3.50 | 11.14               |
| Break (Paid)          | 0.50 | 0.00                |
| Clock out             | 0.00 | 0.00                |

The calculation of the cost price per hour for the paid break depends on a setting for the direct payroll costs. Select **Time and attendance** &gt; **Setup** &gt; **Time and attendance parameters**. On the **Cost price** tab, under **Direct payroll costs**, in the **Standard time** field, you can select **Yes**, **No**, or **Allocation**.

- **Yes** – This value is used for the preceding example. The cost is allocated to the production or project activity that runs in parallel with the paid break activity. In the example, this activity is the production job for order 4712. As you can see, the cost price per hour for the paid break is 0 (zero), and it's allocated to the job that runs in parallel with the break.

    The paid break has a duration of 0.5 hour, and the pay rate is 8. Therefore, the total cost for the paid break is 4. The total cost is then allocated to the 3.5-hour process job. Therefore, the paid break contributes 1.14 per hour to the cost (4 ÷ 3.5 = 1.14).

- **Allocation** – The paid break is equally distributed to the jobs that are registered for the day. If this value is used for the preceding example, the following transferred registrations are generated.

    | Registration type     | Time | Cost price per hour |
    |-----------------------|------|---------------------|
    | Clock-in              | 0.00 | 0.00                |
    | Process (Order: 4711) | 4.00 | 10.53               |
    | Process (Order: 4712) | 3.50 | 10.53               |
    | Break (Paid)          | 0.50 | 0.00                |
    | Clock out             | 0.00 | 0.00                |

    The total process time for the two production jobs is 7.5 hours, and the total cost of the paid break is 4. Therefore, the cost of the break is calculated as 0.53 (= 4 ÷ 7.5).

- **No** – The cost of the paid break doesn't increase the hourly cost of the process activities.

    | Registration type     | Time | Cost price per hour |
    |-----------------------|------|---------------------|
    | Clock-in              | 0.00 | 0.00                |
    | Process (Order: 4711) | 4.00 | 10.00               |
    | Process (Order: 4712) | 3.50 | 10.00               |
    | Break (Paid)          | 0.50 | 0.00                |
    | Clock out             | 0.00 | 0.00                |

## Absence

An absence code is used to register the period of a worker's absence. Like breaks and switch codes, an absence code is a type of an indirect activity. Absence time can be either planned or registered, and absence can be either legal or illegal. Examples of legal absence include a doctor's appointment, a seminar, or jury duty. Illegal absence is absence that has no good reason, such as when a worker is late for work. Usually, legal absence doesn't cause a deduction in a worker's pay, whereas illegal absence does cause a deduction.

### Planned absence

You can create planned absence for workers on the **Create planned absence** page (**Time and attendance** &gt; **Create planned absence**). There, the planned absence is registered as an absence job for a specified date and time interval.

The job is based on a query. Therefore, you can create planned absence for multiple workers, such as workers who belong to the same calculation group. If the planned absence is for a single worker, the registration can be entered from either the **Attendance** page or the **Time registration workers** page.

- To enter an absence registration from the **Attendance** page, select **Time and attendance** &gt; **Inquiries and reports** &gt; **Attendance** &gt; **Attendance**, and then select **Absence registration**.
- To enter an absence registration from the *<strong><em>Time registration workers</em></strong>* page, select <strong>Time and attendance</strong> &gt; <strong>Setup</strong> &gt; <strong>Time registration workers</strong>, and then, on the <strong>Time</strong> tab, under <strong>Time assignment</strong>, select <strong>Absence registrations</strong>.

You can use the **Planned absences** report to see an overview of planned absences for workers. To open this report, select **Time and attendance** &gt; **Inquiries and reports** &gt; **Absence reports** &gt; **Planned absences**.

### Registered absence

In general, workers are considered absent if they aren't at work for any period between their planned clock-in time and their planned clock-out time. If workers clock in later than planned, or if they clock out earlier than planned, they are prompted to select an absence code to indicate the reason for the absence. An absence code can be set up so that it's applicable to registration. Only applicable codes will be available for selection in the list.

## Scenarios based on various combinations of work hour registrations

The following scenarios show the pay items and entries for approval that are generated for workers based on their registrations. All the scenarios are based on the following time profile.

| Profile type  | Start    | End      | Day     |
|---------------|----------|----------|---------|
| Over time     | 00:00 AM | 06:00 AM | Monday  |
| Flex+         | 06:00 AM | 07:00 AM | Monday  |
| Clock in      | 07:00 AM | 07:00 AM | Monday  |
| Standard time | 07:00 AM | 02:30 PM | Monday  |
| Flex-         | 02:30 PM | 03:30 PM | Monday  |
| Clock out     | 03:30 PM | 03:30 PM | Monday  |
| Over time     | 03:30 PM | 06:00 AM | Tuesday |

### Scenario 1: The worker clocks in later than planned

The worker clocks in at 08:30 AM. Because their planned clock-in time is 07:00 AM, they are 1.50 hours late for work. Because the 1.50 hour is considered absence time, the worker is prompted to select an absence code. The worker leaves work at 03:30 PM, which is the planned clock-out time. When the worker's registrations are calculated and approved, the absence registration, together with the absence code that the worker selected at clock-in, appears for the time between 07:00 AM and 08:30 AM.

In the time profile, you can configure the **Clock-in** registration type so that there is a tolerance when workers are late for work. For example, if you set up a tolerance of 5, the worker is prompted for an absence code only if they clock in later than 07:05 AM.

In this case, because the worker doesn't have a good reason for being late for work, they select an absence code that is defined for illegal absence. An absence code is considered applicable to illegal absence if the setting for overtime deduction is enabled for the absence group that the absence code belongs to. To set the setting, select **Time and attendance** &gt; **Setup** &gt; **Groups** &gt; **Absence groups**, and then select the **Deduct overtime** check box.

Here is how the worker's registrations for the day appear on the **Approve** page after calculation.

| Journal registration type         | Start    | End      | Time |
|-----------------------------------|----------|----------|------|
| Absence (illegal - late for work) | 07:00 AM | 08:30 AM | 1.5  |
| Clock in                          | 08:30 AM | 08:30 AM |      |
| Production job                    | 07:30 AM | 03:30 PM | 7.0  |
| Clock out                         | 03:30 PM | 03:30 PM |      |

Here is the resulting pay item after the registrations are transferred.

| Wage type     | Pay type | Pay units | Rate |
|---------------|----------|-----------|------|
| Standard time | 1201     | 7.00      | 10   |

### Scenario 2: The worker clocks out before the planned clock-out time during a standard-time period

The worker clocks in at 07:00 AM and clocks out early at 01:00 PM. Because 01:00 PM is before planned clock-out at 03:30 PM, and 01:00 AM is in a standard-time period, the worker is prompted to select an absence code. The worker selects an absence code for a doctor's appointment, which is defined as legal absence. The pay rate for legal absence is defined in the pay agreements for the **Absence** registration type (**Time and attendance** &gt; **Setup** &gt; **Payroll** &gt; **Pay agreements**).

Here is how the worker's registrations for the day appear on the **Approve** page after calculation.

| Journal registration type              | Start    | End      | Time |
|----------------------------------------|----------|----------|------|
| Clock in                               | 07:00 AM | 07:00 AM |      |
| Production job                         | 07:00 AM | 01:00 PM | 4.0  |
| Clock out                              | 01:00 PM | 01:00 PM |      |
| Absence (legal – doctor's appointment) | 01:00 PM | 03:30 PM | 3.5  |

Here is the resulting pay item after the registrations are transferred.

| Wage type     | Pay type | Pay units | Rate |
|---------------|----------|-----------|------|
| Standard time | 1201     | 7.50      | 10   |

### Scenario 3: The worker clocks out before the planned clock-out time during a Flex- period

The worker clocks in at 07:00 AM and clocks out at 02:15 PM, which is in the planned Flex- period. The time between the actual clock-out time and the planned clock-out time isn't considered absence, and the worker isn't prompted to select an absence code. The amount is deducted from the worker's flex account, and the worker is granted pay during the remaining part of the Flex- period, from 02:15 to 03:30 PM.

Here is how the worker's registrations for the day appear on the **Approve** page after calculation.

| Journal registration type | Start    | End      | Time |
|---------------------------|----------|----------|------|
| Clock in                  | 07:00 AM | 07:00 AM |      |
| Production job            | 07:00 AM | 02:15 PM | 7.25 |
| Clock out                 | 02:15 PM | 02:15 PM |      |

Here is the resulting pay item after the registrations are transferred.

| Wage type     | Pay type | Pay units | Rate |
|---------------|----------|-----------|------|
| Standard time | 1201     | 8.50      | 10   |

### Scenario 4: The worker clocks in late and clocks out after the planned clock-out time during an overtime period

The worker clocks in late at 09:30 AM and then, to compensate for their late attendance, they work overtime and clocks out at 05:00 PM. Because the worker came in late and compensated by working longer, the company doesn't want to grant the worker overtime pay for the hours that they worked between the planned clock-out at 03:30 PM and their actual clock-out at 05:00 PM, even though this period is defined as overtime in the time profile.

To handle this scenario, the absence code can be set up to reduce overtime hours by any hours of illegal absence that the worker has on the same day. Select **Time and attendance** &gt; **Setup** &gt; **Groups** &gt; **Absence groups**, and select the **Deduct overtime** check box to deduct overtime from hours of illegal absence.

Here is how the worker's registrations for the day appear on the **Approve** page after calculation.

| Journal registration type         | Start    | End      | Time |
|-----------------------------------|----------|----------|------|
| Absence (illegal - late for work) | 07:00 AM | 09:30 AM | 1.5  |
| Clock in                          | 09:30 AM | 09:30 AM |      |
| Production job                    | 09:30 AM | 05:00 PM | 7.5  |
| Clock out                         | 05:30 PM | 05:30 PM |      |

If the **Deduct overtime** check box is selected for the selected absence code, the overtime payment is deducted by the hours that the worker was illegally absent. In this case, the following pay items are generated after the registrations are transferred.

| Wage type     | Pay type | Pay units | Rate |
|---------------|----------|-----------|------|
| Standard time | 1201     | 9.00      | 10   |
| Overtime      | 1301     | 0.5       | 15   |

Here, the 1.5 hours of illegal absence, from 07:00 AM to 09:30 AM, deduct the 2.0 hours of overtime, from 03:30 PM to 05:30 PM. The result of the registration is 1.5 hours of standard time and 0.5 hours of overtime.

By contrast, if the **Deduct overtime** check box is cleared for the selected absence code, the overtime payment is granted to the worker, even though they were late and had an illegal absence. In this case, the following pay items are generated after the registrations are transferred.

| Wage type     | Pay type | Pay units | Rate |
|---------------|----------|-----------|------|
| Standard time | 1201     | 7.50      | 10   |
| Overtime      | 1301     | 2.0       | 15   |

### Scenario 5: The worker clocks out before the planned clock-out time and can convert the absence period to a Flex- period

The following example shows how a worker's flex account can be reduced by converting the absence period to a Flex- period.

The worker clocks in at 07:00 AM and clocks out at 01:00 PM. The worker has an agreement that they can go home for the weekend if they deduct these hours from their flex account. When the worker clocks out at 01:00 PM, they are prompted to select an absence code, because the period of absence for the remaining part of the workday that is affected isn't in a planned Flex- period. To convert the remaining part of the workday to a Flex- period, the worker can select an absence code that is set up to reduce their flex account.

To reduce the balance of flexible hours for workers who register absence on a workday, select **Time and attendance** &gt; **Setup** &gt; **Groups** &gt; **Absence groups**, and select the **Reduce flex** check box.

Here is how the worker's registrations for the day appear on the **Approve** page before calculation.

| Journal registration type | Start    | End      | Time |
|---------------------------|----------|----------|------|
| Clock in                  | 07:00 AM | 07:00 AM |      |
| Production job            | 07:00 AM | 01:00 PM | 6.0  |
| Clock out                 | 01:00 PM | 01:00 PM |      |

If the worker selects an absence code for illegal absence, here is how the resulting pay item will look after the registration is transferred.

| Wage type     | Pay type | Pay units | Rate |
|---------------|----------|-----------|------|
| Standard time | 1201     | 6.00      | 10   |

If the worker selects an absence code for legal absence, and the absence code is set up to reduce their flex account, here is how the resulting pay items will look after the registrations are transferred.

| Wage type     | Pay type | Pay units | Rate |
|---------------|----------|-----------|------|
| Standard time | 1201     | 8.50      | 10   |

In this case, the worker's flex balance is reduced by the hours between the actual clock-out time and the planned clock-out time (that is, the 2.5 hours from 01:00 PM to 03:30 PM).

> [!NOTE]
> We don't recommend that you select both the **Deduct flex** check box and the **Deduct overtime** check box for an absence code, because this setup will deduct the illegal hours from the worker's overtime hours and at the same time reduce the worker's flex account.

### Scenario 6: There is no planned absence for the day and no worker attendance for the day

If the worker doesn't show up for work on a workday, and there is no planned absence for the worker on that day, a default absence code is used for the calculation of the worker's registrations. To define default absence codes, select **Time and attendance** &gt; **Time and attendance parameters**. You can then select an absence code in the following fields:

- Auto insert Flex-
- Auto insert absence

When the daily registrations are calculated for a worker who is enabled for flexible hours, the absence code that is specified in the **Auto insert flex-** field is used as a default absence code. If the worker isn't enabled for flexible hours, the absence code that is specified in the **Auto insert absence** field is used. If a company has a combination of workers who are enabled for flexible hours and workers who aren't enabled for flexible hours, both parameters must be set up.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
