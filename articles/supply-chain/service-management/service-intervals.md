---
title: Service intervals
description: Learn how to work with service intervals, which indicates the frequency with which service order lines are created for service agreement lines.
author: ChristianRytt
ms.author: crytt
ms.topic: article
ms.date: 02/20/2018
ms.custom:
ms.reviewer: kamaybac
ms.search.form: SMAAgreementTable
---

# Service intervals

[!include [banner](../includes/banner.md)]

The service agreement interval indicates the frequency with which service order lines are created for service agreement lines when you create service orders automatically.

When you create service orders automatically, service order lines are created according to the interval that you have specified for the service agreement line from the start date of the agreement line.

If the **Interval** field of a service agreement line in the **Service agreements** page is blank, the line is a one-time event, and it is not used to create service orders repeatedly.

## Example

This example illustrates how a service interval will affect service agreement lines and service order lines on a service order.

### Create a service agreement

First, you create a service agreement and set the **Combine service orders** option to **By service agreement**.

1. Click **Service agreements**
2. On the **Action Pane**, on the **Service agreement** tab, in the **New** group, click **Service agreement** to create a new service agreement.
3. Enter a description, select a project in the **Project ID** field, and enter a date in the **Start date** field.
4. In the **Combine service orders** field, select **By service agreement**.

You have now created the following service agreement:

| Project      | Start date                                                                         |
|--------------|------------------------------------------------------------------------------------|
| Your project | The date you specified for the project. In this example, the current date is used. |

### Create a service agreement line

Next, you create a service agreement line that has the transaction type **Hour**.

To complete this part of the example, you must create a service interval of 10 days in the **Service intervals** page. 

1. Select the service agreement that you just created. 
2. On the **Lines** FastTab, click the **Add** button to create a new line in the lower pane of the **Service agreements** page.
3. In the **Transaction type** field, select **Hour**.
4. In the **Worker** field, select the worker who will deliver the service.
5. In the **Service interval** field, select the 10 days interval.

You have now created a service agreement line with the following information:

| Transaction type | Start date                               | Service interval |
|------------------|------------------------------------------|------------------|
| Hour             | The current date.                        | Every 10 days    |
| Worker           | The worker who will perform the service. |                  |

There is no time window specified for the line. 

### Create planned service orders

You can now create planned service orders and service order lines for the coming month.

1. In the **Service agreements** page, on the **Action Pane**, on the **Deliver** tab, click **Planned service orders**.
2. In the **Create service orders** page, enter the current date in the **From date** field and a date that is one month from the current date in the **To date** field.
3. Set the **Hour** slider to **Yes**. 
4. Click **OK**.

Because there is no grouping on the service order (defined by the **By service agreement** option in the **Combine service orders** field), one service order line is created per service order.

### Service orders created

Three service order lines have been created within the time frame that you specified in the **Create service orders** dialog box. You can view the service order lines in the **Service agreements** page (**Action Pane** \> **Deliver** tab \>**View** button).

## Related articles

[Set up service intervals](set-up-service-intervals.md)  



[!INCLUDE[footer-include](../../includes/footer-banner.md)]