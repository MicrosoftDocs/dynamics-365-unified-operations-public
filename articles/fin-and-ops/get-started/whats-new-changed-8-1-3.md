---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations version 8.1.3 (January 2019)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 8.1.3. This version will be released in January 2019.
author: tonyafehr
manager: AnnBe
ms.date: 12/05/2018
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
ms.assetid: b364a31d-34de-45c5-b698-64c5262c592e
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2018-12-31 
ms.dyn365.ops.version: Release 8.1.3

---
# What's new or changed in Dynamics 365 for Finance and Operations version 8.1.3 (January 2019)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 8.1.3. This version will be released in January 2019 and has a build number of 8.1.227.

To learn about the new features and changes in the latest releases of Microsoft Dynamics 365 for Retail, see [What's new or changed in Dynamics 365 for Retail](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/get-started/whats-new).

### Dynamics 365 October '18 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform? 

[Check out the October '18 release notes](https://go.microsoft.com/fwlink/?linkid=870424). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning. 

### Bug fixes
For information about the bug fixes included in each of the updates that are part of Finance and Operations version 8.1.3, sign in to Lifecycle Services (LCS) and view the [KB article](https://go.microsoft.com/fwlink/?linkid=) (**not yet available**).

### Platform update 23
Microsoft Dynamics 365 for Finance and Operations version 8.1.3 includes Platform update 23. To learn more about Platform update 23, see 
[What's new or changed in Dynamics 365 for Finance and Operations platform update 23 (December 2018)](whats-new-platform-update-23.md).

## Collection letters
You can now set up collection letters at the customer level, so that the collection letter code for each transaction is tracked but the collection letter processing will be based on a single collection letter level that is stored for the customer. 

## Settle remainder
You can settle the amount remaining from settlement activity by applying that amount to a ledger account or another customer. You can settle the remainder when you are settling amounts entered into a journal or when you are only settling open transactions.

## Globalization
### Electronic reporting: import from files in JSON format
You can now configure and ER format to parse incoming files in JSON format. You can then set up ER mappings specifying how information from JSON files is used to update application data.

### Electronic reporting: support country context specific ER model mappings
You can now restrict the usage of an ER model mapping by specifying a particular country context for it. You can now manage for an ER data model many country context specific ER model mappings simultaneously. It allows you isolate country specific logic of data access in a single ER model mapping. Appropriate ER model mapping will be automatically selected when an ER format is executed depending on the country context of a legal entity in scope of which this execution is performed and depending on settings of available ER model mappings.
