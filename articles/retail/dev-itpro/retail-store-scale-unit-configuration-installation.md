---
# required metadata

title: Retail Store Scale Unit configuration and installation
description: This topic explains how you can use self-service to configure Retail Store Scale Unit in Retail headquarters, download it, and install it on one or more computers in a brick-and-mortar store. 

author: jashanno
manager: AnnBe
ms.date: 08/24/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 219744
ms.assetid: 5e28948f-d40a-40e8-843b-8c2747916546
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Retail Store Scale Unit configuration and installation

[!include[banner](../includes/banner.md)]

This topic explains how you can use self-service to configure Retail Store Scale Unit in Microsoft Dynamics 365 for Retail headquarters, download it, and install it on one or more computers in a brick-and-mortar store. Retail Store Scale Unit combines the Retail channel database, Retail Async Client, Retail Server, and Retail Cloud POS components. A Microsoft Dynamics 365 for Retail environment already provides these components. However, you can now configure them so that they work locally in a store, in either a single-computer setup (the default option) or a multiple-computer setup. This topic also explains how to uninstall and troubleshoot Retail Store Scale Unit.

## Before you begin
> [!IMPORTANT]
> To help maintain a high level of security across the company, we strongly recommend that you create a new application ID (client ID) and secret for each retail store that is created. This step requires a new Web App.

1. Generate a Microsoft Azure Active Directory (Azure AD) app registration to create an application ID (client ID) and secret. For instructions, see [Create an Azure Active Directory Application](/azure/azure-resource-manager/resource-group-create-service-principal-portal#create-an-azure-active-directory-application). This article reviews Azure user permissions and requirements, and explains how to generate an app registration.
2. After an application ID (client ID) and secret are created for Retail Store Scale Unit, the client ID must be accepted in Retail. Go to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**. Enter the application ID (client ID) in the **Client ID** column, enter descriptive text in the **Name** column, and enter **RetailServiceAccount** in the **User ID** column.

## Configure a new Retail Store Scale Unit
To create a functioning Retail Store Scale Unit, complete the procedures in all sections of this topic through the "Run the Retail Store Scale Unit installer" section. To complete the configuration and installation, the user must first do the initial configuration in Retail headquarters. Next, the user must complete the installation. Finally, the user must return to Retail headquarters to finish the configuration, so that the Retail Store Scale Unit works correctly.

1. Use your Azure AD credentials to sign in to the Retail headquarters or Retail trial.
2. On the **Welcome** page, use the menu in the upper left to go to **Retail** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Channel database**.
3. On the **Channel database** page, on the Action Pane, select **New**.
4. In the **Channel database ID** field, enter a unique value.
5. In the **Channel data group** field, select the **Default** option.

     You can select any other option that you've already created.

6. In the **Type** field, leave the default value (**Channel database**) selected.
7. You can leave the **Data sync interval** field blank. Alternatively, you can select a value in this field. For example, in the demo data, the value **D60-U15** specifies a 15-minute synchronization interval.
8. On the **Retail channel** FastTab, select **Add**, and then, in the **Channel** field, select the appropriate Retail store channel. Repeat this step to add all the channels that use this database.

     You can also add channels that don't use this database. In this way, you keep the data for those channels in the Retail Store Scale Unit channel database. The Retail store channels that actively use this database can then access that data locally.

9. On the **Store Scale Unit package** FastTab, in the **Name** field, select the appropriate Retail Store Scale Unit package.

     Each environment generates a base Retail Store Scale Unit package. Therefore, this field always contains at least one option.

10. On the Action Pane, select **Save**.
11. Go to **Retail** &gt; **Channel setup** &gt; **Channel profiles**.
12. On the Action Pane, select **New**.
13. In the **Name** field, enter a unique name for the channel profile.
14. On the Action Pane, select **Save**.
15. On the **Profile properties** FastTab for the new channel profile, select **Add**.
16. In the **Property key** field, select **Retail server URL**.
17. In the **Property value** field, enter the URL of the Retail Server that will be installed for Retail Store Scale Unit.

     The standard format for the URL of an on-premises store installation of Retail Store Scale Unit is **https://&lt;Computer Name&gt;:&lt;Port&gt;/RetailServer/Commerce**. In this format, **&lt;Computer Name&gt;** is either the fully qualified domain name (FQDN) of the computer where Retail Store Scale Unit is installed or, for systems that aren't joined to a domain, the full computer name. **&lt;Port&gt;** is the port number that will be used in the installation. The port number must be a value between 1 and 65535. If you're using the default HTTPS port (443), you don't have to specify the port number.

18. On the **Profile properties** FastTab for the new channel profile, select **Add**.
19. In the **Property key** field, select **Cloud POS URL**.
20. In the **Property value** field, enter the URL of the Retail Server that will be installed for Retail Store Scale Unit.

     The standard format for the URL of an on-premises store installation of Retail Store Scale Unit is **https://&lt;Computer Name&gt;:&lt;Port&gt;/POS**. In this format, **&lt;Computer Name&gt;** is either the FQDN of the computer where Retail Store Scale Unit is installed or, for systems that aren't joined to a domain, the full computer name. **&lt;Port&gt;** is the port number that will be used in the installation. The port number must be a value between 1 and 65535. If you're using the default HTTPS port (443), you don't have to specify the port number.

21. On the Action Pane, select **Save**.
22. Go to **Retail** &gt; **Channels** &gt; **Retail stores** &gt; **All retail stores**.
23. Select the Retail channel ID for the retail store that will use the new channel database.
24. On the details page for the selected store, on the Action Pane, select **Edit**.
25. On the **General** FastTab for the store, in the **Live channel database** field, select the channel database that you created in step 3.
26. On the Action Pane, select **Save**.
27. On the **General** FastTab for the store, in the **Channel profile** field, select the channel profile that you created in step 12.
28. Go to **Retail** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Channel data group**.
29. Select the **Default** data group, and then, on the Action Pane, select **Full data sync**. In the **Select a distribution schedule** field, select job **9999**, and then select **OK**. In the dialog box that appears, select **OK** to confirm the full synchronization. All the data in the channel database is prepared for download.

### Download the Retail Store Scale Unit installer

1. Use your Azure AD credentials to sign in to the Retail headquarters or Retail trial.
2. On the **Welcome** page, use the menu in the upper left to go to **Retail** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Channel database**.
3. In the list of channel databases on the left, select the channel database that you created earlier.
4. On the Action Pane, select **Download**.
5. On the drop-down menu, select **Configuration file**.

    > [!NOTE]
    > To help guarantee that the Retail Store Scale Unit installer correctly uses the configuration file (XML file), you must save the configuration file to the same location as the installer.

6. On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.)

     Browsers might block the download pop-up that is generated. Select either **Allow once** or **Options for this site** &gt; **Always allow**. Then select **Download** again.

7. On the Action Pane, select **Download**.
8. On the drop-down menu, select **Retail Store Scale Unit package**.
9. On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.)

     The correct installation package is automatically selected for download, based on the Retail Store Scale Unit package on the selected channel database.

10. After the setup installer has been saved, on the Notification bar, select **Run**. (This step might differ, depending on the type of browser.)

### Run the Retail Store Scale Unit installer

> [!NOTE]
> If you will install and use Retail Cloud POS, you must initialize the configuration the first time that you run the installer, as described in the following procedure. 

Before you run the Retail Store Scale Unit installer, make sure that the following requirements are met:

- The installer requires that the Microsoft .NET Framework version 4.5.1 be installed on the system.
- The installer installs the Retail Store Scale Unit components only on the following operating systems. (Before you install any component, you must update the operating system with all service packs and updates that are available for it.)

    - Windows 7 Professional, Enterprise, or Ultimate edition (both x86 and x64 architectures). Home edition and Embedded edition aren't supported.
    - Windows 8.1 Update 1 Pro or Enterprise edition (both x86 and x64 architectures). Standard edition isn't supported.
    - Windows 10 Pro or Enterprise edition (both x86 and x64 architectures). Home edition isn't supported.
    - Microsoft Windows Server 2012 or Microsoft Windows Server 2012 R2.

The Retail Store Scale Unit installer first extracts the associated files. It then begins the installation.

1. On the first page of the installer, select the components to install. You can install the following components:

    - Retail channel database with Async Client
    - Retail Server
    - Retail Cloud POS 

    > [!NOTE]
    > - To install Retail Cloud POS, you must also select and install Retail Server. If you will use only Retail Modern POS in the store, clear the **Retail Cloud POS** check box, and continue with installation process as it's described here.
    > - By default, the installer installs all components on one computer. To install the components across multiple computers, you must complete additional manual steps. For more information, see the "Multiple-computer installation" section.

    After you've selected all the components to install, select **Next** to continue.

2. The installer validates that all prerequisites are met. If a valid version of Microsoft SQL Server isn't found, the installer downloads and installs Microsoft SQL Server 2014 Express with Service Pack 2. 

    > [!NOTE]
    > - To meet the prerequisites, SQL Server must have full-text search, and it must support, at a minimum, Transport Layer Security (TLS) 1.2. For Microsoft SQL Server 2012, Service Pack 3 must be installed, at a minimum. For Microsoft SQL Server 2014, Service Pack 2 must be installed. 
    > - If a system restart is required, the installer shows this requirement. Although the restart is recommended, the installer can continue without it.

3. Verify the URL for Application Object Server (AOS), and then select **Next**. (The AOS URL is the URL that is used to access Retail headquarters.) 

    > [!NOTE]
    > The Retail Server URL is automatically entered from the configuration file.

4. Select a valid Secure Sockets Layer (SSL) certificate to use for HTTPS communication. 

     The certificate must use private key storage, and server authentication must be listed in the enhanced key usage property. Additionally, the certificate must be trusted locally, and it can't be expired. It must be stored in the personal certificate store location on the local computer.

5. If a specific user is required, enter the user name and password that the application pool will run under. By default, the installer automatically generates a service account to use. This approach is more secure and is recommended.
6. On the next page, enter the user account and password for the Retail Server application pool and Async Client. By default, this account is automatically generated. However, you can manually enter the user account and password.
7. Enter the HTTPS port to use, and verify that the host name of the computer is correct. Select **Next** to continue. 

    > [!NOTE]
    > - The HTTPS port is listed in the Store system profile. To access the Store system profile, on the **Retail store details** page, on the **Store systems** FastTab, select the profile ID of the selected Store system. 
    > - The installer automatically enters the host name. If, for any reason, the host name must be changed for the installation, change it here. The host name must be the FQDN of the system, and it must be entered in the **Host name** field for the selected Store system entry.

8. Enter the application ID (client ID) and secret that are associated with this Retail Store Scale Unit installation. Additionally, verify the channel database ID, which is automatically entered from the configuration file. Then select **Install**. If you will use Retail Cloud POS, make sure that the **Configure Retail Cloud POS** check box at the bottom of this page is selected. This configuration requests Azure AD sign-in and automatically generates all required information in Azure, so that Retail Cloud POS can be used on-premises. 

     For information about how to create web applications in Azure, see [Create an Azure Active Directory Application](/azure/azure-resource-manager/resource-group-create-service-principal-portal#create-an-azure-active-directory-application). 
    
     When you create the Web App, the initial URI and URL don't have to be any specific value. Only the application ID (client ID) and key (secret) that are created are important.

9. After the application ID (client ID) and secret are created for Retail Store Scale Unit, the application ID (client ID) must be accepted in Retail. Follow the next procedure to finish the configuration in Retail headquarters.
10. After the installation is completed, the final health page appears. This page shows whether the installation was successful. It also shows the health of each component, based on basic connection tests, and the location of this topic. If the installation wasn't successful, the page shows the location of the log files. We recommend that you keep this final health page open until you've completed the Retail Store Scale Unit configuration and all components are working correctly.

### Finish the Retail Store Scale Unit configuration in headquarters
The last steps require validation and verification that the Azure application ID (client ID) and key (secret) are correctly accepted in Retail headquarters, so that connections can be made between the environment and the new Retail Store Scale Unit.

1. After the application ID (client ID) and key (secret) are created for Retail Store Scale Unit and entered in the installer, the application ID (client ID) must be accepted in Retail headquarters. In Retail headquarters, go to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**. Enter the application ID (client ID) in the **Client ID** column, enter descriptive text in the **Name** column, and enter **RetailServiceAccount** in the **User ID** column.
2. If Retail Cloud POS is configured for use, a client ID is shown at the end of the installation. You must add this client ID to the **Retail shared parameters** page in Retail.

    1. In Retail, go to **Retail** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Retail shared parameters**.
    2. Select **Identity providers**.
    3. On the **Identity providers** FastTab, select the provider that begins with `HTTPS://sts.windows.net/`. The values on the **Relying parties** FastTab are set, based on your selection.
    4. On the **Relying parties** FastTab, select **+Add**. Enter the client ID that is listed in the final health screen of the Retail Store Scale Unit installer. Set the **Type** field to **Public** and the **UserType** field to **Worker**. Then, on the Action Pane, select **Save**.
    5. Select the new relying party, and then, on the **Server resource IDs** FastTab, select **+Add**. In the **Server Resource ID** column, enter `https://retailstorescaleunit.retailserver.com`.
    6. On the Action Pane, select **Save**.

3. In Retail, go to **Retail** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Retail shared parameters**.
4. Select **Identity providers**.
5. On the **Identity providers** FastTab, select **+Add**.
6. In the new **Issuer** row, enter the Retail Server URL of the newly installed Retail Store Scale Unit. At the end of the URL, add **/auth**.  The URL will resemble `https://MyComputerName/RetailServer/auth`.

    > [!NOTE]
    > There will be a new identity provider line for each Retail Store Scale Unit that is installed. Each Retail Store Scale Unit will have a URL that resembles this URL.

7. In the **Name** column, enter a description for the store that the URL belongs to.
8. In the **Type** column, select **Open ID Connect**.

    > [!NOTE]
    > This new row must be duplicated for every Retail Store Scale Unit installation (that is, for every unique URL).

9. On the Action Pane, select **Save**.
10. On the **Identity providers** FastTab, select the newly created line. The values on the **Relying parties** FastTab are set, based on your selection.
11. On the **Relying parties** FastTab, select **+Add**, and add the following two entries:

    - In the **ClientId** column, enter **Cloud POS**. Set the **Type** field to **Public** and the **UserType** field to **Worker**. 
    - In the **ClientId** column, enter **Modern POS**. Set the **Type** field to **Public** and the **UserType** field to **Worker**.

12. On the Action Pane, select **Save**.
13. When you've finished, return to the installer, and select **Finish**.

     The final page of the installer includes valuable information that you can use to test and validate that all components work correctly. Keep this page open until you've completed the validation.

> [!NOTE]
> - If the installer doesn't show a check mark for Retail Server, Async Client, or any other component, wait 10 minutes, so that any cached values can be updated in the cloud. Then check again. If the installer still isn't fully successful, run a full synchronization on the new channel database that this installation uses.
> - If you followed all the steps correctly, your configuration should have these characteristics:
>     - In Azure, two web applications have been automatically generated through the installer:
>         - Retail Store Scale Unit Cloud POS
>         - Retail Store Scale Unit Retail Server for Cloud POS
>     - In Azure, a web application (that is, an App registration in the new Azure portal) has been manually created for each Retail Store Scale Unit installation (for example, RetailStoreScaleUnitHouston). A key (secret) has been created that can be used in the installer, as described earlier.
>     - The application ID (client ID) of the manually created web application has been added to the **Azure Active Directory applications** page in Retail, as explained in step 1 of the preceding procedure.
>     - The Retail Cloud POS application ID (client ID) that was shown at the end of the Retail Store Scale Unit installer has been added on the **Identity providers** FastTab, as explained in steps 3 and 4 of the preceding procedure.

### Multiple-computer installation

Only advanced users should install Retail Store Scale Unit across multiple computers. The following set of procedures explains how to install the Retail channel database and Async Client on one computer, and Retail Server and Retail Cloud POS on a second computer. The instructions assume that both systems are on the same domain, and that users for the services that will be installed have already been created on both systems. It's important that you do all configuration in Retail headquarters.

#### Installation on the first computer

On the first computer, run the Retail Store Scale Unit self-service installer as described earlier in this topic, but make the following changes.

1. Select only Retail Channel Database and Async Client as the components to install. Then select **Next** to continue with the installation. 

    > [!NOTE]
    > You can use a generated service account for Async Client, because Async Client won't be accessed outside the computer that it's installed on.

2. Enter the client ID and secret. Keep these details available, so that you can use them again on the second computer.
3. After a client ID and secret are created for Retail Store Scale Unit, the client ID must be accepted in Retail. Go to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**. Enter the client ID in the **Client ID** column, enter descriptive text in the **Name** column, and enter **RetailServiceAccount** in the **User ID** column.
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

For detailed information about SQL Server and Windows Firewall, see [Configure a Windows Firewall for Database Engine Access](https://msdn.microsoft.com/en-us/library/ms175043.aspx).

#### Installation on the second computer

On the second computer, run the Retail Store Scale Unit Self-service installer as described earlier in this topic, but make the following changes.

1. Select only Retail Server and Retail Cloud POS as the components to install. If only Retail Server must to be installed, don't select Retail Cloud POS. Then select **Next** to continue with the installation.
2. Enter the domain user credentials (user name and password) that have permission to access SQL Server on the first computer. Then select **Next**.

    > [!NOTE]
    > A generated service account can't be used, because Retail Server requires access to the SQL database on the first computer. You must use a domain account.

3. Enter the same client ID and secret that are used on the first computer.

    > [!IMPORTANT]
    > It's critical that you add this client ID to Retail as described earlier.

4. Select **Configure Cloud POS**, and then enter Azure AD credentials that have the correct permissions to create Azure Web Apps. 

     For more information about Azure Web Apps, how to create them, and how to generate new secrets, see [Use portal to create Active Directory application and service principal that can access resources](https://azure.microsoft.com/en-us/documentation/articles/resource-group-create-service-principal-portal/). Note that the sign-in URL and the App ID URI aren't important.

5. When setup is successful, don't exit the installer. 

    > [!NOTE]
    > At first, the healthcheck ping won't be successful, because the database isn't yet set up correctly. After you've completed the remaining steps of this procedure, you can test the healthcheck again.

6. Go to **IIS**, select the **Retail Store Scale Unit** website, and select the **Retail Server** web application.
7. Explore the working directory.
8. Open the Web.config file, and then, in the **connectionStrings** section, add **Server name**. **Server name** is the name of the first computer where you installed components. Save the file.
9. If the certificate that is used isn't a valid, trusted certificate from a trusted authority, open CERTMGR.MSC, and follow these steps:

    1. Import the SQL Server SSL certificate that you created earlier, and add it to Trusted Root.
    2. Open a **Command Prompt** window as an administrator, type **IISRESET**, and then press **Enter**.

10. If Retail Cloud POS is configured for use, a client ID is shown. You must add this client ID to the **Retail shared parameters** page in Retail.

    1. In Retail, go to **Retail** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Retail shared parameters**.
    2. Select **Identity providers**.
    3. On the **Identity providers** FastTab, select the provider that begins with `HTTPS://sts.windows.net/`. The values on the **Relying parties** FastTab are set, based on your selection.
    4. On the **Relying parties** FastTab, select **+Add**. Enter the client ID that is listed in the Retail Store Scale Unit installer. Set the **Type** field to **Public** and the **UserType** field to **Worker**. Then, on the Action Pane, select **Save**.
    5. Select the new relying party, and then, on the **Server resource IDs** FastTab, select **+Add**. In the **Server Resource ID** column, enter `https://retailstorescaleunit.retailserver.com`.
    6. On the Action Pane, select **Save**.

11. In Retail, go to **Retail** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Channel database**, and follow these steps:

    1. Select the channel database that you created at the beginning of this topic.
    2. On the Action Pane, select **Full Sync** &gt; **Job 9999**. Full synchronization might require several minutes.
    3. In the Retail Store Scale Unit installer, retest to verify that all functionality is working correctly.

12. Start Retail Cloud POS from the computer that you're using for point of sale (POS) operations. (This computer is a third computer that is separate from the Retail Store Scale Unit systems.)
13. Activate the Retail Cloud POS device that you're using for this computer.
14. Do a simple sale to verify full end-to-end functionality.

### Help secure Retail Store Scale Unit

According to current security standards, the following options should be set in a production environment:

- You should completely disable SSL (v2 and v3) on the computer.
- You should enable and use only TLS version 1.2 (or the current highest version).

    > [!NOTE]
    > By default, SSL and all versions of TLS except TLS 1.2 are disabled. To edit or enable these settings, follow these steps:
    > 1. Press the Windows logo key+R to open a **Run** window.
    > 2. In the **Open** field, enter **Regedit**, and then select **OK**.
    > 3. In the **User Account Control** window, select **Yes** (if this step is required), and then, in the new **Registry Editor** window, go to **HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\SecurityProviders\\SCHANNEL\\Protocols**.
    > 4. The following keys have been automatically entered to enable only TLS 1.2:
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
> It's critical that you review security guidelines for Internet Information Services (IIS) and Payment Card Industry (PCI) requirements.

### Troubleshoot Retail Store Scale Unit

Here is a checklist of things to verify:

1. In Retail, on the **Retail shared parameters** page, verify that the correct client ID has been added to the **Relying parties** FastTab. Additionally, verify that the correct `https://retailstorescaleunit.retailserver.com` entry has been added to the **Server resource IDs** FastTab.
2. In Retail, verify that every client ID that was generated for each retail store exists on the **Azure Active Directory applications** page.
3. In Retail, on the **Channel profile** page, verify that the URLs are correct. (In other words, verify that the computer name in each URL is correct, the URL is correctly formatted, and so on.)
4. In Retail, on the **Channel database** page, verify that full synchronization correctly occurred for the new channel database.
5. Verify that the retail store is correctly configured to use the new channel database.

### Uninstall Retail Store system

Use Control Panel in Microsoft Windows to uninstall Retail Store system.

1. Press the Windows logo key, and then enter **Control Panel** in the search box. In the search results, select **Control Panel**.
2. In Control Panel, select **Programs** &gt; **Uninstall a program**.
3. In the **Programs and Features** window, select **Microsoft Dynamics 365 for Retail Store system**, and then, above the list of programs, select **Uninstall**.
4. Wait for the uninstaller to finish removing the program.
