---
# required metadata

title: Add-ins overview
description: Description
author: tonyafehr
manager: AnnBe
ms.date: 01/25/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: NotInTOC
ms.search.region: Global
# ms.search.industry:
ms.author: tfehr
ms.search.validFrom: 2021-02-28
ms.dyn365.ops.version: 10.0.16
---

# Add-ins overview

[!include[banner](../includes/banner.md)]

Add-ins provide a way to extend functionality of Finance and Operations apps. The following topics provide some of examples of add-ins.

- [Planning Optimization overview](https://docs.microsoft.com/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-overview)

- [Inventory Visibility Add-in](https://docs.microsoft.com/dynamics365/supply-chain/inventory/inventory-visibility)

- [Configure export to Azure Data Lake](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/configure-export-data-lake)

- [IoT Intelligence home page](https://docs.microsoft.com/dynamics365/supply-chain/iot/iot-intelligence-home-page)


## Prerequisites for setting up Add-ins

- Be sure that there is at least 1 GB of Dataverse space available, otherwise setup would fail.

- Setup must be done by a user who is assigned to the **Project Owner** role in Lifecycle Services.

- Be sure that the Finance and Operations app user who is trying to perform the set up is one of the admins: Global admin, Dynamics 365 service admin, Power Platform service admin or Delegated admin). Or follow below step for allowing Dataverse environment creation.

    Go to Power Platform admin portal -\> Click on gear icon -\> Power Platform Settings -\>

    ![](media/PowerPlatformSettings.png)

## Setup for Add-ins

1. After the Finance and Operations environment is deployed through Lifecycle Services, go to the **Environment details** page. 

2. In **Power Platform integration** section, click the **Setup** button.

3. In the **Power platform environment setup** pane, select the check box and click **Setup** at the bottom of the pane.

    > [!Note]
    > This will set up the Dataverse environment with dual write setup. This will generally consume around 1 GB of Dataverse space. 

4.  A message appears indicationg that the Power Platform environment is being provisioned. Click **OK**.

    The **Power Platform integration** section of the **Environment details** page now displays a message indicating that the Power Platform enviornment is being provisioned. 
    
5. After a few minutes, refresh the **Environment Details** page. 

6. In the **Power Platform integration** section, notice that the **Status** field says **Environment setup is in progress**. 
     
    It generally takes between 60-90 minutes for the setup to be complete.

7.  AFter the Dataverse environment is provisioned, “Install a new add-in” button would be enabled under “Environment add-ins” section in “Power Platform Integration”  
    
    ![](media/InstallANewAddIn.png)

Note: If you are just planning on installing Add-ins which does not require “Dual write linking”, then that setup does not need to be performed.

## Handling Failures:  
1. Since the setup tries to setup “Dual write”, the “Dual write setup” might fail sometimes after provisioning Dataverse environment. Refer to below screenshot. In those cases “Install a new add-in” button is still enabled to unblock installation of add-ins. If you would like to continue setting up “Dual write” you can just click on “Resume”

![](media/d93a025d176d8fde5d207705f79c44f4.png)

2. Sometimes Dataverse environment provisioning might be failing due t0 capacity/licensing issues. Please logon to PPAC portal to resolve those issue and click on the “Resume” button in Lifecycle services.

