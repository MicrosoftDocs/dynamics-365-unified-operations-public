---
title: Subscription workflow overview 
description: Access an overview of subscription workflow, including outlines on setting up subscriptions and creating subscription transactions. 
author: ChristianRytt
ms.author: crytt
ms.topic: overview
ms.date: 05/07/2018
ms.reviewer: kamaybac
ms.search.form: SMASubscriptionGroup, SMASubscriptionCreateDialog
---


# Subscription workflow overview 

[!include [banner](../includes/banner.md)]


You are the subscriptions administrator for a light company that offers subscriptions for lighting rig maintenance. A customer contacts your company to purchase a yearly subscription for lighting rig maintenance.

## Setting up subscriptions

To set up a subscription, you must first create a subscription group for the new service agreement or verify that a subscription group exists. If a subscription group exists, you must set it up to invoice the customer yearly and to accrue sales revenue every month of the year. For more information about how to set up subscriptions, see [Set up subscription groups](set-up-subscription-groups.md).

After the subscription group is created, you can create the subscription. For more information about how to create service subscriptions, see [Create service subscriptions from a subscription group](create-service-subscriptions-from-subscription-group.md).

## Create and modify subscription transactions

After you set up the subscription, you create the subscription fee transaction for the first invoicing period, which is one year. The transactions are of the **Regular** type. Therefore, you can only create subscription transactions where the from date and the to date correspond to periods that were previously created in the **Period types** form. For more information about fee transactions, see [Create subscription fee transactions](create-subscription-fee-transactions.md).

After you set up the subscription for your customer, you remember that they have negotiated a 10 percent discount on all list prices for service offerings. Therefore, you must reduce the price of the transaction fee that you created.

Later in the day, your customer contact calls to say that, although they still want the service agreement for the lighting rig, they plan to introduce a new lighting rig later in the year. Therefore, they only need maintenance coverage until October 2013. To reduce the number of months for the customer’s subscription, you create a new subscription fee transaction of the **Reduction days** type. For more information about how to reduce days, see [Reduce the days on subscription fees](reduce-the-days-on-subscription-fees.md).

## Invoice and accrue subscription transactions

You have now finished setting up the subscription, and you are ready to invoice your customer for it. For more information about how to invoice subscriptions, see [Invoice subscription transactions](invoice-subscription-transactions.md).

Two days later, your customer calls to say that the subscription should be invoiced in U.S. dollars, not Euros. Therefore, you create a credit note, and you also create a new subscription transaction in the correct currency. For more information about how to credit subscription transactions, see [Credit subscription transactions](credit-subscription-transactions.md).

At the end of each month, one month's revenue can be accrued from the customer's subscription to the profit and loss account and the WIP accounts. For more information about how to accrue revenue for subscriptions, see [Accrue subscription revenue](accrue-subscription-revenue.md).

  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]