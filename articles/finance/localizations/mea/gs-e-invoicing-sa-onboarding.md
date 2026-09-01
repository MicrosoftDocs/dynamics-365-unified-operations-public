---
title: Onboarding for electronic invoicing in Saudi Arabia
description: Learn how to onboard taxpayers and their electronic invoicing software with the Saudi Arabian tax authority in Microsoft Dynamics 365 Finance.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.date: 09/01/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.custom: 
  - bap-template
---

# Onboarding for electronic invoicing in Saudi Arabia

[!INCLUDE [banner](../../../includes/banner.md)]

This article explains how to onboard taxpayers and their electronic invoicing software with the Saudi Arabian tax authority in Microsoft Dynamics 365 Finance.

Onboarding is mandatory for all taxpayers who are subject to electronic invoicing in Saudi Arabia. As a result of the onboarding process, taxpayers get Cryptographic Stamp Identifiers (CSIDs). You need CSIDs for integration with the electronic invoicing portal that the Saudi Arabian tax authority (Zakat, Tax and Customs Authority \[ZATCA\]) manages, and for further submission of electronic invoices.

## Prerequisites

- The legal entity must be registered as a taxpayer in Saudi Arabia and must have a valid value-added tax (VAT) registration number.
- The legal entity must have access to the [Saudi Arabian Taxation Portal (ERAD)](https://fatoora.zatca.gov.sa/).

## Onboarding process

The onboarding process consists of two steps:

1. Get a Compliance CSID (CCSID), which ZATCA assigns to perform compliance checks on electronic invoice generation solutions (EGSs).
1. Get a Production CSID (PCSID), which ZATCA assigns to compliant EGSs.

### Obtain a CCSID

To obtain a CCSID, follow these steps:

1. In the [Saudi Arabian Taxation Portal (ERAD)](https://fatoora.zatca.gov.sa/), go to the Onboarding and Management Portal by selecting the relevant tile.
1. On the main landing page of the Onboarding and Management Portal, select the **Onboard new solution unit/device** tile, and then select **Generate OTP code**.
1. Select the number of one-time password (OTP) codes to generate. The number depends on the number of e-invoicing generation units (devices) that you'll use.
1. Save the generated OTP codes so you can use them in later steps.

    > [!IMPORTANT]
    > OTP codes are valid for only one hour after they're generated. Ensure you use them within that time.

1. Prepare a configuration file for the certificate signing request (CSR). Create this configuration file as a plain text file that contains the following data.

    ```txt
    oid_section = OIDs
    [OIDs]
    certificateTemplateName = 1.3.6.1.4.1.311.20.2
    [req]
    default_bits = 2048
    emailAddress = MyEmail@email.com
    req_extensions = v3_req
    x509_extensions = v3_ca
    prompt = no
    default_md = sha256
    req_extensions = req_ext
    distinguished_name = dn
    [dn]
    C=SA
    OU=Riyad Branch
    O=Contoso
    CN=PREZATCA-Code-Signing
    [v3_req]
    basicConstraints = CA:FALSE
    keyUsage = digitalSignature, nonRepudiation, keyEncipherment
    [req_ext]
    certificateTemplateName = ASN1:PRINTABLESTRING:PREZATCA-Code-Signing
    subjectAltName = dirName:alt_names
    [alt_names]
    SN=1-TST|2-TST|3-ed22f1d8-e6a2-1118-9b58-d9a8f11e445f
    UID=310122393500003
    title=1100
    registeredAddress= MyAddress
    businessCategory=Industry
    ```

1. Save the CSR configuration file to the same location as the onboarding script, and name it **csr\_config.txt**.
1. In the CSR configuration file, update the **emailAddress** value and the following data.

    | Code              | Description | Specification |
    |-------------------|-------------|---------------|
    | C                 | The country/region code. | A two-letter code (ISO 3166 Alpha-2). |
    | OU                | The name of the organization unit. | For normal taxpayers, the value is free text. For VAT groups, identify the value through the fact that the eleventh digit of the organization identifier is "1". Validate that the input is a 10-digit Tax Identification Number (TIN). |
    | O                 | The name of the organization or taxpayer. | Free text. |
    | CN                | Unique Name or Asset Tracking Number of the Solution Unit provided by the Taxpayer for each Solution unit| Use <ul><li>**PREZATCA-Code-Signing** value for simulation</li><li>your actual number for production</li></ul> |
    | certificateTemplateName| The unique name of the solution or unit. | Use <ul><li>**ASN1:PRINTABLESTRING:PREZATCA-Code-Signing** value for simulation</li><li>**ASN1:PRINTABLESTRING:ZATCA-Code-Signing** for production</li></ul> |
    | SN                | Manufacturer or Solution Provider Name, Model or Version and Serial Number. Automatically filled and not by the Taxpayer: Unique identification code for the EGS. | Free text. |
    | UID               | The VAT registration number of the taxpayer. | A 15-digit number that begins with "3" and ends with "3". |
    | title             | The document type that the taxpayer's solution unit will issue. | Four-digit numerical input that uses "0" and "1" mapped to "TSCZ": "0" = False/Not supported, and "1" = True/Supported. "T" = Tax invoice (standard), "S" = Simplified tax invoice, "C" = For future use, and "Z" = For future use. |
    | registeredAddress | The address of the branch or location where the device or solution unit is primarily situated. | Free text. |
    | businessCategory  | The industry or sector that the device or solution will generate invoices for. | Free text. |

1. Run the [onboarding script](#script) that's provided later in this article. Specify the OTP code and the CSR configuration file as input parameters. Here's an example.

    - for CCSID in simulation environment: 
    `.\OnboardingScript.ps1 -action getComplianceCSID -otp 123345 -csrconfig .\csr_config.txt -environment simulation`

    - for CCSID in production environment: 
    `.\OnboardingScript.ps1 -action getComplianceCSID -password 123 -environment production`

    > [!NOTE]
    > The **password** parameter is optional and can be omitted. If you include it, the certificate you generate has the specified password.

1. You receive the CCSID as a certificate file, **CCSID.pfx**. Save the secret for the CCSID as a text file, **CCSIDSecret.txt**. Save the CCSID certificate file in the Microsoft Azure Key Vault certificate, and save the secret in the Key Vault secret. For more information, see [Customer certificates and secrets](../global/e-invoicing-customer-certificates-secrets.md).
1. Configure the related feature setup in the **Saudi Arabian ZATCA compliance check (SA)** Electronic invoicing feature, and reference the CCSID certificate that you saved in the key vault. Use the certificate for communication with the ZATCA electronic invoicing portal.

### Compliance check

After you get a CCSID by using the PowerShell script, ZATCA requires that you complete specific compliance checks by submitting sample invoices. This step is a prerequisite for requesting a PCSID.

Ensure that you successfully submit to ZATCA all types of sample invoices that you configured in the CSR configuration file. Use the standard process for issuing electronic invoices. For more information, see [Issue electronic invoices in Finance and Supply Chain Management](../global/e-invoicing-submit-electronic-documents.md).

Follow the steps in [Electronic invoicing in Saudi Arabia - Phase two](gs-e-invoicing-sa-get-started.md). Use the **Saudi Arabian ZATCA compliance check (SA)** Electronic invoicing feature and the CCSID that you get.

After you complete the compliance checks, use the PowerShell script to get a PCSID. (See the [onboarding script](#script) that's provided later in this article.)

> [!NOTE]
> If you set the document type in the **title** field of the CSR configuration file to **1000**, you must submit the following three sample invoices for the compliance check:
>
> - Standard Tax Invoice
> - Standard Debit Note
> - Standard Credit Note
>
> If you set the document type to **0100**, you must submit the following three sample invoices for the compliance check:
>
> - Simplified Tax Invoice
> - Simplified Debit Note
> - Simplified Credit Note
>
> If you set the document type to **1100**, you must submit all six sample invoices for the compliance check.

### Obtain a PCSID

To obtain a PCSID, you must correctly configure the solution for electronic invoice generation and submission, and the solution must be fully functioning. To achieve this result, you must complete all the required preliminary configuration steps. For more information, see [Electronic invoicing in Saudi Arabia - Phase two](GS-e-invoicing-sa-get-started.md).

To obtain a PCSID, follow these steps:

1. Ensure that you successfully submit all electronic invoices to ZATCA.
1. Run the [onboarding script](#script) that's provided later in this article. Specify the CCSID as an input parameter. Here's an example.

   `.\OnboardingScript.ps1 -action getProductionCSID -password 123 -environment production`  
    
   > [!NOTE]
    > The **password** parameter is optional and can be omitted. If you include it, the generated certificate has the specified password.

1. Receive the PCSID as a certificate file in PFX format. Save this PCSID certificate and secret file in the key vault.
1. Configure the related feature setup in the **Saudi Arabian Zatca submission (SA)** Electronic invoicing feature. Include the PCSID certificate and secret in the Key Vault parameters.

After you complete all the configuration steps, the system is ready to use in production mode.

To review the obtained CSIDs on the ZATCA side, use the **Review Existing Cryptographic Stamp Identifier (CSID)** tile on the landing page of the Onboarding and Management Portal. You can access this portal from the main [Saudi Arabian Taxation Portal (ERAD)](https://fatoora.zatca.gov.sa/).

## <a id="script"></a>Onboarding script

> [!NOTE]
> Microsoft doesn't support the sample scripts under any standard support program or service. The sample scripts are provided as-is without warranty of any kind. Microsoft disclaims all implied warranties, including without limitation, any implied warranties of merchantability or of fitness for a particular purpose. You assume all risk arising from the use or performance of the sample scripts and documentation. In no event is Microsoft, its authors, or anyone else involved in the creation, production, or delivery of the scripts liable for any damages whatsoever, including without limitation, damages for loss of business profits, business interruption, loss of business information, or other pecuniary loss, arising from the use of or inability to use the sample scripts or documentation, even if Microsoft has been advised of the possibility of such damages.

1. Use the following Windows PowerShell script to get a CCSID and a PCSID.

```powershell
#Saudi Arabian electronic invoice onboarding script
#Version 1.3 (adds -environment switch for Simulation vs Production, better error output)
param(
    $action,
    $otp,
    $csrconfig,
    $password,
    [ValidateSet("simulation","production")]
    $environment = "production"
)
$env:path = $env:path + ";C:\Program Files\Git\usr\bin"

# Select the correct ZATCA base URL for the target environment.
# Simulation onboarding (Fatoora Simulation portal) and Production onboarding
# (Fatoora portal) use DIFFERENT endpoints on the same gateway host.
if ($environment -eq "simulation")
{
    $baseUri = 'https://gw-fatoora.zatca.gov.sa/e-invoicing/simulation'
}
else
{
    $baseUri = 'https://gw-fatoora.zatca.gov.sa/e-invoicing/core'
}
$complianceUri = "$baseUri/compliance"
$productionCsidUri = "$baseUri/production/csids"
Write-Host "Target environment: $environment"
Write-Host "Compliance endpoint: $complianceUri"

# Helper to print a meaningful error (HTTP status + response body when available)
function Write-ZatcaError($err, $contextMessage)
{
    Write-Host "`nZatca service communication error:"
    Write-Host $err.Exception.Message
    try {
        if ($err.Exception.Response -ne $null)
        {
            $statusCode = [int]$err.Exception.Response.StatusCode
            Write-Host "HTTP status code: $statusCode"
            $stream = $err.Exception.Response.GetResponseStream()
            if ($stream -ne $null)
            {
                $reader = New-Object System.IO.StreamReader($stream)
                $body = $reader.ReadToEnd()
                if ($body) { Write-Host "Response body: $body" }
            }
        }
    } catch { }
    Write-Host $contextMessage
    Write-Host "Also confirm you are using the correct environment endpoint (simulation vs. core) and that the OTP was generated in the matching Fatoora portal and used within 1 hour."
}

if ($action -eq "getComplianceCSID")
{
    if (-not (Test-Path -Path $csrconfig))
    {
        throw "CSR configuration file does not exist, please make sure to provide a valid file path for the '-csrconfig' parameter."
    }
 
if ($otp -eq $null)
    {
        throw "OTP code is not provided, please carry correct parameters."
    }
 
#Generate private key
    openssl ecparam -name secp256k1 -genkey -noout -out privatekey.pem
    Write-Host "Private key generated."
 
#Generate public key
    openssl ec -in privatekey.pem -pubout -conv_form compressed -out publickey.pem
    Write-Host "Public key generated."
 
#Generate CSR(Certificate signing request)
    openssl base64 -d -in publickey.pem -out publickey.bin
    openssl req -new -sha256 -key privatekey.pem -extensions v3_req -config $csrconfig -out .\taxpayer.csr
    openssl base64 -in taxpayer.csr -out taxpayerCSRbase64Encoded.txt
    $CSRbase64Encoded = Get-Content -path taxpayerCSRbase64Encoded.txt -Raw
    $CSRbase64Encoded = $CSRbase64Encoded -replace "`n",""
    $CSRbase64Encoded = $CSRbase64Encoded -replace "`r",""
 
#Init request for CCSID
    $postParams = @{"csr"=$CSRbase64Encoded} | ConvertTo-Json
    $postHeader = @{
           "Accept"="application/json"
           "OTP"=$otp
           "Content-Type"="application/json"
           "Accept-Version"="V2"}
 
try
    {
        $response = Invoke-WebRequest -Uri $complianceUri -Method POST -Body $postParams -Headers $postHeader
    }
    catch
    {
        Write-ZatcaError $_ "Please make sure the OTP code in script parameter and Serial Number (SN) in configuration file are valid."
        Write-Host "The process of obtaining a Compliance CSID (CCSID) is interrupted."
    }
 
if ($response -ne $null)
    {
        $response = $response | ConvertFrom-Json
        $requestId = $response.requestID
        Write-Host "Request ID:"
        Write-Host $requestId
        $requestId | Out-File -FilePath .\requestId.txt -Encoding utf8 -NoNewline
 
$CCSIDbase64 = $response.binarySecurityToken
        Write-Host "`nCompliance CSID received from Zatca:"
        Write-Host $CCSIDbase64
        $CCSID = [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($CCSIDbase64))
        $CCSIDCertString = "-----BEGIN CERTIFICATE-----`n" + $CCSID + "`n" + "-----END CERTIFICATE-----"
 
$CCSIDSecret = $response.secret
        Write-Host "`nCompliance CSID secret received from Zatca:"
        Write-Host $CCSIDSecret
 
$CCSIDStringFileName = "CCSIDString.txt"
        $CCSIDSecretFileName = "CCSIDSecret.txt"
        $CCSIDCertFileName = "CCSID.pem"
        $CCSIDFolderPath = Get-Location
        $CCSIDCertFilePath = Join-Path $CCSIDFolderPath $CCSIDCertFileName
        $CCSIDStringFilePath = Join-Path $CCSIDFolderPath $CCSIDStringFileName
        $CCSIDSecretFilePath = Join-Path $CCSIDFolderPath $CCSIDSecretFileName
 
$Utf8NoBomEncoding = New-Object System.Text.UTF8Encoding $False
        [System.IO.File]::WriteAllLines($CCSIDCertFilePath, $CCSIDCertString, $Utf8NoBomEncoding)
        [System.IO.File]::WriteAllLines($CCSIDStringFilePath, $CCSIDbase64, $Utf8NoBomEncoding)
        [System.IO.File]::WriteAllLines($CCSIDSecretFilePath, $CCSIDSecret, $Utf8NoBomEncoding)
 
openssl pkcs12 -inkey privatekey.pem -in CCSID.pem -export -passout pass:$password -out CCSID.pfx
        Write-Host "`nCertificate is saved to CCSID.pfx file and secret is saved to CCSIDSecret.txt file."
        Write-Host "The process of obtaining a Compliance CSID (CCSID) is complete, please process the compliance check and do not delete or move any created files before getting PCSID."
    }
}
 
if ($action -eq "getProductionCSID")
{
    if (-not (Test-Path -Path requestId.txt))
    {
        throw "'requestId.txt' file is missing, please make sure you're running the script in the same location where the results of getting the CCSID are stored."
    }
    if (-not (Test-Path -Path CCSIDString.txt))
    {
        throw "'CCSIDString.txt' file is missing, please make sure you're running the script in the same location where the results of getting the CCSID are stored."
    }
    if (-not (Test-Path -Path CCSIDSecret.txt))
    {
        throw "'CCSIDSecret.txt' file is missing, please make sure you're running the script in the same location where the results of getting the CCSID are stored."
    }
 
$requestId = Get-Content -path requestId.txt -Raw
    $requestId = $requestId -replace "`n",""
    $requestId = $requestId -replace "`r",""
    Write-Host "Request ID is:" $requestId
    $CCSID = Get-Content -path CCSIDString.txt -Raw
    $CCSID = $CCSID -replace "`n",""
    $CCSID = $CCSID -replace "`r",""
    Write-Host "`nCompliance CSID read locally:"
    Write-Host $CCSID
    $CCSIDSecretString = Get-Content -path CCSIDSecret.txt -Raw
    $CCSIDSecretString = $CCSIDSecretString -replace "`n",""
    $CCSIDSecretString = $CCSIDSecretString -replace "`r",""
    Write-Host "`nCompliance CSID secret read locally:"
    Write-Host $CCSIDSecretString
    $AuthTokenString = $CCSID + ":" + $CCSIDSecretString
    $BasicAuthToken = "Basic " + [Convert]::ToBase64String([System.Text.Encoding]::UTF8.GetBytes($AuthTokenString))
 
#Init request for Production CSID (PCSID)
    $postParams = @{"compliance_request_id"=$requestId} | ConvertTo-Json
    $postHeader = @{
           "Accept"="application/json"
           "Authorization"=$BasicAuthToken
           "Content-Type"="application/json"
           "Accept-Version"="V2"}
 
try
    {
        $response = Invoke-WebRequest -Uri $productionCsidUri -Method POST -Body $postParams -Headers $postHeader
    }
    catch
    {
        Write-ZatcaError $_ "Please make sure the compliance check process has been done before obtaining a Production CSID (PCSID)."
        Write-Host "The process of obtaining a Production CSID (PCSID) is interrupted."
    }
 
if ($response -ne $null)
    {
        $response = $response | ConvertFrom-Json
        $PCSIDbase64 = $response.binarySecurityToken
        Write-Host "`nProduction CSID received from Zatca:"
        Write-Host $PCSIDbase64
 
$PCSID = [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($PCSIDbase64))
        $PCSIDCertString = "-----BEGIN CERTIFICATE-----`n" + $PCSID + "`n" + "-----END CERTIFICATE-----"
 
$PCSIDSecret = $response.secret
        Write-Host "`nProduction CSID secret received from Zatca:"
        Write-Host $PCSIDSecret
 
$PCSIDCertFileName = "PCSID.pem"
        $PCSIDSecretFileName = "PCSIDSecret.txt"
        $PCSIDFolderPath = Get-Location
        $PCSIDCertFilePath = Join-Path $PCSIDFolderPath $PCSIDCertFileName
        $PCSIDSecretFilePath = Join-Path $PCSIDFolderPath $PCSIDSecretFileName
 
$Utf8NoBomEncoding = New-Object System.Text.UTF8Encoding $False
        [System.IO.File]::WriteAllLines($PCSIDCertFilePath, $PCSIDCertString, $Utf8NoBomEncoding)
        [System.IO.File]::WriteAllLines($PCSIDSecretFilePath, $PCSIDSecret, $Utf8NoBomEncoding)
 
openssl pkcs12 -inkey privatekey.pem -in PCSID.pem -export -passout pass:$password -out PCSID.pfx
        Write-Host "`nCertificate is saved to PCSID.pfx file and secret is saved to PCSIDSecret.txt file."
        Write-Host "The process of obtaining a Production CSID (PCSID) is complete."
    }
}

```

1. Save the output .pfx certificate file that you receive in the key vault.

## Additional resources

- [Electronic invoicing overview](../global/e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](../e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](../e-invoicing-get-started.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
