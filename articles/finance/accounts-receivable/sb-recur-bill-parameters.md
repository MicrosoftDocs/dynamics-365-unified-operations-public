---
title: Recurring contract billing parameters
description: Learn how to set up the default values for billing schedules that are created in Recurring contract billing. It also explains how create billing schedule groups.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 10/25/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.24
---

# Recurring contract billing parameters
Use the **Recurring contract billing parameters** page to set up the default values for billing schedules that are created in Recurring contract billing. (**Subscription billing > Recurring contract billing > Setup > Recurring contract billing parameters**). All billing schedules that you create initially use these default values. However, you can change the values for each billing schedule as you require.

## General tab

1. On the **Recurring contract billing parameters** page, on the **General** tab, in the **Billing schedule group** field, select a billing schedule group. For information about how to set up billing schedule groups, see the [Billing schedule groups](#set-up-billing-schedule-groups) section later in this article.
2. In the **Termination type** field, select how the final invoice is calculated when a billing schedule is terminated:

    - **Adjust schedule** – Cut off the billing schedule on the termination date, change the status of the schedule to **Last billing**, and adjust the associated deferral schedule by reversing the amount that no longer must be recognized. If the billing start date is after the termination date, the remaining billing periods are removed.
    - **Bill remaining** – Add any remaining amounts in the billing schedule to the termination period, change the status of the schedule to **Last billing**, and update the deferral schedule. If the billing start date is after the termination date, the total amount of all remaining billing periods is added to the billing period, and the remaining billing periods are removed.
    - **No adjustment** – Terminate the billing schedule on the termination date. No adjustments are made to the billing schedule.

3. In the **Unique schedule type** field, select **None** to specify that customers are limited to a single billing schedule. Select **Per customer** or **Per end user** to specify that customers are limited to a unique schedule.
4. Set the **Align to month** option to **Yes** to align the billing schedule detail lines with the end of a month when a billing schedule is created or updated. Set it to **No** to use incremental dates.
5. Set the **Prorate partial periods** option to **Yes** to allocate billing amounts based on the number of days in the period. Set it to **No** to have an equal amount in each billing period, regardless of the number of days.
6. If you set the **Prorate partial periods** option to **Yes**, set the **Proration method** field to **Daily** to distribute the amounts based on the number of days in the period. Set it to **Monthly** to have an equal amount every month.
7. Specify whether newly created billing schedules are on hold by default.

    > [!NOTE]
    > To remove the hold on a billing schedule, the user must be part of a user group. Select **Remove hold user group override** to set up a user group where the **Allow remove hold** option is enabled.

8. In the **Invoice transaction type** field, select the default invoice transaction type for new billing schedules.
9. Set the **Align deferral to billing** option to **Yes** to align the corresponding deferral schedule so that it uses the same dates as the billing schedule. Set it to **No** to have different dates.
10. If you're using the revenue split feature, set the **Automatically create revenue split** option to **Yes** when items are added to a billing schedule. The **Revenue split** checkbox is automatically selected on the billing schedule line if the item is set up as a revenue split item. Set the option to **No** if you want to manually select the **Revenue split** checkbox.
11. Set the **Customer split** option to **Yes** to allow a billing schedule to be billed to different customers. When set to **Yes** the **Customer split** option is available on the billing schedule header and billing schedule line. 
12. Set the fields for sales order creation:

    - Invoices can be consolidated by period, customer, or item. Any combination of **Yes** and **No** values can be set. Invoices can also be split by item group.
    - The following posting options are available for invoices:

        - **Create sales order** – Create only the sales order.
        - **Show Posting invoice or Create invoice proposal page** – Invoice the sales order, and open a page where you can manually post the sales order invoice. If you're using a project on the billing schedule, the **Invoice proposal** page is opened, and you can manually post it. 
        - **Create fee text invoice** – Select this option if you're using free text invoices.
        - **Post invoice automatically** – Invoice the sales order, and automatically post it.

    - Set the **Add billing dates to item description** option to **Yes** to add a description that includes the billing start date and end date.
    - Set the **Exclude zero consumption** option to **Yes** to exclude billing schedule lines that have no consumption. Set it to **No** to include those lines on the sales order.
    - Set the **Don't print child items** option to **Yes** if you don't want to print the child items of a revenue split on the sales order. Only the parent item appears on the invoice. If the net amount of the (hidden) child items is a non-zero sum, the net amount of the parent line shows a summary of the child lines. Set the option to **No** to print all child items below the parent item on the sales invoice.

13. Set the fields for support and renewals:

    - Set the **Auto enable support and renewal** option to **Yes** to automatically use the support and renewal feature on a sales order.
    - In the **Support and renewal level** field, select the default support and renewal level.
    - In the **Support and renewal quantity** field, specify the support and renewal quantity.
    - In the **Default support and renewal start date** field, specify the date to use as the default start date for support and renewals:

        - **Transaction date** – Use the transaction date as the start date.
        - **Beginning of current month** – Use the first of the current month as the start date.
        - **Beginning of next month** – Use the first of the next month as the start date. If the transaction date is the first, the first of the current month is used.
        - **Rule of 15** – Use the first of the current month as the start date if the transaction date is between the first and fifteenth of the month. If the transaction date is the sixteenth or later, use the first of the next month as the start date.

    - Set the **Include discount in calculation** option to **Yes** to include the discount amount in the support or renewal amount. Set it to **No** to exclude the discount amount.
    - In the **Support frequency** and **Renewal frequency** fields, select the frequency to use when support and renewal items are added to a billing schedule: **Daily**, **Monthly**, **Quarterly**, **Semiannually**, or **Annually**.
    - Set the **Align by item group** option to **Yes** to align the start and end dates of new items to existing items, based on the item group.
    - Set the **Align to next unbilled period** option to **Yes** to determine the alignment date for a renewal item based on the date of the next unbilled period after the renewal starts.
    - Set the **Copy serial number** option to **Yes** to copy the item serial number from the initial sales order line to the corresponding billing schedule line.

14. If you're using escalation on the billing schedule, select the method that is used for the consumer price index calculation.
15. Set the **Track price change** option to **Yes** to record the price changes on billing schedule lines. If a billing schedule line is manually changed from **Standard** to **Flat**, and a new price entered, audit information is tracked on the billing schedule line. Set the option to **No** if you don't want to track these changes.
16. Set the **Default new line to active when header status is on hold** option to **Yes** if new billing schedule lines should have a status of **Active** when they are added to a billing schedule header that has a status of **On hold**. Set the option to **No** if new billing schedule lines should have a status of **On hold** in this situation.
17. Specify whether records on the **Generate invoice** page are filtered by start date or end date by default.
18. If you use the **Unbilled revenue** feature, specify the options that are used:

    - Set the **Post general journal automatically** option to **Yes** if you want the general journal to be created and posted at the same time. Set it to **No** if you want to create the general journal and then manually post it.
    - In the **Default journal name** field, select the default journal name to use when the general journal is created.
    - In the **Short-term unbilled method** field, select the short-term unbilled method, if you're using one. If you select **None**, the short-term functionality won't be used with unbilled revenue. Select **Rolling periods** to always use 12 months or **Fixed year** to use the remaining fiscal year.
    - Set the **Require journal entry for renewal period** option to **Yes** to create a new journal entry for the unbilled revenue when a billing schedule is renewed. Set the option to **No** if the unbilled revenue journal entry isn't required during the renewal period.
    - Set the **Auto create journal entry for renewal** option to **Yes** to automatically create the unbilled revenue entry when a billing schedule renewal is created. Set the option to **No** to manually create the unbilled revenue journal.
    - The unbilled offset accounts create additional entries when unbilled revenue is used. These accounts are most often used when billing schedules that have unbilled revenue are created in currencies other than the accounting currency. Set the **Use unbilled offset accounts** option to **Yes** to use the unbilled revenue offset and unbilled discount offset accounts. These accounts are set up on the **Unbilled revenue setup** page. 

19. Specify the options that are used when a billing schedule and its lines are terminated:

    - **Issue credit** – Create a credit note when a billing schedule or billing schedule line is terminated.
    - **Credit adjustment** – Create a credit adjustment for a billing schedule when a line is terminated. The credit adjustment appears in a future billing period for the billing schedule. The credit adjustment will update the invoice amount for the next billing period until the credit has finished being applied to the billing schedule.
    - **No credit** – Don't create a credit adjustment or a credit note when a billing schedule or billing schedule line is terminated. This option is available only when the **No adjustment** option is used to terminate a billing schedule.

20. If you set the **One time can terminate with refund** option to **No**, and a billing schedule has a billing frequency of **One time**, the status of the billing schedule line changes to **Terminated** after the billing schedule is invoiced. This billing schedule can't be terminated, and no credit can be issued. If you set the option to **Yes**, the status of the billing schedule line that has a billing frequency of **One time** changes to **Active** after the billing schedule is invoiced. The billing schedule line can be terminated, and a refund can be processed. 
21. The value that is set for the **Prorate daily** option in the parameters is used as a default value on the **Mass termination** page, on the billing schedule header, and in termination dialog boxes. It can be changed during the termination process. When the option is set to **Yes**, any refund amount is calculated by using a daily rate. When it's set to **No**, the credit is based on the termination date and billing frequency. For example, if the billing frequency is **Monthly**, and the billing amount is $100 per month, the credit amount is in increments of $100. If the billing frequency is **One-time**, the credit amount is $0.00. If the billing frequency is **One-time**, you must set the **Prorate daily** option to **Yes** to get a refund.
22. Set the **Create deferral for credit** option to **Yes** to create a new deferral schedule when you credit a billing schedule by using the terminate option. Leave the option set to **No** to adjust the existing deferral schedule when you credit a billing schedule by using the terminate option. This option isn't used for standalone deferral schedules that aren't linked to a billing schedule.
23. Specify the options that are used with trade agreements:

    - **Use trade agreements** – When this option is set to **Yes**, the default item price on a billing schedule line comes from the trade agreement setup for the item. The price, discount, and "from" and "to" dates from the trade agreement are honored on the billing schedule line. When the option is set to **No**, the default item price comes from a trade agreement, but no discounts or "from" and "to" dates from the trade agreement are used.
    - **Use weighted trade agreement price by billing period** – When multiple trade agreement lines cover a single billing schedule period, there can be multiple prices for one billing schedule period. Set this option to **Yes** to prorate the different prices for the billing period. Set it to **No** if you don't want to prorate them.
    - **Update from trade agreement only at renewal** – When this option is set to **Yes**, updates from trade agreements don't update the billing schedule line. Therefore, the billing schedule price is effectively locked. However, when the line is renewed, the new trade agreement price is used. When the option is set to **No**, any updates on the trade agreement always roll down to the billing schedule line, both when trade agreement changes occur and when the trade agreement is renewed.

24. Set the **Use sales agreements** option to **Yes** to select a sales agreement when you create the billing schedule. The default pricing on the billing schedule comes from the sales agreement.

## Sequence number tab

Use the **Sequence number** tab on the **Recurring contract billing parameters** page to set the default value for billing schedule numbers. The default values are set up on the **Number sequences** page (**Organization administration \> Number sequences \> Number sequences**).

## Set up billing schedule groups

Use the **Billing schedule group** page to create a billing schedule group for Recurring contract billing. (**Subscription billing > Recurring contract billing > Setup > Billing schedule group**). When a new billing schedule is created, and a billing schedule group is applied to it, the values that are defined on the **Billing schedule group** page are entered as default values for the billing schedule. You can change any of the default values for the specific billing schedule that you create. You can set up multiple billing schedule groups and then assign one of them as the default billing schedule group on the **Recurring contract billing parameters** page.

To create a billing schedule group for Recurring contract billing, follow these steps:

1. On the **Billing schedule group** page, select **New** to create a billing schedule group.
2. In the **Billing schedule group** field, enter a unique identifier.
3. In the **Description** field, enter a description.
4. In the **Billing frequency** field, specify how often the billing schedule is billed to a customer: **One-time**, **Daily**, **Monthly**, **Quarterly**, **Semiannually**, or **Annually**.
5. In the **Billing interval** field, enter a billing interval. For example, set the **Billing frequency** field to **Monthly** and the **Billing interval** field to **2** to bill every other month.
6. In the **Pricing method** field, select the default pricing method for items on the billing schedule:

    - **Standard** – Calculate the unit price based on the total quantity that is entered, and use the standard pricing from the **Released products** page in Product information management.
    - **Flat** – Apply a flat price that is entered on the billing schedule line.
    - **Tier** – Calculate the unit price by using a fixed quantity at different pricing brackets. Each tier must be filled before moving to the next pricing bracket.
    - **Flat Tier** – Calculate the unit price by using a fixed quantity and extended price amounts for different pricing brackets. The price that is charged in a billing period uses the extended price that corresponds to the tier where the billing quantity exists.

7. In the **Item type** field, select the type of item for the billing group:

    - **Standard** – Select this value if the quantity is static.
    - **Usage** – Select this value for metered or consumption-type items. If you select this value, set the **Usage reading option** field to **Reading** to enter the value (reading) for a billing period on a meter or device. The consumed value is calculated based on the previous billing period and the current reading that you enter.
    - **Milestone** – Select this value to use the Milestone billing functionality. If you select this value, in the **Milestone template** field, select the milestone template if you're using one.
    - **Consumption** – Select this value to enter the value that is consumed for a billing period.

8. Set the **Invoice separately** option to **Yes** to create a combination of consolidated invoices and separate invoices for the same customer. For example, a customer has five billing schedules. Three of them will be consolidated on a single invoice, but each of the other two requires a separate invoice. Set the option to **No** to create only one consolidated invoice for the customer.
9. Set the **Renew automatically** option to **Yes** to automatically renew the recurring billing schedule for the next billing period when the invoice is created. Set it to **No** to manually renew the billing schedule. In the **Lines to add per renewal** field, specify how many lines to add for each renewal.
10. Set the **Escalation** option to **Yes** to apply *escalations* (price increases) to the billing schedules associated with this billing schedule group.

## Item group setup

Use the **Item group setup** page to define item groups for support and renewal proration, alignment dates for renewal items and the Top billing functionality. **Subscription billing > Recurring contract billing > Setup > Item group setup**. 

- **Prorate support and renewal** – Select whether to prorate the support or renewal amount based on the dates. Select the checkbox to prorate the support or renewal amount for items in the item group. When the checkbox isn't selected, the support or renewal amount for items in the item group isn't prorated.
- **Adjust renewal dates** – Select whether the alignment date for a renewal item is to be determined by the item group. Select the checkbox to update the renewal start and end dates based on the specified alignment date. 
- **Number of top lines** – Specify the top most expensive items to charge on an invoice for the specific item group for the Top billing functionality. This number must be zero (0) or a positive value. A zero-value indicates that the top billing feature isn't used. If used, this number typically ranges from zero to six items. 


