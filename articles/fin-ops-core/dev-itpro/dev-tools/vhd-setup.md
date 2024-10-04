---
title: Set up the downloadable VHD for first use
description: Learn about how to set up the downloadable VHD for first use of the Application Object Server and register a new application in Microsoft Entra ID.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 02/17/2022
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-02-09
ms.dyn365.ops.version: AX 7.0.0
---

# Set up the downloadable VHD for first use

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This article applies to the virtual hard drive (VHD) that was released for versions 10.0.24 and later.

When you first sign in to the virtual machine, the **Application Object Server** will not be ready for use. A script needs to be run that will create self-signed certificates to be used on the virtual machine, and a customer-provided application registration ID for authentication. After successfully running the script, the environment will be ready for use.

## Register a new application in Microsoft Entra ID

To register a new application in Microsoft Microsoft Entra ID, follow the steps outlined in [Register app or web API](/azure/active-directory/develop/quickstart-register-app). The new app registration should be for a web application, and the following redirect URIs should be added:

- `https://usnconeboxax1aos.cloud.onebox.dynamics.com/`
- `https://usnconeboxax1aos.cloud.onebox.dynamics.com/oauth/`

Once created, make note of the **Application (client) ID**.

## Run the setup script

After you sign in with the **localadmin** account, right-click the desktop shortcut **Generate Self-Signed Certificates**, and select **Run as administrator**. When the script prompts for the application ID, provide the **Application (client) ID** created in Microsoft Entra ID.

When the script finishes, the environment is ready for use. At this time, you can run the Admin Provisioning tool to set the administrator account, permissions, and tenant. Make sure that the email provided is for the Microsoft Entra tenant in which the application registration was created.

## Steps to renew expired certs

1)	Identify Expired Certificates:
Start Windows PowerShell as administrator and enter the following two commands:
cd cert:\LocalMachine\My
ls | Select-Object NotAfter,Thumbprint,Subject | Where-Object -Property Subject -like "CN=DeploymentsOnebox.*" | Sort-Object -Property Subject,NotAfter
The NotAfter column shows when each of them expires. The Subject column contains descriptive information about certificates. The Thumbprint column contains the key by which the certificate is recognized by the operating system.
2)	Clone Expired Certificates and Extend Their Validity
For each of the four certificates repeat the following commands:
$Thumbprint = (get-childitem -Path 01F93A5974A14DC3B40F1CF0BE78127974187BE5 )
New-SelfSignedCertificate -CloneCert $Thumbprint -NotAfter (Get-Date).AddMonths(120)
Replace “01F93A5974A14DC3B40F1CF0BE78127974187BE5” with the thumbprint of the certificate you want to clone.
You’ll get a new self-signed certificate valid for 10 years, cloned from the existing one, with its new thumbprint:

3)	Update D365FO’s Config Files
To see the new list of certificates run the following command in PowerShell:
ls | Select-Object NotAfter,Thumbprint,Subject | Where-Object -Property Subject -like "CN=DeploymentsOnebox.*" | Sort-Object -Property Subject,NotAfter
Now you see two certificates for each of the certificate types – one with the old validity and thumbprint and one with the new validity (current date + 120 months) and thumbprint.
Now start VisualStudio as administrator and open the following three files in the C:\AOSService\webroot folder:
web.config
wif.config
wif.services.config
Press Ctrl+Shift+H key combination to open Find and Replace dialog. Make sure that you select All Open Documents in the Look in drop-down selection box, so that find and replace action will be applied on all three open files.
Now you will have to repeat the following actions for each pair of certificate types:
In the Find what box enter the thumbnail of the old (expired) certificate.
In the Replace with box enter the thumbnail of the cloned new certificate.
Replace all the occurrences in open files.
After you have done this for all four certificates, save the three config files and close VisualStudio.
Restart your browser and navigate to D365FO. It should start without any problems.
4)	Renew IIS cerfiticate (added in 2024)
The above step might not be required anymore for basic D365FO work, but you definitely need to renew the *.cloud.onebox.dynamics.com certificate that IIS is using for AOSService site on order to work with modern browsers (Edge, Chrome, .etc.).
cd cert:\LocalMachine\My
ls | Select-Object NotAfter,Thumbprint,Subject | Where-Object -Property Subject -like "CN=*cloud.onebox.dynamics.com*" | Sort-Object -Property Subject,NotAfter
Open Manage computer certificates, find new certificate in Personal\Certificates, export it and import it in Trusted Root Certification Authorities\Certificates.
Open IIS and select the new cert for AOSService page binding. Check with View that the right certificate is selected (see Valid to).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
