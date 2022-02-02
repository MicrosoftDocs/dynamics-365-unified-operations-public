---
# required metadata

title: Customer credit groups
description: This topic provides information about customer credit groups.
author: JodiChristiansen
ms.date: 04/14/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschloma
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Customer credit groups

[!include [banner](../includes/banner.md)]

You can define groups of customers who have a shared credit limit. The individual credit limit that is defined on the customer invoice account is also considered.

Members of a customer credit group can be selected from different legal entities. When you add a customer to the list of customers in the customer credit group, the expiration date of the credit limit for each customer is changed to the expiration date that is assigned to the group.

You can set up customer credit groups on the **Customer credit groups** page (**Credit management \> Customer credit groups \> Customer credit groups**).

1. In the **Group number** and **Description** fields, enter an identifier and description for the group.
2. In the **Credit limit** and **Currency** fields, enter the credit limit and currency that should be used when the system checks the credit limit for any member of the group.
3. In the **Credit limit to date** field, enter the date when the credit limit expires. Customer credit groups must have an expiration date.

After you've finished setting up a customer credit group, you can add customers to it by specifying their legal entity and customer account ID. When you add a new customer to a customer credit group, the system searches for the same customer account across all legal entities and prompts you to add it to the customer credit group.

Use the **Aged balances** menu to view the details of the aging balance for all invoice customers in a customer credit group. The **Aging balance** page shows a summary of the aged balances for the invoice customer accounts.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
