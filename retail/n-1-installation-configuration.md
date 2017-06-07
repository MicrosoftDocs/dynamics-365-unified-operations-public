---
# required metadata

title: Installing N-1 components for use with Microsoft Dynamics 365 for Operations - Retail 
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: jashanno
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: margoc
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 44351
ms.search.region: Global
# ms.search.industry: 
ms.author: jashanno
ms.search.validFrom: 2017-07-31
ms.dyn365.ops.version: Retail July 2017 update

---

# Installing N-1 components for use with Microsoft Dynamics 365 for Retail

This topic explains how you can use self-service to configure Connector for Microsoft Dynamics AX (Previously **N-1**) in the Microsoft Dynamics 365 for Retail headquarters, download it, and install it on the domain computers of a Microsoft Dynamics AX 2012 R3 environment to be utilized by previously deployed and running stores. The Connector for Microsoft Dynamics AX consists of two separate installers for the Retail Async Server Connector service and the Real-time service for Dynamics AX 2012 R3. When completed, a Dynamics 365 for Retail environment will be used as the backend infrastructure for currently installed and functioning stores containing Enterprise POS and Modern POS from a Microsoft Dynamics AX 2012 R3. This topic also explains how to uninstall and troubleshoot these installations.

## Before you begin

> [!IMPORTANT]
> To help maintain a high level of security across the company, we strongly recommend that you create a new client ID and secret for this installation. This step requires a new Web App.

1.  Generate a Microsoft Azure Web App to create a client ID and secret. For instructions, see the "Basics of Registering an Application in Azure AD" section in [Create an Azure Active Directory Application](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal#create-an-azure-active-directory-application).
2.  After a client ID and secret are created for the Connector for Microsoft Dynamics AX, the client ID must be accepted in Microsoft Dynamics 365 for Operations. Go to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**. Enter the client ID in the **Client ID** column, enter descriptive text in the **Name** column, and enter **RetailServiceAccount** in the **User ID** column.

## Configure the Connector for Microsoft Dynamics AX
To configure the Connector for Microsoft Dynamics AX (Previously **N-1**), complete the procedures in all sections of this topic through the "Running the Connector for Microsoft Dynamics AX installers" section.

1.  Use Azure Active Directory (Azure AD) credentials to sign in to the Microsoft Dynamics 365 for Retail headquarters or Dynamics 365 for Retail trial.
2.  On the **Welcome** page, use the menu in the upper left to go to **Retail and commerce** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Connector for Microsoft Dynamics AX**.
3.  On this page, on the Action Pane, select **New**.
4.  In the **Profile** field, enter a unique value.
5.  Under the **Real-Time Service location** sub-heading, in the **Server** field, enter the server URL where the Real-Time service for Dynamics AX 2012 R3 will be installed.  

> [!NOTE]
> This can be the same location as the current Real-Time Service that was installed originally or a new installation.

6.  In the **Port** field, enter the port to be used by the new Real-Time Service for Dynamics AX 2012 R3.
7.  In the **Web application name** field, enter the web application name to be used in IIS.  By default, this is pre-selected to be **RetailCDXRealTimeService**.
8.  In the **Protocol** field, select the protocol currently used by the original Real-Time service.  **Note:** It is recommended to use HTTPS, however, net.tcp is listed for better support of previous installation scenarios. 
9.  Under the **Connection information** sub-heading, in the **Common name** field, enter the friendly name of the certificate that will be used by the Real-time Service for Dynamics AX 2012 R3.  This value is used in conjunction with the value that is entered in the **Passphrase** field to allow for connections to the original (and now the new) Real-Time service for Dynamics AX 2012 R3.
10.  On the **Language** field, select the language to be used by the associated stores.
11.  On the Action Pane, select **Save**.
12.  On the Action Pane, select **Retail scheduler parameters**.  This will navigate you to this page to enter the details for the Async Server Connector service.
13.  Under the **HQ Message Database** sub-heading, in the **SQL Server instance name** field, enter the instance name of the SQL Server to be used.
14.  On the **Server name** field, enter the fully qualified domain name of the computer where SQL is being used.  **Note:** If the database will be located on the same computer as the Async Server connector service, enter **localhost** as the value.
15.  On the **Database name** field, enter the name of the HQ Message Database.  **Note:** In Microsoft Dynamics AX 2012 R3, the default value for this field was **HQMessageDB**.
16. On the Action Pane, select **Save**.
17. Go to **Retail and commerce** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Channel data group**.
18. Select the **Default** data group or the data group associated to the channels in your previous installation set (N-1 channels utilizing Enterprise POS and Modern POS from Dynamics AX 2012 R3), and then, on the Action Pane, select **Full data sync**. In the **Select a distribution schedule** field, select job **9999**, and then select **OK**. In the dialog box that appears, select **OK** to confirm the full synchronization. All the data in the channel database is prepared for download.

### Download the Connector for Microsoft Dynamics AX installers

1.  Use Azure AD credentials to sign in to the Microsoft Dynamics Commerce or Dynamics 365 for Retail trial.
2.  On the **Welcome** page, use the menu in the upper left to go to **Retail and commerce** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Connector for Microsoft Dynamics AX**.
3.  In the list of created connectors on the left, select the entry that you created earlier for this installation.
4.  On the Action Pane, select **Download**.
5.  On the drop-down menu, select **Configuration file** below the **Async Server onnector service**. **Note:** To help guarantee that the Connector for Microsoft Dynamics AX installers correctly uses the configuration file (XML file), you must save the configuration file to the same location as the installer.
6.  On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.) **Note:** Browsers might block the download pop-up that is generated. Select either **Allow once** or **Options for this site** &gt; **Always allow**. Then select **Download** again.
7.  On the Action Pane, select **Download**.
8.  On the drop-down menu, select **Async Server Connector service**.
9.  On the Notification bar that appears at the bottom of the Internet Explorer window, select **Save**. (The Notification bar might appear in a different place in other browsers.) **Note:** The correct installation package is automatically selected for download, based on the Connector for Microsoft Dynamics AX package on the selected channel database.
10. After the setup installer has been saved, on the Notification bar, select **Run**. (This step might differ, depending on the type of browser.)
11. Repeat steps 4 - 10 for the **Real-time service for Dynamics AX 2012 R3**.

### Running the Connector for Microsoft Dynamics AX installers

> [!NOTE]
> Before you run the Connector for Microsoft Dynamics AX installers, make sure that the following requirements are met:

-   The installer requires that the Microsoft .NET Framework version 4.5.1 be installed on the system.
-   The installers install the Connector for Microsoft Dynamics AX applications only on the following operating systems. Before you install any component, you must update the operating system with all service packs and updates that are available for it.
    -   Windows 7 Professional, Enterprise, or Ultimate edition (both x86 and x64 architectures). Home edition and Embedded edition aren’t supported.
    -   Windows 8.1 Update 1 Pro or Enterprise edition (both x86 and x64 architectures). Standard edition isn’t supported.
    -   Windows 10 Pro or Enterprise edition (both x86 and x64 architectures). Home edition isn’t supported.
    -   Windows Server 2012 R2 or Windows Server 2016.

The Connector for Microsoft Dynamics AX installers first extract the associated files and then begins the installation.

#### Async Server Connector service

1.  The installer validates that all prerequisites are met. This includes SQL prerequisites such as a local installation of SQL Server or the alternative prerequisites such as SQL Command Line Utilities and other necessary SQL connectivity installations. **Note:** To meet prerequisites, the SQL Server that is connected to must have Full-text search and, at a minimum, support for Transport Layer Security (TLS) 1.2. For Microsoft SQL Server 2012, Service Pack 3 must be installed, at a minimum. For Microsoft SQL Server 2014, Service Pack 2 must be installed. **Note:** If a system restart is required, the installer shows this requirement. Although the restart is recommended, the installer can continue without it.
2.  Verify the Application Object Server (AOS) URL (the URL that is used to access Dynamics 365 for Retail headquarters), and then select **Next**. **Note:** This URL is automatically entered from the configuration file.
3.  Select a valid Secure Sockets Layer (SSL) certificate to use for HTTPS communication. Select **Next** to continue.  **Note:** The certificate must use private key storage, and server authentication must be listed in the enhanced key usage property. Additionally, the certificate must be trusted locally, and it can’t be expired. It must be stored in the personal certificate store location on the local computer.  
4.  If a specific user is required, enter the user name and password that the service will run as. By default, the installer automatically generates a service account to use. This approach is more secure and is recommended, but is not able to be used when the database is located on a separate computer.  Select **Next** to continue.
5.  Verify the HTTPS port to use, and verify that the host name of the computer is correct. Select **Next** to continue. **Note:** The HTTPS port is listed in the Store system profile. To access the Store system profile, on the **Retail store details** page, on the **Store systems** FastTab, select the profile ID of the selected Store system. **Note:** The installer automatically enters the host name. If, for any reason, the host name must be changed for the installation, change it here. The host name must be the FQDN of the system, and it must be the same as the value in the **Connector for Microsoft Dynamics AX** page in the previous section of this article.
6.  Enter the Application ID (Client ID) and secret that are associated with this Connector for Microsoft Dynamics AX installation. Additionally, verify the channel database ID, which is automatically entered from the configuration file. Then select **Install**. > 
[!NOTE]
> For information about how to correctly generate an Azure Web App to create a client ID and secret, see the "Basics of Registering an Application in Azure AD" section in [Create an Azure Active Directory Application](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal#create-an-azure-active-directory-application). **Note:** When you create the Web App, the initial URI and URL don't have to be any specific value. Only the Application ID (Client ID) and secret that are created are important.
7. After the installation is completed, the final health page appears. This page shows whether the installation was successful. It also shows the health of each component, based on basic connection tests, and the location of this topic. If the installation wasn't successful, the page shows the location of the log files.
8.  After an Application ID (Client ID) and secret are created, the Application ID must be accepted in Dynamics 365 for Retail. Navigate to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**. Enter the client ID in the **Client ID** column, enter descriptive text in the **Name** column, and enter **RetailServiceAccount** in the **User ID** column.
9. You must add the client ID generated and used to the **Retail shared parameters** page in Dynamics 365 for Retail.
    1.  In Dynamics 365 for Operations, go to **Retail and commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Retail shared parameters**.
    2.  Select **Identity providers**.
    3.  On the **Identity providers** FastTab, select the provider that begins with **HTTPS://sts.windows.net/**. The values on the **Relying parties** FastTab are set, based on your selection.
    4.  On the **Relying parties** FastTab, select **+Add**. Enter the client ID that was created for this installation. Set the **Type** field to **Public** and the **UserType** field to **Worker**. Then, on the Action Pane, select **Save**.
    5.  On the Action Pane, select **Save**.

12. Back on the application installation, when finished, select **Finish**. **Note:** If the installer doesn't show a check mark for the component, wait 10 minutes so that any cached values can be updated in the cloud. Check again afterwards. If the installer still isn't fully successful, run a full synchronization on the distribution schedule that this installation uses.

#### Real-time service for Dynamics AX 2012 R3

1.  The installer validates that all prerequisites are met. **Note:** If a system restart is required, the installer shows this requirement. Although the restart is recommended, the installer can continue without it.
2.  Verify the Application Object Server (AOS) URL (the URL that is used to access Dynamics 365 for Retail headquarters), and then select **Next**. **Note:** This URL is automatically entered from the configuration file.
3.  Select a valid Secure Sockets Layer (SSL) certificate to use for HTTPS communication. Select **Next** to continue.  **Note:** The certificate must use private key storage, and server authentication must be listed in the enhanced key usage property. Additionally, the certificate must be trusted locally, and it can’t be expired. It must be stored in the personal certificate store location on the local computer.  
4.  If a specific user is required, enter the user name and password that the application pool will run as. By default, the installer automatically generates a service account to use. This approach is more secure and is recommended, but is not able to be used when the database is located on a separate computer.  Select **Next** to continue.
5.  Verify the HTTPS port to use, and verify that the host name of the computer is correct. Select **Next** to continue. **Note:** The HTTPS port is listed in the Store system profile. To access the Store system profile, on the **Retail store details** page, on the **Store systems** FastTab, select the profile ID of the selected Store system. **Note:** The installer automatically enters the host name. If, for any reason, the host name must be changed for the installation, change it here. The host name must be the FQDN of the system, and it must be the same as the value in the **Connector for Microsoft Dynamics AX** page in the previous section of this article.
6.  Enter the Application ID (Client ID) and secret that are associated with this Connector for Microsoft Dynamics AX installation. Then select **Install**. **Note:** This can be the same Application ID and secret used in the Async Server Connector service installation.  For information about how to correctly generate an Azure Web App to create a client ID and secret, see the "Basics of Registering an Application in Azure AD" section in [Create an Azure Active Directory Application](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal#create-an-azure-active-directory-application). **Note:** When you create the Web App, the initial URI and URL don't have to be any specific value. Only the Application ID (Client ID) and secret that are created are important.
7. After the installation is completed, the final health page appears. This page shows whether the installation was successful. It also shows the health of the component, based on basic connection tests, and the location of this article. If the installation wasn't successful, the page shows the location of the log files.
8.  If the Application ID and secret are not the same as used for the Async Server Connector service, the Application ID must be accepted in Dynamics 365 for Retail. Navigate to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**. Enter the client ID in the **Client ID** column, enter descriptive text in the **Name** column, and enter **RetailServiceAccount** in the **User ID** column.
9. If the Application ID and secret are not the same as used for the Async Server Connector service, you must add the Application ID (Client ID) generated and used to the **Retail shared parameters** page in Dynamics 365 for Retail.
    1.  In Dynamics 365 for Operations, go to **Retail and commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Retail shared parameters**.
    2.  Select **Identity providers**.
    3.  On the **Identity providers** FastTab, select the provider that begins with **HTTPS://sts.windows.net/**. The values on the **Relying parties** FastTab are set, based on your selection.
    4.  On the **Relying parties** FastTab, select **+Add**. Enter the client ID that was created for this installation. Set the **Type** field to **Public** and the **UserType** field to **Worker**. Then, on the Action Pane, select **Save**.
    5.  On the Action Pane, select **Save**.
10. Back on the application installation, when finished, select **Finish**. **Note:** If the installer doesn't show a check mark for the component, wait 10 minutes so that any cached values can be updated in the cloud. Check again afterwards. If the installer still isn't fully successful, run a full synchronization on the distribution schedule that this installation uses.

### Help secure the Connector for Dynamics AX applications

According to current security standards (PCI), the following options should be set in a production environment:

-   You should completely disable SSL (v2 and v3) on the computer.
-   You should enable and use only TLS version 1.2 (or the current highest version). **Note:** By default, these settings are not changed by the installers (This is different from other Self-service installers). To edit or enable these settings, follow these steps:
    1.  Press the Windows logo key+R to open a **Run** window.
    2.  In the **Open** field, enter **Regedit**, and then select **OK**.
    3.  In the **User Account Control** window, select **Yes** (if this step is required), and then, in the new **Registry Editor** window, go to **HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\SecurityProviders\\SCHANNEL\\Protocols**.
    4.  The following keys have been automatically entered to enabled only TLS 1.2:
        -   TLS 1.2\\Server:Enabled=1
        -   TLS 1.2\\Server:DisabledByDefault=0
        -   TLS 1.2\\Client:Enabled=1
        -   TLS 1.2\\Client:DisabledByDefault=0
        -   TLS 1.1\\Server:Enabled=0
        -   TLS 1.1\\Client:Enabled=0
        -   TLS 1.0\\Server:Enabled=0
        -   TLS 1.0\\Client:Enabled=0
        -   SSL 3.0\\Server:Enabled=0
        -   SSL 3.0\\Client:Enabled=0
        -   SSL 2.0\\Server:Enabled=0
        -   SSL 2.0\\Client:Enabled=0
> [!NOTE]
> This will have major impact upon communication between Dynamics AX 2012 R3 stores (Enterprise POS and Modern POS) and the headquarters components that are installed as part of this article.  Take great care to review how communication functions currently.
<!-- -->

-   No additional network ports should be open, unless they are required for known, specified reasons.
-   You must disable cross-origin resource sharing, and you must specify the allowed origins that are accepted.
-   You should use only trusted certificate authorities to obtain certificates that will be used on computers where the applications are installed.

> [!IMPORTANT]
> It's critical that you review security guidelines for Internet Information Services (IIS) and Payment Card Industry (PCI) requirements.

### Troubleshoot the Microsoft Connector for Dynamics AX applications

This section will be more thorough in the future. For now, here is a checklist of things to verify:

1.  In Dynamics 365 for Retail, on the **Retail shared parameters** page, verify that the correct client ID has been added to the **Relying Parties** FastTab. 
2.  In Dynamics 365 for Retail, verify that every client ID that was generated exists on the **Azure Active Directory applications** page.

### Uninstall the Microsoft Connector for Dynamics AX applications

Use Control Panel in Microsoft Windows to uninstall Retail Store system.

1.  Press the Windows logo key, and then enter **Control Panel** in the search box. In the search results, select **Control Panel**.
2.  In Control Panel, select **Programs** &gt; **Uninstall a program**.
3.  In the **Programs and Features** window, select **Microsoft Dynamics 365 for Operations for Retail Store system**, and then, above the list of programs, select **Uninstall**.
4.  Wait for the uninstaller to finish removing the program.
