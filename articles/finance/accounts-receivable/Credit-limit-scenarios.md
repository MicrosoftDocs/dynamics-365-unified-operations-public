---
# required metadata

title: Credit limit scenarios
description: This topic describes how the customer credit limit is checked when customer belongs to a customer credit group. 
author: JodiChristiansen
ms.date: 06/28/2022
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
ms.search.validFrom: 2022-06-28
ms.dyn365.ops.version: 10.0.21

---
# Credit limit scenarios

In Credit management, a customer can be assigned a credit limit at the customer level. Each customer can also be assigned to a Customer credit limit group and each group has a credit limit. In general, group credit limits are checked before individual credit limits. When a customer is part of a customer credit group all customers assigned to that group share the credit amount. The individual credit limit amount does not always override the customer group credit limit. There are five scenario combinations that relate to customer credit groups and individual credit limits and they are described below.

## Customer group credit limit is greater than the individual credit limit
Let's assume the customer has an individual credit limit of $10,000. The customer is assigned to a Customer credit group and the group's limit is $15,000. The customer's "effective credit limit" is $10,000 because it is less than the group limit. Blocking rules first check the group limit and then the individual customer credit limit. Any sales order over $10,000 will be blocked. 

## Individual credit limit is greater than the customer group credit limit
Let's assume the customer has an individual credit limit of $20,000. The customer is assigned to a Customer credit group and the group's limit is $15,000. The customer's effective credit limit is $15,000 because the blocking rules always check the customer group credit limit first. Any sales orders over $15,000 will be blocked. 

## Individual credit limit set to 0.00 and mandatory credit limit is set to Yes
If a customer has an individual credit limit set to 0.00 with the Mandatory credit limit set to Yes their effective credit limit is 0.00. Even if they are assigned to a customer credit group the credit limit is $0.00. This allows the customer to be part of a group but all orders will go to Credit management.

## Individual credit limit is set to 0.00 and Unlimited credit limit is set to Yes
If a customer has an individual credit limit set to 0.00 but the Unlimited credit limit option is set to Yes they will will unlimited credit. Even if they are assigned to a customer credit group the credit limit is unlimited. 

## Individual credit limit is set to 0.00 and part of a customer credit group
Let's assume a customer has an individual credit limited set to 0.00, the Unlimited credit set to No and Mandatory credit limit set to No. The customer is assigned to a customer credit group with a limit of $15,000. The customer's effective credit limit is group limit of $15,000 so any sales orders over this amount would be blocked. 
This allows the credit limit to be managed at the customer group level instead of the individual customer level. All customers assigned to one group share the credit limit. 

