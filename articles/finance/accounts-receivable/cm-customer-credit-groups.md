---
# required metadata

title: Customer credit groups
description: 
author: mikefalkner
manager: AnnBe
ms.date: 09/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschloma
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Customer credit groups

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

## Customer credit groups

You can define a group of customers so that members of the group can share a credit limit. In addition, the individual credit limit defined on the customer invoice account is also considered. Members of a customer credit group can be selected from different legal entities. When you add a customer to the list of customers in the customer credit group, the credit limit expiration date for each customer will be changed to the expiration date that is assigned to the group. 

You can set up the customer credit groups on the **Credit management > Customer credit groups > Customer credit groups** page.

- Enter a **Group number** and a **Description** of the group.

- Enter the **Credit limit** and **Currency** that will be used when the system checks the credit limit for any member of the group.

- Enter the **Credit limit to date**, which is the date that the credit limit expires. Customer credit groups must have expiration dates.

After the customer credit group has been set up, you can add customers to the group by specifying their legal entity and customer account ID. When adding a new customer to the customer credit group, the system will search for the same customer account across all legal entities and prompt you to add them to the customer credit group.

Open the **Aged balances** menu to view the details of the aging balance for all invoice customers within the customer credit group. The **Aging balance** page shows a summary of the invoice customer account aged balances.
