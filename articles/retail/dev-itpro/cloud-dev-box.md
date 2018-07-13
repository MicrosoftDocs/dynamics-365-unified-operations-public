---
# required metadata

title: Configuration steps for Retail developers working on cloud-hosted development environments with no administrator access
description: This topic demonstrates the configuration steps for Retail developers working on cloud-hosted development machines.
author: mugunthanm 
manager: AnnBe
ms.date: 05/03/2018
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
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2017-12-08
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---
# Configuration steps for Retail developers working on cloud-hosted development environments with no administrator access

[!include [banner](../../includes/banner.md)]

As of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, Platform update 12, customers will no longer have access to virtual machine (VM) administrator accounts on development or build environments that are running in Microsoft subscriptions. This restriction only applies to new deployments of Platform update 12 (or newer) environments. Environments that were deployed before this update, and  have been updated to Platform update 12, will still have administrator access.

You can use a remote desktop (RDP) to access these restricted environments using the non-admin user provided on the Lifecycle Services (LCS) environment page. For more information about environments that don't allow administrator access, see [Development and build VMs that don't allow administrator access FAQ](../../dev-itpro/sysadmin/VMs-no-admin-access.md).

If you deploy any environment using Microsoft azure subscription in LCS then you will not have admin access in the environment. If you need admin access in your environment, please use your Azure subscription and deploy environment using LCS or you use the downloadable VHD and deploy it in your Azure VM or host it locally to get full admin access in the environments.

If you don’t have admin access in the environment you will not be able to test and debug using Modern POS, you can still do all retail customization for POS but for testing the customization you must use Cloud POS in that environment. From the customization perspective there is no difference between cloud POS and Modern POS whatever the customization you do will work both in Cloud POS and Modern POS and there is no additional logic required/code for customization you did in Cloud POS to work in Modern POS or vice versa except if you added some logic which is browser specific or UWP app specific for Hardware and other scenarios.  Or other option is you can do all the development in the environment using Modern POS and test it in some other environment where you have admin access to install MPOS but most of the cases you should be able to test it using Cloud POS expect offline. But if you want to test offline scenarios you can still create Modern POS installer using the build script and test it in your test environment or some other POS registers.

**If you are using Cloud POS for development please do the following configuration before opening the Cloud POS project:**

1. Open Visual Studio and click **View** > **Application Explorer**. Wait for Internet Information Services (IIS) Express to start with all the Retail websites deployed. You should see the IIS tray icon in the task bar with all the Retail websites running, such as Cloud POS and Retail Server.
4. To debug CRT/RS extensions, attach the CRT/RS project to the IIS Express process.
5. When you open the Cloud POS project from the Retail SDK, IIS Express may fail with the following error. 

    ```
    Filename: redirection.config
    Error: Cannot read configuration file
    ``` 
    To resolve this issue:
    1. Close Visual Studio.
    2. Rename the **%userprofile%\Documents\IISExpress\config** folder. Do not delete the files because you will copy the **applicationhost.config** file to a new location in step *iv*.
    3. Start Visual Studio again with the Cloud POS project. The **%userprofile%\Documents\IISExpress\config** folder will be recreated with the default config files.
    4. Copy the **applicationhost.config** file from the folder that you renamed in step *ii*, to the folder created in step *iii*. 

## Install the Developer topology prerequisites

Cloud-hosted development environments do not include Typescript version 2.2.2 by default, and the default Windows host file does not contain the Cloud POS URL to use for local debugging. The **Developer topology prerequisites** package installs Typescript 2.2.2 and updates the Windows host file with your Cloud POS URL. Deploying the package will take a few minutes. 


To install the Developer topology prerequisites:

   1. Go to Lifecycle Services (https://lcs.dynamics.com) and sign in.
   2. Under **Projects**, select the project where your dev environment is deployed.
   3. In the **More tools** section, click the **Asset library** tile.
   4. Select **Software deployable package** for the Asset library type and click **Import**.
   5. In the **Shared asset library list**, select **Developer topology prerequisites** and click **Pick**.
   6. Go to the **Environments** section, and click your development environment.
   7. Click the **Maintain** tab and select **Apply updates**.
   8. Select **Developer topology prerequisites** and click **Apply**.
