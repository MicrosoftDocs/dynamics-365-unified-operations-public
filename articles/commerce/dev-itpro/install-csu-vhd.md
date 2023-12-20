---
title: Install Commerce Scale Unit on a virtual hard disk
description: This article explains how to install Commerce Scale Unit on a virtual hard disk for Microsoft Dynamics 365 Commerce development.
author: bstorie
ms.date: 12/20/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: brstor
ms.search.validFrom: 2022-03-01
---

# Install Commerce Scale Unit on a virtual hard disk

[!include [banner](../includes/banner.md)]

This article explains how to install Commerce Scale Unit (CSU) on a virtual hard disk (VHD) for Microsoft Dynamics 365 Commerce development.

## Create Azure Active Directory apps

First, you must create two Azure Active Directory (Azure AD) apps, one for CSU and one for the Store Commerce for Web app (formerly CPOS). The Secure Sockets Layer (SSL) certificate will be added to this app. For more information, see [Configure Store Commerce for web to use a custom Azure AD app](cpos-custom-aad.md).

## Create an SSL certificate for a website based on the host name

To create an SSL certificate for a website based on the host name, follow these steps.

1. Remote Desktop Protocol (RDP) into box.
1. Open Internet Information Services (IIS) Manager.
1. Select **Create a Self-Signed Certificate**.
1. Copy the thumbprint value of the new certificate to use later.

## Install IIS components

To install II components, go to **Server Manager \> Local Server \> Manage \> Add roles and features**. Under **IIS**, confirm that the **Management Tools \> IIS 6 Management Compatibility (IIS 6 Metabase Compatibility)** component is checked.

## Obtain a copy of a previously created SSL certificate to add to the Azure Web App

To obtain a copy of a previously created SSL certificate to add to the Azure Web App, follow these steps.

1. Select the Windows logo key + R to open the **Run** dialog box.  
1. Enter "MMC" to open the Microsoft Management Console.  
1. Select **File > Add/Remove Snap-in**.
1. Under **Available snap-ins**, select **Certificates**, and then select **Add**.
1. In the **Certificates snap-in** dialog box, select **Computer Account**, and then select **Next**.
1. Select **Local Computer**, and then select **Finish**. 
1. Select **OK**.  
1. Expand **Certificates \> Personal > Certificates**.  
1. Locate the SSL Certificate you created from IIS in the list, then right-click it and select **All Tasks \> Export**.  
1. In the export dialog box, select **Next**.  
1. Select **No, do not export the private key**, and then select **Next**.  
1. Select **DER encoded binary X.509 (.CER)**.  
1. Select the C:\temp folder, and then enter "DevBoxSelfSigned" as the file name.  
1. Select **OK**, and then select **Save**.  
	
## Add SSL Certificate to the existing CSU Azure Application

To add the SSL certificate to the existing CSU Azure application, follow these steps.

1. In the web browser on the VM, Edit the CSU Azure App registration created at the start of this article.
2. On the Client Credentials field > Select Add a certificate or secret. 
3. Select on the Certificates tab.
4. Select Upload Certificate.
5. Select the DevBoxSelfSigned certificate  from c:\temp.
6. Description = Devbox cert.
7. Set Description = Devbox Self-signed Certificate.
8. Select Add.
	
## Update Commerce headquarters

After you create the app, you must make the following changes in Commerce headquarters. 

### Enter the application ID

You must enter the application ID (client ID) in headquarters for the installation to succeed.

To enter the application ID (client ID) in headquarters, follow these steps.

1. Go to **System administration \> Setup \> Azure Active Directory applications (Microsoft Entra ID Applications)**.
1. In the **Client ID** column, enter the application ID (client ID).
1. in the **Name** column, enter descriptive text.
1. In the **User ID** column, enter "RetailServiceAccount".  

### Create a new channel database record

To create a new channel database record, follow these steps.

1. Go to **Retail and Commerce \> Headquarters Setup \> Commerce Scheduler \> Channel Database**.  
1. Select **New**. 
1. For **Channel Database ID**, enter "DevSealedCSU".  
1. For **Channel Database Group**, enter "Default".  
1. Select **Save**.  
1. On the **Retail Channel** FastTab, select **Add**.  
1. Select the store you normally work with.  
1. Select **Save**.  
1. On the **Mapping a New Retail Channel** warning dialog box, select **Yes**.  
1. Select **Download \> Configuration file**.  
1. Save the configuration file to C:\temp.  
1. Rename the configuration file to "StoreSystemSetup.xml".  

### Create a new channel profile  	

To create a new channel profile, follow these steps.

1. Go to **Retail and Commerce \> Channel Setup \> Channel Profiles**.  
1. Select **New**. 
1. For **Name**, enter "DevSealedCSUProfile".  
1. Select **Save**. 
1. Under **Profile Properties**, select **Add**.  
1. For **Nonexternal VM connectivity**, enter the following:  
    1. For **Property Key**, enter the property key value.  
    1. For **Retail Server URL**, enter `https://<HostName>:446/RetailServer/Commerce`.  
    1. For **Cloud POS URL**, enter `https://<HostName>:446/POS`.  
1. Go to **Retail and Commerce \> Channels \> Stores \> All Stores**.  
1. For each store record you normally work, update the following:  
    1. For **Live Channel Database**, enter "DevSealedCSU".  
    1. For **Channel Profile**, enter "DevSealedCSUProfile".  
    1. Select **Save**.  

> [!NOTE]
> If you get a warning saying "The store's closing method must be set to 'Shift'", on the **Statement/Closing** FastTab of the store, update the **Closing Method** value to **Shift**.  

### Update CDX data groups

To update Commerce Data Exchange (CDX) data groups, follow these steps.

1. Go to **Retail and Commerce \> Distribution Schedule**.
1. Select the **Default Data** group.
1. Remove the default database record from this group, which prevents future errors when trying to replicate to this database.
		
### Execute sync jobs 

To execute sync jobs, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution Schedule**.   
1. Select the **9999** job.  
1. Select **Run now**.  
1. For each warning, select **Yes**.  
1. Select **OK** to schedule the job.  

## Install Sealed CSU prerequisites

1. Install .NET Core hosting bundle on DEV VM.
    A. RDP into the Dev box.
    B. Open a web browser and go to this site Download .NET 6.0 (Linux, macOS, and Windows) (microsoft.com).
    C. Under ASP.Net Core Runtime 6.0.X  section > Select the Hosting Bundle link for Windows.
    D. Run the Dotnet-hosting installer.
2. Download Sealed Self-hosted installer from LCS to the Dev VM, and copy configuration file.
    A. Open a web browser and go to LCS.dynamics.com.
    B. Select your Project from the list.
    C. On the top of the screen click the three dashes > Select Asset Library.
    D. Select Retail Self-service package.  
    E. If you already have a sealed CSU installer in your list, click the package name to start the download.  
        i. If you don’t have a sealed installer in the list, click Import.
        ii. Select the Sealed Installer version you want to use. 
        iii. Select Pick.
        iv. Then follow the step above to download the installer file.
    F. Copy the sealed installer from the Downloads folder to C:\temp.

## Install the Sealed CSU

We're going to use the syntax below to install the Sealed-CSU on the VHD image. Since this is a Dev box, we'll use the same SSL thumbprint to run all services. For Production/UAT systems these values should be different.   

`CommerceStoreScaleUnitSetup.exe install --port 446 --SSLCertThumbprint "<SSL thumbprint of certificate created earlier>" --RetailServerCertThumbprint "<SSL thumbprint of certificate created earlier>" " --AsyncClientCertThumbprint "< SSL thumbprint of certificate created earlier >"  --AsyncClientAADClientID "<CSU Azure APP Client ID>" --RetailServerAADClientID "<CSU Azure APP Client ID>" --CPOSAADClientID "<CPOS Azure APP Client ID>" --RetailServerAADResourceID "<CSU Azure APP Client ID>" --Config "c:\temp\StoreSystemSetup.xml" --SkipSChannelCheck –trustSqlservercertificate`

## Database Restores from UAT

If you previously set up a sealed CSU using the steps above and then restored a database from another environment, you much perform the following actions to make the sealed CSU functional again. 

1. Go through the steps in the **Update Commerce headquarters** section again to recreate the records. 
    > [!NOTE]
    > Make sure you use the same values for Channel Database ID and Channel Profile. If these values are different than the previous install, you must rerun the installer. 
2. Check your download sessions to see if the jobs are applying. 
    - If the jobs are applying, then your CSU is working and you don't need to rerun the installer steps.
    - If the download jobs aren't applying, first check the Windows Event logs to see if there are any obvious errors, then download a new configuration file from the Channel DB form and rerun the CSU installer using the new configuration file.  


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
