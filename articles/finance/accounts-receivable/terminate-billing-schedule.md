---
# required metadata

title: Terminate schedule lines
description: This topic lists the steps for terminating a billing schedule line in Subscription billing. 
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

# Terminate billing schedules

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Modules > Subscription billing > Recurring contract billing > Billing schedules > All or Active billing schedules > [select a billing schedule line] > [click Terminate]

Modules > Subscription billing > Recurring contract billing > Billing schedules > All or Active billing schedules > [click a billing schedule] > [click Terminate] 

Modules > Subscription billing > Recurring contract billing > Billing schedules > All or Active billing schedules > [click a billing schedule] >[select a billing schedule line] > [click Terminate] 

This topic lists the steps for terminating a billing schedule line in Subscription billing. When you terminate a billing schedule, the billing schedule must be **Active**. It can't have a status of **On hold**. Also, the line must have a status of **Active** when you terminate a billing schedule line. The header section of the billing schedule is not affected when terminating a billing schedule ine. 

You can terminate a billing schedule or billing schedule line in one of the following ways: 
- From the **All/Active Billing Schedules** list 
- From the billing schedule displayed on the **All billing schedules page
- From a specific billing schedule line on the **All billing schedules page

**Note:** If you want to terminate several billing schedules simultaneously, use the **Mass termination processing** page. 


## Terminate a Billing Schedule or Line

To terminate a billing schedule or billing schedule line, follow these steps: 
1. Select a billing schedule or a billing schedule line, and select **Terminate**. 
2. Enter the **Termination date**, the **Termination type**, and the **Reason code**. 
3. Set **Credit option** to **Issue credit**. 
4. If needed type any **Termination notes**. 
5. Select **Terminate**. 

The status of the billing schedule changes based on the **Termination type** selected. When **Termination type** is **Bill remaining**, all lines in the billing have the status **Last billing**.  The billing schedule remains **Active** until the last invoice is processed. After the last invoice is processed, the status changes to **Terminated**. When **Termination type** is **Adjust schedule**, the billing schedule status is updated to **Terminated** immediately. No further processing is required for the billing schedule. 

## Terminate with Refund

To terminate a billing schedule or billing schedule line and apply a refund, follow these steps: 
1. Select a billing schedule or a billing schedule line, and select **Terminate**.
2. Select the **Termination date**, the **Termination type**, the **Reason code**, and the **Credit option**. 
3. If needed type any **Termination notes**. 
4. Select **Terminate with refund**. The **Mass Termination Processing** page opens with the billing schedule filtered.  
5. Change any of the options as needed. Select **View preview** to see the billing schedules lines. and select **Process**. 

After the credit is processed, open the **View billing detail** page to review the credit applied to the billing schedule. When the credit amount is greater than zero (0), all future unbilled lines are deleted and replaced with billing detail lines that show the negative amounts for the credit that is applied to the billing schedule. 

### View example

A billing schedule with the following information exists: 
- Start date: January 01, 2020
- End date: December 31, 2020
- Billing period: 100.00 per month
- Invoices for billing periods for January to July have been created. 
- The contract termination date is June 15, 2020

When the credit adjustment is processed, all future billing periods (August to December) are removed from the **View billing detail** page. A credit adjustment line is added after the July billing period. 
- June 16 - July 31 with credit amount 150.00

Also, if unbilled revenue feature is used, the **Unbilled Revenue Journal Entry Audit** is updated with the termination entry.

## Terminate without Credit

To terminate a billing schedule or billing schedule line without a credit, follow these steps: 
1. Select a billing schedule or a billing schedule line, and select **Terminate**: 
2. Select the **Termination date**, and set **Termination type** to **No adjustment**. The **Credit option** is automatically set to **No credit**. 
3. Select the **Reason code** and if needed type any **Termination notes**. 
4. Select **Terminate**. 

When the termination is processed, all billing detail lines after the termination date (including the line that contains the termination date) are removed. Invoices for these lines cannot be created. If the termination is removed, all terminated lines are added back to View billing details, and become available for invoicing. 

## Fields

This page contains the following fields: 

| Field| Description|
| :------------- |:-------------| 
|**Termination date**|Select the date on which you want to terminate a billing schedule or billing schedule line. |
|**Termination type**|Select the termination type: <br />- **Adjust schedule**: Cuts off the billing periods for the line at the termination date and changes the status of the line to **Last Billing**. If a deferral schedule exists for the line item, it is also adjusted by reversing the amount that no longer must be recognized. When the billing start date is after the termination date, the remaining billing periods are removed.<br />- **Bill remaining**: Adds any remaining amount for the billing period to the termination period and changes the status of the line to **Last Billing**.  If a deferral schedule exists for the line item, the deferral end date is also updated. When the billing start date is after the termination date, the total amount of all remaining billing periods is added to the billing period and the remaining billing periods are removed. <br />- **No adjustment**: Terminates the billing periods for the line at the termination date specified. No adjustments are made. When selected, **Credit option** is set to **No credit** and **Prorate daily** is set to **No**. Both options become read-only and cannot be changed. |
|**Credit option**|When terminating a billing schedule line, select how the credit is applied: <br />* **Credit adjustment**: Creates a credit adjustment for a billing schedule when a line is terminated. The credit adjustment appears in a future billing period for the billing schedule and automatically adjusts the invoice amount for the next billing period until the credit is finished being applied to the billing schedule.  <br />- **Issue credit**: Creates a credit note when a billing schedule or billing schedule line is terminated. <br />- **No credit**: No credit adjustment or note is created upon termination of a billing schedule or billing schedule line. Available only when terminating a billing schedule using the **No adjustment** option. <br />The default option is from the **Recurring contract billing parameters** page. |
|**Reason code**|Select the reason code for the termination. |
|**Reason description**|Displays the reason code description. |
|**Termination notes**|Type any notes regarding the termination. |


## Additional information

