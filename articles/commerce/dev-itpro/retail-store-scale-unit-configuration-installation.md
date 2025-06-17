---
title: Configure and install Commerce Scale Unit (self-hosted)
description: This article explains how to use self-service to configure and install Commerce Scale Unit (self-hosted) on computers in a brick-and-mortar store.
author: jashanno
ms.date: 06/01/2025
ms.topic: install-set-up-deploy
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: brstor
ms.search.validFrom: 2016-11-30
ms.assetid: 5e28948f-d40a-40e8-843b-8c2747916546
ms.search.form: SysMicrosoft Entra IDClientTable, RetailCDXDataStore, RetailCDXDataGroup, RetailChannelProfile, RetailSharedParameters, RetailStoreTable
ms.custom: 
  - bap-template
---

# Configure and install Commerce Scale Unit (self-hosted)

[!include [banner](../includes/banner.md)]

This article explains how you can use self-service to configure a Commerce Scale Unit in Microsoft Dynamics 365 Commerce headquarters, download it, and install it on one or more computers in a brick-and-mortar store. Commerce Scale Unit (CSU) combines the Commerce channel database, Commerce async client, Retail Server, and Cloud point of sale (POS) components. A Commerce environment already provides these components in the cloud. However, you can now configure them so that they work locally in a store or datacenter, in either a single-computer setup (the default option) or a multiple-computer setup. This article also explains how to uninstall and troubleshoot Commerce Scale Unit.

> [!IMPORTANT]
> - A basic design principle to follow is that if you're not able to customize in a requested manner on a Commerce Scale Unit (Cloud), you should not customize this way with a CSU (self-hosted). It is critical to understand that direct database access is not supported and can easily cause breaks in customizations that use this concept. A CSU (self-hosted) is primarily for enabling cross-terminal scenarios, reducing latency or backup for poor WAN connectivity, and providing scale-out to spread the load of POS terminals across multiple CSU components.
> - This component uses a server certificate in addition to Azure Service-to-Service authentication. Both the generated Azure web application keys (formerly called *secrets*) and the server certificate must be managed for expiration. By default, a certificate and a generated Azure web application key expires in one calendar year (365 days).
> - It's critical that you have a plan to rotate this key at least one month prior to expiration. Planning is necessary when working with a high number of stores to ensure that there's sufficient time to roll out the change to all stores.

## Prerequisites  

Before beginning a Commerce Scale Unit (Retail Server) installation, you must complete the following one time tasks. These operations often need specific permissions and therefore may require the help of your organization's administrative personnel.


### 1. Create Azure Active Directory apps and Register in Headquarters

First, you must create two Microsoft Entra ID (formerly known as Azure Active Directory) apps, one for the CSU and one for the Store Commerce for Web app (formerly known as Cloud point of sale or CPOS). For instructions, see [Set up a custom Retail Server app in Microsoft Entra ID](cpos-custom-aad.md#set-up-a-custom-retail-server-app-in-microsoft-entra-id), [Set up a custom app for Store Commerce for Web in Microsoft Entra ID](cpos-custom-aad.md#set-up-a-custom-app-for-store-commerce-for-web-in-microsoft-entra-id).
and [Update identity providers settings in Commerce headquarters](cpos-custom-aad.md#update-identity-providers-settings-in-commerce-headquarters).

[!IMPORTANT]
> - To help maintain a high level of security across the company, we strongly recommend that you create a new application ID (client ID) and key (secret) for each store that is created.
> - If you're installing Commerce Scale Unit for use with an on-premises environment using Active Directory Federation Services, instead of Azure, follow the instructions in the Commerce installation document for on-premises environments. For more information, see [Installation steps for Commerce channel components in an on-premises environment](../../fin-ops-core/dev-itpro/deployment/deploy-retail-onprem.md).


### 2. Configure headquarters for a new Commerce Scale Unit
To create a functioning Commerce Scale Unit, complete the procedures in all sections of this article. You will first complete the initial configuration in headquarters then continue with installing the Commerce Scale Unit. 

> [!IMPORTANT]
> - Channel functionality in an on-premises environment is enabled exclusively via use of Commerce Scale Unit (self-hosted). For an overview, see Commerce Scale Unit (self-hosted). Unlike a cloud deployment, an on-premises environment does not enable seamless, high-availability deployment of channel components via Lifecycle Services (LCS). The only way to use channel components is by installing Commerce Scale Unit (self-hosted).
> - For on-premises deployments, perform the following steps:
>   1. Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database group**.
>   2. On the Action pane, select **New**.
>   3. In the **Name** field, enter **Default**. Enter a description in the **Description** field, if needed.
>   4. In the **Channel schema** field, select **AX7**.
>   5. In the **Working folders** field, select **File storage**.
>   6. On the Action Pane, select **Save**.

### Create a new channel database record

1. In headquarters, go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database**.
2. On the **Channel database** page, on the Action Pane, select **New**.
3. In the **Channel database ID** field, enter a unique value.
4. In the **Channel data group** field, select the **Default** option. Select any option that has been created.

    > [!IMPORTANT]
    > For on-premises deployments, this value will be the **Default** value that was previously described in this article.

5. In the **Type** field, leave the default value (**Channel database**) selected.
6. You can leave the **Data sync interval** field blank. Alternatively, you can select a value in this field. For example, in the demo data, the value **D60-U15** specifies a 15-minute synchronization interval.

    The **Data sync interval** value determines how often the data is synchronized between the channel database (Commerce Scale Unit) and headquarters. If no value is entered, the default interval that is set up in Commerce Scale Unit is used. This default interval is three minutes.

7. On the **Retail channel** FastTab, select **Add**, and then, in the **Channel** field, select the appropriate store channel. Repeat this step to add all the channels that should use this database.
8. Select **Save**.

9. If you encounter the **Mapping a New Retail Channel** warning dialog box, select **Yes**.  

    You can also add channels that don't use this database. In this way, you keep the data for those channels in the Commerce Scale Unit channel database. The channels that actively use this database can then access that data locally.

### 3. Create a new channel profile
Next, you must create a new channel profile record for the CSU URL, and then update the existing store records to use the new channel database and profile. 

> [!NOTE]
> Alternatively, you can instead modify the existing channel profile record to use the CSU URLs. 

To create a new channel profile in headquarters and update the existing store records to use the new channel database and profile, follow these steps.

12. Go to **Retail and Commerce \> Channel setup \> Channel profiles**.
13. On the Action Pane, select **New**.
14. In the **Name** field, enter a unique name for the channel profile.

    > [!IMPORTANT]
    > For on-premises deployments, any value can be entered in this field, however, the value **Default** is common.

15. On the Action Pane, select **Save**.
16. On the **Profile properties** FastTab for the new channel profile, select **Add**.
17. In the **Property key** field, select **Retail Server URL**.
18. In the **Property value** field, enter the URL of the Retail Server that will be installed. (Note: When configuring for a development environment, enter `https://<HostName>:446/RetailServer/Commerce`.)

    The standard format for the URL of Commerce Scale Unit is `https://<Computer Name>:<Port>/RetailServer/Commerce`. In this format, **\<Computer Name\>** is either the fully qualified domain name (FQDN) of the computer where Commerce Scale Unit is installed or, for systems that aren't joined to a domain, the full computer name. **\<Port\>** is the port number that should be used in the installation. The port number must be a value between 1 and 65535. If you're using the default HTTPS port (443), you don't have to specify the port number.

19. On the **Profile properties** FastTab for the new channel profile, select **Add**.
20. In the **Property key** field, select **Cloud POS URL**.
21. In the **Property value** field, enter the URL of the Cloud POS instance that should be installed for Commerce Scale Unit. 

    The standard format for the URL of Cloud POS is `https://<Computer Name>:<Port>/POS`. In this format, **\<Computer Name\>** is either the FQDN of the computer where the Commerce Scale Unit is installed. or for systems that aren't joined to a domain, the full computer name. **\<Port\>** is the port number that used in the installation. The port number must be a value between 1 and 65535. If you're using the default HTTPS port (443), you don't have to specify the port number.

    > [!NOTE]
    > - When configuring for a development environment, enter `https://<HostName>:446/POS`. 
    > - The \<HostName\> value typically starts with "DEV" and can be found by opening IIS Manager and reviewing the server name value shown in the upper left corner. It can also be found on the LCS Environments page in the **VM Name** column under **Manage environment \> LOCAL ACCOUNTS**.

22. On the Action Pane, select **Save**.

    > [!NOTE]
    > - If media is commonly used, it will be necessary to generate a **Media Server Base URL** for the profile. For testing and simplicity, the URL that exists for the **Default** Channel profile can be reused.
    > - For on-premises deployments, the **Media Server Base URL** will be where all media is stored for POS devices.

23. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
24. Click the channel ID link for the store that uses the new channel database.
25. On the details page for the selected store, on the Action Pane, select **Edit**.
26. On the **General** FastTab for the store, in the **Live channel database** field, select the channel database that you created in step 3.
27. On the Action Pane, select **Save**.
28. On the **General** FastTab for the store, in the **Channel profile** field, select the channel profile that you created in step 12.
28. On the Action Pane, select **Save**.
> [!NOTE]
> - If you receive a warning stating `The store's closing method must be set to 'Shift'`, on the **Statement/Closing** FastTab of the store, update the **Closing Method** value to **Shift**.

29. Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database group**.
30. Select the **Default** data group, and then, on the Action Pane, select **Full data sync**. In the **Select a distribution schedule** field, select job **9999**, and then select **OK**. In the dialog box that appears, select **OK** to confirm the full synchronization. All the data in the channel database is prepared for download.

If no jobs appear, then initialize the base configuration [Update configurations](cdx-best-practices.md#update-configurations)

    > [!IMPORTANT]
     ### Update CDX data groups
     The following change removes the default database from the Commerce Data Exchange (CDX) data groups in headquarters, because this database is no longer used. Failure to make this update can result in data sync errors later on. 

     To update CDX data groups in headquarters, follow these steps.

     1. Go to **Retail and Commerce \> Distribution Schedule**.
     1. Select the **Default Data** group.
     1. Remove the default database record from this group.

    > For on-premises deployments, there's no **Default** channel data group. Create a new data group (and associate it to the channel database and distribution schedule jobs).
    
## Download and Install a new Commerce Scale Unit
To download and execute the Commerce Scale Unit installer, see [Downloading and Running the Commerce Scale Unit Installer](retail-store-scale-unit-download-install.md). This article describes the steps necessary to download required configuration from Headquarters, download the installation program, and how to run the installer.

Once installation is complete, return here for security recommendations and troubleshooting.

## Help secure Commerce Scale Unit

According to current security standards, the following options should be set in a production environment:

- You should completely disable SSL (v2 and v3) on the computer.
- You should enable and use only TLS version 1.2 (or the current highest version).

    > [!NOTE]
    > By default, SSL and all versions of TLS except TLS 1.2 are disabled.

    To edit or enable SSL and TLS settings, follow these steps:
    1. Press the Windows logo key+R to open a **Run** window.
    2. In the **Open** field, enter **Regedit**, and then select **OK**.
    3. In the **User Account Control** window, select **Yes** (if this step is required), and then, in the new **Registry Editor** window, go to **HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\SecurityProviders\\SCHANNEL\\Protocols**.
    4. The following keys have been automatically entered to enable only TLS 1.2:
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

## Troubleshoot Commerce Scale Unit

Here's a checklist of things to verify:

1. Open the configuration file and verify that the Retail Server URL specified contains the suffix **/Commerce** and is correctly formed based on what is expected for the machine name and port used. Validate that there's no trailing or additional slash (the character **/**) in the URL or at the end of it.
2. In headquarters, on the **Commerce shared parameters** page, verify that the correct client ID is added to the **Relying parties** FastTab. Additionally, verify that the correct `https://retailstorescaleunit.retailserver.com` entry is added to the **Server resource IDs** FastTab.
3. In headquarters, verify that every client ID that was generated for each store exists on the **Microsoft Entra applications** page.
4. On the headquarters **Channel profile** page, verify that the computer name in each URL is correct, and that each URL is correctly formatted, and so on.
5. On the headquarters **Channel database** page, verify that full and correct synchronization occurred for the new channel database.
6. Verify that the store is correctly configured to use the new channel database.

If the Retail Server stops functioning after a period of time, there are two simple things to verify:

- Verify if the password policy requires the service account that was generated to change the password (password expiration).
- Rerun the same installer over the current installation (idempotent), which updates a service account's password or allow the user to update the selected account's password.

We highly recommended that you also review [SQL Server versions and licenses](../dev-itpro/implementation-considerations-cdx.md#sql-server-versions-and-licenses).

## Uninstall Commerce Scale Unit

Use Control Panel in Microsoft Windows to uninstall Commerce Scale Unit components.

1. Press the Windows logo key, and then enter **Add or remove programs** in the search box. In the search results, select **Add or remove programs**.
2. In the Settings > Apps > Installed Apps Window, search for or locate  **Microsoft Dynamics 365 Commerce Scale Unit** in the application list, and then, click the "..." button to select **Uninstall**.
4. Wait for the uninstaller to finish removing the program.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
