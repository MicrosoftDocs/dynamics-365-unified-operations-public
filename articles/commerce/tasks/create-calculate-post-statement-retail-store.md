--- 
title: Create, calculate, and post statements for a retail store
description: Learn how to manually create, calculate, and post a statement for a store in Microsoft Dynamics 365 Commerce. 
author: jashanno
ms.date: 02/06/2026
ms.topic: how-to 
ms.search.form: RetailChannelOperationsWorkspace, RetailStatementTable   
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template
---
# Create, calculate, and post statements for a retail store

[!include [banner](../includes/banner.md)]

This article describes the manual steps for creating, calculating, and posting a statement for a store in Microsoft Dynamics 365 Commerce.

You can also configure batch jobs for the same tasks.

To complete the following procedure, you must have transactions that were completed in POS and then pulled into Dynamics 365 Commerce. The procedure uses the USRT company in demo data.

To create, calculate, and post statements for a retail store, follow  these steps:

1. In Commerce headquarters, go to **Store financials**.
1. Select **New statement**.
1. In the **Store number** field, select an option from the drop-down list.
1. Select **OK**.
1. The **Setup** group has the settings that control what transactions are included in the statement and how they're grouped into statement lines. You can open the **Setup** group and change these settings, or you can use the default settings.  
    - The **Statement method** field defines how the statement lines are grouped.  
    - Select a staff member or a register in the **staff/register** field if you want to calculate a statement only for the specific staff member or register.  
1. In the **Closing method** field, select an option.
1. Select **Calculate statement** from the Action Pane.
1. Select **Yes**.
        - After calculating the statement, the system creates lines with total amounts for each payment method and statement method you used.    
    - Enter a counted amount in each line if it needs to be entered or updated. The counted field is populated with amounts from tender declarations done in POS.  
1. Select **Post statement** from the Action Pane.
1. Select **Close**.
1. Close the pane.
1. At the home page, select **Store financials**.
1. Select the **Posted statements** tab.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
