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
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail
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

This topic explains how to set up criteria and rules to place potentially fraudulent sales orders on hold for further review.  This feature currently works only with Retail Call Center channel sales order processing.  When defining the Call Center channel, the **Enable Order Completion** option must be set to **Yes** for this feature to work.   Enabling the Order Completion process allows users to view the order recap and use the Submit button to finalize the order, as well as providing options for the user to manually place the sales order on Fraud Review hold.  Sales orders keyed in by a Call Center user are processed through fraud check rules and criteria during the order **Submit** process.

Fraud functionality is used to determine the validity of information in a sales order. If the information in the sales order appears to be questionable based on your organizations fraud criteria and rules, the order can be put on hold for further review by an 
administrator.

There are two types of Fraud criteria that the system will reference to check if the order should be held for Fraud review:

-   **Static rules** use a specific value, such as a phone number that has been blacklisted or an email address that has been flagged as being known as used for past fraudulent transactions.  In the **Static Fraud Data** form, fraud information can be added manually or through data import, with scores attached to the fraudulent information. If fraud checking is turned on, every sales order entered will be compared to the static data. If the data is found in either the customer’s billing or delivery address, or if the data is found in the sales line’s delivery address, the scores of all unique matches will be summed.  
-   **Dynamic rules** can be composed from variables and conditions defined for those variables. Dynamic rules will allow you to check other criteria not defined in the Static rules form and allow for more complex “AND/OR” statements to consider multiple conditions to determine if there is a positive match against the rule criteria and the sales order being submitted.   For example, if you wanted all orders for customers that were tied to a specific Customer Group value that ordered a specific Product to be held for fraud, the conditions to validate customer and validate products could be defined in the **Rules** form with an “AND” condition.  The order would fall into Fraud hold only if both conditions were true and if the score value assigned to the rule put the order’s total fraud score over the minimum fraud score as defined in Call Center parameters.

A call center user may also manually place an order into the fraud hold queue.  If the order entry user believes the customer placing the order may be suspicious and wants someone else to further review the validity of the order before it is processed, they can choose the **Manual Fraud Hold** option from the **Holds** dropdown menu on the **Sales Order Summary** form which appears after the **Complete** order function is called.  When doing this, they will be prompted to enter a note to further explain why they feel the order may be fraudulent.  This note can better inform the person reviewing the hold as to why it might be fraudulent.

All orders held through manual fraud hold or by systematic calculation of fraud scores will appear in the **Order Holds** form which allows for someone to review the order and determine the appropriate action such as canceling the order or releasing it to processing if desired.

**Note:** Use of multiple rules or overly complex rules will result in poor system performance when submitting sales orders.  This feature has not been optimized to handle a large volume of static fraud data entries and many active rules.  It’s important to remember that every rule is being evaluated during the “Submit” function of call center sales order entry.  The rules are being evaluated against the sales order header and all order lines.   The more rules you have and the more complex the rule statements are, the longer it will take to process.  If you have a large number of line items on your order, and a large number of active rules and static data entries, this systematic process of reviewing/validating all of the data and calculating a fraud score can have a severe performance impact.  Organizations using this feature should always test and confirm that the order submission processing time is acceptable before applying any changes to rules or static fraud criteria into your production environment.
