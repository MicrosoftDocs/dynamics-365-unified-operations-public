--- 
# required metadata 
 
title: Create, calculate, and post statements for a retail store
description: This article describes the manual steps for creating, calculating, and posting a statement for a store. 
author: jashanno
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: RetailChannelOperationsWorkspace, RetailStatementTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create, calculate, and post statements for a retail store

[!include [banner](../includes/banner.md)]

This article describes the manual steps for creating, calculating, and posting a statement for a store. There are also batch jobs that can be configured for the same tasks. The steps for configuring and running the batch jobs can be found in other articles. To complete this procedure, you must have transactions that were completed in POS and then pulled into Dynamics 365 Commerce. This recording uses the USRT company in demo data.

1. Select **Store financials** from the home page.
2. Select **New statement**.
3. In the **Store number** field, select a option from the drop-down.
4. Select **OK**.
5. The **Setup** group has the settings that control what transactions are included in the statement and how they are grouped into statement lines. You can open the **Setup** group and change these settings, or you can use the defaults.  
    - The **Statement method** field defines how the statement lines will be grouped.  
    - Select a staff member or a register in the **staff/register** field if you want to calculate a statement only for the specific staff member or register.  
6. In the **Closing method** field, select an option.
7. Select **Calculate statement** from the Action Pane.
8. Select **Yes**.
    - After calculating the statement, there should be lines created with total amounts for each payment method and statement method that was used.  
    - Enter a counted amount in each line if it needs to be entered or updated. The counted field is populated with amounts from tender declarations done in POS.  
9. Select **Post statement** from the Action Pane.
10. Select **Close**.
11. Close the pane.
12. At the home page, select **Store financials**.
13. Select the **Posted statements** tab.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]