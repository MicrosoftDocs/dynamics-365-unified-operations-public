---
# required metadata

title: Flex groups
description: This article describes how flex groups are used in Time and attendance.
author: johanhoffmann
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: JmgFlexGroup, JmgFlexCorrection
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
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 8.0.0
---

# Flex groups

[!include[banner](../includes/banner.md)]

Flexible working hours let companies minimize payments for overtime by offering workers extra time off during periods when the workload is low. This feature is relevant, for example, in segments that experience seasonal changes in workload.

You can use flex groups to set the following rules and principles for a worker's flexible hours:

- Rules for flex regulations
- Principle for calculating the worker's flex balance

## Set up flexible working hours in flex groups

- Select **Time and attendance** \> **Setup** \> **Groups** \> **Flex groups** to set up flex groups for flexible hours.

## Associate workers with flex groups

- Select **Time and attendance** \> **Setup** \> **Time registration workers**.

## Rules for flex regulations

You can use rules for flex regulations to define flex limits, or the minimum and maximum number of hours that are allowed in the worker's flex account. The flex limits are set up on the flex group. When the flex limits are exceeded, a worker's flex balance and pay can be adjusted.

If a worker's allowed flex minimum is exceeded (that is, if the number of hours in the flex account is below the specified minimum), you can use these methods to adjust the worker's flex balance by making a flex regulation:

- The worker's flex account can be adjusted to the specified allowed minimum, but without deducting the worker's pay for the number of hours that the flex account is below the allowed minimum.
- The worker's pay can be deducted for the number of hours that the flex account is below the allowed minimum. This deduction is done by generating pay items for a specific pay type that have a negative or positive pay unit.

If the worker's allowed flex maximum is exceeded, you can use these methods to adjust the worker's flex balance by making a flex regulation:

- The worker's flex account can be adjusted back to the specified allowed maximum, but without compensating the worker's pay for the number of hours that the worker worked above the allowed maximum.
- The number of hours that the worker worked above the allowed maximum can be converted to pay. This conversion is done by generating pay items for a specific pay type.

You can adjust a flex balance at the following times:

- When a payment file that is based on payroll data is exported by using the **Transfer pay** job. The payroll data is generated when you transfer the worker's registration from the **Approve** page.
- When the **Adjust flex balance** job is processed.

> [!NOTE]
> Flex regulations don't occur during the daily approval and transfer of worker registrations on the **Approve** page.

## Principle for calculating a worker's flex balance

The principle for calculating the hours that the worker's flex balance are adjusted by is set up on the flex group. Select **Time and attendance** \> **Setup** \> **Groups** \> **Flex groups**. 

The following two principles can be used:

- **Time** – The worker's flexible hours are calculated only from the worker's registered time for the day. When the worker's daily registrations are calculated, the number of Flex+ and Flex- hours for the day is calculated from the Flex+ and Flex- zones that are defined in the worker's time profile.
- **Pay types** – The worker's flexible hours are calculated based on earnings of the pay types for Flex+ and Flex- that are defined in the worker's pay agreement. The pay agreement is associated with the time registration worker. You might want to use pay types to manage flex accounts if, for example, you want to increase a worker's flex account by a specific factor in one or more flex zones.

### Scenario 1: Adjusting a worker's pay and flex account because the allowed flex minimum is exceeded

A worker who can work flexible hours has a negative flex account.

- **Flex account:** -4

The worker is associated with a flex group that has the following configuration:

- **Flex minimum:** -0.5
- **Minimum pay type:** 1302
- **Pay type factor:** -1.00

As the difference between the worker's flex account and the allowed flex minimum indicates, the worker has exceeded the allowed flex minimum by 3.5 hours.

When the payroll administrator transfers the worker's pay data by running the **Transfer to pay** or **Flex adjustment** job, the following adjustments are made:

- The worker's flex account is adjusted by 3.5 hours. Therefore, the flex balance of -4.0 hours becomes adjusted to the worker's allowed flex minimum of -0.5 hours.
- A pay item for pay type 1302 is created. This pay item has a pay unit of -3.5 hours that will be deducted from the worker's pay. In this case, the pay unit is a negative number, because the positive adjustment of 3.5 hours is multiplied by the negative pay type factor of -1.0 that is defined on the flex group. This pay item will be part of the pay file that is generated by the **Transfer to pay** job.

### Scenario 2: Adjusting a worker's pay and flex account because the allowed flex maximum is exceeded

A worker who can work flexible hours has a positive flex account.

- **Flex account:** 6

The worker is associated with a flex group that has the following configuration:

- **Flex maximum:** 2.0
- **Minimum pay type:** 1302
- **Pay type factor:** -1.0

As the difference between the worker's flex account and their allowed flex maximum indicates, the worker has exceeded their allowed flex maximum by 4.0 hours.

When the payroll administrator transfers the worker's pay data by running the **Transfer to pay** or **Flex adjustment** job, the following adjustments are made:

- The worker's flex account is adjusted by -4.0 hours. Therefore, the flex balance of 6.0 hours becomes adjusted to the worker's allowed flex maximum of 2.0 hours.
- A pay item for pay type 1302 is created. This pay item has a pay unit of 4.0 hours that will be added to the worker's pay. In this case, the pay unit is a positive number, because the negative adjustment of 4.0 hours is multiplied by the negative pay type factor of -1.0 that is defined on the flex group. This pay item will be part of the pay file that is generated by the **Transfer to pay** job.

### Scenario 3: Managing a worker's flex balance based on pay types

As we explained earlier, flex accounts can be managed based either on the time that is registered in the Flex+ and Flex- zones that are defined the worker's time profile, or on the pay types that are defined in the worker's pay agreements. If pay types are used, a worker's flex account is adjusted by the pay items that are generated when you transfer the worker's registration from the **Approve** page. You might want to use pay types to manage flex accounts if, for example, you want to increase a worker's flex account by a specific factor in one or more flex zones.

This scenario uses the following flex profile that represents a workday.

| Profile type  | Start    | End      |
|---------------|----------|----------|
| Flex+         | 12:00 AM | 08:00 AM |
| Clock in      | 08:00 AM | 08:00 AM |
| Flex-         | 08:00 AM | 09:00 AM |
| Standard time | 09:00 AM | 11:30 AM |
| Paid break    | 11:30 AM | 12:00 PM |
| Flex-         | 12:00 PM | 04:00 PM |
| Clock out     | 04:00 PM | 04:00 PM |
| Flex+         | 04:00 PM | 12:00 AM |

In this case, you want to be able to manage the worker's flex balance based on pay types. Therefore, you must set the **Based on pay types** option to **Yes** on the worker's flex group.

To account for the flexible hours, you must also define a new pay type. For this scenario, the pay type is named **FlexCnt**.

| Pay type | Description  |
|----------|--------------|
| FlexCnt  | Flex counter |

Next, follow these steps to set up a pay type and add lines of the new type to a pay profile.

1. Select **Time and attendance** \> **Setup** \> **Groups** \> **Flex groups**, and then select **New**.
2. In both the **Flex+** field and the **Flex-** field, specify the new pay type, **FlexCnt**.
3. Select **Time and attendance** \> **Setup** \> **Pay agreements**, and then select **Agreement lines**.
4. For **Monday**, for the **Flex+** profile type, add the following three lines.

    | Pay type | Description  | From time | To time  | Minimum | Maximum | Factor |
    |----------|--------------|-----------|----------|---------|---------|--------|
    | FlexCnt  | Flex counter | 12:00 AM  | 06:00 PM | 00.00   | 00.00   | 1.00   |
    | FlexCnt  | Flex counter | 06:00 PM  | 12:00 AM | 00.00   | 02.00   | 1.50   |
    | FlexCnt  | Flex counter | 06:00 PM  | 12:00 AM | 02.00   | 06.00   | 2.00   |

    > [!NOTE]
    > Each line is used for a different time interval and has a different factor. The flexible hours that the worker works in a time interval are multiplied by the factor for that line. For example, hours that are worked from 06:00 PM to 08:00 PM are multiplied by 1.50. The factor is specified in the **Factor** field on the **General** tab of the **Pay agreement lines** page.

The worker enters the following registrations for the day.

| Journal registration type | Start    | End      |
|---------------------------|----------|----------|
| Clock in                  | 07:00 AM | 07:00 AM |
| Production job            | 07:00 AM | 09:00 PM |
| Clock out                 | 09:00 PM | 09:00 PM |

The amount that must be paid is calculated on the **Approve** page, based on the worker's registration. After the registration is calculated, you can view the result on the **Times** tab. For this scenario, you're interested in the following fields.

| Flex + | Flex - | Time  | Pay time |
|--------|--------|-------|----------|
| 6.00   | 0.00   | 13.50 | 08.00    |

The amount of Flex+ time is six hours, and the calculation is based on the flex zones in the time profile. This amount consists of one hour of Flex+ time from 07:00 AM to 08:00 AM and five hours of Flex+ time from 04:00 PM to 09:00 PM.

When you transfer the registrations, you will notice that the amount of Flex+ time is changed from 6.0 hours to 8.0 hours.

| Flex + | Flex - | Time  | Pay time |
|--------|--------|-------|----------|
| 8.00   | 0.00   | 13.50 | 08.00    |

This change occurs after the transfer because the flexible hours have been calculated based on pay types instead of time. The following table shows how the eight hours are calculated.

| From     | To       | Time | Factor    | Flex account |
|----------|----------|------|-----------|--------------|
| 07:00 AM | 08:00 AM | 1    | 1         | 1            |
| 04:00 PM | 06:00 PM | 2    | 1         | 2            |
| 06:00 PM | 08:00 PM | 2    | 1.5       | 3            |
| 08:00 PM | 09:00 PM | 1    | 2         | 2            |
|          |          |      | **Total** | **8**        |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
