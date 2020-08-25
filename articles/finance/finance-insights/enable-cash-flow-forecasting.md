---
# required metadata

title: Enable Cash flow forecasts 
description: This topics lists the steps to complete to enalbe the Cash flow forecasts feature within Finance Insights. 
author: ShivamPandey-msft
manager: AnnBe
ms.date: 07/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-24
ms.dyn365.ops.version: AX 10.0.13

---
# Enable Cash flow forecasting (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Complete the following steps to enable the Cash flow forecasts capability within Finance Insights. <!--*Do customers need to complete configuration steps before they enable this feature?*-->

1. Using information from the Llifecycle Services (LCS) environment page, connect to the primary Azure SQL instance for the environment. Run the following T-SQL commands to enable flights for the sandbox environment (may need to enable access in LCS for your IP before connecting remotely to AOS) :
	INSERT INTO SYSFLIGHTING (FLIGHTNAME, ENABLED) VALUES ('CashflowInsightsFeature', 1), ('BudgetIntelligentBudgetRegisterProposalFeature', 1)

2. Go to the **Feature management** workspace and complete the following steps. 
   - Click 'Check for updates'.
   - Turn ON following features:
     - New grid control
     - (Preview) Grouping in grids
     - Customer payment predictions (preview)
     - Cash flow forecasts (preview)

3. Open the Cash flow forecasts setup page (**Cash and bank management > Cash flow forecast setup**) and add liquidity accounts you want to include in the forecasts.

 > [!NOTE]
 > If liquidity accounts are setup, the cash flow cannot be generated.

   Link to the Cash flow forecasting content.

4. Open the **Cash flow forecasts** page (**Cash and bank management > Setup > Finance Insights (preview) > Cash flow forecasts (preview)**).
   - On the Cash flow forecast tab
   - Click Enable feature
   - Click Create prediction model
	
    For more information, see Cash flow forecasts. 

 #### Privacy notice

Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
