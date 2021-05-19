---
# required metadata

title: Dual-write setup from Lifecycle Services
description: This topic explains how to set up a dual-write connection from Microsoft Dynamics Lifecycle Services (LCS).
author: RamaKrishnamoorthy
ms.date: 05/11/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-01-06

---

# Dual-write setup from Lifecycle Services

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes the steps to enable the Dual-write application directly from Lifecycle Services (LCS).  

## Prerequisites

You must complete the Power Platform Integration setup as defined below:
* [Power Platform Integration - Enable during environment deployment](../../power-platform/overview.md#Enable-during-enviornment-deployment)
* [Power Platform integration - Set up after environment deployment](../../power-platform/overview.md#Set-up-after-environment-deployment)

## Setup Dual-write application for new Dataverse environments

Follow these steps to perform the setup from LCS environment details page:

1. Expand the Power Platform Integration section and the **Setup Dual-write application** button should be available to you. 
<img src="media/powerplat_integration_step2.png" width="500px" /><br/>

Click this button, and agree to the terms and conditions then click **Configure**.
2. A message indicating that the setup has been triggered should be presented, click **Ok** to continue.
3. You may monitor the progress by refreshing the environment details page periodicially.  Setup typically takes 30 minutes or less.  
4. Once finished, you will see if the setup was successful or if there was a failure and a related error message displayed.  
5. If successful, a new button will appear titled **Link to Power Platform environment**.  
<img src="powerplat_integration_step3.png" width="500px" /><br/>

Use this button to create the link between Dataverse and the current environment's databases.  This typically takes less than 5 minutes.  
6. If successful, a hyperlink will be made available for you to login to the Dual-write administration area in the Finance & Operations environment.  From there you can setup entity mappings and more.

## Setup Dual-write application for existing Dataverse environments

Currently, this is only available via opening a support ticket.  Please provide your Finance & Operations environment ID and environment name from Lifecycle Services, and the Dataverse organization ID or Power Platform Environment ID from Power Platform Admin Center in a support ticket and request that to become the instance used for Power Platform Integration.

> [!NOTE]
> You can't unlink environments by using LCS. To unlink an environment, open the **Data integration** workspace in the Finance and Operations environment, and then select **Unlink**.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]