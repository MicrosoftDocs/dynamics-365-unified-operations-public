---
# required metadata

title: Edit financial dimensions on retail transactions
description: This topic describes the feature to edit financial dimensions on retail transactions in Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 10/20/2020
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 

---
# Edit financial dimensions on retail transactions
To edit the financial dimensions for retail store transactions, please follow the following steps:
1.	Navigate to **Financial dimensions configuration for integrating applications** menu item, select the active **Default Dimensions integration** record and make sure that all dimensions that are wanted on the Excel sheet for editing are in the **Selected** column. For more details, please refer to the link: https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/financial/financial-dimension-configuration-integration#data-entities
2.	Download & open the Excel file from the **Statements page**, **Retail transactions** page or the **Transaction validation failures** tile on the **Store financials** workspace   
3.	To change the Transaction header financial dimension please click on the **Design** button and then click on the pencil button that is beside the "Transaction (auditable)" row.
4.	Find the field **FinancialDimensionDisplayValue**, select a cell in the header part of the Excel sheet and click on **Add label**
5.	Select a cell below the cell chosen in the step above and click on **Add Value** and click **Refresh**   
6.	The financial dimensions will be added to the Excel sheet and these can now be edited and published
7.	To change the dimensions on the Transaction lines, select the **Sales transactions (auditable)** row and click on the pencil button and repeat steps 4-6 as per above
8.	To change the dimensions on the Payment lines, select the **Payment transactions (auditable)** row and click on the pencil button and repeat steps 4-6 as per above
