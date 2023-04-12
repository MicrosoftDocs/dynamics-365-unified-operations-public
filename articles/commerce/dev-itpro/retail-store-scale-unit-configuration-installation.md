---
title: Configure and install Commerce Scale Unit (self-hosted)
description: This article explains how to use self-service to configure and install Commerce Scale Unit (self-hosted) on computers in a brick-and-mortar store.
author: jashanno
ms.date: 04/12/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: jashanno
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 219744
ms.assetid: 5e28948f-d40a-40e8-843b-8c2747916546
ms.search.industry: Retail
ms.search.form: SysAADClientTable, RetailCDXDataStore, RetailCDXDataGroup, RetailChannelProfile, RetailSharedParameters, RetailStoreTable
---

# Configure and install Commerce Scale Unit (self-hosted)

[!include [banner](../includes/banner.md)]

This article explains how you can use self-service to configure a Commerce Scale Unit in Microsoft Dynamics 365 Commerce Headquarters, download it, and install it on one or more computers in a brick-and-mortar store. Commerce Scale Unit (CSU) combines the Commerce channel database, Commerce Async Client, Retail Server, and Cloud point of sale (POS) components. A Commerce environment already provides these components in the cloud. However, you can now configure them so that they work locally in a store or datacenter, in either a single-computer setup (the default option) or a multiple-computer setup. This article also explains how to uninstall and troubleshoot Commerce Scale Unit.

> [!IMPORTANT]
> - A basic design principle to follow is that if you are not able to customize in a requested manner on a Commerce Scale Unit (Cloud), you should not customize this way with a CSU (self-hosted).  It is critical to understand that direct database access is not supported and can easily cause breaks in customizations that use this concept.  A CSU (self-hosted) is primarily for enabling cross-terminal scenarios, reducing latency or backup for poor WAN connectivity, and providing scale-out to spread the load of POS terminals across multiple CSU components.
> - Do not install a CSU on a developer environment, which typically already has a configured Retail Server and Channel database.
> - It is critical to note that this component utilizes a server certificate in addition to Azure Service-to-Service authentication.  Both the generated Azure web application keys (formerly called *secrets*) and the server certificate must be managed for expiration.  By default, a certificate and a generated Azure web application key expires in one calendar year (365 days).

## Before you begin

> [!IMPORTANT]
> To help maintain a high level of security across the company, we strongly recommend that you create a new application ID (client ID) and key (secret) for each store that is created. This step requires a new Web app.

1. Generate a Microsoft Azure Active Directory (Azure AD) app registration to create an application ID (client ID) and key (secret). For instructions, see [Create an Azure Active Directory application](/azure/azure-resource-manager/resource-group-create-service-principal-portal#create-an-azure-active-directory-application). This article reviews Azure user permissions and requirements, and explains how to generate an app registration.

    > [!IMPORTANT]
    > If you are installing Commerce Scale Unit for use with an on-premises environment using Active Directory Federation Services, instead of Azure, follow the instructions in the Commerce installation document for on-premises environments. For more information, see [Installation steps for Commerce channel components in an on-premises environment](../../fin-ops-core/dev-itpro/deployment/deploy-retail-onprem.md).

2. After an application ID (client ID) and key are created for Commerce Scale Unit, the client ID must be accepted in Commerce. Go to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**. Enter the application ID (client ID) in the **Client ID** column, enter descriptive text in the **Name** column, and enter **RetailServiceAccount** in the **User ID** column.

## Configure a new Commerce Scale Unit

To create a functioning Commerce Scale Unit, complete the procedures in all sections of this article until the "Multiple-computer installation" section. To complete the configuration and installation, you must first do the initial configuration in Headquarters. Next, you must complete the installation. Finally, you must return to Headquarters to finish the configuration, so that Commerce Scale Unit works correctly.

> [!IMPORTANT]
> Channel functionality in an on-premises environment is enabled exclusively via use of Commerce Scale Unit (self-hosted). For an overview, see Commerce Scale Unit (self-hosted). Unlike a cloud deployment, an on-premises environment does not enable seamless, high-availability deployment of channel components via Lifecycle Services (LCS). The only way to use channel components is by installing Commerce Scale Unit (self-hosted).
>
> For on-premises deployments, perform the following steps:
>   1. Go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Commerce scheduler** &gt; **Channel database group**.
>   2. On the Action pane, select **New**.
>   3. In the **Name** field, enter **Default**. Enter a description in the **Description** field, if needed.
>   4. In the **Channel schema** field, select **AX7**.
>   5. In the **Working folders** field, select **File storage**.
>   6. On the Action Pane, select **Save**.

1. In Headquarters, go to  **Retail and Commerce** &gt; **Headquarters setup** &gt; **Commerce scheduler** &gt; **Channel database**.
2. On the **Channel database** page, on the Action Pane, select **New**.
3. In the **Channel database ID** field, enter a unique value.
4. In the **Channel data group** field, select the **Default** option. Select any option that has been created.

    > [!IMPORTANT]
    > For on-premises deployments, this value will be the **Default** value that was previously described in this article.

5. In the **Type** field, leave the default value (**Channel database**) selected.
6. You can leave the **Data sync interval** field blank. Alternatively, you can select a value in this field. For example, in the demo data, the value **D60-U15** specifies a 15-minute synchronization interval.

    The **Data sync interval** value determines how often the data is synchronized between the channel database (Commerce Scale Unit) and Headquarters. If no value is entered, the default interval that is set up in Commerce Scale Unit is used. This default interval is three minutes.

7. On the **Commerce channel** FastTab, select **Add**, and then, in the **Channel** field, select the appropriate store channel. Repeat this step to add all the channels that should use this database.

    You can also add channels that don't use this database. In this way, you keep the data for those channels in the Commerce Scale Unit channel database. The channels that actively use this database can then access that data locally.

    > [!IMPORTANT]
    > For on-premises deployments, select the **Download** button on the Action pane and select **Commerce Scale Unit package**.  This will cause a known error and initiate the upload logic so that the following step in this document can be correctly completed. Allow for at least one minute to pass while the upload logic completes.

8. On the **Commerce Scale Unit package** FastTab, in the **Package reference** field, select the appropriate Commerce Scale Unit package.  Each environment generates a base Commerce Scale Unit package. Therefore, this field always contains at least one option.
9. On the Action Pane, select **Save**.
10. Go to **Retail and Commerce** &gt; **Channel setup** &gt; **Channel profiles**.
11. On the Action Pane, select **New**.
12. In the **Name** field, enter a unique name for the channel profile.

    > [!IMPORTANT]
    > For on-premises deployments, any value can be entered in this field, however, the value **Default** is common.

13. On the Action Pane, select **Save**.
14. On the **Profile properties** FastTab for the new channel profile, select **Add**.
15. In the **Property key** field, select **Retail Server URL**.
16. In the **Property value** field, enter the URL of the Retail Server that will be installed.

    The standard format for the URL of Commerce Scale Unit is `https://<Computer Name>:<Port>/RetailServer/Commerce`. In this format, **&lt;Computer Name&gt;** is either the fully qualified domain name (FQDN) of the computer where Commerce Scale Unit is installed or, for systems that aren't joined to a domain, the full computer name. **&lt;Port&gt;** is the port number that should be used in the installation. The port number must be a value between 1 and 65535. If you're using the default HTTPS port (443), you don't have to specify the port number.

17. On the **Profile properties** FastTab for the new channel profile, select **Add**.
18. In the **Property key** field, select **Cloud POS URL**.
19. In the **Property value** field, enter the URL of the Cloud POS instance that should be installed for Commerce Scale Unit.

    The standard format for the URL of Cloud POS is `https://<Computer Name>:<Port>/POS`. In this format, **&lt;Computer Name&gt;** is either the FQDN of the computer where the Commerce Scale Unit is installed or, for systems that aren't joined to a domain, the full computer name. **&lt;Port&gt;** is the port number that will be used in the installation. The port number must be a value between 1 and 65535. If you're using the default HTTPS port (443), you don't have to specify the port number.

20. On the Action Pane, select **Save**.

    > [!NOTE]
    > If media is commonly used, it will be necessary to generate a **Media Server Base URL** for the profile.  For testing and simplicity, the URL that exists for the **Default** Channel profile can be reused.
    >
    > For on-premises deployments, the **Media Server Base URL** will be where all media is stored for POS devices.

21. Go to **Retail and Commerce** &gt; **Channels** &gt; **Stores** &gt; **All stores**.
22. Select the channel ID for the store that will use the new channel database.
23. On the details page for the selected store, on the Action Pane, select **Edit**.
24. On the **General** FastTab for the store, in the **Live channel database** field, select the channel database that you created in step 3.
25. On the Action Pane, select **Save**.
26. On the **General** FastTab for the store, in the **Channel profile** field, select the channel profile that you created in step 12.
27. Go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Commerce scheduler** &gt; **Channel data group**.
28. Select the **Default** data group, and then, on the Action Pane, select **Full data sync**. In the **Select a distribution schedule** field, select job **9999**, and then select **OK**. In the dialog box that appears, select **OK** to confirm the full synchronization. All the data in the channel database is prepared for download.

    > [!IMPORTANT]
    > For on-premises deployments, there is no **Default** channel data group.  Create a new data group (and associate it to the channel database and distribution schedule jobs).

### Download the Commerce Scale Unit installer

1. In Headquarters, go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Commerce scheduler** &gt; **Channel database**.
2. In the list of channel databases on the left, select the channel database that you created earlier.
3. On the Action Pane, select **Download**.
4. On the drop-down menu, select **Configuration file**.

    > [!NOTE]
    > To ensure that the Commerce Scale Unit installer correctly uses the configuration file (XML file), you must save the configuration file to the same location as the installer. If the configuration file is not the same file name as the installer executable, either the executable must be run using the command line to specify the configuration file or you need to rename the XML configuration file to have the same base name as the executable file name.
    >
    > For on-premises deployments, the configuration file (at this time) requires manual editing:
    > - StoreSystemAosUrl should have the value used to access headquarters (AX).  It is critical to keep a trailing slash at the end of this URL (for example, `https://myContosoURL.com/namespaces/AXSF/`).
    > - AADTokenIssuerPrefix should have the value `https://NOTUSED.microsoft.com`
    > - TransactionServiceAzureAuthority should have the value `https://<ADFS FQDN including .com>/adfs`.
    > - TransactionServiceAzureResource should have the base URL value of the **StoreSystemAosUrl** edited as shown above. For instance, based on the above example `https://myContosoURL.com` would be used as the value, removing the **/namespaces/AXSF/** portion of the URL.

5. On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.)

    Browsers might block the download pop-up that is generated. Select either **Allow once** or **Options for this site** &gt; **Always allow**. Then select **Download** again.

6. On the Action Pane, select **Download**.
7. On the drop-down menu, select **Commerce Scale Unit package**.
8. On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.)

    The correct installation package is automatically selected for download, based on the Commerce Scale Unit package on the selected channel database.

9. After the setup installer has been saved, on the Notification bar, select **Run**. (This step might differ, depending on the type of browser.)

### Run the Commerce Scale Unit installer

> [!NOTE]
> - If the CSU (Self-hosted) installer is being run to update a current installation, verify that the version is the same or newer. If an earlier version is required to be installed for any reason, it is critical to uninstall the current CSU (Self-hosted) and delete the CSU SQL database. If you do not delete the database in the scenario where an earlier version is required, the database schema and data will be of a newer version than the CSU installation and errors and issues will occur.
> - Do not install a CSU on a developer environment, which typically already has a configured Retail Server and Channel database.
> - Before running the Commerce Scale Unit (self-hosted) installer, verify that the configuration file is named the same as the installer executable. This would look like **ExecutableInstallerName.xml** and put both files in the same folder. Alternatively, there is a command line delimiter to specify the configuration file manually.
> - If you plan to install and use Retail Cloud POS, you must initialize the configuration the first time that you run the installer, as described in the following procedure.

Before you run the Commerce Scale Unit installer, make sure that all [system requirements](../../fin-ops-core/fin-ops/get-started/system-requirements.md) are met.

> [!IMPORTANT]
> If you are installing Commerce Scale Unit for use with an on-premises environment, you must start it from a command line using administrator privileges as follows:
> StoreSystemSetup.exe -UseAdfsAuthentication

The Commerce Scale Unit installer first extracts the associated files. It then begins the installation.

1. On the first page of the installer, select the components to install. You can install the following components:

   - Commerce channel database together with Async Client
   - Retail Server
   - Cloud POS

     > [!NOTE]
     > - To install Cloud POS, you must also select and install Retail Server.
     > - By default, the installer installs all components on one computer. To install the components across multiple computers, you must complete additional manual steps. For more information, see the "Multiple-computer installation" section.

     After you've selected all the components to install, select **Next** to continue.

2. The installer validates that all prerequisites are met. If a valid version of Microsoft SQL Server isn't found, the installer will fail during the prerequisites check.  Install a supported version of SQL Server and try the installer again.

    > [!NOTE]
    > - To meet the prerequisites, SQL Server must have full-text search, and it must support, at a minimum, Transport Layer Security (TLS) 1.2. Review the system requirements for the supported versions of SQL Server. It is highly recommended to review [SQL Server versions and licenses](../dev-itpro/implementation-considerations-cdx.md#sql-server-versions-and-licenses).
    > - If a system restart is required, the installer will prompt the user.  This prompt is based upon a Windows system registry key that notifies all applications when a restart is required. While it is recommended to restart prior to continuing the installation, a restart is not required and the installer can continue without restarting the computer.

3. Verify the URL for Application Object Server (AOS), and then select **Next**. (The AOS URL is the URL that is used to access Headquarters.)

    > [!NOTE]
    > The Retail Server URL is automatically entered from the configuration file.

4. Select a valid Secure Sockets Layer (SSL) certificate to use for HTTPS communication.

    The certificate must use private key storage, and server authentication must be listed in the enhanced key usage property. Additionally, the certificate must be trusted locally, and it can't be expired. It must be stored in the personal certificate store location on the local computer.

5. If a specific user is required, enter the user name and password that the application pool should run under. By default, the installer automatically generates a service account to use. This approach is more secure and is recommended.

    > [!NOTE]
    > It is important to note that service accounts, out of box, still function under the same password policy that is defined for all other accounts.  This means that the minimum password age policy still applies to the Retail Server service account and must be updated when necessary.  By default, on Windows Server 2012 R2, this is typically 42 days.  If the password does expire on a used service account, the Commerce Scale Unit components will fail to continue functioning until the issue is resolved.

6. On the next page, enter the user account and password for the Retail Server application pool and Async Client. By default, this account is automatically generated. However, you can manually enter the user account and password.
7. Enter the HTTPS port to use, and verify that the host name of the computer is correct. Then select **Next** to continue.

    > [!NOTE]
    > - The installer automatically enters the host name. If, for any reason, the host name must be changed for the installation, change it here. The host name must be the FQDN of the system, and it must be entered in the **Host name** field for the selected Store system entry.

8. Enter the application ID (client ID) and key (secret) that are associated with this Commerce Scale Unit installation. Additionally, verify the channel database ID, which is automatically entered from the configuration file. Then select **Install**. If you will use Retail Cloud POS, make sure that the **Configure Retail Cloud POS** check box at the bottom of the page is selected. This configuration requests Azure AD sign-in and automatically generates all required information in Azure, so that Retail Cloud POS can be used on-premises. If you are installing Commerce Scale Unit for use with an on-premises environment, you must clear this option.

    For information about how to create web applications in Azure, see [Create an Azure Active Directory application](/azure/azure-resource-manager/resource-group-create-service-principal-portal#create-an-azure-active-directory-application).

    > [!IMPORTANT]
    > - When installing Commerce Scale Unit for use with an on-premises environment, Cloud POS does not require an Azure or AD FS application to be configured, so it is important to unmark **Configure Retail Cloud POS**.
    > - When installing Commerce Scale Unit for use with an on-premises environment, the Client ID (Application ID) and Secret (Key) used will be the values generated by the PowerShell script performed in the configuration steps performed in steps 6-8 in the [Installation steps for Commerce channel components in an on-premises environment](../../fin-ops-core/dev-itpro/deployment/deploy-retail-onprem.md) article. (Step 6 creates the Client ID and step 8 resets the Secret to be copied.)

    When you create the Web App, the initial URI and URL don't have to be any specific value. Only the application ID (client ID) and key (secret) that are created are important.

9. After the application ID (client ID) and key (secret) are created for Commerce Scale Unit, the application ID (client ID) must be accepted in Commerce. Follow the next procedure to finish the configuration in Headquarters.
10. After the installation is complete, the final health page appears. This page shows whether the installation was successful. It also shows the health of each component, based on basic connection tests, and the location of this article. If the installation wasn't successful, the page shows the location of the log files. We recommend that you keep this final health page open until you've completed the configuration of Commerce Scale Unit and all components are working correctly (Requiring the completion of the following section).

### Finish the configuration in Headquarters

The last steps require validation and verification that the Azure application ID (client ID) and key (secret) are correctly accepted in Headquarters, so that connections can be made between the environment and the new Commerce Scale Unit.

1. After the application ID (client ID) and key (secret) are created for Commerce Scale Unit and entered in the installer, the application ID (client ID) must be accepted in Headquarters.

    In Headquarters, go to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**. Enter the application ID (client ID) in the **Client ID** column, enter descriptive text in the **Name** column, and enter **RetailServiceAccount** in the **User ID** column.

2. If Cloud POS is configured for use, a client ID is shown at the end of the installation. You must add this client ID to the **Commerce shared parameters** page in Commerce.

    > [!IMPORTANT]
    > In an on-premises environment, this step is not required to be completed.

    1. In Headquarters, go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Commerce shared parameters**.
    2. Select **Identity providers**.
    3. On the **Identity providers** FastTab, select the provider that begins with `HTTPS://sts.windows.net/`. The values on the **Relying parties** FastTab are set, based on your selection.
    4. On the **Relying parties** FastTab, select **Add**. Enter the client ID that is listed on the final health page of the Commerce Scale Unit installer. Set the **Type** field to **Public** and the **UserType** field to **Worker**. Then, on the Action Pane, select **Save**.
    5. Select the new relying party, and then, on the **Server resource IDs** FastTab, select **Add**. In the **Server Resource ID** column, enter `https://retailstorescaleunit.retailserver.com`.
    6. On the Action Pane, select **Save**.

3. In Headquarters, go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Commerce shared parameters**.
4. Select **Identity providers**.
5. On the **Identity providers** FastTab, select **Add**.
6. In the new **Issuer** row, enter the URL of the newly installed Commerce Scale Unit. At the end of the URL, add **/auth**. The URL will resemble `https://<My Case-Sensitive Computer Name>:<Port Number>/RetailServer/auth`.

    > [!NOTE]
    > The URL described above is case sensitive.
    > There will be a new identity provider line for each Commerce Scale Unit that is installed. Each will have a URL that resembles this URL.

7. In the **Name** column, enter a description for the store that the URL belongs to.
8. In the **Type** column, select **Open ID Connect**.

    > [!NOTE]
    > This new row must be duplicated for every Commerce Scale Unit installation (that is, for every unique URL).

9. On the Action Pane, select **Save**.
10. On the **Identity providers** FastTab, select the newly created line. The values on the **Relying parties** FastTab are set, based on your selection.
11. On the **Relying parties** FastTab, select **Add**, and add the following two entries:

    - In the **ClientId** column, enter **Cloud POS**. Set the **Type** field to **Public** and the **UserType** field to **Worker**.
    - In the **ClientId** column, enter **Modern POS**. Set the **Type** field to **Public** and the **UserType** field to **Worker**.

12. On the Action Pane, select **Save**.
13. In Commerce, go to **Retail and commerce** &gt; **Retail and commerce IT** &gt; **Distribution Schedule**, and run CDX Job **1110**.
14. When you've finished, return to the installer, and select **Finish**.

    The final page of the installer includes valuable information that you can use to test and validate that all components work correctly. Keep this page open until you've completed the validation.

> [!NOTE]
> If the installer doesn't show a check mark for Retail Server or Async Client, wait 10 minutes so that any cached values can be updated in the cloud. Then check again. If the installer still isn't fully successful, run a full synchronization on the new channel database that this installation uses.
>
> If you followed all the steps correctly, your configuration should have these characteristics:
>
> - In Azure, two web applications have been automatically generated through the installer:
>
>   - Retail Store Scale Unit Cloud POS
>   - Retail Store Scale Unit Retail Server for Cloud POS
>
> - In Azure, a web application (that is, an App registration in the new Azure portal) has been manually created for each Commerce Scale Unit installation (for example, CommerceScaleUnitHouston). A key (secret) has been created that can be used in the installer, as described earlier.
> - The application ID (client ID) of the manually created web application has been added to the **Azure Active Directory applications** page in Commerce, as explained in step 1 of the preceding procedure.
> - The Cloud POS application ID (client ID) that was shown at the end of the Commerce Scale Unit installer has been added on the **Identity providers** FastTab, as explained in the final steps of the "Run the Commerce Scale Unit installer" section.

### Multiple-computer installation

Only advanced users should install Commerce Scale Unit across multiple computers. The following set of procedures explains how to install the Commerce channel database and Async Client on one computer, and Retail Server and Cloud POS on a second computer. The instructions assume that both systems are on the same domain, and that users for the services that will be installed have already been created on both systems. It's important that you do all configuration in Headquarters.

#### Installation on the first computer

On the first computer, run the Commerce Scale Unit self-service installer as described earlier in this article, but make the following changes.

1. Select only Commerce channel database and Async Client as the components to install. Then select **Next** to continue with the installation.

    > [!NOTE]
    > You can use a generated service account for Async Client, because Async Client won't be accessed outside the computer that it's installed on.

2. Enter the client ID and key (secret). Keep these details available, so that you can use them again on the second computer.
3. After a client ID and key (secret) are created for Commerce Scale Unit, the client ID must be accepted in Commerce. Go to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**. Enter the client ID in the **Client ID** column, enter descriptive text in the **Name** column, and enter **RetailServiceAccount** in the **User ID** column.
4. When setup is successful, start SQL Server Configuration Manager.
5. Go to **SQL Server Network Configuration** &gt; **Protocols** for the SQL Server instance.
6. Right-click, and then select **Properties**.
7. In the **Flags** section, change the value of **Set Force Encryption** to **Yes**.
8. In the **Certificate** section, select the SSL certificate on the drop-down menu. This SQL Server SSL certificate is the same certificate that is used in the installer.
9. Select **OK**.
10. Go back to **Protocols** in SQL Server Configuration Manager, and enable the following protocols:

    - Named Pipes
    - TCP/IP

11. Right-click the **TCP/IP** protocol, and then select **Properties**.
12. In the **IP Address** section, scroll down the list to **IPALL**.
13. Enter **TCPPort = 1433**.
14. Select **OK**.
15. Start Microsoft Windows Firewall with Advanced Security.
16. In Windows Firewall, create an inbound rule to open TCP port 1433.

For detailed information about SQL Server and Windows Firewall, see [Configure a Windows Firewall for Database Engine Access](/sql/database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access).

#### Installation on the second computer

On the second computer, run the Commerce Scale Unit Self-service installer as described earlier in this article, but make the following changes.

1. Select only Retail Server and Cloud POS as the components to install. If you are installing only Retail Server, don't select Cloud POS. Then select **Next** to continue with the installation.
2. Enter the domain user credentials (user name and password) that have permission to access SQL Server on the first computer. Then select **Next**.

    > [!NOTE]
    > A generated service account can't be used, because Retail Server requires access to the SQL database on the first computer. You must use a domain account.

3. Enter the same Client ID and key (secret) that are used on the first computer.

    > [!IMPORTANT]
    > It's critical that you add this Client ID to Commerce headquarters as described earlier.

4. Select **Configure Cloud POS**, and then enter Azure AD credentials that have the correct permissions to create Azure Web Apps.

    For more information about Azure Web Apps, how to create them, and how to generate a new key (secret), see [Use portal to create an Azure Active Directory application and service principal that can access resources](/azure/active-directory/develop/howto-create-service-principal-portal). Note that the sign-in URL and the App ID URI are not important.

5. When setup is successful, don't exit the installer.

    > [!NOTE]
    > At first, the health check ping won't be successful, because the database isn't yet set up correctly. After you've completed the remaining steps of this procedure, you can test the health check again.

6. Start **Microsoft Internet Information Services (IIS)**, select the **Retail Server** website, and select the **Retail Server** web application.
7. Explore the working directory.
8. Open the Web.config file, and then, in the **connectionStrings** section, add **Server name**. **Server name** is the name of the first computer where you installed components. Save the file.
9. If the certificate that is used isn't a valid, trusted certificate from a trusted authority, open CERTMGR.MSC, and follow these steps:

    1. Import the SQL Server SSL certificate that you created earlier, and add it to Trusted Root.
    2. Open a **Command Prompt** window as an administrator, type **IISRESET**, and then press Enter.

10. If Cloud POS is configured for use, a client ID is shown. You must add this client ID to the **Commerce shared parameters** page.

    1. In Commerce, go to **Retail and commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Commerce shared parameters**.
    2. Select **Identity providers**.
    3. On the **Identity providers** FastTab, select the provider that begins with `HTTPS://sts.windows.net/`. The values on the **Relying parties** FastTab are set, based on your selection.
    4. On the **Relying parties** FastTab, select **Add**. Enter the client ID that is listed in the Commerce Scale Unit installer. Set the **Type** field to **Public** and the **UserType** field to **Worker**. Then, on the Action Pane, select **Save**.
    5. Select the new relying party, and then, on the **Server resource IDs** FastTab, select **Add**. In the **Server Resource ID** column, enter `https://retailstorescaleunit.retailserver.com`.
    6. On the Action Pane, select **Save**.

11. In Commerce, go to **Retail and commerce** &gt; **Headquarters setup** &gt; **Commerce scheduler** &gt; **Channel database**, and follow these steps:

    1. Select the channel database that you created at the beginning of this article.
    2. On the Action Pane, select **Full Sync** &gt; **Job 9999**. Full synchronization might require several minutes.
    3. In the Commerce Scale Unit installer, retest to verify that all functionality is working correctly.

12. Start Cloud POS from the computer that you're using for POS operations. (This computer is a third computer that is separate from the Commerce Scale Unit systems.)
13. Activate the Cloud POS device that you're using for this computer.
14. Do a simple sale to verify full end-to-end functionality.

### Help secure Commerce Scale Unit

According to current security standards, the following options should be set in a production environment:

- You should completely disable SSL (v2 and v3) on the computer.
- You should enable and use only TLS version 1.2 (or the current highest version).

    > [!NOTE]
    > By default, SSL and all versions of TLS except TLS 1.2 are disabled. To edit or enable these settings, follow these steps:
    >
    > 1. Press the Windows logo key+R to open a **Run** window.
    > 2. In the **Open** field, enter **Regedit**, and then select **OK**.
    > 3. In the **User Account Control** window, select **Yes** (if this step is required), and then, in the new **Registry Editor** window, go to **HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\SecurityProviders\\SCHANNEL\\Protocols**.
    > 4. The following keys have been automatically entered to enable only TLS 1.2:
    >
    >     - TLS 1.2\\Server:Enabled=1
    >     - TLS 1.2\\Server:DisabledByDefault=0
    >     - TLS 1.2\\Client:Enabled=1
    >     - TLS 1.2\\Client:DisabledByDefault=0
    >     - TLS 1.1\\Server:Enabled=0
    >     - TLS 1.1\\Client:Enabled=0
    >     - TLS 1.0\\Server:Enabled=0
    >     - TLS 1.0\\Client:Enabled=0
    >     - SSL 3.0\\Server:Enabled=0
    >     - SSL 3.0\\Client:Enabled=0
    >     - SSL 2.0\\Server:Enabled=0
    >     - SSL 2.0\\Client:Enabled=0

- No additional network ports should be open, unless they are required for known, specified reasons.
- You must disable cross-origin resource sharing, and you must specify the allowed origins that are accepted.
- You should use only trusted certificate authorities to obtain certificates that will be used on Commerce Scale Unit computers.

> [!IMPORTANT]
> It's critical that you review security guidelines for IIS and the Payment Card Industry (PCI) requirements.

### Troubleshoot Commerce Scale Unit

Here is a checklist of things to verify:

1. Open the configuration file and verify that the Retail Server URL specified contains the suffix **/Commerce** and is correctly formed based on what is expected for the machine name and port used.  Validate that there is no trailing or additional slash (the character **/**) in the URL or at the end of it.
2. In Commerce, on the **Commerce shared parameters** page, verify that the correct client ID has been added to the **Relying parties** FastTab. Additionally, verify that the correct `https://retailstorescaleunit.retailserver.com` entry has been added to the **Server resource IDs** FastTab.
3. In Commerce, verify that every client ID that was generated for each store exists on the **Azure Active Directory applications** page.
4. In Commerce, on the **Channel profile** page, verify that the URLs are correct. To do this, verify that the computer name in each URL is correct, the URL is correctly formatted, and so on.
5. In Commerce, on the **Channel database** page, verify that full synchronization correctly occurred for the new channel database.
6. Verify that the store is correctly configured to use the new channel database.

If the Retail Server stops functioning after a period of time, there are two simple things to verify:

- Verify if the password policy requires the service account that was generated to change the password (password expiration).
- Re-run the same installer over the current installation (idempotent), which will update a service account's password or allow the user to update the selected account's password.

We highly recommended that you also review [SQL Server versions and licenses](../dev-itpro/implementation-considerations-cdx.md#sql-server-versions-and-licenses).

### Uninstall Commerce Scale Unit

Use Control Panel in Microsoft Windows to uninstall Commerce Scale Unit components.

1. Press the Windows logo key, and then enter **Control Panel** in the search box. In the search results, select **Control Panel**.
2. In Control Panel, select **Programs** &gt; **Uninstall a program**.
3. In the **Programs and Features** window, select **Microsoft Dynamics 365 Commerce Scale Unit**, and then, above the list of programs, select **Uninstall**.
4. Wait for the uninstaller to finish removing the program.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
