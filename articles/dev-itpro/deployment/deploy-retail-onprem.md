---
# required metadata

title: Installation steps for Retail channel components in an on-premises environment
description: This topic covers the installation steps for Retail channel components in an on-premises environment. 
author: jashanno
manager: AnnBe
ms.date: 11/12/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [retail
ms.author: jashanno
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1.1
---

# Installation steps for Retail channel components in an on-premises environment

[!include[banner](../includes/banner.md)]

This topic covers the installation steps for Retail channel components in an on-premises environment.

## Overview

Retail channel functionality, in an on-premises environment, is enabled exclusively via use of Retail Store Scale Unit. For an overview of Retail Store Scale Unit, see [Retail Store Scale Unit](../../retail/dev-itpro/retail-store-system-begin.md). 

Unlike a cloud deployment, an on-premises environment does not enable seamless, high-availability deployment of Retail channel components via Lifecycle Services (LCS). The only way to use Retail channel components is by installing Retail Store Scale Unit.

## Prerequisites 

Before you can start installation of Retail channel components, you must first complete all prior installation steps for an on-premises environment. These steps are listed in [Set up and deploy on-premises environments (Platform update 12 and later)](setup-deploy-on-premises-pu12.md).

You must also ensure that you use a secure network to connect Retail Store Scale Unit (RSSU) to Retail headquarters that is not publicly  accessible. You must also restrict network access to Retail headquarters only to known RSSU devices via network filtering or other means.  This means that a firewall must exist and whitelisting is highly recommended.

## Installation steps

1.	On the previously created [file share](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-pu12#setupfile), create a new folder called **RetailSelfServicePackages**.
2.	On each AOS computer, run the following PowerShell script:

```powershell
.\RetailUpdateDatabase.ps1 -DatabaseServer '<Database server name for AOS database -DatabaseName 'Database name for AOS database ' -envName '<Environment name>' -RetailSelfServicePackages '<Local path of Retail self-service packages>’ -SendProductSupportTelemetryToMicrosoft
```
> [!NOTE]
> The parameters **-DatabaseServer** and **-DatabaseName** should be known based on the environment setup.
> The parameter **-envName** should be known based on creation when the environment is generated.
> The parameter **-RetailSelfServicePackages** is the full path location created in the previous step.
> The parameter **-SendProductSupportTelemetryToMicrosoft** is a required value to enable telemetry to Microsoft.  This is critical to maximize support from Microsoft.
> This script will perform a variety of actions, including updating the Retail Service user and role and updating Retail registry keys.
  
3.	Download the binary update from LCS. For instructions, see [Get updates from Lifecycle Services (LCS)](../migration-upgrade/download-hotfix-lcs.md).
4.	Extract the zip file and copy all six Self-service installers (AsyncServerConnectorServiceSetup.exe, RealtimeServiceAX63Setup.exe, HardwareStationSetup.exe, ModernPosSetup.exe, ModernPosSetupOffline.exe, and StoreSystemSetup.exe) into the folder **RetailSelfServicePackages** defined and created in step 1 in each of the AOS machines.
5.	Follow the installation steps for installing the Retail Store Scale Unit. For instructions, see [Configure and install Retail Store Scale Unit](../../retail/dev-itpro/retail-store-scale-unit-configuration-installation.md).
6.  Navigate to the same file directory where the previously run Retail PowerShell script was located (**RetailUpdateDatabase.ps1**) to find the PowerShell script **Create-ADFSServerApplicationForRetail.ps1**.
7.  Run this script in a new PowerShell window using the command **.\Create-ADFSServerApplicationForRetail -HostUrl 'https://ax.d365ffo.onprem.contoso.com'**, where the **HostUrl** value is the AOS URL to access headquarters without the **/namespaces/AXSF/** portion of the URL.
8.  Access the newly generated Server application from the **Application Groups** in AD FS Management.
9.  Edit the newly generated Server application and select to **Reset the Secret**.

> [!NOTE]
> It is critical to keep this secret safe.  This secret should only ever be copied once and never stored on the system.  The Client ID and Secret generated will be used during the Retail Store Scale Unit installer, so it is required to be used at a later time.  You can always reset the secret again, but it must then be updated on any Retail Store Scale Unit that used the previous secret.

10.  In Retail headquarters, navigate to **Retail** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Retail shared parameters**.
11.  Select **Identity providers**.
12.  On the **Identity providers** FastTab, select **+Add**.
13.  In the new **Issuer** row, enter the new Identity provider value **https://sts.windows.net/** in the field.
14.  Navigate to **Retail** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Retail parameters**.
15.  On the **General** tab, select the **Initialize** link to configure seed data for Retail functionality.

> [!NOTE]
> CURRENTLY must go to Connector for Microsoft Dynamics AX to create a RTS profile, and go to RetailSharedParameters  -> Security -> Transaction service legacy properties -> real-time service profile, and select the created RTS profile.   NEWNENWNNEWNENWNEWNENWNENWNENWENEW



> [!NOTE]
> The installers will not download from their relevant pages the first time a download is attempted.  This is due to the installers have only just been placed into the download location and the associated database values not yet existing.  In headquarters, when the **Download** functionality is attempted (Retail Store Scale Unit or Retail Modern POS, for example), an error will be shown and then an automated upload functionality will be initiated to allow the installers to be downloaded correctly the second time it is attempted (Allow one minute of time before attempting to download the installer again).
> At multiple locations in the **Configure and install Retail Store Scale Unit** document (linked above) there will be notes referencing changes to the instructions for an on-premises deployment.

