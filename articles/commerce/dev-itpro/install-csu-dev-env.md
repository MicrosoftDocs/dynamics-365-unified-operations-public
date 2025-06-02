---
title: Install Commerce Scale Unit on a development environment
description: This article explains how to install Commerce Scale Unit (CSU) on virtual hard disk (VHD) local development and cloud development environments for Microsoft Dynamics 365 Commerce.
author: bstorie
ms.date: 6/01/2025
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

## Prerequisites  

Before beginning a Commerce Scale Unit installation, you must complete various one time tasks. These operations often need specific permissions and therefore may require the help of your organization's administrative personnel.

First, you must create two Microsoft Entra ID (formerly known as Azure Active Directory) apps, one for the CSU and one for the Store Commerce for Web app (formerly known as Cloud point of sale or CPOS). The newly created apps must then be registered in Microsoft Dynamics 365 Commerce headquarters.

Please follow the **Prerequisites** section in [Configure and install Commerce Scale Unit](retail-store-scale-unit-configuration-installation.md#prerequisites) and then return to this document to continue.


## Create an SSL certificate for a website based on the host name

Next, you need to create a Secure Sockets Layer (SSL) certificate based on the hostname for the CSU website and the Entra ID app authentication. 

To create the SSL certificate, follow these steps.

1. Connect to the development machine using Remote Desktop Protocol (RDP).
1. Open PowerShell with administrator privileges from Command Prompt.
1. Enter the following command.
```cmd
$cert = New-SelfSignedCertificate -Subject "CN=$env:computerName" -DnsName $env:computerName,$([System.Net.Dns]::GetHostByName($env:computerName).HostName) -KeyAlgorithm RSA -KeyLength 2048 -CertStoreLocation "Cert:\LocalMachine\My" -NotBefore (Get-Date) -NotAfter (Get-Date).AddYears(2) -KeyUsage KeyEncipherment,DataEncipherment,CertSign,CRLSign,DigitalSignature -KeyUsageProperty All -FriendlyName "$env:computerName" -KeyExportPolicy Exportable
Export-Certificate -Cert $cert -FilePath "$env:temp\https.cer"
Import-Certificate -CertStoreLocation cert:\LocalMachine\Root -FilePath "$env:temp\https.cer"
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
> SSL certificates are issued for one year by default. It's critical that you have a plan to update the SSL certificate associated with your Azure App registration and the Sealed CSU at least one month before expiration. Failure to perform this planned update results in the Sealed CSU no longer being able to communicate with Commerce headquarters. For instructions on how to apply a new SSL certificate, see (Update an expired SSL certificate)[#update-an-expired-SSL-certificate].
	
## Update Commerce headquarters

The following sections list all the changes you must make in Commerce headquarters before you run the CSU installation. 

### Enter the application ID (client ID) of the CSU Entra ID app

To enter the application ID (client ID) of the CSU Entra ID app in headquarters, follow these steps.

1. Go to **System administration \> Setup \> Azure Active Directory applications (Microsoft Entra ID Applications)**.
1. In the **Client ID** column, enter the application ID (client ID) of the CSU Entra ID app in the Entra portal.
1. in the **Name** column, enter descriptive text.
1. In the **User ID** column, enter "RetailServiceAccount".  



## Install Sealed CSU prerequisites

Before you can run the Sealed CSU installer, you must complete the following steps. 

### Verify IIS components installed

To verify that the **IIS 6 Management Compatibility (IIS 6 Metabase Compatibility)** component is installed on the development machine, follow these steps.

1. Go to **Server Manager \> Local Server \> Manage \> Add roles and features**.
1. Under **IIS**, confirm that the **Management Tools \> IIS 6 Management Compatibility (IIS 6 Metabase Compatibility)** component is checked.

### Install .NET Core hosting bundle

To install the .NET Core hosting bundle on the development machine, follow these steps.

1. Connect to the development machine using Remote Desktop Protocol (RDP).
1. Open a web browser and go to [Download .NET 8.0 (Linux, macOS, and Windows](https://dotnet.microsoft.com/en-us/download/dotnet/8.0).
1. In the **ASP.NET Core Runtime 8.0.X** section, select the **Hosting Bundle** installer for Windows to download it.
1. Run the **dotnet-hosting-8.0.x-win.exe** installer.


## Download and Install
To download and execute the Commerce Scale Unit installer, see [Downloading and Running the Commerce Scale Unit Installer](retail-store-scale-unit-download-install). This article describes the steps necessary to download required configuration from Headquarters, download the installation program, and how to run the installer.

Once installation is complete, return here.


## Additional steps for cloud (LCS) deployed development environments 

The setup steps in [Download and Install](#download-and-install) assume that you'll RDP into the development environment when accessing the CSU URL. To make the development environment sealed CSU accessible from outside the development VM, you must perform the following additional tasks.   


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

To update an expiring or expired certificate for the Sealed CSU, you don't need to completely reinstall the Sealed CSU. Instead, create the new SSL certificate, and then execute the following command.

```cmd
CommerceStoreScaleUnitSetup.exe updateCertificates --SslCertFullPath "store:///My/LocalMachine?FindByThumbprint=YourNewSslCertificateThumbprint" --AsyncClientCertFullPath "store:///My/LocalMachine?FindByThumbprint=YourNewAsyncClientAadAppCertThumbprint" --RetailServerCertFullPath "store:///My/LocalMachine?FindByThumbprint=YourNewRsAadAppCertThumbprint"
```


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
