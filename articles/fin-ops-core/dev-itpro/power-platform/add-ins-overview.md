---
# required metadata

title: Add-ins overview
description: This topic provides information about add-ins, which can be used to extend the functionality of Finance and Operations apps.
author: ankugo
manager: AnnBe
ms.date: 01/26/2021
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
ms.author: ankugo
ms.search.validFrom: 2021-02-28
ms.dyn365.ops.version: 10.0.15
---

# Add-ins overview

[!include[banner](../includes/banner.md)]

Add-ins provide a way to extend the functionality of Finance and Operations apps. The following topics provide some examples of add-ins:

- [Planning Optimization overview](https://docs.microsoft.com/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-overview)
- [Inventory Visibility Add-in](https://docs.microsoft.com/dynamics365/supply-chain/inventory/inventory-visibility)
- [Configure export to Azure Data Lake](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/configure-export-data-lake)
- [IoT Intelligence home page](https://docs.microsoft.com/dynamics365/supply-chain/iot/iot-intelligence-home-page)

## Prerequisites for setting up add-ins

- Make sure that at least 1 gigabyte (GB) of Microsoft Dataverse space is available. Otherwise, setup will fail.
- The setup must be done by a user who is assigned to the **Project Owner** role in Microsoft Dynamics Lifecycle Services (LCS).
- Make sure that the Finance and Operations app user who is trying to do the setup is one of the following admins: global admin, Dynamics 365 service admin, Microsoft Power Platform service admin, or delegated admin.

    Alternatively, sign in to the Power Platform admin center, select the **Settings** button (gear symbol), select **Power Platform settings**, and set the options to enable users to create Dataverse environments.

    ![Power Platform settings](media/PowerPlatformSettings.png)

## Set up add-ins

> [!NOTE]
> If the add-ins that you're planning to install don't require "dual-write linking," you don't have to complete this procedure.

1. After the Finance and Operations environment has been deployed through LCS, open the **Environment details** page in LCS.
2. In the **Power Platform integration** section, select **Setup**.
3. In the **Power platform environment setup** dialog box, select the check box, and then select **Setup** at the bottom of the dialog box.

    > [!NOTE]
    > The Dataverse environment is set up so that it includes dual-write functionality. Typically, this setup consumes about 1 GB of Dataverse space.

4. When you receive a message that states that the Microsoft Power Platform environment is being provisioned, select **OK**.

    The **Power Platform integration** section of the **Environment details** page now shows a message that states that the Microsoft Power Platform environment is being provisioned.

5. After a few minutes, refresh the **Environment details** page.
6. In the **Power Platform integration** section, notice that the value of the **Status** field is **Environment setup is in progress**.

    Typically, the setup takes between 60 and 90 minutes.

    After the Dataverse environment is provisioned, the **Install a new add-in** button becomes available in the **Power Platform integration** section.

    ![Install a new add-in button](media/InstallANewAddIn.png)

## Troubleshoot the setup

- Because the setup process tries to set up dual-write functionality, the dual-write setup might sometimes fail after the Dataverse environment is provisioned, as shown in the following illustration. In these cases, the **Install a new add-in** button is still available, so that you can unblock the installation of add-ins. If you want to continue to set up dual-write functionality, select **Resume**.

    ![Dual-write setup failure](media/Error.png)

- Provisioning of the Dataverse environment might sometimes fail because of capacity and licensing issues. In these cases, sign in to the Power Platform admin center, and fix the issues. Then, in the **Power Platform integration** section of the **Environment details** page in LCS, select **Resume**.
