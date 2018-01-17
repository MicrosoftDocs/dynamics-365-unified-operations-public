---
# required metadata

title: Configuration steps for Retail developers working on cloud-hosted development machines
description: This topic demonstrates the configuration steps for Retail developers working on cloud-hosted development machines.
author: mugunthanm 
manager: AnnBe
ms.date: 01/16/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: 
ms.search.validFrom: 2017-12-08
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---


# Configuration steps for Retail developers working on cloud-hosted development environment with no administrator access

As of platform update 12, customers will no longer have access to virtual machine (VM) admin accounts on development or build environments that are running in Microsoft subscriptions. This restriction only applies to new deployments of platform update 12 (or newer) environments, meaning that environments deployed before the update, but have been updated to platform 12, will still have admin access.
You can remote desktop (RDP) to these restricted environments using a non-admin user provided on the Lifecycle Services (LCS) environment page. This blog article contains more information on how to access these VMs: 
https://blogs.msdn.microsoft.com/lcs/2017/10/31/restricted-admin-access-with-platform-12-updates/”

Retail developers do not have administsrative access to cloud-hosted development virtual machines (VMs). Modern POS (MPOS) development is possible if you use Cloud POS. Before starting the development for any retail application, configure Cloud POS as follows:


1. Open Visual Studio and click **View** > **Application Explorer**. Wait for Internet Information Services (IIS) Express to start with all the Retail websites deployed. You should see the IIS tray icon in the task bar with all the Retail websites running, such as Cloud POS and Retail Server.
4. To debug CRT/RS extensions, attach the CRT/RS project to the IIS Express process.
5. When you open the Cloud POS project from the Retail SDK, IIS Express may fail with the following error. 

    ```
    Filename: redirection.config
    Error: Cannot read configuration file
    ``` 
    To resolve this issue, follow these steps:
    1. Close Visual Studio.
    2. Rename the **%userprofile%\Documents\IISExpress\config** folder. Do not delete the files because you will copy the **applicationhost.config** file to a new location in step *iv*.
    3. Start Visual Studio again with the Cloud POS project. The **%userprofile%\Documents\IISExpress\config** folder will be recreated with the default config files.
    4. Copy the **applicationhost.config** file from the folder that you renamed in step *ii*, to the folder created in step *iii*. 

Also, the cloud-hosted development environments are missing Typescript version 2.2.2 and windows host file is missing cloud POS URL to do local debugging. To fix these issues, follow the below steps:

    1. Navigate to lcs.dynamics.com and sign in with your account.
    2. Under projects, select the project where your dev environment id deployed.
    3. In More tools section, click the Asset library tile.
    4. Select the asset library type as Software deployable package and click Import button under Software deployable package files.
    5. In the Shared asset library list, select Developer topology prerequisite and click the pick button.
    6. Navigate back to and under environments section, click your dev environment.
    7. Once navigated to your environment details page, Click the Maintain tab and select Apply updates.
    8. From the list select the Developer topology prerequisite and click Apply.
    
    This package will install typescript 2.2.2 and update the windows host file with cloud POS URL. 
    Note: This will take few mins to get the package applied in the environment.
    
    

