---
# required metadata

title: Development in cloud-hosted development environments without admin access
description: This topic demonstrates the configuration steps for Commerce developers working on cloud-hosted development machines.
author: mugunthanm 
manager: AnnBe
ms.date: 05/31/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
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
# Development in cloud-hosted development environments without admin access

[!include [banner](../../includes/banner.md)]

As of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, Platform update 12, customers will no longer have access to virtual machine (VM) administrator accounts on development or build environments that are running in Microsoft subscriptions. This restriction only applies to new deployments of Platform update 12 (or newer) environments. Environments that were deployed before this update, and  have been updated to Platform update 12, will still have administrator access.

You can use a remote desktop (RDP) to access these restricted environments using the non-admin user provided on the Lifecycle Services (LCS) environment page. For more information about environments that don't allow administrator access, see [Development and build VMs that don't allow administrator access FAQ](../../dev-itpro/sysadmin/VMs-no-admin-access.md).

If you deploy an environment using Microsoft Azure subscription in Lifecycle Services (LCS), then you will not have admin access in this environment. If you need admin access in your environment, use your Azure subscription and deploy the environment using LCS. You can also use the downloadable VHD and deploy it in your Azure virtual machine (VM) or host it locally to get full admin access.

If you don’t have admin access in the environment, you will not be able to test and debug using Modern POS. You can still do all commerce customization for POS if you are testing the customization, you must use Cloud POS in that environment. From a customization perspective, there is no difference between Cloud POS and Modern POS - any customization will work both in Cloud POS and Modern POS. There is no additional logic or code for customization completed in Cloud POS in order to work in Modern POS or vice versa, unless you added logic that is browser-specific or UWP app- specific for Hardware and other scenarios. Another option is to do all development work in the environment using Modern POS and test it in some other environment where you have admin access to install MPOS. In most cases, you should be able to test using Cloud POS, expect if you want to test for offline scenarios. If you want to test offline scenarios, you can create a Modern POS installer using the build script, and then test it in your test environment or some other POS registers.

**If you are using Cloud POS for development, set up the following configuration before opening the Cloud POS project**

1. Open Visual Studio and click **View** > **Application Explorer**. Wait for Internet Information Services (IIS) Express to start with all the Commerce websites deployed. You should see the IIS tray icon in the task bar with all the websites running, such as Cloud POS and Commerce Scale Unit.
4. To debug CRT/RS extensions, attach the CRT/RS project to the IIS Express process.
5. When you open the Cloud POS project from the Retail SDK, IIS Express may fail with the following error. 

    ```
    Filename: redirection.config
    Error: Cannot read configuration file
    ``` 

**To resolve this issue**

1. Close Visual Studio.
2. Copy the **aspnet.config** and **redirection.config** files to **%userprofile%\Documents\IISExpress\config**.
3. Open the **applicationhost.config** file in the **%userprofile%\Documents\IISExpress\config** folder.
4. In **applicationhost.config**, change the physcialPath of RetailCloudPos to point to your SDK location.
   For example, physicalPath="K:\RetailSDK\POS\Web". The overall section will look like the following:
   
    ```
   <site name="RetailCloudPOs" id="4" serverAutoStart="true">
        <application path="/" applicationPool="Dynamics365">
            <virtualDirectory path="/" physicalPath="K:\RetailSDK\POS\Web" />
        </application>
    ```
5. Save the changes to **applicationhost.config** 
6. Rename the **%userprofile%\Documents\IISExpress\config** folder. Do not delete the files because you will copy the                      **applicationhost.config** file to a new location in **step 8**.
7. Start Visual Studio again with the Cloud POS project. The **%userprofile%\Documents\IISExpress\config** folder will be recreated         with the default config files.
8. Copy the **applicationhost.config** file from the folder that you renamed in **step 6**, to the folder created in **step 7**. 
9. Right-click the Pos.Web project and click **Properties**.
10. In the **Properties** window, click the **Web** tab. Select the **Start URL radio** option and set the start URL as your Cloud POS URL. For example, `https://usnconeboxax1pos.cloud.onebox.dynamics.com`.
11. Save the changes.

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
