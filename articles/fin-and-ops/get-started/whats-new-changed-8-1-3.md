---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations version 8.1.3 (December 2018)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 8.1.3. This version was released in December 2018.
author: tonyafehr
manager: AnnBe
ms.date: 12/04/2018
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
# What's new or changed in Dynamics 365 for Finance and Operations version 8.1.3 (December 2018)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 8.1.3. This version was released in December 2018 and has a build number of 8.1.227.

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

## Russian-specific features
This release contains the following feautres specific for Russia:

### Accounts receivable debts tax registers. AR bad debts writing-off
 - Tax registers: Accounts receivable inventory act in tax and business accounting; Bad debts reserve calculation in tax and business accounting; Bad debts reserve movement in tax and business accounting; Accounts receivable movement in tx and business accounting
 - Procedure for writing-off AR bad debts
 
### Accounts payable debts tax registers. AP bad debts writing-off
 - Tax registers: Accounts payable inventory act; Accounts payable debt movement 
 - Procedure for writing-off AP bad debts 

### Client-bank interface and reconciliation procedure
Added the interface and GER configurations examples required to use the Client-Bank functionality.
To use this feature, following GER configurations should be imported from LCS and selected in the settings:
•	Payment model.version.22
•	Payment model mapping to destination (RU).version.22.4
•	Bank statement (RU).version.22.6
•	Payment order (RU).version.22.4
