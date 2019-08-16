---
# required metadata

title: Revenue recognition setup 
description: 
author: kweekley
manager: aolson
ms.date: 08/24/2018
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  Customer
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2018-08-30
ms.dyn365.ops.version: 8.0.4

---

# Revenue recognition setup
This topic describes the setup options and their implications for Revenue recognition.  

The Revenue recognition module includes the following setup options. 
- Revenue recognition journals
- Parameters for revenue recognition
- Revenue schedules 
- Inventory setup
 > - Item groups and released products
 > - Defining revenue schedule
 > - Defining revenue price
 >  > - Posting profiles
 >  > - Bundles
 > - Bundle components
 > - Bundle item
- Project setup

A new Revenue recognition module has been added, which includes menu items for all the setup. 

## Revenyue recognition journals
A new journal type has been introduced for revenue recognition. The journal is required and will be used in two scenarios. 

The first scenario occurs when after the contractual obligations are complete, the deferred revenue is recognized by creating a revenue recognition journal based on the details on the revenue schedule. The journal contains an accounting entry to move the balance from the deferred revenue ledger account to the revenue ledger account. 

The second scenario occurs when a journal is created after a reallocation occurs. Reallocation occurs when an additional sales order line is added to a previously invoiced sales order, or when a new sales order is created with a line that is part of the original contract. If an invoice has been posted before the new sales order line is added, a correcting accounting entry must be created for the posted customer invoice.

The journal is set up under **Revenue recognition > Setup > Journal names**. The journal type must be defined as Revenue recognition. The revenue recognition journal allows you to select the posting layer to post to. 

## Parameters for revenue recognition
Revenue recognition settings are specified using the General ledger parameters page.  The General ledger parameters page can be opened from **Revenue recognition > Setup > General ledger parameters > Revenue recognition**. Here are the available options. 


