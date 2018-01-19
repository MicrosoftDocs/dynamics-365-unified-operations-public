---
# required metadata

title: Mass deployment of Retail self-service components
description: This topic explains how you can use self-service to do silent servicing updates, initial deployments, and some concepts of special deployment. This topic will be updated as the feature is developed and more functionality becomes available. Currently, only the capability for silent servicing updates and mass deployment and activation of Retail Modern POS is available.
author: jashanno
manager: AnnBe
ms.date: 11/07/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
# ms.reviewer: sericks
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jashanno
ms.search.validFrom: 2017-09-31]
ms.dyn365.ops.version: Application update 3
---

# Mass deployment of Retail self-service components

This topic explains how you can use self-service to do silent servicing updates, initial deployments, and some aspects of special deployment. This topic will be updated as the feature is developed and more functionality becomes available. Currently, only the capability for silent servicing updates is available.

## Delimiters for mass deployment
The following table shows the delimiters that can currently be used in execution commands for mass deployment. These delimiters apply to App update 3 and later.

| Delimiter                 | Description |
|---------------------------|-------------|
| -S or -Silent             | Silently run the installer. (No graphical user interface is used.) |
| -C or -Config             | Specify the location and file name of the configuration file to use as part of this installation. |
| -FilePath                 | Specify a custom installation location. (We don't recommend that you use this delimiter for a standard installation.) |
| -LogFile                  | Specify a custom log file location for the installation logs. (We don't recommend that you use this delimiter for a standard installation.) |
| -SkipPrerequisiteCheck    | Skip the check for prerequisites and prerequisite installation.  You should use this delimiter only for development and testing. (We don't recommend that you use this delimiter for a standard installation.) |
| -SkipSystemInfoCollection | Skip the process of collecting system information at the beginning of the installation. You should use this delimiter only for development and testing. (We don't recommend that you use this delimiter for a standard installation.) |
| -SkipMerchantInfo         | Skip the installation of merchant account information at the end of the self-service installer for Hardware station. You should use this delimiter only for development and testing. (We don't recommend that you use this delimiter for a standard installation.) |

## Silent servicing
### Before you begin
This functionality works in Microsoft Dynamics 365 for Retail. The July 2017 version with Application update 3 or later is required. Note that silent servicing maintains all components that are currently installed. If any configuration is still required, please complete this prior to following the directions explained in this article.

### Examples of commands for silent servicing
This section shows examples of commands for self-service mass deployment. The commands that are shown work for all the standard self-service installers. These installers include Retail Modern POS (both the installer with offline support and the installer without offline support), hardware station, and Retail Store Scale Unit.

#### Silently update the current installation of Retail Modern POS
The following command silently updates the current installation of Modern POS. It has the standard command structure that is used for silent servicing of currently installed components. The structure uses the basic values of **InstallerName.exe** and the command for silent installation, **-S**. This command uses the configuration file that is located in the same file location as the installer, if a configuration file exists there.

```
ModernPOSSetup_V72.exe -S
```

> [!NOTE]
> A configuration file is still required for Retail Store Scale Unit. However, the installer still keeps all possible values that are currently installed.

#### Silently update the current installation of Retail Store Scale Unit
The following command silently updates the current installation of Retail Store Scale Unit by using a specific configuration file. (E.g. This configuration file might not be in the same location as the executable file for the installer.) This command skips the prerequisite check and continues to the installation steps. We recommend that you use this command only for testing and development purposes.

```
StoreSystemSetup_V72.exe -S -C "C:\Temp\StoreSystemSetup_V72_Houston.xml" -SkipPrerequisiteCheck
```

## Retail Modern POS mass deployment
### Before you begin
This functionality works in Microsoft Dynamics 365 for Retail. The December 2017 version (Major release version 7.3) or later is required.  It is assumed that all stores, registers, devices, and other configurations in headquarters have already been completed. If any configuration is still required, please complete this prior to following the directions explained in this article.

It is important to note that devices should only be configured for mass deployment only right before they are deployed and activated.  Once the activation is complete, it is important to verify that no remaining devices are still configured to be activated in this manner.  Leaving this configuration for extended periods of time in an unmanaged state could be considered a security risk.

#### Important concepts
There are two important concepts to the mass deployment of Retail Modern POS.  Device permission and user permission.
1. Each Retail Modern POS device now has a permission to **Allow mass activation**.  This permission allows the device to be activated one, and only one, time without Azure Active Directory credentials (AAD credentials are required for device activation normally).  While not recommended, if the device requires reactivation and the mass deployment flow is still needed, it is required to reset the **Activation status** of the device to the **Pending** state.  Then set the **Allow mass activation** permission to yes.
2. Each user has a new POS permissions.  This permission, **Allow mass activation**, has been created to allow a user to activate a device that has been configured to activate through mass deployment.  This permission can be set directly on the user's POS permissions or at the group level.  To update a group's permissions, use the menu in the upper left to go to **Retail** &gt; **Employees** &gt; **Permission groups**.  In this page, select the appropriate permission group (E.g. Manager) and set the permission **Allow mass activation** to yes.  This will allow all users set to this permission group to activate a mass deployed Retail Modern POS device.

### Configure mass deployment

#### Configure user permission
1. Use your Azure AD credentials to sign in to Retail headquarters.
2. On the **Welcome** page, use the menu in the upper left to go to **Retail** &gt; **Employees** &gt; **Permission groups**.
3. On the lefthand side, select the appropriate group that requires the new permission (E.g. Manager).
4. In the **Permissions** group, change the setting for **Allow mass activation** to **Yes**.
5. On the Action Pane, select **Save**.
6. On the drop-down menu, select **Configuration file**.
7. Use the menu in the upper left to go to **Retail** &gt; **Retail IT** &gt; **Distribution schedule**.
8. On the lefthand side, select the **1060** job.
9. On the Action Pane, select **Run now**.
10. On the verification message that appears stating **Do you want to run job 1060**, select **Yes**.

#### Configure device permission
1. Use your Azure AD credentials to sign in to Retail headquarters.
2. On the **Welcome** page, use the menu in the upper left to go to **Workspaces** &gt; **Channel deployment**.  This workspace can also be accessed directly on the homepage for users with permission.
3. On the Action Pane, select **Mass deployment**.
4. On the drop-down menu, select **Mass device update**.
5. On the slide-out that appears from the right-hand side of the window, select the organization nodes that require permission (E.g. In demo data, Houston is a well configured store with many devices to test with) and use the arrow in the center of the slide-out panel that is facing to the right to take your selection from the lefthand **Available organization nodes** and move it to the righthand **Selected organization nodes**.  Repeat this process until all required nodes are shown on the righthand node list.

    > [!NOTE]
    > To verify that permission has appropriately been set, use the menu in the upper left to go to **Retail** &gt; **Channel setup** &gt; **POS setup** &gt; **Devices**.  On this page, select any device that exists in the nodes configured above and verify that the permission **Allow mass activation** is currently set to **Yes**.

6. Select **OK** at the bottom of the slide-out to complete device permission configuration.


#### Download the configured devices
1. Use your Azure AD credentials to sign in to Retail headquarters.
2. On the **Welcome** page, use the menu in the upper left to go to **Workspaces** &gt; **Channel deployment**.  This workspace can also be accessed directly on the homepage for users with permission.
3. On the Action Pane, select **Mass deployment**.
4. On the drop-down menu, select **Mass download**.
5. On the slide-out that appears from the right-hand side of the window, select the organization nodes that require permission (E.g. In demo data, Houston is a well configured store with many devices to test with) and use the arrow in the center of the slide-out panel that is facing to the right to take your selection from the lefthand **Available organization nodes** and move it to the righthand **Selected organization nodes**.  Repeat this process until all required nodes are shown on the righthand node list.
6. Select **OK** at the bottom of the slide-out to complete and download the zipped configurations.

    > [!NOTE]
    > The system will generate and collect all of the configuration files and unique Retail Modern POS packages associated with the selected nodes and create a zipped folder to download. If the nodes listed contain a large amount of devices, the generation and collection can take some time to complete and show the download. 
    > Further, a new file titled **RetailAssociationMap.xml** will be generated. This new file allows for easy consumption of configurations.  A configuration includes the name of the configuration file, the name of the installer, the name of the device (Also known as terminal), and the name of the register.
    
7. On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.)

     Browsers might block the download pop-up that is generated. Select either **Allow once** or **Options for this site** &gt; **Always allow**. Then select **Download** again.

### Examples of commands for silent mass deployment
This section shows examples of commands for self-service mass deployment. The commands that are shown work for all the standard self-service installers. These installers include Retail Modern POS (both the installer with offline support and the installer without offline support), hardware station, and Retail Store Scale Unit.

#### Silently install Retail Modern POS
The following command silently updates the current installation of Modern POS. It has the standard command structure that is used for silent servicing of currently installed components. The structure uses the basic values of **InstallerName.exe** and the command for silent installation, **-S**. This command uses the configuration file that is located in the same file location as the installer, if a configuration file exists there.

```
ModernPOSSetup_V72.exe -S
```

> [!NOTE]
> A configuration file is still required for Retail Store Scale Unit. However, the installer still keeps all possible values that are currently installed.

#### Silently update the current installation of Retail Store Scale Unit
The following command silently updates the current installation of Retail Store Scale Unit by using a specific configuration file. (This configuration file might not be in the same location as the executable file for the installer.) This command skips the prerequisite check and installation steps. We recommend that you use this command only for testing and development purposes.

```
StoreSystemSetup_V72.exe -S -C "C:\Temp\StoreSystemSetup_V72_Houston.xml" -SkipPrerequisiteCheck
```
