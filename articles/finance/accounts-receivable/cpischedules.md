---
# required metadata

title: Consumer price index schedule
description: This topic explains how to create the list of consumer price index (CPI) schedules that you obtain from the internet to help determine the escalation charge in Subscription billing. You can create many CPI schedules based on the latest dates and statistics. This topic also explains how the consumer price index calculation works with an example.
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
ms.reviewer: roschlom
ms.search.scope: Core, Operations
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
[!include [preview banner](../includes/preview-banner.md)]

Modules > Subscription billing > Recurring contract billing > Setup > Consumer price index schedule

This topic explains how to create, delete, review and process Consumer price index (CPI) schedules. A Consumer price index schedule can be used to determine the prices for consumer goods and services that you add as billing schedule lines. A Consumer price index schedule can then be used with escalation and discount pricing on a billing schedule or manually processed to update the billing amounts on billing schedules. Consumer price index schedules can be manually entered or imported using the Consumer price index schedule composite entity.

To add a Consumer price index schedule select **New**. Enter a unique **Consumer price index schedule** and a **Description**. Select **Add** under **Consumer price index schedule** tab. In **Consumer price index date**, add a date on which the Consumer price index schedule becomes active. Type the **Consumer price index schedule** value. Select **Save**. 

To delete a Consumer price index schedule date, select one or more lines that you want to delete and select **Remove**. To delete the entire Consumer price index schedule select **Delete** in Action pane. If the Consumer price index schedule is associated with any billing schedule, you cannot delete it.

Select the **Process** button in the Action pane to update the billing schedules that use the selected Consumer price index schedule. The billing schedule prices will update using the latest consumer price index dates and schedule amounts. The **Date last run** and **Last run by user** fields are read-only and will update after processing. The **Consumer price index process** fasttab displays the Billing schedule number, Item number, Billing start date, Billing end date, Escalation date and Escalation frequency that were updated during the processing. 

Once Consumer price index schedules are setup they can be used for Escalation and discount price changes on billing schedules.

---

# Consumer price index calculation

In this example, the period is January 01, 2020, to December 31, 2022. On January 01, 2021, the current Consumer price index is 110.5, and the base Consumer price index rate is 105.65 (the Consumer price index value at the time the contract starts).

In the **Recurring contract billing parameters** page, you set **Consumer price index index calculation** to **Base Consumer price index**.

The escalation amount is calculated with the initial amount of $1000: 
* 1000 + (110.5–105.65)/105.65*1000 = 1045.91

Similarly, the escalation amount for period January 01, 2022, where the Consumer price index is 114.25 is calculated as follows:
* 1000 + (114.25-105.65)/105.65*1000 = 1081.40

In the **Recurring Contract Billing Parameters** page, you set **Consumner price index calculation** to **Prior consumer price index**.

The period is January 01, 2020, to December 31, 2022. The current consumer price index on January 01, 2021, is 110.5, and the base consumer price index rate is 105.65 (the consumer price index value at the time the contract starts).

The first escalation amount is calculated with the amount of $1000:
* 1000 + (110.5–105.65)/105.65*1000 = 1045.91

Similarly, the escalation amount for period January 01, 2022, where consumer price index is 114.25 is calculated as follows:
* 1045.91 + (114.25-110.5)/110.5*1045.91 = 1081.40

**Note:** 
* The escalation process uses the latest consumer price index value, regardless of the index date.   
For example,  if the escalation happens in September, but the latest consumer price index value is for July, the July index is used. No adjustments are made after the September index is entered.

## Prorated Escalation

If the escalation happens in the middle of a billing period, the amount will be prorated. For example, the billing period is August 01, 2020, to July 31, 2021. The consumer price index value is 244 on consumer price index date September 01, 2019, and 250 on consumer price index date September 01, 2020. If the previous rate is 1000, the following equations show how the billing amount for this period is calculated:
* Consumer price index changes = (250 – 244)/244 = 2.459%
* Current Rate = 1000*2.459% = 1024.59
* Number of days @ current rate = July 31, 2021 – September 01, 2020 = 334
* Previous Rate = 1000
* Number of days @ previous rate = August 31, 2020 – August 01, 2020 = 31
* Total number of days in the billing period = July 31, 2021 – August 01, 2020 + 1 = 365
* The billing amount for this period = 1000*31/365 + 1024.59*334/365 = 1022.50

## Escalation Using Consumer price index and %

Escalations can also be done by consumer price index. The consumer price index + 3% escalation starts on January 01, 2020, with Annual frequency. Amount billed for January 01, 2019 to December 31, 2020, is 4000. The billing period to be escalated is January 01, 2020 to December 31, 2020. The consumer price index value is 205.3 on the consumer price index date December 01, 2018, and also is 219.6 on the consumer price index date December 01, 2019. If previous rate is 4000, the following equations show the billing amount for this period is calculated:
* Consumer price index changes = (219.6 – 205.3)/205.3 = 6.965%
* Current Rate = 4000*6.965% - 4000 = 278.60
* Percentage changes = 4000*1.03 - 4000 = 120
* Billing amount = 4000 + 278.6 + 120 = 4398.6
