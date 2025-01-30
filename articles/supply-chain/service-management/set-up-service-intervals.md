---
title: Set up service intervals 
description: Learn how to set up service intervals, which indicate when service order lines are created for service agreement lines when you create service orders.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAAgreementinterval
ms.topic: how-to
ms.date: 01/30/2025
ms.custom: 
  - bap-template
---

# Set up service intervals  

[!include [banner](../includes/banner.md)]

Service interval indicates the frequency with which service order lines are created for service agreement lines when you create service orders.

1. Go to **Service management** \> **Setup** \> **Service agreements** \> **Service intervals**.
2. On the Action Pane, select **New**.
3. Enter the ID and description of the service interval.
4. In the **Range** field, select the range.
5. In the **Frequency** field, type the frequency. The frequency is the factor by which you must multiply the range to obtain the interval for a service agreement.
6. On the Action Pane, select **Save**.

## Example

You want to create a service interval of 10 days, so you take the following steps.

1. Go to **Service management** \> **Setup** \> **Service agreements** \> **Service intervals**.
2. On the Action Pane, select **New**.
3. Enter the ID and description of the service interval.
4. In the **Range** field, select *Daily*.
5. In the **Frequency** field, type *10*.
6. On the Action Pane, select **Save**.

## Related information

- [Service intervals](service-intervals.md)  

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
