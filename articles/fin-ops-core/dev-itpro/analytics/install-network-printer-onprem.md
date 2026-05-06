---
title: Install network printer devices in on-premises environments
description: Learn how to connect an on-premises deployment of Microsoft Dynamics 365 Finance + Operations (on-premises), to existing network printer devices.
author: faix
ms.author: osfaixat
ms.topic: install-set-up-deploy
ms.date: 04/08/2026
ms.custom: 
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-12-31
ms.search.form: SysCorpNetPrinterList
ms.dyn365.ops.version: 7.3
ms.service: dynamics-365-op
search.app:
  - financeandoperationsonprem-docs
---

# Install network printer devices in on-premises environments

[!include [banner](../includes/banner.md)]

This article explains how to connect an on-premises deployment of Microsoft Dynamics 365 Finance + Operations (on-premises) to existing network printer devices. The [Print and Document Services](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831468(v=ws.11)) feature in Microsoft Windows Server 2016 supports network printing in the on-premises application. This feature centralizes tasks that are related to printer management. To install and configure Print and Document Services, you must have administrative access to the server that hosts the primary instance of Application Object Server (AOS).

Two roles are associated with the configuration of network printing services:

- **Service Administrator** – The person responsible for installing and configuring components of the platform infrastructure. Traditionally, this role is an Active Directory account that has elevated domain privileges. It has enough privileges to install components of Microsoft Windows Server.
- **Organization Administrator** – The person who manages application security privileges. This Active Directory account is assigned to the **System Administrator** role.

Before the organization administrator can add network printers, the service administrator must install and configure Print and Document Services on the server that hosts the primary AOS instance. The organization administrator can then use built-in tools to configure network printer devices.

## Install and configure Print and Document Services

The environment administrator uses the information in this section to enable network printing services.

1. Install Print and Document Services by following the instructions in [Install Print and Document Services](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj134159(v=ws.11)).
1. Configure Print and Document Services by following the instructions in [Configure Print and Document Services](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj134163(v=ws.11)).
1. Follow these steps for each server that hosts the AXService application:
    1. On the local server, start the **Local Users and Groups** manager.
    1. Select the **Groups** node.
    1. Right-click **Print Operators**, and then select **Add to Group**.
    1. Add the network Active Directory account that runs the AXService application to the group.

> [!NOTE]
> Starting with version 2.9.0 of the infrastructure scripts, the accounts are automatically added to the appropriate group.

### Install printers on nodes where AXService runs under a domain account
To install printers on nodes where AXService runs under a domain account, follow these steps:

1. Install network printers by using the AXService user account. This step ensures that the printer driver is available to the AXService user account.
1. Print a test page on the installed printers to make sure that all the connections are correctly configured.
1. Restart the AXService application to help ensure that the user's profile is correctly loaded so that it can locate the printer driver.

### Install printers on nodes where AXService runs under a group Managed Service Account (gMSA)
To install printers on nodes where AXService runs under a gMSA, follow these steps:

> [!IMPORTANT]
> This section requires at least version 2.9.0 of the infrastructure scripts.
> Additionally, you need to download the [SysInternals Suite](/sysinternals/downloads/).

1. Update the `Printers.json` file by adding the network location of each printer that should be available to the AOS. Ensure that you remove the example entries. 
1. Run the following command from the Infrastructure Scripts folder.

```powershell
# Exports the script files to be executed on each VM into a directory VMs\<VMName>.
.\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml    
```

1. Copy the contents of each `infrastructure\VMs\<VMName>` folder to the corresponding VM. If you use the remoting scripts, they automatically copy the contents to the target VMs. Then run the following command as an administrator.

> [!NOTE]
> - The following procedure requires execution on multiple VMs. However, to simplify the process, you can use the remoting scripts that are provided. These scripts let you run the required scripts from a single machine, such as the same machine that you use to run the **.\\Export-Scripts.ps1** command. When the remoting scripts are available, they are declared after a **\# If Remoting** comment in the Windows PowerShell sections.
> - Remoting uses [WinRM](/windows/win32/winrm/portal?redirectedfrom=MSDN). In some cases, it requires that [CredSSP](/windows/win32/secauthn/credential-security-support-provider?redirectedfrom=MSDN) be enabled. The remoting module enables and disables CredSSP on an execution-by-execution basis. Disable CredSSP when it isn't used. Otherwise, there's a risk of credential theft. When you complete the setup, run the following command.
> 
> ```powershell
> .\Disable-CredSSP-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml.
> ```

```powershell
# If Remoting, execute
# .\Install-PrintersOnGmsa-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -SysInternalsFolderLocation \\networkshare\SysInternalsSuite -ForcePushLBDScripts

.\Install-PrintersOnGmsa.ps1 -PrintersJsonFilePath .\Printers.json -SysInternalsFolderLocation \\networkshare\SysInternalsSuite
```

## Manage network printers

Use the information in this section to define network printers.

1. Go to **Organization administration** > **Setup** > **Network printers**.
1. On **Network printers**, add new printers. For each printer, specify a name, description, path, and status. Make sure that the printer path matches the network path of the installed printer.

When you mark a printer **Active**, application users can immediately use it to print document-style reports on network printer devices.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
