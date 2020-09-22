---
# required metadata

title: Enable Budget proposal 
description:  
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
# Enable Budget proposals

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists the steps for enabling the Budget proposals feature within Finance Insights. 

1. If your Dynamics 365 Finance deployment is a Service Fabric deployment, you can skip this step. The Finance Insights team should have already tuned ON the flight for you. If you cannot see the features on the Feature management workspace or have issues turning them ON, please contact fiap@microsoft.com. 

	Using information from the Llifecycle Services (LCS) environment page, connect to the primary Azure SQL instance for the environment. Run the following T-SQL commands to enable flights for the sandbox environment (may need to enable access in LCS for your IP before connecting remotely to AOS) :
	INSERT INTO SYSFLIGHTING (FLIGHTNAME, ENABLED) VALUES ('BudgetIntelligentBudgetRegisterProposalFeature', 1)

3. After step 1 from *previous page, **Enabled cash flow forecasting**, then go to the **Feature Management** workspace.

   - Click **Check for updates**.
   - Search for "Budget proposal" and enable that feature.

4. Open the **Budget proposals** page (**Budgeting > Setup > basic Budgeting > Budget proposal (preview)**). Choose **Enable feature**.


#### Privacy notice
Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
