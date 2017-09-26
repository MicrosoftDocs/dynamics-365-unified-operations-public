--- 
# required metadata 
 
title: Create, calculate, and post a statement for a retail store
description: This procedure walks through the manual steps for creating, calculating, and posting a statement for a store. 
author: jashanno
manager: AnnBe 
ms.date: 11/15/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create, calculate, and post a statement for a retail store

[!include[task guide banner](../includes/task-guide-banner.md)]

This procedure walks through the manual steps for creating, calculating, and posting a statement for a store. There are also batch jobs that can be configured for the same tasks. The steps for configuring and running the batch jobs can be found in other topics. To complete this procedure, you must have transactions that were completed in POS and then pulled into Dynamics AX. This recording uses the USRT company in demo data. This procedure may refer to Microsoft Dynamics AX. Please note that Dynamics AX is now called Microsoft Dynamics 365 for Operations.

1. Go to All workspaces > .. > Retail store financials.
2. Click New statement.
3. In the Store number field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.
5. Click OK.
    * The Setup group has the settings that control what transactions are included in the statement and how they are grouped into statement lines. You can open the Setup group and change these settings, or you can use the defaults.  
    * The Statement method field defines how the statement lines will be grouped.  
    * Select a staff member or a register if you want to calculate a statement only for the specific staff member or register.  
6. In the Closing method field, select an option.
7. Click Calculate statement.
8. Click Yes.
    * After calculating the statement, there should be lines created with total amounts for each payment method and statement method that was used.  
    * Enter a counted amount in each line if it needs to be entered or updated. The counted field is populated with amounts from tender declarations done in POS.  
9. Click Post statement.
10. Click Close.
11. Go to Retail and commerce > Channels > Retail store financials.
12. Click the Posted statements tab.

