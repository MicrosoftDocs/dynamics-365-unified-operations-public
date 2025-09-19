---
title: Configure and install Commerce Scale Unit (self-hosted)
description: Learn how to use self-service to configure and install Microsoft Dynamics 365 Commerce Scale Unit (self-hosted) on computers in a brick-and-mortar store.
author: jashanno
ms.date: 09/19/2025
ms.topic: install-set-up-deploy
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ritakimani
ms.search.validFrom: 2016-11-30
ms.assetid: 5e28948f-d40a-40e8-843b-8c2747916546
ms.search.form: SysMicrosoft Entra IDClientTable, RetailCDXDataStore, RetailCDXDataGroup, RetailChannelProfile, RetailSharedParameters, RetailStoreTable
ms.custom:
  - bap-template
  - sfi-ropc-nochange
---

# Configure and install Commerce Scale Unit (self-hosted)

[!include [banner](../includes/banner.md)]

This article explains how you can use self-service to configure a Commerce Scale Unit in Microsoft Dynamics 365 Commerce headquarters, download it, and install it on one or more computers in a brick-and-mortar store. Commerce Scale Unit (CSU) combines the Commerce channel database, Commerce async client, Retail Server, and Cloud point of sale (POS) components. A Commerce environment already provides these components in the cloud. However, you can now configure them so that they work locally in a store or datacenter, in either a single-computer setup (the default option) or a multiple-computer setup. This article also explains how to uninstall and debug Commerce Scale Unit.

> [!IMPORTANT]
> - A basic design principle to follow is that if you're unable to customize in a requested manner on a CSU (Cloud), you shouldn't customize this way with a CSU (self-hosted). It's critical to understand that direct database access isn't supported and can easily cause breaks in customizations that use this concept. A CSU (self-hosted) is primarily used for enabling cross-terminal scenarios, reducing latency or backup for poor WAN connectivity, and providing scale-out to spread the load of POS terminals across multiple CSU components.
> - This component uses a server certificate in addition to Azure Service-to-Service authentication. Both the generated Azure web application keys (formerly called *secrets*) and the server certificate must be managed for expiration. By default, a certificate and a generated Azure web application key expire in one calendar year (365 days).
> - It's critical that you have a plan to rotate this key at least one month before expiration. Planning is necessary when working with a high number of stores to ensure that there's sufficient time to roll out the change to all stores.

## Prerequisites  

Before you begin a CSU (Retail Server) installation, you must complete the following one-time tasks. These operations often need specific permissions and may require the help of your organization's administrative personnel.

### Configure headquarters for a new CSU

To create a functioning CSU, complete the procedures in all sections of this article. You must first complete the initial configuration in headquarters before continuing with installing the CSU. 

> [!IMPORTANT]
> - Channel functionality in an on-premises environment is enabled exclusively via use of Commerce Scale Unit (self-hosted). For an overview, see Commerce Scale Unit (self-hosted). Unlike a cloud deployment, an on-premises environment doesn't enable seamless, high-availability deployment of channel components via Lifecycle Services (LCS). The only way to use channel components is by installing Commerce Scale Unit (self-hosted).
> - For on-premises deployments, perform the following steps:
>    1. Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database group**.
>    1. On the Action pane, select **New**.
>    1. In the **Name** field, enter **Default**. Enter a description in the **Description** field, if needed.
>    1. In the **Channel schema** field, select **AX7**.
>    1. In the **Working folders** field, select **File storage**.
>    1. On the Action Pane, select **Save**.

### Create a new channel database record

To create a new channel database record, follow these steps.

1. In headquarters, go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database**.
1. On the **Channel database** page, on the Action Pane, select **New**.
1. In the **Channel database ID** field, enter a unique value.
1. In the **Channel data group** field, select the **Default** option. Select any available option.

    > [!IMPORTANT]
    > For on-premises deployments, this value is the **Default** value that was previously described in this article.

1. In the **Type** field, leave the default value (**Channel database**) selected.
1. You can leave the **Data sync interval** field blank. Alternatively, you can select a value in this field. For example, in the demo data, the value **D60-U15** specifies a 15-minute synchronization interval.

    The **Data sync interval** value determines how often the data is synchronized between the channel database (Commerce Scale Unit) and headquarters. If no value is entered, the default interval that is set up in Commerce Scale Unit is used. This default interval is three minutes.

1. On the **Retail channel** FastTab, select **Add**, and then, in the **Channel** field, select the appropriate store channel. Repeat this step to add all the channels that should use this database.
1. Select **Save**.
1. If you encounter the **Mapping a New Retail Channel** warning dialog, select **Yes**.  

You can also add channels that don't use this database. In this way, you keep the data for those channels in the Commerce Scale Unit channel database. The channels that actively use this database can then access that data locally.

### Create a new channel profile

Next, you must create a new channel profile record for the CSU URL, and then update the existing store records to use the new channel database and profile. 

> [!NOTE]
> Alternatively, you can modify the existing channel profile record to use the CSU URLs. 

To create a new channel profile in headquarters and update the existing store records to use the new channel database and profile, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Channel profiles**.
1. On the Action Pane, select **New**.
1. In the **Name** field, enter a unique name for the channel profile.

    > [!IMPORTANT]
    > For on-premises deployments, any value can be entered in this field, however, the value **Default** is common.

1. On the Action Pane, select **Save**.
1. On the **Profile properties** FastTab for the new channel profile, select **Add**.
1. In the **Property key** field, select **Retail Server URL**.
1. In the **Property value** field, enter the URL of the Retail Server to be installed. (When configuring for a development environment, enter `https://<HostName>:446/RetailServer/Commerce`.)

    The standard format for the URL of Commerce Scale Unit is `https://<Computer Name>:<Port>/RetailServer/Commerce`. In this format, **\<Computer Name\>** is either the fully qualified domain name (FQDN) of the computer where Commerce Scale Unit is installed or, for systems that aren't joined to a domain, the full computer name. **\<Port\>** is the port number that should be used in the installation. The port number must be a value between 1 and 65531. If you're using the default HTTPS port (443), you don't have to specify the port number.

1. On the **Profile properties** FastTab for the new channel profile, select **Add**.
1. In the **Property key** field, select **Cloud POS URL**.
1. In the **Property value** field, enter the URL of the Cloud POS instance that should be installed for Commerce Scale Unit. 

    The standard format for the URL of Cloud POS is `https://<Computer Name>:<Port>/POS`. In this format, **\<Computer Name\>** is either the FQDN of the computer where the Commerce Scale Unit is installed. or for systems that aren't joined to a domain, the full computer name. **\<Port\>** is the port number that used in the installation. The port number must be a value between 1 and 65531. If you're using the default HTTPS port (443), you don't have to specify the port number.

    > [!NOTE]
    > - When configuring for a development environment, enter `https://<HostName>:446/POS`.
    > - The `<HostName>` value typically starts with "DEV" and can be found by opening Internet Information Services (IIS) Manager and reviewing the server name value shown in the upper left corner. It can also be found on the LCS Environments page in the **VM Name** column under **Manage environment \> LOCAL ACCOUNTS**.

1. On the Action Pane, select **Save**.

    > [!NOTE]
    > - If media is commonly used, you must generate a **Media Server Base URL** for the profile. For testing and simplicity, you can reuse the URL that exists for the **Default** channel profile.
    > - For on-premises deployments, the **Media Server Base URL** is where all media is stored for POS devices.

1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. Select the channel ID link for the store that uses the new channel database.
1. On the details page for the selected store, on the Action Pane, select **Edit**.
1. On the **General** FastTab for the store, in the **Live channel database** field, select the channel database that you created in step 3.
1. On the Action Pane, select **Save**.
1. On the **General** FastTab for the store, in the **Channel profile** field, select the channel profile that you created in step 12.
1. On the Action Pane, select **Save**.
    > [!NOTE]
    > If you receive a warning stating "The store's closing method must be set to 'Shift'", on the **Statement/Closing** FastTab of the store, update the **Closing Method** value to **Shift**.

1. Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database group**.
1. Select the **Default** data group, and then, on the Action Pane, select **Full data sync**. In the **Select a distribution schedule** field, select job **9999**, and then select **OK**. In the dialog that appears, select **OK** to confirm the full synchronization. All the data in the channel database is prepared for download.

If no jobs appear, then initialize the base configuration. Learn more in [Update configurations](cdx-best-practices.md#update-configurations).

> [!IMPORTANT]
>  - You must remove the default database from the Commerce Data Exchange (CDX) data groups in headquarters, because this database is no longer used. Failure to make this update can result in data sync errors later on. 
>  - To update CDX data groups in headquarters, follow these steps.
>
>       1. Go to **Retail and Commerce \> Distribution Schedule**.
>       1. Select the **Default Data** group.
>       1. Remove the default database record from this group.
>
>   - For on-premises deployments, there's no **Default** channel data group. You must create a new data group and associate it with the channel database and distribution schedule jobs.

### Create Microsoft Entra ID apps and register them in headquarters

You must first create two Microsoft Entra ID (formerly known as Azure Active Directory) apps, one for Retail Server and one for the Store Commerce for web app (formerly known as Cloud point of sale or CPOS). For instructions, see [Set up a custom Retail Server app in Microsoft Entra ID](cpos-custom-aad.md#set-up-a-custom-retail-server-app-in-microsoft-entra-id), [Set up a custom app for Store Commerce for Web in Microsoft Entra ID](cpos-custom-aad.md#set-up-a-custom-app-for-store-commerce-for-web-in-microsoft-entra-id),
and [Update identity providers settings in Commerce headquarters](cpos-custom-aad.md#update-identity-providers-settings-in-commerce-headquarters).

[!IMPORTANT]
> - To help maintain a high level of security across the company, Microsoft strongly recommends that you create a new application ID (client ID) and key (secret) for each store that is created.
> - If you're installing CSU for use with an on-premises environment using Active Directory Federation Services instead of Azure, follow the instructions in [Installation steps for Commerce channel components in an on-premises environment](../../fin-ops-core/dev-itpro/deployment/deploy-retail-onprem.md).
    
## Download and Install a new CSU

To download and execute the CSU installer, follow the instructions in [Download and install Commerce Scale Unit](retail-store-scale-unit-download-install.md). This article describes the steps necessary to download the required configuration from headquarters, download the installation program, and run the installer.

Once installation is complete, proceed to the next section for security recommendations and debugging tips.

## Help secure CSU

According to current security standards, the following options should be set in a production environment tp help secure CSU:

- You should completely disable SSL (v2 and v3) on the computer.
- You should only enable and use Transport Layer Security (TLS) version 1.2 (or the current highest version).

> [!NOTE]
> By default, SSL and all versions of TLS except TLS 1.2 are disabled.

To edit or enable SSL and TLS settings, follow these steps.

1. Press the Windows logo key+R to open a **Run** window.
1. In the **Open** field, enter **Regedit**, and then select **OK**.
1. In the **User Account Control** window, select **Yes** (if this step is required), and then, in the new **Registry Editor** window, go to **HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\SecurityProviders\\SCHANNEL\\Protocols**.
1. The following keys are entered automatically to enable only TLS 1.2:
        - TLS 1.2\\Server:Enabled=1
        - TLS 1.2\\Server:DisabledByDefault=0
        - TLS 1.2\\Client:Enabled=1
        - TLS 1.2\\Client:DisabledByDefault=0
        - TLS 1.1\\Server:Enabled=0
        - TLS 1.1\\Client:Enabled=0
        - TLS 1.0\\Server:Enabled=0
        - TLS 1.0\\Client:Enabled=0
        - SSL 3.0\\Server:Enabled=0
        - SSL 3.0\\Client:Enabled=0
        - SSL 2.0\\Server:Enabled=0
        - SSL 2.0\\Client:Enabled=0

- No additional network ports should be open, unless they're required for known, specified reasons.
- You must disable cross-origin resource sharing, and you must specify the allowed origins that are accepted.
- You should only use trusted certificate authorities to obtain certificates to be used on Commerce Scale Unit computers.

> [!IMPORTANT]
> It's critical that you review security guidelines for IIS and the Payment Card Industry (PCI) requirements.

## Debug CSU

To debug CSU, follow these steps.

1. Open the configuration file and verify that the Retail Server URL specified contains the suffix **/Commerce** and is correctly formed based on what is expected for the machine name and port used. Validate that there's no trailing or additional slash (the character **/**) in the URL or at the end of it.
1. In headquarters, on the **Commerce shared parameters** page, verify that the correct client ID is added to the **Relying parties** FastTab. Additionally, verify that the correct `https://retailstorescaleunit.retailserver.com` entry is added to the **Server resource IDs** FastTab. If not, substitute the actual Retail Server URL.
1. In headquarters, verify that every client ID that was generated for each store exists on the **Microsoft Entra applications** page.
1. On the headquarters **Channel profile** page, verify that the computer name in each URL is correct, and that each URL is correctly formatted, and so on.
1. On the headquarters **Channel database** page, verify that full and correct synchronization occurred for the new channel database.
1. Verify that the store is correctly configured to use the new channel database.

If the Retail Server stops functioning after a period of time, there are two things you must verify:

- Verify if the password policy requires the service account that was generated to change the password (password expiration).
- Rerun the same installer over the current installation (idempotent), which updates a service account's password or allow the user to update the selected account's password.

Microsoft highly recommends that you also review [SQL Server versions and licenses](../dev-itpro/implementation-considerations-cdx.md#sql-server-versions-and-licenses).

## Uninstall CSU

To uninstall Commerce Scale Unit components, follow these steps.

1. Select the Windows logo key, and then enter "Add or remove programs" in the search box. In the search results, select **Add or remove programs**.
1. In the **Settings** \> **Apps** \> **Installed Apps** window, locate  **Microsoft Dynamics 365 Commerce Scale Unit** in the application list, select the ellipsis (**...**), and then select **Uninstall**.
1. Wait for the uninstaller to finish removing the program.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
