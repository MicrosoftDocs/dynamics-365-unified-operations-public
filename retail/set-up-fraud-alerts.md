---
# required metadata

title: Set up fraud alerts
description: This topic explains how to set up rules to alert customer service representatives of potentially fraudulent information when orders are processed. You can define specific codes to use to automatically or manually put suspicious orders on hold. 
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2041
ms.search.scope: AX 7.0.0, Operations, Core, Retail
# ms.tgt_pltfrm: 
ms.custom: 79103
ms.assetid: e342af8d-7498-4d20-8483-ab368429c578
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up fraud alerts

[!include[banner](includes/banner.md)]


This topic explains how to set up rules to alert customer service representatives of potentially fraudulent information when orders are processed. You can define specific codes to use to automatically or manually put suspicious orders on hold. 

Before you set up and use fraud checking rules, you must enable fraud checking and define the basic fraud checking values in the call center parameters. There are two types of fraud rules:

-   **Static rules** use a specific value, such as a phone number that has been blacklisted.
-   **Dynamic rules** can be composed from variables and conditions.

Before you create a dynamic rule, you must create the variables and conditions that define who the rule applies to and when the rule should be applied. For example, you want to create a rule to require that any sales order that customer 1202 places that is worth 1,000.00 or more be put on hold until the customer payment can be verified. In this case, the variables are customer 1202 and an order total of 1,000.00. The condition specifies that if customer 1202 places an order, and the total amount of the order is equal to or more than 1,000.00, the sales order must be put on hold until the customer payment can be verified.



