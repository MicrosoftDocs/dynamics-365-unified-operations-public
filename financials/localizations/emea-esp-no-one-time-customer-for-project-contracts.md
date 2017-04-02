---
# required metadata

title: One-time customers
description: This topic provides information about one-time customers.  
author: ShylaThompson
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CustTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 264394
ms.assetid: 28357e20-5e7e-4fe9-bbdf-d4812951369e
ms.search.region: Spain
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# One-time customers

This topic provides information about one-time customers.  

A one-time customer is a customer who does not have a long-term relationship with your company. For one-time customers, you typically don't need to save information like address, contact, or tax exempt details. To indicate that a customer is a one-time customer, complete the following steps:

1.  Open the **All customers** page.
2.  Select a customer name to open the customer's record.
3.  On the **Miscellaneous details** FastTab, set the **One-time customer** option to **Yes**.
4.  Click **Save**.

**Note:** Before you can post transactions for a one-time customer, you must specify an account to use for one-time customers in the **One-time customer account** field on the **Accounts receivable parameters** page. For Spain, you can restrict users from creating project contracts for one-time customers. To do this, complete the following steps:

1.  Open the **Project management and accounting parameters** page.
2.  Set the **No one-time customer for project contracts** parameter to **True**.
3.  Click **Save**.


