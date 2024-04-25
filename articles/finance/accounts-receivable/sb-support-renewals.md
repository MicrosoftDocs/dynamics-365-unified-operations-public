---
title: Support and renewals
description: Learn how to set up and use the support and renewal process on sales orders to create a billing schedule for renewal items.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 11/04/2021
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form:  
ms.dyn365.ops.version: 10.0.24
---

# Support and renewals 

This article explains how to enter support items or renewal items when you enter sales orders. These items are used to calculate the charge amount for the original support contract and/or the renewal amount that is used when a billing schedule is created in Subscription billing. For example, your company sells a server to a customer, and you offer a data backup subscription for the first year and the option to renew that subscription every year. The *support item* is the subscription for the first year, and the *renewal item* is the renewal for every successive year.

You can enter information for the support contract, the renewal contract, or both. When you enter the support contract information, only the support item is added to the sales order. When you enter the renewal contract information, the renewal item is used to create a billing schedule.

## Support and renewal setup

On the **Support and renewal levels** page, you can set up different support levels for support and renewal items. The support or renewal can be a percentage of the original item amount, or it can be a standard amount.

You can select the default support levels on the **Recurring contract billing parameters** page.

For example, a company might offer the following support and renewal levels.

| Support level | Support percentage | Renewal percentage |
|---|---|---|
| Unlimited | 40% | 30% |
| Gold | 25% | 18% |
| Silver | 20% | 14% |
| Bronze | 15% | 10% |

To create a support or renewal level, follow these steps.

1. On the **Support and renewal levels** page, select **New**.
2. In the **Support level** field, enter a unique name.
3. In the **Description** field, enter a description.
4. In the **Support calculation method** field, select the support calculation method. If you select **Percent**, enter a support percentage in the **Support percentage** field.
5. In the **Renewal calculation method** field, select the renewal calculation method. If you select **Percent**, enter a renewal percentage in the **Renewal percentage** field.
6. Select **Save**.

### Fields

The **Support and renewal levels** page contains the following fields.

| Field | Description |
|---|---|
| Support level | A unique identifier for the support or renewal level (for example, **Gold** or **Silver**). |
| Description | A description of the support or renewal level. |
| Support calculation method | Select the support calculation method for the level: **Percent** or **Standard amount**. |
| Support percentage | If you selected **Percent** as the support calculation method, specify the percentage that is used to calculate the price of the support item. If you selected **Standard amount** as the calculation method, the amount is specified when the transaction is created. |
| Renewal calculation method | Select the renewal calculation method for the level: **Percent** or **Standard amount**. |
| Renewal percentage | If you selected **Percent** as the renewal calculation method, specify the percentage that is used to calculate the price of the renewal item. If you selected **Standard amount** as the calculation method, the amount is specified when the transaction is created. |

## Support and renewal process

The support and renewal functionality can apply different support levels to items and update renewal information in Subscription billing.

Before you use the support and renewal functionality, the following tasks must be completed.

1. On the **Support and renewal levels** page, create at least one support or renewal level.
2. On the **Item setup** page, associate an item with support and renewal items. This task is required only if you want to set up default values for support and/or renewal items.
3. On the **Recurring contract billing parameters** page, specify the default support and renewal settings for new billing schedules.

To apply different support levels to items and update renewal information, follow these steps.

1. On the **All sales orders** page, create a sales order.
2. On the **Sales order lines** FastTab, add an item.
3. On the **Invoice** tab, select **Support and renewal \> Add support and renewal**.
4. On the **Support and renewal process** page, the header section is updated with the settings from the **Recurring contract billing parameters** page. These values apply to all the support and renewal items. (For example, if the billing frequency is set to **Annually**, all sales lines that are created that have a renewal item have an annual frequency.) To associate the sales order with an existing billing schedule, select a value in the **Billing schedule number** field.
5. To change the support or renewal start date, set the **Override start date** option to **Yes**.
6. To add or edit the support item, select the **Support** checkbox, and then enter a support item in the **Support item** field. The item is added to the sales order.
7. To add or edit the renewal item, select the **Renewal** checkbox, and then enter a renewal item in the **Renewal item** field. When the sales order is invoiced, a billing schedule that includes the item will be created.
8. Select **OK**.
9. On the **Generate** tab, select **Invoice**. When the sales order is posted, the billing schedule is created. A notification that includes the billing schedule information appears in the message details.
10. On the **All/Active billing schedules** list page, select the billing schedule number to review the details of the billing schedule on the **Billing schedules** page.
11. On the **Billing schedule lines** FastTab, select **Support and renewal** to review the details of the lines that were created.

> [!NOTE]
> If the renewal start date for a billing schedule line must be changed, you can edit the **Start date** value for the line on the **Billing schedules** page. When you open the **View billing detail** page for the line, the **Billing start date** field is updated with the new date. The **Billing end date** value is recalculated based on the billing frequency. The renewal start date can be updated only if the first invoice for the renewal billing schedule hasn't been created and posted. After the first invoice is created and posted, the start date can't be edited.

The support and renewal process is available for the sales order only. When you add support and renewal items to a sales order, you can create a new billing schedule or add the renewal item to an existing billing schedule.

## Support and renewal audit

On the **Support and renewal audit** page, you can review the details of the billing schedule lines that are created from the renewal item on a sales order. This option is available when the billing schedule line item is a renewal item.

To edit support and renewal information for a billing schedule line, follow these steps.

1. On the **All billing schedules** page, select the billing schedule number.
2. In the **Billing schedule lines** section, select a line, and then select **Support and renewal**.
3. Review all the information for the support or renewal item.
4. Make any required changes to the support level, or the renewal percentage or amount, and then enter a value in the **Reason for change** field.
5. Select **Process**.

### Fields

The **Support and renewal audit** page contains the following fields.

| Field | Description |
|-------|-------------|
| Item number | The item number for the billing schedule line. |
| Product name | The product name. |
| Support plan level | View or change the support level for the renewal item. |
| Renewal percentage | Enter the renewal percentage that is used when the unit price is calculated for a renewal item in a billing schedule. |
| Renewal amount | Enter the renewal amount that is used when the unit price is calculated for a renewal item in a billing schedule. |
| Reason for change | Enter your reason for changing the support and renewal information. You must enter a reason when you change the **Renewal percentage**, **Renewal amount**, or **Support plan level** value. |
| Original sales item | The original sales item number from the sales order. |
| Original net amount | The original net amount for the item. |
| Original support level | The original support level for the item. |
| Original renewal percentage | The original renewal percentage for the item. |
| Original renewal amount | The original renewal amount for the item. |
| **Grid** | |
| Original support level | The previous support level. |
| Original renewal percentage | The previous renewal percentage. |
| Original renewal amount | The previous renewal amount. |
| Modified by | The user name of the user who made the change. |
| Modified date and time | The date when the change occurred. |
| Reason | The reason for the change. |
