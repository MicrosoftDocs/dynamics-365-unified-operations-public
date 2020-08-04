---
# required metadata

title: Create data integrator project 
description: This topics lists the steps that must be completed to create a data inegrator project. 
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
# Create data integrator project (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Complete the following steps to create a data integrator project.

1. Login to Microsoft Dynamics 365 for Finance.

2. Open the **Data entities** page (**Workspaces > Data Management > Data entities**). Wait until the all the data entities have refreshed before continuing to the next step. 

3. Open the [Power Apps](https://make.powerapps.com/) portal.

	1. Choose the appropriate environment.
  
	2. On the left hand navigation pane select Data > Connections.  
		a. Connect to appropriate instances of:
			i. Dynamics 365
			ii. Dynamics 365 for Fin & Ops

4. Open the [Power Apps environments](https://admin.powerapps.com/environments).

  1. Select Data Integrator
      a. Select Connection sets
      b. Click New connection set
        i. Provide connection name
        ii. Select the appropriate connections for
          i. Dynamics 365
          ii. Dynamics 365 for Fin & Ops
        iii. Chose the appropriate Organization mapping
        iv. Click Create

  2. Go to: Projects tab
      a. Create data integration projects for following templates using the connection set created above:
        i. Customer payment insights results (CDS to Fin and Ops)
        ii. Cash flow time series results (CDS to Fin and Ops)
        iii. Budget time series results (CDS to Fin and Ops)
      b. Set appropriate Scheduling for each project.


#### Privacy notice
Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
