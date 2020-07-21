---
# required metadata

title: Configuration for Finance Insights (preview)
description: 
author: ShivamPandey-msft
manager: AnnBe
ms.date: 07/20/2020
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
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.13

---
# Configuration for Finance Insights (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Introductory information 

## Deploy Dynamics 365 Finance

Deploy the environments by completing the following steps.

1. Create or update an F&O environment in Lifecycle Services (LCS). The environment needs App Version 10.0.11/Platform Update 35 or later versions.
  
2. The environment must be an HA environment in Sandbox (also known as a Tier-2 environment).
  
Configure the Common Data Service 

1. Create a new Common data services environment in the same Active Directory Tenant.
   a. Go to  https://admin.powerplatform.microsoft.com/  
   
      [![Power Platform Admin Center](./media/power-pltfrm-admin-center.png)](power-pltfrm-admin-center.png)
   
      i. Click +New environment
      ii. Select Sandbox for the environment Type.
           a. Toggle to Yes for Create Database. 
           b. Click Next. 
 	      a) Select Language and Currency.
              b) Leave other options set to the default values.
              c) Click Save.
           c. Navigate to the environment page - refresh environments page and wait until State shows Ready - once ready

   b. Record the CDS Organization ID.
   a. Select the environment and click on Settings.

  
  
