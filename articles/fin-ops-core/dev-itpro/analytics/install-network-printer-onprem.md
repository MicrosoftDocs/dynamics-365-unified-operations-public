---
# required metadata

title: Install network printer devices in on-premises environments
description: This topic explains how to connect an on-premises deployment of Microsoft Dynamics 365 Finance + Operations (on-premises), to existing network printer devices.
author: TJVass
manager: AnnBe
ms.date: 11/13/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysCorpNetPrinterList
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Install network printer devices in on-premises environments

[!include [banner](../includes/banner.md)]

This topic explains how to connect an on-premises deployment of Microsoft Dynamics 365 Finance + Operations (on-premises) to existing network printer devices. Network printing in the on-premises application is supported by the [Print and Document Services](https://technet.microsoft.com/library/hh831468(v=ws.11).aspx) feature in Microsoft Windows Server 2016. This feature lets you centralize tasks that are related to printer management. To install and configure Print and Document Services, you must have administrative access to the server that hosts the primary instance of Application Object Server (AOS).

Two roles are associated with the configuration of network printing services:

- **Service Administrator** – The person who has this role is responsible for installing and configuring components of the platform infrastructure. Traditionally, this role is an Active Directory account that has elevated domain privileges. It has enough privileges to install components of Microsoft Windows Server.
- **Organization Administrator** – The person who has this role manages application security privileges. This Active Directory account is assigned to the **System Administrator** role.

Before the organization administrator can begin to add network printers, the service administrator must install and configure Print and Document Services on the server that hosts the primary AOS instance. The organization administrator can then begin to use built-in tools to configure network printer devices.

## Install and configure Print and Document Services

The environment administrator uses the information in this section to enable network printing services.

1. Install Print and Document Services by following the instructions in [Install Print and Document Services](https://technet.microsoft.com/library/jj134159(v=ws.11).aspx).
2. Configure Print and Document Services by following the instructions in [Configure Print and Document Services](https://technet.microsoft.com/library/jj134163(v=ws.11).aspx).
3. Follow these steps for each server that is used to host the AXService application:
    1. On the local server, start the **Local Users and Groups** manager.
    2. Select the **Groups** node.
    3. Right-click **Print Operators**, and then select **Add to Group**.
    4. Add the network Active Directory account that is used to run the AXService application to the group.

> [!NOTE]
> Starting with version 2.9.0 of the Infrastructure Scripts the accounts are automatically added to the appropriate group.

### Install printers on nodes where AXService is executing under a domain account

1. Install network printers by using the AXService user account. This step helps guarantee that the printer driver is available to the AXService user account.
2. Print a test page on the installed printers to make sure that all the connections are correctly configured.
3. Restart the AXService application to help guarantee that the user's profile is correctly loaded so that it can look up the printer driver.

### Install printers on nodes where AXService is executing under a gMSA

> [!IMPORTANT]
> This section requires at least version 2.9.0 of the Infrastructure Scripts.
> Additionally, you need to download the [SysInternals Suite](https://docs.microsoft.com/sysinternals/downloads/).

1. Update the Printers.json file by adding the network location of each printer that should be made available to the AOS. Ensure you remove the example entries. 
2. Run the following command from the Infrastructure Scripts folder:

```powershell
# Exports the script files to be executed on each VM into a directory VMs\<VMName>.
.\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml    
```

3. Copy the contents of each infrastructure\VMs\<VMName> folder to the corresponding VM. (If the remoting scripts are used, they will automatically copy the contents to the target VMs.) Then run the following command as an administrator.

> [!NOTE]
> - The following procedure requires execution on multiple VMs. However, to simplify the process, you can use the remoting scripts that are provided. These scripts let you run the required scripts from a single machine, such as the same machine that is used to run the **.\\Export-Scripts.ps1** command. When the remoting scripts are available, they are declared after a **\# If Remoting** comment in the Windows PowerShell sections.
> - Remoting uses [WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx). In some cases, it requires that [CredSSP](https://msdn.microsoft.com/library/windows/desktop/bb931352(v=vs.85).aspx) be enabled. The remoting module enables and disables CredSSP on an execution-by-execution basis. We recommend that you disable CredSSP enabled when it isn't used. Otherwise, there is a risk of credential theft. When you've completed the setup, run:
> ```powershell
> .\Disable-CredSSP-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml.
> ```

```powershell
# If Remoting, execute
# .\Install-PrintersOnGmsa-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -SysInternalsFolderLocation \\networkshare\SysInternalsSuite -ForcePushLBDScripts

.\Install-PrintersOnGmsa.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -SysInternalsFolderLocation \\networkshare\SysInternalsSuite
```

## Manage network printers

The system administrator uses the information in this section to define network printers.

1. Go to **Organization administration** \> **Setup** \> **Network printers**.
2. On the **Network printers** page, add new printers. For each printer, specify a name, description, path, and status. Make sure that the printer path matches the network path of the installed printer.

Items that are marked **Active** immediately become available to application users, so that they can begin to print document-style reports on network printer devices.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]