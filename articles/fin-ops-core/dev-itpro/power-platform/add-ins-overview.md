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

Add-ins provide a way to extend functionality of Finance and Operations apps. Below
are some of examples of add-ins.

- **Planning optimization**: [Planning Optimization overview](https://docs.microsoft.com/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-overview)

- **Inventory management**: [Inventory Visibility Add-in](https://docs.microsoft.com/dynamics365/supply-chain/inventory/inventory-visibility)

- **Export to Azure Data Lake**: [Configure export to Azure Data Lake](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/configure-export-data-lake)

- **IOT Intelligence**: [IoT Intelligence home page](https://docs.microsoft.com/dynamics365/supply-chain/iot/iot-intelligence-home-page)



## Prerequisites for setting up Add-ins

1.  Please ensure that there is at least 1 GB of Dataverse space otherwise setup
    would fail

2.  Setup must be done by users having “Project Owner” role in Lifecycle
    Services.

3.  Please ensure that Finance & Operations user who is trying to setup is one
    of the admin(Global admins, Dynamics 365 service admins, Power Platform
    service admins or Delegated admins) Or follow below step for allowing
    Fataverse environment creation.

    Go to Power Platform admin portal -\> Click on gear icon -\> Power Platform
    Settings -\>

    ![](media/c4f534080246691fb6d2492d5b720ed6.png)

## Setup for Add-ins

1.  Once the finance and operations environment is deployed thru lifecycle
    services, go to the environment details page. There would be a section
    called “Power Platform Integration”

    ![](media/d5faf02c8e6178282a7048b34eb6c68e.png)

2.  Click on “Setup” button, this would open a slider, click on the check box
    and click “Setup” button at the bottom of slider.

    Note: This would setup Dataverse environment with dual write setup. This
    would generally  
    consume around 1 GB of Dataverse space  
    
    ![](media/eca00435b0b4d10da2f09ecbb6e35fdc.png)

3.  It would show a pop up message like below. Click “OK”

    ![](media/b966f146466402cca93e7b3805e5f47a.png)

1.  You can see below message in “Power Platform Integration” section. Please
    give a few minutes before refreshing the page so that the status of setup
    can be shown.

    ![](media/39e6f8080e4caef11a952dd454cadb03.png)

2.  After few minutes once page is refreshed, the status should change to
    “Environment setup is in progress”. It generally takes around 60 to 90
    minutes for the setup to be complete.   
    
    ![](media/ea010be87dd534681b7f91203f8ae850.png)

3.  Once the Dataverse environment is provisioned, “Install a new add-in” button
    would be enabled under “Environment add-ins” section in “Power Platform
    Integration”  
    ![](media/c5a4117ef8a77110685537f4a62b0771.png)

Note: If you are just planning on installing Add-ins which does not require
“Dual write linking”, then that setup does not need to be performed.

Handling Failures:  
1\. Since the setup tries to setup “Dual write”, the “Dual write setup” might
fail sometimes after provisioning Dataverse environment. Refer to below
screenshot. In those cases “Install a new add-in” button is still enabled to
unblock installation of add-ins. If you would like to continue setting up “Dual
write” you can just click on “Resume”

![](media/d93a025d176d8fde5d207705f79c44f4.png)

2\. Sometimes Dataverse environment provisioning might be failing due to
capacity/licensing issues. Please logon to PPAC portal to resolve those issues
and click on the “Resume” button in Lifecycle services.

