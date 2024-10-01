---
title: Install Commerce Scale Unit on a development environment
description: This article explains how to install Commerce Scale Unit (CSU) on virtual hard disk (VHD) local development and cloud development environments for Microsoft Dynamics 365 Commerce.
author: bstorie
ms.date: 10/01/2024
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: brstor
ms.search.validFrom: 2022-03-01
ms.custom: 
  - bap-template
---

# Install Commerce Scale Unit on a development environment

[!include [banner](../includes/banner.md)]

This article provides step-by-step instructions on how to install an Internet Information Services (IIS) based Commerce Scale Unit (CSU) on virtual hard disk (VHD) local development and Microsoft Dynamics Lifecycle Services (LCS) cloud development environments for Microsoft Dynamics 365 Commerce. This article is divided into sections representing the different actions you must take to complete the installation, and each section should be followed in order. 

## Create Azure Active Directory apps

First, you must create two Microsoft Entra ID (formerly known as Azure Active Directory) apps, one for the CSU and one for the Store Commerce for Web app (formerly known as Cloud point of sale or CPOS). For instructions, see [Set up a custom Retail Server app in Microsoft Entra ID](cpos-custom-aad.md#set-up-a-custom-retail-server-app-in-microsoft-entra-id) and [Set up a custom app for Store Commerce for Web in Microsoft Entra ID](cpos-custom-aad.md#set-up-a-custom-app-for-store-commerce-for-web-in-microsoft-entra-id).

## Create an SSL certificate for a website based on the host name

Next, you need to create a Secure Sockets Layer (SSL) certificate based on the hostname for the CSU website and the Entra ID app authentication. 

To create the SSL certificate, follow these steps.

1. Connect to the development machine using Remote Desktop Protocol (RDP).
1. Open PowerShell with administrator privileges from Command Prompt.
1. Enter the following command.
```cmd
$cert = New-SelfSignedCertificate -Subject "CN=$env:computerName" -DnsName $env:computerName,$([System.Net.Dns]::GetHostByName($env:computerName).HostName) -KeyAlgorithm RSA -KeyLength 2048 -CertStoreLocation "Cert:\LocalMachine\My" -NotBefore (Get-Date) -NotAfter (Get-Date).AddYears(2) -KeyUsage KeyEncipherment,DataEncipherment,CertSign,CRLSign,DigitalSignature -KeyUsageProperty All -FriendlyName "$env:computerName" -KeyExportPolicy Exportable
Export-Certificate -Cert $cert -FilePath "$env:temp\https.cer"
Import-Certificate -CertStoreLocation cert:\LocalMachine\Root -FilePath "$env:temp\https.cer"'
```

4. Copy the thumbprint value of the new certificate for use later during the CSU install section.

> [!NOTE]
> If you create your SSL certificate using a method other than the PowerShell command, ensure that the SSL certificate contains the following `keyUsage` property values: `keyEncipherment`, and `dataEncipherment`. The SSL certificate should also be capable of performing KeyExchange. 

## Convert the SSL certificate you created to the .CER file format

Next, you must convert the SSL certificate you created to the .CER file format.

> [!NOTE]
> To add a SSL certificate to the CSU Entra ID app, it must be in the `.CER` file format.

To convert the SSL certificate you created to the `.CER` file format, follow these steps.

1. On the development machine, select the Windows logo key + R to open the **Run** dialog box.  
1. Enter "MMC" to open the Microsoft Management Console.  
1. Select **File > Add/Remove Snap-in**.
1. Under **Available snap-ins**, select **Certificates**, and then select **Add**.
1. In the **Certificates snap-in** dialog box, select **Computer Account**, and then select **Next**.
1. Select **Local Computer**, and then select **Finish**. 
1. Select **OK**.  
1. Expand **Certificates \> Personal > Certificates**.  
1. Locate the SSL certificate you created earlier, right-click the certificate, and then select **All Tasks \> Export**.  
1. In the export dialog box, select **Next**.  
1. Select **No, do not export the private key**, and then select **Next**.  
1. Select **DER encoded binary X.509 (.CER)**.  
1. Select the C:\temp folder, and then enter "DevBoxSelfSigned" as the file name.  
1. Select **OK**, and then select **Save**.  
	
## Add the SSL certificate to the existing CSU Entra ID app

Next, you must add the SSL certificate you created and converted to the `.CER` file format to the existing CSU Entra ID app. This step is required for the CSU to generate an authentication token for communication with Commerce headquarters.

To add the SSL certificate you created to the CSU Entra ID app, follow these steps.

1. In a web browser on the virtual machine (VM), edit the CSU Azure App registration created earlier.
1. For **Client Credentials**, select **Add a certificate or secret**. 
1. Select the **Certificates** tab.
1. Select **Upload Certificate**.
1. From C:\temp, select the **DevBoxSelfSigned** certificate.
1. For **Description**, enter "Devbox cert".
1. For **Set Description**, enter "Devbox Self-signed Certificate".
1. Select **Add**.

> [!NOTE]
> SSL certificates are issued for one year by default. It's critical that you have a plan to update the SSL certificate associated with your Azure App registration and the Sealed CSU at least one month before expiration. Failure to perform this planned update results in the Sealed CSU no longer being able to communicate with Commerce headquarters. For instructions on how to apply a new SSL certificate, see (Update an expired SSL certificatec)[#update-an-expired-SSL-certificate].
	
## Update Commerce headquarters

The following sections list all the changes you must make in Commerce headquarters before you run the CSU installation. 

### Enter the application ID (client ID) of the CSU Entra ID app

To enter the application ID (client ID) of the CSU Entra ID app in headquarters, follow these steps.

1. Go to **System administration \> Setup \> Azure Active Directory applications (Microsoft Entra ID Applications)**.
1. In the **Client ID** column, enter the application ID (client ID) of the CSU Entra ID app in the Entra portal.
1. in the **Name** column, enter descriptive text.
1. In the **User ID** column, enter "RetailServiceAccount".  

### Create a new channel database record

You must create a new channel database record for the CSU. After creating that database record, you should obtain a copy of its configuration file, which will help to simplify the installation process. 

To create a new channel database record for the CSU in headquarters, follow these steps.

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

Next, you must create a new channel profile record for the CSU URL, and then update the existing store records to use the new channel database and profile. 

> [!NOTE]
> Alternatively, you can instead modify the existing channel profile record to use the CSU URLs. 

To create a new channel profile in headquarters and update the existing store records to use the new channel database and profile, follow these steps.

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
1. For each store record you normally work, update the following fields:  
    1. For **Live Channel Database**, enter "DevSealedCSU".  
    1. For **Channel Profile**, enter "DevSealedCSUProfile".  
    1. Select **Save**.  

> [!NOTE]
> - If you receive a warning stating `The store's closing method must be set to 'Shift'`, on the **Statement/Closing** FastTab of the store, update the **Closing Method** value to **Shift**.
> - The \<HostName\> value typically starts with "DEV" and can be found by opening IIS Manager and reviewing the server name value shown in the upper left corner. It can also be found on the LCS Environments page in the **VM Name** column under **Manage environment \> LOCAL ACCOUNTS**.

### Update CDX data groups

The following change removes the default database from the Commerce Data Exchange (CDX) data groups in headquarters, because this database is no longer used. Failure to make this update can result in data sync errors later on. 

To update CDX data groups in headquarters, follow these steps.

1. Go to **Retail and Commerce \> Distribution Schedule**.
1. Select the **Default Data** group.
1. Remove the default database record from this group.
		
### Execute sync jobs 

The following sync jobs are executed in headquarters before installation so that data package files are available for the CSU Async Client service once the installation is completed. If CSU installation is successful, these jobs show an applied status as the Async Client applies them. It isn't required to execute this section before CSU installation, however this step can help with early troubleshooting and verification that everything is working. 

To execute sync jobs in headquarters, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution Schedule**.   
1. Select the **9999** job.  
1. Select **Run now**.  
1. For each warning, select **Yes**.  
1. Select **OK** to schedule the job.  

## Install Sealed CSU prerequisites

Before you can run the Sealed CSU installer, you must complete the following steps. 

### Verify IIS components installed

To verify that the **IIS 6 Management Compatibility (IIS 6 Metabase Compatibility)** component is installed on the development machine, follow these steps.

1. Go to **Server Manager \> Local Server \> Manage \> Add roles and features**.
1. Under **IIS**, confirm that the **Management Tools \> IIS 6 Management Compatibility (IIS 6 Metabase Compatibility)** component is checked.

### Install .NET Core hosting bundle

To install the .NET Core hosting bundle on the development machine, follow these steps.

1. Connect to the development machine using Remote Desktop Protocol (RDP).
1. Open a web browser and go to [Download .NET 6.0 (Linux, macOS, and Windows](https://dotnet.microsoft.com/en-us/download/dotnet/6.0).
1. In the **ASP.Net Core Runtime 6.0.X** section, select the **Hosting Bundle** installer for Windows to download it.
1. Run the **dotnet-hosting-6.0.x-win.exe** installer.

### Download the sealed self-hosted installer

> [!NOTE]
> Sealed CSU installers are only available from the LCS Asset library.  

To download the sealed self-hosted CSU installer to the development machine, follow these steps.

1. Open a web browser on the development machine and sign in to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com).
1. Select your project from the list.
1. From the hamburger menu at the top of the page, select **Asset library**.
1. Select **Retail Self-service package**.  
1. If you already have a sealed CSU installer in your list, select the package name to start the download.  
1. If you don’t have a CSU sealed installer in the list, select **Import**, select the sealed installer version you want to use, select **Pick**, and then select the package name to start the download. 
1. Copy the sealed installer from the **Downloads** folder to C:\temp.

## Install the sealed CSU

The process of installing a sealed CSU usually employs a configuration file downloaded from headquarters that contains all of the information needed for Retail Transaction Service (RTS) authentication. If you don't use a configuration file, then you must specify additional parameters such as `--AadTokenIssuerPrefix`, `--StoreSystemAosURL`, `--StoreSystemChannelDatabaseId`, and `--TenantId`. For a full list of installer commands, see [Mass deployment of sealed Commerce self-service components](enhanced-mass-deployment.md). 

To install the sealed CSU on the development machine, follow these steps.

1. Open a Windows Command Prompt with administrator privileges.
1. Change directory to C:\temp (for example, `CD C:\temp`).
1. Execute the following command.

`CommerceStoreScaleUnitSetup.exe install --port 446 --SSLCertThumbprint "<SSL thumbprint of certificate created earlier>" --RetailServerCertThumbprint "<SSL thumbprint of certificate created earlier>" --AsyncClientCertThumbprint "<SSL thumbprint of certificate created earlier >"  --AsyncClientAADClientID "<CSU Azure APP Client ID>" --RetailServerAADClientID "<CSU Azure APP Client ID>" --CPOSAADClientID "<CPOS Azure APP Client ID>" --RetailServerAADResourceID "<Application ID URI>" --Config "c:\temp\StoreSystemSetup.xml" --SkipSChannelCheck --trustSqlservercertificate`

> [!NOTE]
> - Since this is a development machine, using the same SSL thumbprint to run all services is allowed. For production and user acceptance testing (UAT) environments, these values should be different.
> - Don't enter port 80 or 443 during installation. Entering either of these values interferes with the application object server (AOS) service that hosts the Commerce headquarters website. 

## Additional steps for cloud (LCS) deployed development environments 

The setup steps in [Install the sealed CSU](#install-the-sealed-csu) assume that you'll RDP into the development environment when accessing the CSU URL. To make the development environment sealed CSU accessible from outside the development VM, you must perform the following additional tasks.   

> [!NOTE]
> External accessible redirection has only been tested with Commerce version 10.0.39 and earlier. This functionality is based on redirecting the previous legacy (default) Retail Server URL to the sealed CSU on the VM. Support for this functionality will be removed in future versions along with the removal of the legacy (default) Retail Server. 

### Create a channel profile for external access

To create a channel profile for external access, follow these steps.

1. In headquarters, go to **Retail and Commerce \> Channel Setup \> Channel Profiles** and create a new channel profile.
1. Set the following property values: 
    1. For **Retail Server URL**, enter `https://<LCSEnvironmentName>devret.axcloud.dynamics.com/RetailServer/Commerce`.
    1. For **Cloud POS**, enter `https://<LCSEnvironmentName>devret.axcloud.dynamics.com/POS`.	
1. Select **Save**.
1. Go to **Retail and Commerce \> Channels \> Stores \> All Stores**.
1. Edit the store record you normally work with. 
1. Update the **Channel Profile** to the value you created.
1. Select **Save**.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution Schedule** and execute the **1070 (Channel configuration)** sync job.

### Update IIS binding for website

The IIS binding for the legacy Retail Server and Sealed CSU must be updated to support the redirection. 

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

## Database restores from UAT

If you previously set up a sealed CSU using the steps in [Install the sealed CSU](#install-the-sealed-csu) and then restored the headquarters database from another environment, you must perform the following steps to make the sealed CSU functional again. 

1. To recreate the records, follow the steps in [Update Commerce headquarters](#update-commerce-headquarters). 
    > [!NOTE]
    > You must use the same values for **Channel Database ID** and **Channel Profile** that you used in the previous installation. If these values are different than the previous installation, you must rerun the installer. 
2. Check your download sessions to see if the jobs are applying. 
    - If the jobs are applying, then your CSU is working and you don't need to rerun the installer steps.
    - If the download jobs aren't applying, first check the Windows Event logs to see if there are any obvious errors, then download a new configuration file from the channel database form and rerun the CSU installer using the new configuration file.
    - 
## Update the sealed CSU to a new version  

To update the sealed CSU to a newer version, obtain a newer version of the Sealed CSU installer file and then run the same command line arguments you used to first install the sealed CSU. 

## Update an expired SSL certificate

To update an expiring or expired certificate for the Sealed CSU, you don't need to completely reinstall the Sealed CSU. Instead, create the new SSL certificate, and then run the following command.

```cmd
CommerceStoreScaleUnitSetup.exe updateCertificates --SslCertFullPath "store:///My/LocalMachine?FindByThumbprint=YourNewSslCertificateThumbprint" --AsyncClientCertFullPath "store:///My/LocalMachine?FindByThumbprint=YourNewAsyncClientAadAppCertThumbprint" --RetailServerCertFullPath "store:///My/LocalMachine?FindByThumbprint=YourNewRsAadAppCertThumbprint"
```


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
