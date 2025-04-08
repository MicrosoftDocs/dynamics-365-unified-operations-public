---
title: Service intervals
description: Learn how to work with service intervals, which indicate the frequency with which service order lines are created for service agreement lines.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAAgreementTable
ms.topic: how-to
ms.date: 01/06/2025
ms.custom: 
  - bap-template
---

# Service intervals

[!include [banner](../includes/banner.md)]

The service agreement interval indicates the frequency with which service order lines are created for service agreement lines when you create service orders automatically.

When you create service orders automatically, service order lines are created according to the interval that you have specified for the service agreement line from the start date of the agreement line.

If the **Interval** field of a service agreement line on the **Service agreements** page is blank, the line is a one-time event, and it isn't used to create service orders repeatedly.

## Example

This example illustrates how a service interval affects service agreement lines and service order lines on a service order.

### Create a service agreement

First, you create a service agreement and set the **Combine service orders** option to *By service agreement*.

1. Select **Service agreements**
2. On the Action Pane, on the **Service agreement** tab, in the **New** group, select **Service agreement** to create a new service agreement.
3. Enter a description, select a project in the **Project ID** field, and enter a date in the **Start date** field.
4. In the **Combine service orders** field, select *By service agreement*.

You have now created the following service agreement:

| Project      | Start date                                                                         |
|--------------|------------------------------------------------------------------------------------|
| Your project | The date you specified for the project. In this example, the current date is used. |

### Create a service agreement line

Next, you create a service agreement line that has the transaction type *Hour*.

To complete this part of the example, you must create a service interval of 10 days on the **Service intervals** page.

1. Select the service agreement that you just created.
2. On the **Lines** FastTab, select the **Add** button to create a new line in the lower pane of the **Service agreements** page.
3. In the **Transaction type** field, select *Hour*.
4. In the **Worker** field, select the worker who will deliver the service.
5. In the **Service interval** field, select the 10 days interval.

You have now created a service agreement line with the following information:

| Transaction type | Start date                               | Service interval |
|------------------|------------------------------------------|------------------|
| Hour             | The current date.                        | Every 10 days    |
| Worker           | The worker who will perform the service. |                  |

There's no time window specified for the line.

### Create planned service orders

You can now create planned service orders and service order lines for the coming month.

1. On the **Service agreements** page, on the Action Pane, on the **Deliver** tab, select **Planned service orders**.
2. On the **Create service orders** page, enter the current date in the **From date** field and a date that is one month from the current date in the **To date** field.
3. Set the **Hour** slider to *Yes*.
4. Select **OK**.

Because there's no grouping on the service order (defined by the **By service agreement** option in the **Combine service orders** field), one service order line is created per service order.

### Service orders created

Three service order lines were created within the time frame that you specified in the **Create service orders** dialog box. You can view the service order lines on the **Service agreements** page (Action Pane \> **Deliver** tab \> **View** button).

## Related information

- [Set up service intervals](set-up-service-intervals.md)  

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
