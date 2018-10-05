---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations version 8.1.1 (October 2018)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 8.1.1. This version was released in October 2018.
author: tonyafehr
manager: AnnBe
ms.date: 10/05/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: b364a31c-52d3-45c5-b698-64c5242c592a
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2018-10-01 
ms.dyn365.ops.version: Release 8.1.1

---
# What's new or changed in Dynamics 365 for Finance and Operations version 8.1.1 (October 2018)

[!include [banner](../includes/banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 8.1.1 (October 2018). This version was released in October 2018 and has a build number of XXX.

### Announcing the Dynamics 365 October '18 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform? 

[Check out the October '18 release notes](https://go.microsoft.com/fwlink/?linkid=870424). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning. 

## Platform update 21
Microsoft Dynamics 365 for Finance and Operations version 8.1.1 includes Platform update 21. To learn more about Platform update 21, see 
[What's new or changed in Dynamics 365 for Finance and Operations platform update 21 (October 2018).](whats-new-platform-update-21.md)

## Ledger settlements
Ledger settlements let you match debit and credit transactions in the general ledger, and mark them as settled. In this way, you can make sure that related transactions have been cleared. You can also reverse settlements if they were made by mistake.

## Simulate posting
You can find Simulate posting on the Validate menu for most journals. When you validate a journal using the Validate function, the system tests the journal for specific error conditions. If you use the Simulate posting function, the system runs all of the same processes that are run during posting without actually posting the journal. You can then review the posting messages that are displayed, fix any errors that you find, and then click the Post menu to post the journal.

Simulate posting is not available for batch processing. However, there is code available to simulate posting in batch and developers can extend the code to add that functionality.
