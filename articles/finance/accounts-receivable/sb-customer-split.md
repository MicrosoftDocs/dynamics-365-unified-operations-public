---
title: Customer split on billing schedules
description: Learn about how to split a customer when subscription billing is used, including an overview on customer split on billing schedule lines. 
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 08/20/2026
ms.reviewer: twheeloc 
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2022-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.31
---

# Customer split on billing schedules

[!INCLUDE [banner](../../includes/banner.md)]

On a billing schedule, the *invoice account* is the customer who receives the sales order invoice so that they can pay the bill. In some scenarios, more than one customer can pay an invoice. The **Customer split** functionality lets you add more customers that can be billed for the same billing schedule. To enable this functionality, go to **Subscription billing \> Recurring contract billing \> Setup \> Recurring contract billing parameters**, and set the **Customer split** option to **Yes**.

## Customer split on the billing schedule header

After a billing schedule is created, you can add more customers to the billing schedule header.

To add a customer, follow these steps:

1. On the **Billing schedule** tab, select **Customer split**. The **Customer account** and **Customer account name** fields at the top specify the customer who is assigned as the **Billing schedule customer**.

    > [!NOTE]
    > The customer account that you add can't be the same as the invoice account.

2. On the **Customer split lines** tab, select **Add line**.
3. Select a customer, and then enter the percentage of each invoice for that customer.
4. By default, the start and end dates of the billing schedule are used as the start and end dates. Enter different start and end dates if the new customer will pay the specified percentage for only a portion of the billing schedule. For example, if the billing schedule has a start date of January 1 and an end date of December 31, and the new customer is billed 40 percent for the first nine months, specify January 1 as the start date and September 30 as the end date, and enter **40.00** as the percentage.

You can add more than one customer to the customer split lines. In this case, the total percentage that you enter must not exceed 100 percent. Enter a customer reference and customer requisition as informational fields that appear on the sales order line during the **Generate invoice** process.

The line details show the contact information, delivery address, bill-to address, and payment details of the added customers. This information also appears on the sales order for the customers.

When you add customer split information to the billing schedule header, if there are unbilled billing schedule lines on the billing schedule, you receive the following message that prompts you to roll down the changes: "Do you want to roll down the change from the header to the lines? Changes only update the billing schedule lines that aren't billed." Select **Yes** to update the customer split information on the billing schedule line. Changes aren't updated if the billing schedule line is already billed.

If you create a billing schedule by using the **Copy schedule** option, default information is entered on customer split header lines. It can't be the same as the customer account.

When you complete the **Generate invoice** process, multiple sales orders are created. (Multiple sales invoices are also created if automatic posting is used.) You can view these sales orders and sales invoices on the **Invoice** tab on the **Line details** FastTab of the **View billing detail** page. **Multiple** is shown on the billing detail line to indicate that multiple sales orders and sales invoices were created.

## Customer split on billing schedule lines

Add the customer split to individual billing schedule lines if you want to split only specific billing schedule lines. Select the **Customer split** checkbox on the line. Then, select **Customer split** on the menu for the billing schedule line to update or enter the customer split information.

The audit information updates if the billing schedule is already billed, but then the percentage changes on the billing schedule line. Any lines that are billed after that change use the new percentage.

> [!NOTE]
>
> - You can't use the customer split option with stocked products.
> - If you select the **Unbilled revenue** checkbox, you can't select the **Customer split** checkbox.
> - If you use the **Revenue split only** option, the parent line has the **Customer split** option, but the child line items don't.
