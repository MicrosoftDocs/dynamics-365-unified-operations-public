---
# required metadata

title: Consumer price index schedule
description: This article explains how to create the list of consumer price index (CPI) schedules that you obtain from the internet to help determine the escalation charge in Subscription billing. 
author: JodiChristiansen
ms.date: 11/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc

# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Consumer price index schedule

[!include [banner](../includes/banner.md)]

This article explains how to create, delete, review, and process consumer price index (CPI) schedules. A CPI schedule can be used to determine the prices for consumer goods and services that you add as billing schedule lines. The CPI schedule can then be used with escalation and discount pricing on a billing schedule, or it can be manually processed to update the billing amounts on billing schedules. You can manually enter CPI schedules, or you can import them by using the CPI schedule composite entity.

To add a CPI schedule, follow these steps.

1. On the **Consumer price index schedule** page, select **New**.
2. In the **Consumer price index schedule** field, enter a unique name.
3. In the **Description** field, enter a description.
4. On the **Consumer price index schedule** tab, select **Add**.
5. In the **Consumer price index date** field, specify the date when the new CPI schedule becomes active.
6. In the **Consumer price index schedule** field, enter the name that you entered in step 2.
7. Select **Save**.

To delete a CPI schedule date, follow these steps.

1. On the **Consumer price index schedule** page, select one or more lines that you want to delete, and then select **Remove**.
2. To delete the whole CPI schedule, on the Action Pane, select **Delete**. You can't delete the selected CPI schedule if it's associated with any billing schedule.
3. On the Action Pane, select **Process** to update the billing schedules that use the selected CPI schedule. The latest CPI dates and schedule amounts will be used to update the billing schedule prices.
4. On the **Consumer price index process** FastTab, review the updated **Billing schedule number**, **Item number**, **Billing start date**, **Billing end date**, **Escalation date**, and **Escalation frequency** fields.

After CPI schedules are set up, they can be used for escalation and discount price changes on billing schedules.

## CPI calculation

For these examples, the period is from January 1, 2020, through December 31, 2022. The base CPI rate (the CPI value when the contract starts) is 105.65. On January 1, 2021, the current CPI is 110.5. On January 1, 2022, the current CPI is 114.25. The initial amount is $1,000.

**Example 1**

On the **Recurring contract billing parameters** page, you set the **Consumer price index calculation** field to **Base Consumer price index**.

For the period January 1, 2021, the first escalation amount is calculated in the following way, based on the initial amount:

1,000 + (110.5 – 105.65) &divide; 105.65 &times; 1,000 = 1,045.91

For the period January 1, 2022, the escalation amount is calculated in the following way:


1,045.91 + (114.25 – 105.65) &divide; 110.5 &times; 1,045.91 = 1,127.31

**Example 2**

On the **Recurring contract billing parameters** page, you set the **Consumer price index calculation** field to **Prior consumer price index**.

For the period January 1, 2021, the first escalation amount is calculated in the following way, based on the initial amount:

1,000 + (110.5 – 105.65) &divide; 105.65 &times; 1,000 = 1,045.91

For the period January 1, 2022, the escalation amount is calculated in the following way, based on the first escalation amount:

1,045.91 + (114.25 – 105.65) &divide; 105.65 &times; 1,000 = 1,081.40

> [!NOTE]
> The escalation process always uses the latest CPI value, regardless of the index date. For example, if the escalation is in September, but the latest CPI value is for July, the July index is used. No adjustments are made after the September index is entered.

## Prorated escalation

If the escalation occurs in the middle of a billing period, the amount is prorated. For example, the billing period is from August 1, 2020, through July 31, 2021. On the CPI date September 1, 2019, the CPI value is 244. On the CPI date September 1, 2020, this CPI value is 250. If the previous rate is 1,000, the following formulas are used to calculation the billing amount for the period:

* *CPI changes* = (250 – 244) &divide; 244 = 2.459%
* *Current rate* = 1,000 &times; 2.459% = 1,024.59
* *Number of days at the current rate* = July 31, 2021 – September 1, 2020 = 334
* *Previous rate* = 1,000
* *Number of days at the previous rate* = August 31, 2020 – August 1, 2020 = 31
* *Total number of days in the billing period* = July 31, 2021 – August 1, 2020 + 1 = 365
* *Billing amount for this period* = (1,000 &times; 31 &divide; 365) + (1,024.59 &times; 334 &divide; 365) = 1,022.50

## Escalation that uses the CPI and percentage

Escalations can be done by using the CPI. The CPI plus a 3-percent escalation starts on January 1, 2020, and it has an annual frequency.

- The amount that is billed for January 1, 2019, through December 31, 2020, is 4,000.
- The billing period that will be escalated is January 1, 2020, through December 31, 2020.
- On the CPI date December 1, 2018, the CPI value is 205.3. On the CPI date December 1, 2019, the CPI value is 219.6.

If the previous rate is 4,000, the billing amount for this period is calculated in the following way:

- *CPI changes* = (219.6 – 205.3) &divide; 205.3 = 6.965%
- *Current rate* = (4,000 &times; 6.965%) – 4000 = 278.60
- *Percentage changes* = (4,000 &times; 1.03) – 4,000 = 120
- *Billing amount* = 4,000 + 278.6 + 120 = 4,398.6
