---
# required metadata

title: Mass deployment of Retail self-service components
description: This topic explains how you can use self-service to do silent servicing updates and initial deployments. It also explains some aspects of special deployment. 
author: jashanno
manager: AnnBe
ms.date: 01/25/2018
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
ms.search.validFrom: 2017-09-31
ms.dyn365.ops.version: Application update 3
---

# Mass deployment of Retail self-service components

[!include[banner](../includes/banner.md)]

This topic explains how you can use self-service to do silent servicing updates and initial deployments. It also explains some aspects of special deployment. This topic will be updated as the feature is developed and more functionality becomes available. Currently, only the capability for silent servicing updates is available.

## Delimiters for mass deployment

The following table shows the delimiters that can currently be used in execution commands for mass deployment. These delimiters apply to Application update 3 for Microsoft Dynamics 365 for Retail and later.

| Delimiter                 | Description |
|---------------------------|-------------|
| -S or -Silent             | Silently run the installer. No graphical user interface (GUI) is used. The **-Q** and **-Quiet** delimiters have the same effect and can also be used. |
| -C or -Config             | Specify the location and file name of the configuration file to use as part of this installation. |
| -FilePath                 | Specify a custom installation location.<p>We don't recommend that you use this delimiter for a standard installation.</p> |
| -LogFile                  | Specify a custom file location for the installation logs.<p>We don't recommend that you use this delimiter for a standard installation.</p> |
| -SkipPrerequisiteCheck    | Skip the check for prerequisites and prerequisite installation.<p>You should use this delimiter only for development and testing. We don't recommend that you use it for a standard installation.</p> |
| -SkipSystemInfoCollection | Skip the process of collecting system information at the beginning of the installation.<p>You should use this delimiter only for development and testing. We don't recommend that you use it for a standard installation.</p> |
| -SkipMerchantInfo         | Skip the installation of merchant account information at the end of the self-service installer for Hardware station.<p>You should use this delimiter only for development and testing. We don't recommend that you use it for a standard installation.</p> |

## Silent servicing

### Before you begin

This functionality works in Microsoft Dynamics 365 for Retail. The July 2017 version with Application update 3 or later is required. Note that silent servicing maintains all components that are currently installed. If any configuration is still required, complete it before you begin to follow the instructions in this topic.

### Examples of commands for silent servicing

This section shows examples of commands that are used for self-service mass deployment. These commands work for all the standard self-service installers, such as the installers for Retail Modern POS (both the installer that has offline support and the installer that doesn't have offline support), Hardware station, and Retail Store Scale Unit.

#### Silently update the current installation of Retail Modern POS

The following command silently updates the current installation of Retail Modern POS. This command has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe** and the command for silent installation, **-S**. This command uses the configuration file that is located in the same file location as the installer, if a configuration file exists there.

```
ModernPOSSetup_V72.exe -S
```

> [!NOTE]
> A configuration file is still required for Retail Store Scale Unit. However, the installer keeps all the values that are currently installed, whenever it can.

#### Silently update the current installation of Retail Store Scale Unit

The following command silently updates the current installation of Retail Store Scale Unit by using a specific configuration file. (This configuration file might not be in the same location as the executable file for the installer.) This command skips the prerequisite check and moves on to the installation steps. We recommend that you use this command only for testing and development purposes.

```
StoreSystemSetup_V72.exe -S -C "C:\Temp\StoreSystemSetup_V72_Houston.xml" -SkipPrerequisiteCheck
```

## Mass deployment of Retail Modern POS

### Before you begin

This functionality works in Retail. The December 2017 version (release version 7.3.1) with Application update 1 or later is required. It's assumed that the configuration of all stores, registers, and devices, and other configurations in the headquarters, have already been completed. If any configuration is still required, complete it before you follow the instructions in this topic.

> [!NOTE]
> It's important that you configure devices for mass deployment just before the devices are deployed and activated. After these devices are activated, verify that no devices are still configured for activation through mass deployment. By default, a device can be activated through the mass deployment workflow only one time. Devices that you leave configured for mass deployment in an unmanaged state for extended periods could be considered a security risk.

#### Important concepts

There are two important concepts for mass deployment of Retail Modern POS: device permission and user permission.

- **Device permission** – Every Retail Modern POS device now has a permission that is named **Allow mass activation**. Usually, Microsoft Azure Active Directory (Azure AD) credentials are required for device activation. However, this permission allows a device to be activated exactly one time without Azure AD credentials. If the device requires reactivation, and the mass deployment workflow is still required, you must reset the activation status of the device to **Pending** and then set the **Allow mass activation** permission to **Yes**. However, we don't recommend this approach.
- **User permission** – Every user now has a point of sale (POS) permission that is named **Allow mass activation**. This permission allows a user to activate a device that has been configured for activation through mass deployment. This permission can be set either directly on the user's POS permissions or at the group level. To update a group's permissions, use the menu in the upper left to go to **Retail** &gt; **Employees** &gt; **Permission groups**. On the **Permission groups** page, select the appropriate permission group (for example, **Manager**), and set the **Allow mass activation** permission to **Yes**. All users who belong to this permission group can now activate a Retail Modern POS device that has been mass-deployed.

### Configure mass deployment

#### Configure user permission

1. Use your Azure AD credentials to sign in to Retail headquarters.
2. On the **Welcome** page, use the menu in the upper left to go to **Retail** &gt; **Employees** &gt; **Permission groups**.
3. On the left side of the page, select the group that requires the new permission (for example, the **Manager** or **Cashier** group).
4. In the **Permissions** group, change the setting for **Allow mass activation** to **Yes**.
5. On the Action Pane, select **Save**.
6. On the drop-down menu, select **Configuration file**.
7. Use the menu in the upper left to go to **Retail** &gt; **Retail IT** &gt; **Distribution schedule**.
8. On the left side of the page, select the **1060** job (also known as the **Staff** job).
9. On the Action Pane, select **Run now**.
10. When you're prompted to confirm that you want to run job 1060, select **Yes**.

#### Configure device permission

1. Use your Azure AD credentials to sign in to Retail headquarters.
2. On the **Welcome** page, use the menu in the upper left to go to **Workspaces** &gt; **Channel deployment**. Users who have the appropriate permission can also access the **Channel deployment** workspace directly from the home page.
3. On the Action Pane, select **Mass deployment**.
4. On the drop-down menu, select **Mass device update**.
5. In the dialog box that appears, select an organization node that requires permission. (For example, in the demo data, the Houston store is well configured with many devices that you can use for testing.) Then use the right arrow button in the center of the dialog box to move your selection from the **Available organization nodes** list on the left to the **Selected organization nodes** list on the right. Repeat this step until all required nodes appear in the **Selected organization nodes** list.

    > [!NOTE]
    > To verify that permission has been set in the appropriate manner, use the menu in the upper left to go to **Retail** &gt; **Channel setup** &gt; **POS setup** &gt; **Devices**. On the **Devices** page, select any device that exists in the nodes that you configured in this step, and verify that the **Allow mass activation** permission is set to **Yes**. As an alternative to the preceding steps of this procedure, you can manually set the permission for each device to **Yes** on the **Devices** page.

6. Select **OK** at the bottom of the dialog box to complete the configuration of device permission.

#### Download the configured devices

1. Use your Azure AD credentials to sign in to Retail headquarters.
2. On the **Welcome** page, use the menu in the upper left to go to **Workspaces** &gt; **Channel deployment**. Users who have the appropriate permission can also access the **Channel deployment** workspace directly from the home page.
3. On the Action Pane, select **Mass deployment**.
4. On the drop-down menu, select **Mass download**.
5. In the dialog box that appears, select an organization node that requires permission. (For example, in the demo data, the Houston store is well configured with many devices that you can use for testing.) Then use the right arrow button in the center of the dialog box to move your selection from the **Available organization nodes** list on the left to the **Selected organization nodes** list on the right. Repeat this step until all required nodes appear in the **Selected organization nodes** list.
6. Select **OK** at the bottom of the dialog box to download the configurations as a zip file.

    > [!NOTE]
    > The system generates and collects all the configuration files and unique Retail Modern POS packages that are associated with the selected nodes, and creates a zip file that you can download. If the selected nodes contain many devices, the system can require some time to generate and collect the configuration files, and to show the download.
    >
    > Additionally, a new file that is named **RetailAssociationMap.xml** is generated. This file enables easy consumption of configurations. A configuration includes the name of the configuration file, the name of the installer, the name of the device (also known as the terminal), and the name of the register. This file is discussed in more detail later in this topic.

7. On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.)

    Browsers might block the download pop-up that is generated. Select either **Allow once** or **Options for this site** &gt; **Always allow**. Then select **Download** again.

#### How to proceed

The zip file that is generated and downloaded in the previous section includes files that are a part of three buckets:

- **The list of XML configuration files** – There is one file for each device that was selected for download.
- **The list of one or more executable files for Retail Modern POS installation** – There is one file for each unique instance of Retail Modern POS across all the devices that were selected for download.

    For example, ten devices are downloaded. On the **Devices** page in headquarters, one device was configured to use the customized version of Retail Modern POS that is named **MPOS\_V1.1.7.exe**. The other nine devices were configured to use the previous customized version of Retail Modern POS, **MPOS\_V1.1.6.exe**. In this case, although there are ten devices, there are only two unique versions of the installer. When you download these ten devices, only two executable installers are downloaded (one for each unique version of the installer).

- **The RetailAssociationMap.xml file** – This file identifies the association between a device (terminal) and the installer by using a list of configurations. A configuration shows the specific unique installer (see the previous item in this list), the associated configuration file, the associated register, and the associated device (terminal). This XML file is generated to help users push the appropriate files out to the appropriate systems and run the installer correctly.

Many methods can be used to push data across an organization (that is, to individual computers). For example, the whole folder can be pushed to each computer, the XML can be parsed so that only the required files are pushed to each computer, or the files can be accessed remotely and never pushed to each computer. (Detailed discussion of the various methods is outside the scope of this topic.) However the files are used, the result is the same: either a scheduled task or a Microsoft Windows PowerShell script is run to do the silent installation of Retail Modern POS.

After Retail Modern POS is installed on a device, the device works like an activated device. The first time that Retail Modern POS is started, it requests the user credentials of a user who has been given permission, as described earlier in this topic. After the user enters his or her standard sign-in credentials, the POS quickly completes device activation and signs the user in. The user can then work in Retail Modern POS in the usual manner. Every subsequent sign-in follows the standard flow.

If a device must be reactivated, either the device must be set back to the **Pending** state in headquarters, or it must be reactivated by using Azure AD credentials. The mass deployment workflow can't be used to reactivate a device that has already been activated.

### Examples of commands for silent mass deployment

This section shows examples of commands that are used for self-service mass deployment of Retail Modern POS, even Retail Modern POS with offline and the installer without offline support. Examples of Windows PowerShell scripts are also included to help users do the installations.

#### Examples of Windows PowerShell scripts

The following basic script lists the configurations in the RetailAssociationMap.xml file.

```
$path = ".\RetailAssociationMap.xml"
$Xpath = "/Configurations/Configuration"
select-xml -path $Path -xPath $xpath | Select-Object -ExpandProperty Node
```

The following basic script filters on a specific value to select a specific configuration in the RetailAssociationMap.xml file. This script can be used as the basis for a larger script that helps pull a specific XML configuration file and executable installer to a computer.

```
$path = ".\RetailAssociationMap.xml"
$Xpath = "/Configurations/Configuration[@Device='HOUSTON-3']"
select-xml -path $Path -xPath $xpath | Select-Object -ExpandProperty Node
```

The last command can also be put into a variable, so that the values can more easily be accessed directly. This concept will be used later in this topic.

#### Silently install Retail Modern POS

The following command silently updates the current installation of Retail Modern POS. This command has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe** and the command for silent installation, **-S**. This command uses the configuration file that is located in the same file location as the installer, if a configuration file exists there. This command should not be used if multiple configuration files are available for selection.

```
ModernPOSSetup_V73.exe -S
```

> [!NOTE]
> A configuration file isn't required for Retail Modern POS. However, the Retail Modern POS application that is installed can't be activated in the appropriate manner unless the associated configuration file can be read from.

#### Silently install Retail Modern POS by using a specific configuration file

The following command silently installs the current installation of Retail Modern POS by using a specific configuration file. This configuration file might not be in the same location as the executable file for the installer, or multiple configuration files might be available.

```
ModernPOSSetup_V72.exe -S -C "C:\Temp\ModernPOSSetup_V73_Houston-3.xml"
```

#### Bring it all together

By using all the preceding commands together as starting points, you can create a basic script that reads through the RetailAssociationMap.xml file, selects the correct device, and then does the installation. For this installation, it's assumed that both the configuration file and the installer are in the same directory that the Windows PowerShell script is run from.

```
$path = ".\RetailAssociationMap.xml"
$Xpath = "/Configurations/Configuration[@Device='HOUSTON-3']"
$configuration = select-xml -path $Path -xPath $xpath | Select-Object -ExpandProperty Node
$installer = '.\' + $configuration.Installer

& $installer -S -C $configuration.File
```
