---
title: Install Commerce Scale Unit on a virtual hard disk
description: This article explains how to install Commerce Scale Unit on a virtual hard disk for Microsoft Dynamics 365 Commerce development.
author: bstorie
ms.date: 12/20/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: bstor
ms.search.validFrom: 2022-03-01
---

# Install Commerce Scale Unit on a virtual hard disk

[!include [banner](../includes/banner.md)]

This article explains how to install Commerce Scale Unit (CSU) on a virtual hard disk (VHD) for Microsoft Dynamics 365 Commerce development.

## PreRequisite

The following documentation provides a walk through for how to setup the base Sealed CSU in a VHD image that can be used for Development work.  

## Create AAD Apps

Two AAD Apps need to be created one for CSU and one for CPOS (Store commerce for Web) App. The below SSL Certificate will be added to this app. For more information, see [Configure Store Commerce for web to use a custom Azure AD app](cpos-custom-aad.md).

## Create SSL certificate to be used for website based on Host name

1.  RDP into box
2. Open IIS Manager
3. Select to create a new Self-Signed Certificate  
4. Copy the ThumbPrint value of the new certificate to notepad as you will need it later

## Install IIS components

Open Server Manager > Local Server > Manage > Add roles and features > Under IIS make sure the following component is marked: Management Tools > IIS 6 Management Compatibility (IIS 6 Metabase Compatibility)

## Obtain a copy of previous created SSL Cert for adding to Azure Web App

1.  Right Click Windows Start button > Run  
2.  Type:  MMC  
3.  Click File > Add/Remove Snap-in > Select Certificates > Click Add > Select Computer Account > Click Next > Select Local Computer > Click Finish  
4.  Click Ok  
5.  Expand Certificates > Personal > Certificates  
6.  Locate the SSL Certificate you created from IIS in the list > Right Click it > All Tasks > Export  
7.  In the export wizard > Click Next  
8.  Select “No, do not export the private key” > Click Next  
9.  Select “DER encoded binary X.509 (.CER)”  
10. Select the folder C:\temp  and enter the file name = DevBoxSelfSigned  
11. Click OK/Save  
	
## Add SSL Certificate to the existing CSU Azure Application

1. In the web browser on the VM, Edit the CSU Azure App registration created at the start of this article
2. On the Client Credentials field > Click Add a certificate or secret 
3. Click on the Certificates tab
4. Click Upload Certificate
5. Select the DevBoxSelfSigned certificate  from c:\temp
6. Description = Devbox cert
7. Set Description = Devbox Self-signed Certificate
8. Click Add
	
# Update Commerce headquarters

After creating the above App, the following changes need to be made inside Commerce HQ:  

1. The application ID (client ID) must be entered in Commerce HQ for the installation to succeed. Go to System administration > Setup > Azure Active Directory applications (Microsoft Entra ID Applications). Enter the application ID (client ID) in the Client ID column, enter descriptive text in the Name column, and enter RetailServiceAccount in the User ID column.  

 2. Create a new Channel DB record. Go to Retail and Commerce > Headquarters Setup > Commerce Scheduler > Channel Database  
	A. Click New  
	B. Enter the following:  
		- Channel Database ID = DevSealedCSU  
		- Channel Database Group = Default  
	C. Click Save  
	D. Expand the Retail Channel Fast tab  
	E. Click Add  
	F. Select the Store you normally work with  
	G. Click Save  
	H. Click Yes on the Mapping a New Retail Channel warning prompt  
	I. Click Download > Configuration file  
	J. Save the configuration file to C:\temp  
	K. Rename the configuration file to  StoreSystemSetup.xml  after its downloaded  
3. Create new Channel Profile  	
		A. Go to Retail and Commerce > Channel Setup > Channel Profiles  
		B. Click New  
		C. Name = DevSealedCSUProfile  
		D. Click Save  
		E. Under Profile Properties – Click Add  
		F. For non-external VM connectivity set the following:  
                   - Property Key: Property value  
                   - Retail Server URL:`https://<HostName>:446/RetailServer/Commerce`  
                   - Cloud POS URL: `https://<HostName>:446/POS`  
		G. Go to **Retail and Commerce \> Channels \> Stores \> All Stores**.  
		H. Edit the Houston and San Francisco record you normally work with.  
		I. Update the Live Channel Database field = DevSealedCSU  
		J. Update Channel Profile = DevSealedCSUProfile  
		K. Click Save  
			> Note: You may get a warning about “The store’s Closing method must be set to ‘shift’.   If you receive this expand the Statement/Closing fast tab on the store > Change the Closing Method field to "Shift"  
4. Update CDX Data Groups
	       L. Go to > Retail and Commerce > Distribution Schedule
               M. Select the Default Data group
               N. Remove the Default database record from this group (this will prevent future errors with trying to replicate to this DB)
		
5. Execute Sync jobs  
   A. Go to Retail and Commerce > Retail and Commerce IT > Distribution Schedule   
   B. Select the 9999 job  
   C. Click Run now  
   D. Click Yes to all the warning  
   E. Click OK to schedule the job  

# Install Sealed CSU Pre-requisites
	1. Install .NET Core hosting bundle on DEV VM
		A. RDP into the Dev box
		B. Open a web browser and go to this site Download .NET 6.0 (Linux, macOS, and Windows) (microsoft.com)
		C. Under ASP.Net Core Runtime 6.0.X  section > Click the Hosting Bundle link for Windows
		D. Run the Dotnet-hosting installer
	2. Download Sealed Self-hosted installer from LCS to the Dev VM, and copy configuration file
		A. Open a web browser and go to LCS.dynamics.com
		B. Select your Project from the list
		C. On the top of the screen click the three dashes > Select Asset Library
		D. Select Retail Self-service package  
		E. If you already have a sealed CSU installer in your list, click the package name to start the download.  
			i. If you don’t have a sealed installer in the list, click Import
			ii. Select the Sealed Installer version you want to use 
			iii. Click Pick
			iv. Then follow the step above to download the installer file
		F. Copy the sealed installer from the Downloads folder to C:\temp

## Install the Sealed CSU

We are going to use the below syntax to install the Sealed-CSU on the VHD image.   Since this is a Dev box, we will use the same SSL thumbprint to run all services. For Production/UAT systems these values should be different.   

`CommerceStoreScaleUnitSetup.exe install --port 446 --SSLCertThumbprint "<SSL thumbprint of certificate created earlier>" --RetailServerCertThumbprint "<SSL thumbprint of certificate created earlier>" " --AsyncClientCertThumbprint "< SSL thumbprint of certificate created earlier >"  --AsyncClientAADClientID "<CSU Azure APP Client ID>" --RetailServerAADClientID "<CSU Azure APP Client ID>" --CPOSAADClientID "<CPOS Azure APP Client ID>" --RetailServerAADResourceID "<CSU Azure APP Client ID>" --Config "c:\temp\StoreSystemSetup.xml" --SkipSChannelCheck –trustSqlservercertificate`

## Database Restores from UAT

If you previous setup a sealed CSU using the above steps and then restored a database from another environment, you will need to perform the following actions to make the Sealed CSU functional again. 

1) Go through the steps in the **Update Commerce HQ** section again to recreate the records. 
   >Note: Make sure you use the same values for Channel Database ID and Channel Profile. If these values are different than the previous install you will need to re-run the installer. 
2) Check your download sessions to see if the jobs are applying. 
    - If the jobs are applying, then your CSU is working and you don't need to re-run the installer steps.
    - If the download jobs are not applying, first check the Windows Event logs to see if there are any obvious errors, then download a new configuration file from the Channel DB form and re-run the CSU installer using the new configuration file.  


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
