---
title: Download and install Commerce Scale Unit
description: This article explains how to download and install Commerce Scale Unit (self-hosted) on computers in a brick-and-mortar store.
author: jashanno
ms.date: 06/01/2025
ms.topic: install-set-up-deploy
audience: IT Pro
ms.reviewer: 
ms.search.region: Global
ms.author: brstor
ms.search.validFrom: 2025-06-01
ms.assetid: 
ms.search.form: SysMicrosoft Entra IDClientTable, RetailCDXDataStore, RetailCDXDataGroup, RetailChannelProfile, RetailSharedParameters, RetailStoreTable
ms.custom: 
  - bap-template
---

# Download and install Commerce Scale Unit

[!include [banner](../includes/banner.md)]

This article explains how you can download and install a Commerce Scale Unit on one or more computers in a brick-and-mortar store. Commerce Scale Unit (CSU) combines the Commerce channel database, Commerce async client, Retail Server, and Cloud point of sale (POS) components. A Commerce environment already provides these components in the cloud. However, you can now configure them so that they work locally in a store or datacenter.

### Download the sealed self-hosted installer

> [!NOTE]
> Sealed CSU installers are only available from the LCS Asset library.  

To download the sealed self-hosted CSU installer, follow these steps.

1. Open a web browser and sign in to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com).
1. Select your project from the list.
1. From the hamburger menu at the top of the page, select **Asset library**.
1. Select **Retail Self-service package**.  
1. If you already have a sealed CSU installer in your list, select the package name to start the download.  
1. If you don’t have a CSU sealed installer in the list, select **Import**, select the sealed installer version you want to use, select **Pick**, and then select the package name to start the download. 
1. Copy the sealed installer from the **Downloads** folder to C:\temp.

### Download the Commerce Scale Unit channel configuration file

1. In headquarters, go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database**.
2. In the list of channel databases on the left, select the channel database that you created earlier.
3. On the Action Pane, select **Download**.
4. On the drop-down menu, select **Configuration file**.

    > [!NOTE]
    > - Save the configuration file (XML file) to the same location as the installer. Example: C:\temp\StoreSystemSetup.xml
    > - For on-premises deployments, currently the configuration file requires the following manual edits:
    >     - StoreSystemAosUrl should have the value used to access headquarters. It is critical to keep a trailing slash at the end of this URL (for example, `https://myContosoURL.com/namespaces/AXSF/`).
    >     - Microsoft Entra IDTokenIssuerPrefix should have the value `https://NOTUSED.microsoft.com`
    >     - TransactionServiceAzureAuthority should have the value `https://<ADFS FQDN including .com>/adfs`.
    >     - TransactionServiceAzureResource should have the base URL value of **StoreSystemAosUrl**. For example, `https://myContosoURL.com` is the base URL value, after removing the **/namespaces/AXSF/** portion of the URL.

5. On the notification bar that appears at the bottom of the Microsoft Edge window, select **Save**. (The notification bar might appear in a different place in other browsers.)

    Browsers might block the download pop-up that is generated. Select either **Allow once** or **Options for this site \> Always allow**. Then select **Download** again.

## Install the sealed CSU

The process of installing a sealed CSU usually employs a configuration file downloaded from headquarters that contains all of the information needed for Retail Transaction Service (RTS) authentication. If you don't use a configuration file, then you must specify additional parameters such as `--AadTokenIssuerPrefix`, `--StoreSystemAosURL`, `--StoreSystemChannelDatabaseId`, and `--TenantId`. For a full list of installer commands, see [Mass deployment of sealed Commerce self-service components](enhanced-mass-deployment.md). 

To install the sealed CSU, follow these steps.

1. Open a Windows Command Prompt with administrator privileges.
1. Change directory to C:\temp (for example, `CD C:\temp`).
1. Execute the following command.

```cmd
CommerceStoreScaleUnitSetup.exe install --port 446 --SSLCertThumbprint "<SSL thumbprint of certificate created earlier>" --RetailServerCertThumbprint "<SSL thumbprint of certificate created earlier>" --AsyncClientCertThumbprint "<SSL thumbprint of certificate created earlier >"  --AsyncClientAADClientID "<CSU Azure APP Client ID>" --RetailServerAADClientID "<CSU Azure APP Client ID>" --CPOSAADClientID "<CPOS Azure APP Client ID>" --RetailServerAADResourceID "<Application ID URI>" --Config "c:\temp\StoreSystemSetup.xml" --SkipSChannelCheck --trustSqlservercertificate
```

> [!NOTE]
> - When installing on a development machine, using the same SSL thumbprint to run all services is allowed. For production and user acceptance testing (UAT) environments, these values should be different.
> - Don't enter port 80 or 443 during installation. Entering either of these values interferes with the application object server (AOS) service that hosts the Commerce headquarters website. 

