---
title: Reduce the days on subscription fees  
description: Learn how to reduce the number of days of an existing subscription fee, including a step-by-step process and examples of subscription fee reductions.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 05/01/2018
ms.custom:
ms.reviewer: kamaybac
ms.search.form: SMASubscriptionTable
---

# Reduce the days on subscription fees

[!include [banner](../includes/banner.md)]

To reduce the number of days of an existing subscription fee, you can create a new transaction in which you remove the period of time that should no longer be part of the subscription fee interval.

## Reduce the days on a subscription fee

1. Go to **Service management** \> **Service subscriptions** \> **All service subscriptions**. Select the service subscription, and on the Action Pane, select **Subscription fees**

2. In the **Subscription type** field, select **Reduction days**.

3. Use the **From date** field and the **To date** fields to define the date interval of the subscription fee that you want to remove from the subscription fee period, and then select **OK**.

To view the transaction that was created, on the **Subscription** page, select **Fee transactions**.

## Example

If a subscription transaction period runs from January 1 to January 31, and you want to reduce the period by 10 days, create a new transaction in which the reduction period is January 1 to January 10. (The reduction period could also be January 5 to January 15, or any other ten day period).

Also, if the **From date** on the reduction period is January 21 (31 minus 10), you could set the **To date** to any date after January 31, and 10 days will still be removed from the fee transaction period.

## Related information

- [Reduction days example](reduction-days-example.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
