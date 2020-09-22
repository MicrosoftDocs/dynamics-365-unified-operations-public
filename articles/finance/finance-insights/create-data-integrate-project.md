---
# required metadata

title: Create data integrator project 
description: This topic lists the steps that must be completed to create a data integrator project. 
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

This topic lists the steps that must be completed to create a data integrator project. Complete the following steps to create the project.

1. Log in to Microsoft Dynamics 365 for Finance.

2. Open the **Data entities** page (**Workspaces > Data Management > Data entities**). Wait until the all the data entities have refreshed before continuing to the next step. 

3. Open the [Power Apps](https://make.powerapps.com/) portal.
   - Choose the appropriate environment.
   - On the left navigation pane select **Data > Connections. Connect to appropriate instances of:**
     - Dynamics 365
     - Dynamics 365 for Fin & Ops

4. Open the [Power Apps environments](https://admin.powerapps.com/environments).
   - Select Data Integrator
   - Select Connection sets
   - Click New connection set
   - Provide connection name
   - Select the appropriate connections for
     - Dynamics 365
     - Dynamics 365 for Fin & Ops
    - Choose the appropriate Organization mapping
    - Click Create

5. Open the [Power Apps environments](https://admin.powerapps.com/environments).
   - Create data integration projects for following templates using the connection set created above:
     - Customer payment insights results (CDS to Fin and Ops)
     - Cash flow time series results (CDS to Fin and Ops)
     - Budget time series results (CDS to Fin and Ops)
   - Set appropriate Scheduling for each project.


#### Privacy notice
Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
