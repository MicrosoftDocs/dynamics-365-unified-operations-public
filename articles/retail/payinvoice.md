---
# required metadata

title: Enhancement to Pay Invoices
description: Enhancement to Pay Invoices
author: josaw1
manager: AnnBe
ms.date: 10/31/2018
ms.topic: index-page
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
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 

---
# Enhancement to Pay invoice operation

## Overview

The ‘Pay invoice’ operation that existed in the product supported the payment of a a single open sales order invoice at a time using the POS application. It did not allow the user to pay off multiple sales order invoices in a single POS transaction and nor did it support payment of other customer invoice types like Free text invoice, Project based invoices, Credit notes etc.

The Pay invoice operation has been significantly enhanced to support these scenarios.

**Setup**

The enhancements around the Pay invoice operation can be leveraged by configuring the functionality profile for stores as per the below steps:

1.  Navigate to **Retail > Channel setup > POS setup > POS profiles > Functionality profiles** and choose a profile linked to the stores where you want the users to have the enhanced Pay invoice operation

2.  In the **Functions** tab of the Functionality profiles, there are four new parameters that are introduced and the details for the same are as follows:

    1.  **Sales order invoice**: Setting this field to Yes will allow users to pay one or more sales order-based invoices in a single POS transaction

    2.  **Free text invoice:** Setting this field to Yes will allow users to pay one or more free text-based invoices in a single POS transaction

    3.  **Project invoice:** Setting this field to Yes will allow users to pay one or more project-based invoices in a single POS transaction

    4.  **Sales order credit note:** Setting this field to Yes will allow users to settle multiple sales order-based credit notes against open invoices or process the refund to the customer for the open credit note

**Notes:** The enhancement around Pay invoice operation still does not support payment / settlement of partial amounts for the support document types.
