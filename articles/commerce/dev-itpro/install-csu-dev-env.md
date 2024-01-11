---
title: Install Commerce Scale Unit on a development environment
description: This article explains how to install Commerce Scale Unit (CSU) on virtual hard disk (VHD) local development and cloud development environments for Microsoft Dynamics 365 Commerce.
author: bstorie
ms.date: 12/21/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: brstor
ms.search.validFrom: 2022-03-01
---

# Install Commerce Scale Unit on a development environment

[!include [banner](../includes/banner.md)]

This article explains how to install Commerce Scale Unit (CSU) on virtual hard disk (VHD) local development and cloud development environments for Microsoft Dynamics 365 Commerce. 

## Create Azure Active Directory apps

First, you must create two Azure Active Directory (Azure AD) apps, one for CSU and one for the Store Commerce for Web app (formerly CPOS). The Secure Sockets Layer (SSL) certificate will be added to this app. For more information, see [Configure Store Commerce for web to use a custom Azure AD app](cpos-custom-aad.md).

## Create an SSL certificate for a website based on the host name

To create an SSL certificate for a website based on the host name, follow these steps.

1. Connect to the development machine using Remote Desktop Protocol (RDP).
1. Open Internet Information Services (IIS) Manager.
1. Select **Create a Self-Signed Certificate**.
1. Copy the thumbprint value of the new certificate for use later.

## Install IIS components

To install IIS components on the development machine, go to **Server Manager \> Local Server \> Manage \> Add roles and features**. Under **IIS**, confirm that the **Management Tools \> IIS 6 Management Compatibility (IIS 6 Metabase Compatibility)** component is checked.

## Obtain a copy of a previously created SSL certificate to add to the Azure Web App

To obtain a copy of a previously created SSL certificate to add to the Azure Web App, follow these steps.

1. On the development machine, select the Windows logo key + R to open the **Run** dialog box.  
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
	
## Add SSL certificate to the existing CSU Azure application

To add the SSL certificate to the existing CSU Azure application, follow these steps.

1. In a web browser on the virtual machine (VM), edit the CSU Azure App registration created earlier.
1. For **Client Credentials**, select **Add a certificate or secret**. 
1. Select the **Certificates** tab.
1. Select **Upload Certificate**.
1. From C:\temp, select the **DevBoxSelfSigned** certificate.
1. For **Description**, enter "Devbox cert".
1. For **Set Description**, enter "Devbox Self-signed Certificate".
1. Select **Add**.
	
## Update Commerce headquarters

After you create the app, you must make the following updates in Commerce headquarters. 

### Enter the application ID

You must enter the application ID (client ID) in headquarters for the installation to succeed.

To enter the application ID (client ID) in headquarters, follow these steps.

1. Go to **System administration \> Setup \> Azure Active Directory applications (Microsoft Entra ID Applications)**.
1. In the **Client ID** column, enter the application ID (client ID).
1. in the **Name** column, enter descriptive text.
1. In the **User ID** column, enter "RetailServiceAccount".  

### Create a new channel database record

To create a new channel database record in headquarters, follow these steps.

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

To create a new channel profile in headquarters, follow these steps.

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

To update Commerce Data Exchange (CDX) data groups in headquarters, follow these steps.

1. Go to **Retail and Commerce \> Distribution Schedule**.
1. Select the **Default Data** group.
1. Remove the default database record from this group, which prevents future errors when trying to replicate to this database.
		
### Execute sync jobs 

To execute sync jobs in headquarters, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution Schedule**.   
1. Select the **9999** job.  
1. Select **Run now**.  
1. For each warning, select **Yes**.  
1. Select **OK** to schedule the job.  

## Install sealed CSU prerequisites

To install sealed CSU prerequisites, complete the following steps.

### Install .NET Core hosting bundle on the development machine

To install .NET Core hosting bundle on the development machine, follow these steps.

1. Connect to the development machine using Remote Desktop Protocol (RDP).
1. Open a web browser and go to [Download .NET 6.0 (Linux, macOS, and Windows](https://dotnet.microsoft.com/en-us/download/dotnet/6.0).
1. In the **ASP.Net Core Runtime 6.0.X** section, select the **Hosting Bundle** installer for Windows to download it.
1. Run the **dotnet-hosting-6.0.x-win.exe** installer.

### Download the sealed self-hosted installer to the development machine and copy the configuration file

To download the sealed self-hosted installer to the development machine and copy the configuration file, follow these steps.

1. Open a web browser on the development machine and sign in to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com).
1. Select your project from the list.
1. From the hamburger menu at the top of the page, select **Asset library**.
1. Select **Retail Self-service package**.  
1. If you already have a sealed CSU installer in your list, select the package name to start the download.  
1. If you don’t have a CSU sealed installer in the list, select **Import**, select the sealed installer version you want to use, select **Pick**, and then select the package name to start the download. 
1. Copy the sealed installer from the **Downloads** folder to C:\temp.

## Install the sealed CSU

> [!NOTE]
> Since this is a development machine, use the same SSL thumbprint to run all services. For production and user acceptance testing (UAT) environments, these values should be different.   

To install the sealed CSU on the development machine, follow these steps.

1. Open a Windows Command Prompt with administrator privileges.
1. Change directory to C:\temp (for example, `CD C:\temp`).
1. Execute the following command.

`CommerceStoreScaleUnitSetup.exe install --port 446 --SSLCertThumbprint "<SSL thumbprint of certificate created earlier>" --RetailServerCertThumbprint "<SSL thumbprint of certificate created earlier>" " --AsyncClientCertThumbprint "<SSL thumbprint of certificate created earlier >"  --AsyncClientAADClientID "<CSU Azure APP Client ID>" --RetailServerAADClientID "<CSU Azure APP Client ID>" --CPOSAADClientID "<CPOS Azure APP Client ID>" --RetailServerAADResourceID "<CSU Azure APP Client ID>" --Config "c:\temp\StoreSystemSetup.xml" --SkipSChannelCheck --trustSqlservercertificate`

> [!Note]
> This process uses a downloaded configuration file from HQ as it contains all of the information need for the RTS authentication.  If you don't use a configuration file then additional parameters such as --AadTokenIssuerPrefix, --StoreSystemAosURL, --StoreSystemChannelDatabaseId, --TenantId need to be specified.  For a full list of installer commands review the [Mass Deployment of sealed Commerce Self-service components](enhanced-mass-deployment.md)

## Database restores from UAT

If you previously set up a sealed CSU using the steps above and then restored a database from another environment, you must perform the following steps to make the sealed CSU functional again. 

1. Go through the steps in [Update Commerce headquarters](#update-commerce-headquarters) to recreate the records. 
    > [!NOTE]
    > You must use the same values for **Channel Database ID** and **Channel Profile** that you used in the previous installation. If these values are different than the previous installation, you must rerun the installer. 
2. Check your download sessions to see if the jobs are applying. 
    - If the jobs are applying, then your CSU is working and you don't need to rerun the installer steps.
    - If the download jobs aren't applying, first check the Windows Event logs to see if there are any obvious errors, then download a new configuration file from the channel database form and rerun the CSU installer using the new configuration file.  

## Additional steps for cloud (LCS) deployed development environments 

To make the development environment accessible from outside the development VM, you must perform the following additional tasks. 

> [!NOTE]
> External accessible redirection has only been tested with Commerce version 10.0.37 and earlier. Support for this functionality is retired in newer versions with the removal of the legacy (default) Retail Server. 

### Create a channel profile for external access

Create a channel profile for external access, follow these steps.

1. In headquarters, go to **Retail and Commerce \> Channel Setup \> Channel Profiles** and create a new channel profile.
1. Set the following property values: 
    1. For **Retail Server URL**, enter `https://<LCSEnvironmentName>devret.axcloud.dynamics.com/RetailServer/Commerce`.
    1. For **Cloud POS**, enter `https://<LCSEnvironmentName>devret.axcloud.dynamics.com/POS`.	
1. Select **Save**.
1. Go to **Retail and Commerce \> Channels \> Stores \> All Stores**.
1. Edit the store record you normally work with. 
1. Update the **Channel Profile** to the value you just created.
1. Select **Save**.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution Schedule** and execute the **1070 (Channel configuration)** sync job.

### Update IIS binding for website

To update the IIS binding for the website, follow these steps.

1. Connect to the development machine using Remote Desktop Protocol (RDP).
1. Open IIS Manager and expand **Sites**.
1. Select the **RetailServer** website.
1. On the right side of the screen, select **Bindings**.
1. Select the **HTTPS** binding, and then select **Edit**.
1. Set the **Port** value to "444".
1. For **Host name**, copy the entire URL string value for use later, and then delete the value.
1. Select **OK**.
1. Select **Close**.
1. Select the **RetailStoreScaleUnitWebsite.AspNetCore** website.
1. On the right side of the screen, select **Bindings**.
1. Select the **HTTPS** binding, and then select **Edit**.
1. Set the **Port** value to "443".
1. For **Host name**, enter the **Host name** URL string value you copied earlier.
1. For **SSL Certificate**, select the downward arrow.
1. Select the SSL certificate that ends in `<LCS name>devaos.axcloud.dynamics.com`.
1. Select **OK**.
1. Select **Close**.








[!INCLUDE[footer-include](../../includes/footer-banner.md)]
