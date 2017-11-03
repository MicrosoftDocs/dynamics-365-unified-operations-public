---
# required metadata

title: Set up fraud alerts
description: This topic explains how to set up rules to alert customer service representatives of potentially fraudulent information when orders are processed. You can define specific codes to use to automatically or manually put suspicious orders on hold. 
author: josaw1
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 79103
ms.assetid: e342af8d-7498-4d20-8483-ab368429c578
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Set up fraud alerts

[!include[banner](includes/banner.md)]

This topic explains how to set up criteria and rules to place potentially fraudulent sales orders on hold for further review. Fraud review functionality is used to determine the validity of information in a sales order. If the information in the sales order appears to be questionable based on an organization’s fraud criteria and rules, the order may be put on hold for further review by an administrator.

> [!NOTE]
> This feature can only be used with Retail Call Center channel sales order processing. 

When the Call Center channel is defined, **Enable Order Completion** must be set to **Yes**. When order completion is enabled, users can view the order recap and click **Submit** to finalize the order. Users will also be provided options to manually place the sales order on fraud review hold. Sales orders keyed in by a Call Center user are processed through fraud check rules and criteria during the submit process.

There are two types of fraud criteria that the system will reference to check if the order should be held for fraud review:

-   **Static rules** use a specific value, such as a phone number that has been blacklisted or an email address that has been flagged as being known as used for past fraudulent transactions. On the **Static Fraud Data** page, fraud information can be added manually or through data import, with scores attached to the fraudulent information. If fraud checking is turned on, every sales order entered will be compared to the static data. If the data is found in either the customer’s billing or delivery address, or if the data is found in the delivery address on the sales line, the scores of all unique matches will be summed.  
-   **Dynamic rules** are composed from variables and conditions defined for those variables. With dynamic rules, other criteria not defined in the static rules can be checked. More complex “AND/OR” statements can be used to consider multiple conditions to determine if there is a positive match against the rule criteria and the sales order being submitted. For example, if a user wants to hold for fraud review all orders for customers that are tied to a specific customer group value and that ordered a specific product, the conditions to validate customer and validate products would be defined on the **Rules** page with an “AND” condition. The order would fall into fraud hold only if both conditions were true and if the score value assigned to the rule put the order’s total fraud score over the minimum fraud score as defined in Call Center parameters.

A call center user may also manually place an order into the fraud hold queue. If the user entering the order believes the customer placing the order may be suspicious and wants someone else to further review the validity of the order before it is processed, the user entering the order can choose the **Manual Fraud Hold** option from the **Holds** dropdown menu on the **Sales Order Summary** page (this appears after the **Complete** order function is called). The user will be prompted to enter a note to further explain why they feel the order may be fraudulent so that the reviewer has more context.

All orders held through manual fraud hold or by systematic calculation of fraud scores will appear on the **Order Holds** page, where the order can be reviewed and then either canceled or released to processing.

> [!NOTE]
> Use of multiple rules or overly complex rules will result in poor system performance when sales orders are submitted. The fraud alert feature hasn't been optimized to handle a large volume of static fraud data entries and many active rules. It’s important to remember that every rule is evaluated during the submit function of call center sales order entry. The rules are evaluated against the sales order header and all order lines. The more rules there are and the more complex the rule statements are, the longer it will take to process. If you have a large number of line items on your order, and a large number of active rules and static data entries, this systematic process of reviewing and validating all of the data and calculating a fraud score can have a severe performance impact.  Organizations using this feature should always test and confirm that the order submission processing time is acceptable before applying any changes to rules or static fraud criteria into the production environment.
