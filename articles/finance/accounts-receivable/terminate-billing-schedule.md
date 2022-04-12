---
# required metadata

title: Terminate billing schedules
description: This topic explains how to terminate billing schedules and billing schedule lines in Subscription billing.
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
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Terminate billing schedules

[!include [banner](../includes/banner.md)]

This topic explains how to terminate billing schedules and billing schedule lines in Subscription billing. When you terminate a billing schedule, it must have a status of **Active**. It can't have a status of **On hold**. Likewise, when you terminate a billing schedule line, it must have a status of **Active**. The header section of the billing schedule isn't affected when you terminate a billing schedule line.

To terminate a billing schedule or billing schedule line, go to one of the following places:

- The **All/Active billing schedules** list page
- A specific billing schedule on the **All billing schedules** page
- A specific billing schedule line on the **All billing schedules** page

> [!NOTE]
> If you want to terminate several billing schedules at the same time, use the **Mass termination processing** page.

## Terminate a billing schedule or line

To terminate a billing schedule or billing schedule line, follow these steps.

1. Select a billing schedule or a billing schedule line, and then select **Terminate**. 
2. Set the **Termination date**, **Termination type**, and **Reason code** fields.
3. Set the **Credit option** field to **Issue credit**.
4. Select **Terminate**.

The status of the billing schedule changes, based on the termination type that you selected. If you selected **Bill remaining** as the termination type, the status of all lines in the billing schedule is **Last billing**. The status of the billing schedule remains **Active** until the last invoice is processed. After the last invoice is processed, the status is updated to **Terminated**. If you selected **Adjust schedule** as the termination type, the status of the billing schedule is immediately updated to **Terminated**.

## Terminate a billing schedule or line and apply a refund

To terminate a billing schedule or billing schedule line and apply a refund, follow these steps.

1. Select a billing schedule or a billing schedule line, and then select **Terminate**.
2. Set the **Termination date**, **Termination type**, **Reason code**, and **Credit option** fields.
3. Select **Terminate with refund**. The **Mass termination processing** page appears and is filtered so that it shows the billing schedule.
4. Select **View preview** to view the billing schedules lines, and then select **Process**.

After the credit is processed, open the **View billing detail** page to review the credit that was applied to the billing schedule. If the credit amount is more than 0 (zero), all future unbilled lines are deleted and replaced with billing detail lines that show the negative amounts for the credit that was applied to the billing schedule.

### View example

A billing schedule has the following information:

- The start date is January 1, 2020.
- The end date is December 31, 2020.
- The billing period amount is 100.00 per month.
- Invoices have been created for billing periods from January through July.
- The contract termination date is June 15, 2020.

When the credit adjustment is processed, all future billing periods (August through December) are removed from the **View billing detail** page. A credit adjustment line is added after the July billing period:

- June 16–July 31, with a credit amount of 150.00

If the unbilled revenue feature is used, the **Unbilled revenue journal entry audit** page is updated with the termination entry.

## Terminate a billing schedule or line without applying a credit

To terminate a billing schedule or billing schedule line without applying a credit, follow these steps.

1. Select a billing schedule or a billing schedule line, and then select **Terminate**.
2. Set the **Termination date** field.
3. Set the **Termination type** field to **No adjustment**. The **Credit option** field is automatically set to **No credit**.
3. Set the **Reason code** field.
4. In the **Termination notes** field, enter any notes that are required.
5. Select **Terminate**. 

When the termination is processed, all billing detail lines after the termination date are removed. (These lines include the line that contains the termination date.) Invoices can't be created for the terminated lines. If the termination is removed, all terminated lines are added back to the **View billing details** page and become available for invoicing.

## Fields

The **View billing details** page contains the following fields.

| Field | Description |
|-------|-------------| 
| Termination date | Select the date when you want to terminate a billing schedule or billing schedule line. |
| Termination type | <p>Select the termination type:</p><ul><li>**Adjust schedule** – Cut off the billing periods for the line at the termination date, and change the status of the line to **Last billing**. If a deferral schedule exists for the line item, it's adjusted by reversing the amount that must no longer be recognized. If the billing start date is after the termination date, the remaining billing periods are removed.</li><li>**Bill remaining** – Add any remaining amount for the billing period to the termination period, and change the status of the line to **Last billing**. If a deferral schedule exists for the line item, the deferral end date is updated. If the billing start date is after the termination date, the total amount of all remaining billing periods is added to the billing period, and the remaining billing periods are removed.</li><li>**No adjustment** – Terminate the billing periods for the line on the specified termination date. No adjustments are made. When this termination type is selected, the **Credit option** field is set to **No credit**, and the **Prorate daily** field is set to **No**. Both those fields then become read-only and can't be changed.</li></ul> |
| Credit option | <p>Select how the credit is applied when you terminate a billing schedule line:</p><ul><li>**Credit adjustment** – Create a credit adjustment for a billing schedule when a line is terminated. The credit adjustment appears in a future billing period for the billing schedule. The adjustment also automatically adjusts the invoice amount for the next billing period until the credit has finished being applied to the billing schedule.</li><li>**Issue credit** – Create a credit note when a billing schedule or billing schedule line is terminated.</li><li>**No credit** – Don't create a credit adjustment or a credit note when a billing schedule or billing schedule line is terminated. This option is available only when you use a termination of the **No adjustment** type to terminate a billing schedule.</li></ul><p>The default option is from the **Recurring contract billing parameters** page.</p> |
| Reason code | Select the reason code for the termination. |
| Reason description | The description of the reason code. |
| Termination notes | Enter any notes about the termination. |

<!--## Additional information-->
