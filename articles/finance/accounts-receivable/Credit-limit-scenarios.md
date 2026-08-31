---
title: Credit limit scenarios
description: Learn about how the customer credit limit is checked when the customer belongs to a customer credit limit group.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 08/05/2026
ms.reviewer: twheeloc 
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2022-06-28
ms.search.form: 
ms.dyn365.ops.version: 10.0.21
---

# Credit limit scenarios

[!INCLUDE [banner](../../includes/banner.md)]

In Credit management, assign a credit limit to customers at the customer level. Assign each customer to a *customer credit limit group*, and set a credit limit for each group. Therefore, you can also assign a credit limit to customers at the group level. All customers that you assign to the same customer credit group have the same credit limit.

In general, the system checks group credit limits before individual credit limits. The individual credit limit doesn't always override the group credit limit.

This article describes five scenarios that relate to customer credit groups and individual credit limits.

## The customer group credit limit is more than the individual credit limit

For example, the customer has an individual credit limit of $10,000. The customer is assigned to a customer credit group, and the group's credit limit is $15,000. In this case, the customer's "effective credit limit" is $10,000, because that amount is less than the group limit. Blocking rules first check the group limit. They then check the individual limit. Any sales order over $10,000 is blocked.

## The individual credit limit is more than the customer group credit limit

For example, the customer has an individual credit limit of $20,000. The customer is assigned to a customer credit group, and the group's credit limit is $15,000. In this case, the customer's effective credit limit is $15,000, because the blocking rules always check the group limit first. Any sales orders over $15,000 are blocked.

## The individual credit limit is set to 0.00 and Mandatory credit limit is set to Yes

If the customer has an individual credit limit that is set to **0.00**, and the **Mandatory credit limit** option is set to **Yes**, the customer's effective credit limit is $0.00, even if the customer is assigned to a customer credit group. In this way, the customer can be part of a group, but all orders go to Credit management.

## The individual credit limit is set to 0.00 and Unlimited credit limit is set to Yes

If the customer has an individual credit limit that is set to **0.00**, but the **Unlimited credit limit** option is set to **Yes**, the customer has unlimited credit, even if they are assigned to a customer credit group.

## The individual credit limit is set to 0.00 and the customer is part of a customer credit group

For example, the customer has an individual credit limit that is set to **0.00**, the **Unlimited credit** option is set to **No**, and the **Mandatory credit limit** option is set to **No**. The customer is assigned to a customer credit group, and the group's credit limit is $15,000. In this case, the customer's effective credit limit is the group's limit, $15,000. Therefore, any sales orders over that amount are blocked. This behavior enables you to manage the credit limit at the customer credit group level instead of the individual customer level. All customers that you assign to the same group have the same credit limit.
