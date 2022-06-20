---
# required metadata

title: Electronic invoicing onboarding in Saudi Arabia
description: This topic provides information about onboarding process of taxpayers and their electronic invoicing software by Saudi Arabian tax authorities.
author: ilkond
ms.date: 06/20/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Saudi Arabia
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2022-07-15
ms.dyn365.ops.version: AX 10.0.28

---

# Electronic invoicing onboarding in Saudi Arabia

[!include [banner](../includes/banner.md)]

Onboarding is mandatory for all taxpayers who are subjects to electronic invoicing in Saudi Arabia. As the result of onboarding process, taxpayers will obtain Cryptographic Stamp Identifiers (**CSID**) which are required for integration with Saudi Arabian electronic invoicing portal and further electronic invoices submission.
This topic provides information about onboarding process for taxpayers and their electronic invoicing software by Saudi Arabian tax authorities.

## Prerequisites

- The legal entity must be registered as a Taxpayer in Saudi Arabia and have a valid VAT registration number.
- The legal entity must have the access to Saudi Arabian Taxation Portal - [ERAD](https://fatoora.zatca.gov.sa/) 

## Onbaording process

1. In the Taxation Portal (**ERAD**), navigate to the Onboarding and Management Portal by clicking on the relevant tile.
2. On the main landing page of the Onboarding and Management Portal select the **Onboard new solution unit/device** tile and then click on 
**Generate OTP code**.
3. Choose to the number of **OTP** (*on-time password*) codes to be generated. The number depends on how many e-invoicing generation units (devices) will be used.
4. Save the generated OTP codes to be used on the next steps.

Text [Customer certificates and secrets](e-invoicing-customer-certificates-secrets.md). 

> [!NOTE]
> Some .

   ![Property type added on the Electronic document property types page.](media/e-invoicing-pol-parameters.jpg)
   
   
### Create an app registration

1. Use the following Windows PowerShell script to create a self-signed certificate for service-to-service (S2S) authentication.

    ```powershell
    $certOutputLocation = "C:\certs\proxytest"
    $certName = "sdiProxyClientS2SCert"
    $certPassword = "123"

    $certCerFile = Join-Path $certOutputLocation "$certName.cer"
    $certPfxFile = Join-Path $certOutputLocation "$certName.pfx"

    $securePassword = ConvertTo-SecureString $certPassword -AsPlainText -Force

    $cert = New-SelfSignedCertificate -KeyLength 2048 -KeyExportPolicy Exportable -FriendlyName "CN=$certName" -CertStoreLocation Cert:\CurrentUser\My -Subject $certName -Provider "Microsoft Enhanced RSA and AES Cryptographic Provider"

    Export-Certificate -Cert $cert -FilePath $certCerFile -type CERT | Out-Null
    Export-PfxCertificate -Cert $cert -FilePath $certPfxFile -Password $securePassword | Out-Null
    ```

2. Save the .pfx certificate file to the key vault, and then delete the local copy.

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
