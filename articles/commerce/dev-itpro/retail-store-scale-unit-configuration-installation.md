---
# required metadata

title: Configure and install Commerce Scale Unit
description: This topic explains how you can use self-service to configure Commerce Scale Unit in Commerce Headquarters, download it, and install it on one or more computers in a brick-and-mortar store.
author: jashanno
manager: AnnBe
ms.date: 01/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata

ms.search.form: SysAADClientTable, RetailCDXDataStore, RetailCDXDataGroup, RetailChannelProfile, RetailSharedParameters, RetailStoreTable
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 219744
ms.assetid: 5e28948f-d40a-40e8-843b-8c2747916546
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Configure and install Commerce Scale Unit

[!include [banner](../includes/banner.md)]

This topic explains how you can use self-service to configure a Commerce Scale Unit (Formerly titled as Retail Store Scale Unit) in Microsoft Dynamics 365 Commerce Headquarters, download it, and install it on one or more computers in a brick-and-mortar store. Commerce Scale Unit combines the Commerce channel database, Commerce Async Client, Retail Server, and Cloud point of sale (POS) components. A Commerce environment already provides these components in the cloud. However, you can now configure them so that they work locally in a store or datacenter, in either a single-computer setup (the default option) or a multiple-computer setup. This topic also explains how to uninstall and troubleshoot Commerce Scale Unit.

> [!IMPORTANT]
> It is critical to note that this component utilizes a server certificate in addition to Azure Service to Service authentication.  Both the generated Azure web application keys (Formerly called Secrets) and the server certificate must be managed for expiration.  By default, a certificate and a generated Azure web application key expires in one calendar year (365 days).

## Before you begin

> [!IMPORTANT]
> To help maintain a high level of security across the company, we strongly recommend that you create a new application ID (client ID) and key (secret) for each store that is created. This step requires a new Web app.

1. Generate a Microsoft Azure Active Directory (Azure AD) app registration to create an application ID (client ID) and key (secret). For instructions, see [Create an Azure Active Directory application](/azure/azure-resource-manager/resource-group-create-service-principal-portal#create-an-azure-active-directory-application). This topic reviews Azure user permissions and requirements, and explains how to generate an app registration. 

    > [!IMPORTANT]
    > If you are installing Commerce Scale Unit for use with an on-premises environment using Active Directory Federation Services, instead of Azure, follow the instructions in the Commerce installation document for on-premises environments. For more information, see [Installation steps for Commerce channel components in an on-premises environment](../../dev-itpro/deployment/deploy-retail-onprem.md).

2. After an application ID (client ID) and key are created for Commerce Scale Unit, the client ID must be accepted in Commerce. Go to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**. Enter the application ID (client ID) in the **Client ID** column, enter descriptive text in the **Name** column, and enter **RetailServiceAccount** in the **User ID** column.

## Configure a new Commerce Scale Unit

To create a functioning Commerce Scale Unit, complete the procedures in all sections of this topic until the "Multiple-computer installation" section. To complete the configuration and installation, you must first do the initial configuration in Headquarters. Next, you must complete the installation. Finally, you must return to Headquarters to finish the configuration, so that Commerce Scale Unit works correctly.

> [!IMPORTANT]
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
    > For on-premises deployments, this value will be the **Default** value that was previously described in this topic.

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

    The standard format for the URL of Commerce Scale Unit is **https://&lt;Computer Name&gt;:&lt;Port&gt;/RetailServer/Commerce**. In this format, **&lt;Computer Name&gt;** is either the fully qualified domain name (FQDN) of the computer where Commerce Scale Unit is installed or, for systems that aren't joined to a domain, the full computer name. **&lt;Port&gt;** is the port number that should be used in the installation. The port number must be a value between 1 and 65535. If you're using the default HTTPS port (443), you don't have to specify the port number.

17. On the **Profile properties** FastTab for the new channel profile, select **Add**.
18. In the **Property key** field, select **Cloud POS URL**.
19. In the **Property value** field, enter the URL of the Cloud POS instance that should be installed for Commerce Scale Unit.

    The standard format for the URL of Cloud POS is **https://&lt;Computer Name&gt;:&lt;Port&gt;/POS**. In this format, **&lt;Computer Name&gt;** is either the FQDN of the computer where the Commerce Scale Unit is installed or, for systems that aren't joined to a domain, the full computer name. **&lt;Port&gt;** is the port number that will be used in the installation. The port number must be a value between 1 and 65535. If you're using the default HTTPS port (443), you don't have to specify the port number.

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

    > [!NOTE]
    > After the first Commerce Scale Unit is created, it requires less data generation to perform a full data sync from the Channel database instead of the Channel data group.
    
    > [!IMPORTANT]
    > For on-premises deployments, there is no **Default** channel data group.  Create a new data group (and associate it to the channel database and distribution schedule jobs).

### Download the Commerce Scale Unit installer

1. In Headquarters, go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Commerce scheduler** &gt; **Channel database**.
2. In the list of channel databases on the left, select the channel database that you created earlier.
3. On the Action Pane, select **Download**.
4. On the drop-down menu, select **Configuration file**.

    > [!NOTE]
    > To help ensure that the Commerce Scale Unit installer correctly uses the configuration file (XML file), you must save the configuration file to the same location as the installer.
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
> If you will install and use Retail Cloud POS, you must initialize the configuration the first time that you run the installer, as described in the following procedure.

Before you run the Commerce Scale Unit installer, make sure that all [system requirements](../../fin-and-ops/get-started/system-requirements.md) are met. 

> [!IMPORTANT]
> If you are installing Commerce Scale Unit for use with an on-premises environment, you must start it from a command line using administrator privileges as follows:
> StoreSystemSetup.exe -UseAdfsAuthentication

The Commerce Scale Unit installer first extracts the associated files. It then begins the installation.

1. On the first page of the installer, select the components to install. You can install the following components:

   - Commerce channel database together with Async Client
   - Commerce Scale Unit
   - Cloud POS

     > [!NOTE]
     > - To install Cloud POS, you must also select and install Commerce Scale Unit. If you will use only Modern POS in the store, clear the **Retail Cloud POS** check box, and continue with installation process as it's described here.
     > - By default, the installer installs all components on one computer. To install the components across multiple computers, you must complete additional manual steps. For more information, see the "Multiple-computer installation" section.

     After you've selected all the components to install, select **Next** to continue.

2. The installer validates that all prerequisites are met. If a valid version of Microsoft SQL Server isn't found, the installer downloads and installs Microsoft SQL Server 2014 Express with Service Pack 2.

    > [!NOTE]
    > - To meet the prerequisites, SQL Server must have full-text search, and it must support, at a minimum, Transport Layer Security (TLS) 1.2. For Microsoft SQL Server 2014, Service Pack 2 must be installed.  For Microsoft SQL Server 2016, Service Pack 1 is the minimum required.
    > - If a system restart is required, the installer will prompt the user.  This prompt is based upon a Windows system registry key that tells all applications if a restart is required.  While it is recommended to restart prior to continuing the installation, a restart is not mandatory and the installer can continue without restarting the computer.

3. Verify the URL for Application Object Server (AOS), and then select **Next**. (The AOS URL is the URL that is used to access Headquarters.)

    > [!NOTE]
    > The Commerce Scale Unit URL is automatically entered from the configuration file.

4. Select a valid Secure Sockets Layer (SSL) certificate to use for HTTPS communication.

    The certificate must use private key storage, and server authentication must be listed in the enhanced key usage property. Additionally, the certificate must be trusted locally, and it can't be expired. It must be stored in the personal certificate store location on the local computer.

5. If a specific user is required, enter the user name and password that the application pool should run under. By default, the installer automatically generates a service account to use. This approach is more secure and is recommended.

    > [!NOTE]
    > It is important to note that service accounts, out of box, still function under the same password policy that is defined for all other accounts.  This means that the minimum password age policy still applies to the Commerce Scale Unit service account and must be updated when necessary.  By default, on Windows Server 2012 R2, this is typically 42 days.  If the password does expire on a used service account, the Commerce Scale Unit will fail to continue functioning until the issue is resolved.

6. On the next page, enter the user account and password for the Commerce Scale Unit application pool and Async Client. By default, this account is automatically generated. However, you can manually enter the user account and password.
7. Enter the HTTPS port to use, and verify that the host name of the computer is correct. Then select **Next** to continue.

    > [!NOTE]
    > - The installer automatically enters the host name. If, for any reason, the host name must be changed for the installation, change it here. The host name must be the FQDN of the system, and it must be entered in the **Host name** field for the selected Store system entry.

8. Enter the application ID (client ID) and key (secret) that are associated with this Commerce Scale Unit installation. Additionally, verify the channel database ID, which is automatically entered from the configuration file. Then select **Install**. If you will use Retail Cloud POS, make sure that the **Configure Retail Cloud POS** check box at the bottom of the page is selected. This configuration requests Azure AD sign-in and automatically generates all required information in Azure, so that Retail Cloud POS can be used on-premises. If you are installing Commerce Scale Unit for use with an on-premises environment, you must clear this option.

    For information about how to create web applications in Azure, see [Create an Azure Active Directory application](/azure/azure-resource-manager/resource-group-create-service-principal-portal#create-an-azure-active-directory-application). 
    
    > [!IMPORTANT] 
    > - When installing Commerce Scale Unit for use with an on-premises environment, Cloud POS does not require an Azure or AD FS application to be configured, so it is important to unmark **Configure Retail Cloud POS**.
    > - When installing Commerce Scale Unit for use with an on-premises environment, the Client ID (Application ID) and Secret (Key) used will be the values generated by the PowerShell script performed in the configuration steps performed in steps 6-8 in the [Installation steps for Commerce channel components in an on-premises environment](../../dev-itpro/deployment/deploy-retail-onprem.md) topic. (Step 6 creates the Client ID and step 8 resets the Secret to be copied.)

    When you create the Web App, the initial URI and URL don't have to be any specific value. Only the application ID (client ID) and key (secret) that are created are important.

9. After the application ID (client ID) and key (secret) are created for Commerce Scale Unit, the application ID (client ID) must be accepted in Commerce. Follow the next procedure to finish the configuration in Headquarters.
10. After the installation is complete, the final health page appears. This page shows whether the installation was successful. It also shows the health of each component, based on basic connection tests, and the location of this topic. If the installation wasn't successful, the page shows the location of the log files. We recommend that you keep this final health page open until you've completed the configuration of Commerce Scale Unit and all components are working correctly.

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
> If the installer doesn't show a check mark for Commerce Scale Unit, Async Client, or any other component, wait 10 minutes, so that any cached values can be updated in the cloud. Then check again. If the installer still isn't fully successful, run a full synchronization on the new channel database that this installation uses.
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

Only advanced users should install Commerce Scale Unit across multiple computers. The following set of procedures explains how to install the Commerce channel database and Async Client on one computer, and Commerce Scale Unit and Cloud POS on a second computer. The instructions assume that both systems are on the same domain, and that users for the services that will be installed have already been created on both systems. It's important that you do all configuration in Headquarters.

#### Installation on the first computer

On the first computer, run the Commerce Scale Unit self-service installer as described earlier in this topic, but make the following changes.

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

For detailed information about SQL Server and Windows Firewall, see [Configure a Windows Firewall for Database Engine Access](https://msdn.microsoft.com/library/ms175043.aspx).

#### Installation on the second computer

On the second computer, run the Commerce Scale Unit Self-service installer as described earlier in this topic, but make the following changes.

1. Select only Commerce Scale Unit and Cloud POS as the components to install. If only Commerce Scale Unit must to be installed, don't select Cloud POS. Then select **Next** to continue with the installation.
2. Enter the domain user credentials (user name and password) that have permission to access SQL Server on the first computer. Then select **Next**.

    > [!NOTE]
    > A generated service account can't be used, because Commerce Scale Unit requires access to the SQL database on the first computer. You must use a domain account.

3. Enter the same client ID and key (secret) that are used on the first computer.

    > [!IMPORTANT]
    > It's critical that you add this client ID to Commerce as described earlier.

4. Select **Configure Cloud POS**, and then enter Azure AD credentials that have the correct permissions to create Azure Web Apps. 

    For more information about Azure Web Apps, how to create them, and how to generate a new key (secret), see [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/). Note that the sign-in URL and the App ID URI are not important.

5. When setup is successful, don't exit the installer. 

    > [!NOTE]
    > At first, the health check ping won't be successful, because the database isn't yet set up correctly. After you've completed the remaining steps of this procedure, you can test the health check again.

6. Start **Microsoft Internet Information Services (IIS)**, select the **Commerce Scale Unit** website, and select the **Commerce Scale Unit** web application.
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

    1. Select the channel database that you created at the beginning of this topic.
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
- You should use only trusted certificate authorities to obtain certificates that will be used on Store system computers.

> [!IMPORTANT]
> It's critical that you review security guidelines for IIS and the Payment Card Industry (PCI) requirements.

### Troubleshoot Commerce Scale Unit

Here is a checklist of things to verify:

1. In Commerce, on the **Commerce shared parameters** page, verify that the correct client ID has been added to the **Relying parties** FastTab. Additionally, verify that the correct `https://retailstorescaleunit.retailserver.com` entry has been added to the **Server resource IDs** FastTab.
2. In Commerce, verify that every client ID that was generated for each store exists on the **Azure Active Directory applications** page.
3. In Commerce, on the **Channel profile** page, verify that the URLs are correct. (In other words, verify that the computer name in each URL is correct, the URL is correctly formatted, and so on.)
4. In Commerce, on the **Channel database** page, verify that full synchronization correctly occurred for the new channel database.
5. Verify that the store is correctly configured to use the new channel database.

If the Commerce Scale Unit stops functioning after a period of time, there are two simple things to verify:

- Verify if the password policy requires the service account that was generated to change the password (password expiration).
- Re-run the same installer over the current installation (idempotent), which will update a service account's password or allow the user to update the selected account's password.

### Uninstall Commerce Store system

Use Control Panel in Microsoft Windows to uninstall Commerce Store system.

1. Press the Windows logo key, and then enter **Control Panel** in the search box. In the search results, select **Control Panel**.
2. In Control Panel, select **Programs** &gt; **Uninstall a program**.
3. In the **Programs and Features** window, select **Microsoft Dynamics 365 Commerce Store system**, and then, above the list of programs, select **Uninstall**.
4. Wait for the uninstaller to finish removing the program.
