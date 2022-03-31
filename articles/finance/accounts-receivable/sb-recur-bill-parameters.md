---
# required metadata

title: Recurring contract billing set up
description: This topic explains how to create a billing schedule group for Recurring contract billing.  
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

# Recurring contract billing parameters

Use the **Recurring contract billing parameters** page to set up the default values for creating a billing schedule in Recurring contract billing. All billing schedules that you create will begin with these default values, but you can change the values for each billing schedule as needed. 

## General tab

Setup the default values in the **General** tab.
1. Go to the **Recurring contract billing parameters** page. 
2. Assign the **Billing schedule group**.
3. In **Termination type** field, select how the final invoice will be calculated when a billing schedule is terminated. 
    - **Adjust Schedule** - Cuts off the billing schedule at the termination date, changes the status of the schedule to **Last billing**, and adjusts the associated deferral schedule by reversing the amount that no longer must be recognized. When the billing start date is after the termination date, the remaining billing periods are removed.
    - **Bill remaining** - Adds any remaining amounts in the billing schedule to the termination period, changes the status of the schedule to **Last billing** and updates the deferral schedule. When the billing start date is after the termination date, the total amount of all remaining billing periods is added to the billing period and the remaining billing periods are removed.
    - **No adjustment** - Terminates the billing schedule as of the termination date specified. No adjustments to the billing schedule will be made. 
3. In **Unique schedule type** field, select if customers are limited to a single billing schedule, **None**, or a unique schedule, **Per customer** or **Per end user**. 
4. Select **Yes** in the **Align to month** field to align the billing schedule detail lines to the end of a month when a billing schedule is created or updated. Select **No** to use incremental dates. 
5. If you want to allocate a billing amount based on the number of days in the period, select **Yes** in the **Prorate partial periods** field. To have the same amount in each billing period, regardless of the number of days, select **No**. If you select **Yes**, choose the **Proration method** of **Daily** or **Monthly**. Choose **Daily** to distribute the amounts based on the number of days in the period. Choose **Monthly** to have an equal amount each month. 
6. If you want a newly created billing schedule to default on **Hold**, select **Yes**. 
>[!Note]
>To remove a hold on a billing schedule the user must be part of a user group.   Select **Remove hold user group override** to set up a User group with the option **Allow remove hold**. 
7. Select the default **Invoice transaction type** for a new billing schedule. 
8. Select **Yes** in the **Align deferral to billing** field if you want to align the dates of a corresponding deferral schedule to use the same dates as the billing schedule. Select **No** to have different dates. 
9. If using revenue split feature, select **Yes** in the **Automatically create revenue split** field when items are added to a billing schedule. The **Revenue split** checkbox will be marked automatically on the billing schedule line if the item is set up as a revenue split item. Select **No** to manually mark the **Revenue split** checkbox.
10. For **Sales order creation**:
    a. Invoices can be consolidated by period, customer or item. Any combination of **Yes** and **No** can be selected. Invoices can also be split by item group. 
    b. The **Posting option** for invoices include:
     - **Create sales order** to create only the sales order. 
     - **Show Posting invoice** to invoice the sales order and open the page where you can manually post the invoice. 
     - **Create fee text invoice** if using free text invoices. 
     - **Post invoice automatically** to invoice the sales order and post it. 
    c. Select **Yes** in the **Add billing dates to item description** field to add the description with the billing start date and end date.  
    d. In the **Exclude zero consumption** field, select **Yes** to not include the billing schedule lines with no consumption. Select **No** to include these lines on the sales order.
    e. In the **Don't print child items** field, select **Yes** if you do not want to print child items of a revenue split on the sales order. Only the parent item will appear on the invoice. If the net amount of the (hidden) child items has a non-zero sum, the net amount of the parent line shows a summary of the child lines. Select **No** for all child items to print below the parent item on the sales invoice.
11. In **Support and renewal**:
    a. Select **Yes** in the **Auto enable support and renewal** field to automatically use the support and renewal feature on a sales order.
    b. Select the default **Support and renewal level** and specify the **Support and renewal quantity**. 
    c. Select the **Default support and renewal start date**. 
     - **Transaction date** will use the transaction date as the start date. 
     - **Beginning of current month** uses the 1st of the current month as the start date. 
     - **Beginning of next month** uses the 1st of the following month as the start date. If the transaction date is the 1st, then the 1st of the current month is used. 
     - Select **Rule of 15** to use the 1st of the current month if the transaction date is between the 1st-15th of the month; if the transaction date is the 16th or later it will use the 1st of the next month as the start date. 
    d. Select **Yes** to **Include discount in calculation** to include the discount amount in the support or renewal amount. Select **No** to exclude the discount amount.
    e. Select the **Support frequency** and **Renewal frequency** that will be used when the support and renewal items are added to a billing schedule. Choose from **Daily**, **Monthly**, **Quarterly**, **Semiannually** or **Annually**. 
    f. Select **Yes** to **Align by item group** to align the start and end dates of additional items to existing items based on the item group. 
    g. Select **Yes** to **Align to next unbilled period** to determine the alignment date for a renewal item by the date of the next untilled period after the renewal starts. 
    h. Select **Yes** to **Copy serial number** to copy the item serial number from the initial sales order line to the corresponding billing schedule line.  
12. When using **Escalation** on the billing schedule, select the method used for the **Consumer price index calculation**.  
13. Select **Yes** to **Track price change** if you want a record of a billing schedule line price change. If a billing schedule line is manually changed from standard to flat and a new price entered, audit information is tracked on the billing schedule line. Select **No** to not track these changes. 
14. Select how records are filtered on the **Generate invoice** page. **Start date** or **End date** can be the default. 
15. If you use the **Unbilled revenue feature**, specify which options to use. 
    a. Select **Yes** for **Post general journal automatically** if you want the general journal to be created and posted at the same time. Select **No** to create the general journal and then manually post it. 
    b. Select a **Default journal name** to use when creating the general journal. 
    c. Select a **Short-term unbilled method** if using one. If **None** is selected then the short-term functionality is not used with unbilled revenue. Select **Rolling periods** to always use 12 months. Select **Fixed year** to use the remaining fiscal year.
 16. Specify the **Termination** options to use for terminating a billing schedule and its lines. 
     a. Select **Issue credit** to create a credit note when a billing schedule or billing schedule line is terminated. 
     b. Select **Credit adjustment** to create a credit adjustment for a billing schedule when a line is terminated. The credit adjustment appears in a future billing period for the billing schedule and automatically adjusts the invoice amount for the next billing period until the credit is finished being applied to the billing schedule. 
     c. Select **No credit** if you do not want a credit adjustment or note created when terminating a billing schedule or billing schedule line. This is only available when terminating a billing schedule using the **No adjustment** option. 
 
## Sequence number tab

Use this tab to set the default value for billing schedule numbers. The default values are set up on the **Organization administration > Number sequences > Number sequences** page.

## Billing schedule group

Use the **Billing schedule group** page to create a billing schedule group for Recurring contract billing. The billing schedule group settings default when creating a new billing schedule. When a billing schedule group is applied to newly created billing schedules, the default values of the group are automatically applied to the billing schedule. If needed, you can change any of the default options for the specific billing schedule that you create. Muliple billing schedule groups can be setup but you can assign a default billing schedule group in **Recurring contract billing parameters**.
 
 * Select **New** to create a billing schedule group. 
 * Enter a unique **Billing schedule group** identifier and **Description**. 
 * Use the **Billing frequency** to define how often the billing schedule is billed to a customer: **One-time**, **Daily**, **Monthly**, **Quarterly**, **Semiannually** or **Annually**. 
 * Enter a **Billing interval** to bill bi-monthly or similar intervals. For example, set the **Billing frequency** to **Monthly** and then **Billing interval** to **2**. This will bill every other month. 

Select the default **Pricing method** for items on the billing schedule: 
- **Standard**: Calculates the unit price based on the total quantity entered and uses standard pricing from **Released products** in **Product information management**.
- **Flat**: Applies a flat price entered on the billing schedule line. 
- **Tier**: Calculates unit price using fixed quantity at different pricing brackets. Each tier must be filled before moving to the next pricing tier bracket. 
- **Flat Tier**: Calculates unit price using fixed quantity and extended price amounts for different pricing brackets. The price that is charged in a billing period uses the extended price that corresponds to the tier where the billing quantity exists. 

In the **Item type** field, select a value for the billing group: 
 - Select **Standard** for use with static quantity. 
 - Select **Usage** for metered or consumption type items. 
 - Select **Milestone** to use the Milestone billing functionality. If the **Item type** is **Usage**, set the **Usage reading option** to **Reading** to enter the value on a meter or device for a billing period. The consumed value is will be calculated based on the reading from the previous billing period and the current reading you entered. 
 - Select **Consumption** to enter the value consumed for a billing period. If using Milestone **Item Type**, select the **Milestone template** if using one.

Select whether to create separate invoices based on the customer: 
 - Set **Invoice separately** to **Yes** to create a combination of consolidated invoices and separate invoices for the same customer. For example, a customer has five billing schedules. Three of them are to be consolidated on a single invoice, and the other two each require separate invoices. 
 - Select **No** to only allow one consolidated invoice for the customer. Set **Renew automatically** to **Yes** to automatically renew the recurring billing schedule for the next billing period when the invoice is created. Select **No** to manually renew the billing schedule.  Also, specify how many **Lines to add per renewal**. Set **Escalation** to Yes to apply escalations (price increases) to the billing schedules associated with this billing schedule group.






