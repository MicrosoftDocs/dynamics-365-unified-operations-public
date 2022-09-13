---
title: Electronic invoicing onboarding in Saudi Arabia
description: This article explains how to onboard taxpayers and their electronic invoicing software with Saudi Arabian tax authorities.
author: mrolecki
ms.date: 06/30/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Saudi Arabia
ms.author: mrolecki
ms.search.validFrom: 2022-07-15
ms.dyn365.ops.version: AX 10.0.28
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Electronic invoicing onboarding in Saudi Arabia

[!include [banner](../includes/banner.md)]

Onboarding is mandatory for all taxpayers who are subject to electronic invoicing in Saudi Arabia. As a result of the onboarding process, taxpayers obtain Cryptographic Stamp Identifiers (CSIDs). CSIDs are required for integration with the electronic invoicing portal that is managed by the Saudi Arabian tax authority (ZATCA) and for further submission of electronic invoices.

This article explains how to onboard taxpayers and their electronic invoicing software with Saudi Arabian tax authorities.

## Prerequisites

- The legal entity must be registered as a taxpayer in Saudi Arabia and must have a valid value-added tax (VAT) registration number.
- The legal entity must have the access to the [Saudi Arabian Taxation Portal (ERAD)](https://fatoora.zatca.gov.sa/).

## Onboarding process

The onboarding process consists of two steps:

1. Obtain a Compliance CSID (CCSID), which ZATCA assigns to perform compliance checks of Electronic invoice generation solutions (EGSs).
2. Obtain a Production CSID (PCSID), which ZATCA assigns to compliant EGSs.

### Obtain a CCSID

1. In the [Saudi Arabian Taxation Portal (ERAD)](https://fatoora.zatca.gov.sa/), go to the Onboarding and Management Portal by selecting the relevant tile.
2. On the main landing page of the Onboarding and Management Portal, select the **Onboard new solution unit/device** tile, and then select **Generate OTP code**.
3. Select the number of one-time password (OTP) codes to generate. The number depends on the number of e-invoicing generation units (devices) that will be used.
4. Save the generated OTP codes so that you can use them in later steps.
5. Prepare a configuration file for the certificate signing request. This configuration file should be in the form of a plain text file that contains the following data.

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
    default_md = sha 256
    req_extensions = req_ext
    distinguished_name = dn
    [dn]
    C=SA
    OU=Riyad Branch
    O=Contoso
    CN=EA123456789
    [v3_req]
    basicConstraints = CA:FALSE
    keyUsage = digitalSignature, nonRepudiation, keyEncipherment
    [req_ext]
    certificateTemplateName = ASN1:PRINTABLESTRING:TSTZATCACodeSigning
    subjectAltName = dirName:alt_names
    [alt_names]
    SN=1-TST|2-TST|3-ed22f1d8-e6a2-1118-9b58-d9a8f11e445f
    UID=310122393500003
    title=1100
    registeredAddress= MyAddress
    businessCategory=Industry
    ```

6. In the configuration file, update the **emailAddress** value and the following specific data.

    | Code              | Description | Specification |
    |-------------------|-------------|---------------|
    | C                 | The country/region code. | A two-letter code (ISO 3166 Alpha-2) |
    | OU                | The name of the organization unit. | For normal taxpayers, the value is free text. For VAT groups, identify the value through the eleventh digit of the organization identifier being "1". Validate that the input is a 10-digit Tax Identification Number (TIN). |
    | O                 | The name of the organization or taxpayer. | Free text |
    | CN                | The unique name of the solution or unit. | Free text |
    | SN                | The unique identification code for the solution. | Free text |
    | UID               | The VAT registration number of the taxpayer. | Fifteen digits. This number begins with "3" and ends with "3". |
    | title             | The document type that the taxpayer's solution unit will issue. | Four-digit numerical input that uses "0" and "1" mapped to "TSCZ": 0 = False/Not supported, 1 = True/Supported. T = Tax invoice (standard), S = Simplified tax invoice, C = For future use, Z = For future use. |
    | registeredAddress | The address of the branch or location where the device or solution unit is primarily situated. | Free text |
    | businessCategory  | The industry or sector that the device or solution will generate invoices for. | Free text |

7. Run the [onboarding script](#script) that is provided later in this article. Specify the OTP and configuration file as input parameters. Here is an example:

    `.\OnboardingScript.ps1 -action getComplianceCSID -otp 123345 -csrconfig .\csr_config.txt -password 123`

    > [!NOTE]
    > The **password** parameter is optional and can be omitted. If it's included, the certificate that is generated will have the specified password.

8. The CCSID is received as a certificate file in PFX format. Save this CCSID certificate file in the Microsoft Azure key vault. For more information, see [Customer certificates and secrets](e-invoicing-customer-certificates-secrets.md).
9. Configure the related feature setup in the **Saudi Arabian electronic invoice (SA)** electronic invoicing feature, and reference the CCSID certificate that you saved in the key vault. The certificate will be used for communication with the ZATCA electronic invoicing portal.

### Compliance check

After obtaining Compliance CSID using the PowerShell script, ZATCA requires completion of certain compliance checks by submitting sample invoices. This step is a prerequisite for requesting a Production CSID.

Ensure that all types of sample invoices that were configured in the Certificate Signing Request (CSR) configuration file, are successfully submitted to ZATCA (refer Note for more information). Use the standard process for issuing electronic invoices. For more information, see [Issue electronic invoices in Finance and Supply Chain Management](e-invoicing-issuing-electronic-invoices-finance-supply-chain-management.md).

To do so, use the **"Saudi Arabian ZATCA compliance check (SA)"** feature in RCS and follow the steps mentioned under the Country Specific Configuration section of [Get Started with Electronic invoicing for Saudi Arabia](e-invoicing-sa-get-started.md) along with using of the obtained Compliance CSID.

Once compliance checks are successfully completed, the PowerShell script can be used to obtain Production CSID (refer on-boarding script).

> [!NOTE]
> If the document type (field: title) in the configuration file is set to "1000", then 3 sample invoices need to be submitted for the compliance check:
> 1. Standard Tax Invoice
> 2. Standard Debit Note
> 3. Standard Credit Note
> 
> If the document type (field: title) in the configuration file is set to "0100", then 3 sample invoices need to be submitted for the compliance check:
> 1. Simplified Tax Invoice
> 2. Simplified Debit Note
> 3. Simplified Credit Note
> 
> If is set to "1100", then all 6 sample invoices need to be submitted for the compliance check.

### Obtain a PCSID

To obtain a PCSID, you must correctly configure the solution for electronic invoice generation and submission, and the solution must be fully functioning. To achieve this result, you must complete all the required preliminary configuration steps. For more information, see [Get started with Electronic invoicing for Saudi Arabia](e-invoicing-sa-get-started.md).

1. Make sure that all electronic invoices are successfully submitted to ZATCA.
2. Run the [onboarding script](#script) that is provided later in this article. Specify the CCSID as an input parameter. Here is an example:

    `.\OnboardingScript.ps1 -action getProductionCSID -password 123`

    > [!NOTE]
    > The **password** parameter is optional and can be omitted. If it's included, the certificate that is generated will have the specified password.

3. The PCSID is received as a certificate file in PFX format. Save this PCSID certificate file in the key vault.
4. Configure the related feature setup in the **Saudi Arabian electronic invoice (SA)** electronic invoicing feature. Replace the previously configured CCSID certificate with the obtained CCSID certificate that you saved in the key vault.

After you complete all the configurations steps, the system is ready to be used in production mode.

To review obtained CSIDs on the ZATCA side, use the **Review Existing Cryptographic Stamp Identifier (CSID)** tile on the landing page of the Onboarding and Management Portal. This portal is accessible from the main [Saudi Arabian Taxation Portal (ERAD)](https://fatoora.zatca.gov.sa/).

## <a id="script"></a>Onboarding script

> [!NOTE]
> The sample scripts aren't supported under any Microsoft standard support program or service. The sample scripts are provided AS IS without warranty of any kind. Microsoft further disclaims all implied warranties including, without limitation, any implied warranties of merchantability or of fitness for a particular purpose. The entire risk arising out of the use or performance of the sample scripts and documentation remains with you. In no event shall Microsoft, its authors, or anyone else involved in the creation, production, or delivery of the scripts be liable for any damages whatsoever (including, without limitation, damages for loss of business profits, business interruption, loss of business information, or other pecuniary loss) arising out of the use of or inability to use the sample scripts or documentation, even if Microsoft has been advised of the possibility of such damages.

1. Use the following Windows PowerShell script to obtain a CCSID and a PCSID.

    ```powershell
    param($action, $otp, $csrconfig, $password)
    $env:path = $env:path + ";C:\Program Files\Git\usr\bin"
    
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
               "Content-Type"="application/json"}

        try
        {
            #Change URL to Zatca production URL when officially onboarding
            $response = Invoke-WebRequest -Uri 'https://gw-apic-gov.gazt.gov.sa/e-invoicing/developer-portal/compliance' -Method POST -Body $postParams -Headers $postHeader 
        }
        catch
        {
            Write-Host "Zatca service communication error:"
            Write-Host $_.Exception.Message 
            Write-Host "Please make sure the OTP code in script parameter and Serial Number (SN) in configuration file are valid."
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
            Write-Host "Compliance CSID received from Zatca:"
            Write-Host $CCSIDbase64
            $CCSID = [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($CCSIDbase64))
            $CCSIDCertString = "-----BEGIN CERTIFICATE-----`n" + $CCSID + "`n" + "-----END CERTIFICATE-----"

            $CCSIDStringFileName = "CCSIDString.txt"
            $CCSIDCertFileName = "CCSID.pem"
            $CCSIDFolderPath = Get-Location
            $CCSIDCertFilePath = Join-Path $CCSIDFolderPath $CCSIDCertFileName
            $CCSIDStringFilePath = Join-Path $CCSIDFolderPath $CCSIDStringFileName

            $Utf8NoBomEncoding = New-Object System.Text.UTF8Encoding $False
            [System.IO.File]::WriteAllLines($CCSIDCertFilePath, $CCSIDCertString, $Utf8NoBomEncoding)
            [System.IO.File]::WriteAllLines($CCSIDStringFilePath, $CCSIDbase64, $Utf8NoBomEncoding)

            openssl pkcs12 -inkey privatekey.pem -in CCSID.pem -export -passout pass:$password -out CCSID.pfx
            Write-Host "Certificate is saved to CCSID.pfx file."
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

        $requestId = Get-Content -path requestId.txt -Raw
        $requestId = $requestId -replace "`n",""
        $requestId = $requestId -replace "`r",""
        Write-Host "Request ID for PCSID is:" $requestId
        $CCSID = Get-Content -path CCSIDString.txt -Raw
        $CCSID = $CCSID -replace "`n",""
        $CCSID = $CCSID -replace "`r",""
        Write-Host "Compliance CSID received from Zatca:"
        Write-Host $CCSID

        #Init request for Production CSID (PCSID)
        $postParams = @{"compliance_request_id"=$requestId} | ConvertTo-Json
        $postHeader = @{
               "Accept"="application/json"
               "currentCCSID"=$CCSID
               "Content-Type"="application/json"}

        try
        {
            #Change URL to Zatca production URL when officially onboarding
            $response = Invoke-WebRequest -Uri 'https://gw-apic-gov.gazt.gov.sa/e-invoicing/developer-portal/production/csids' -Method POST -Body $postParams -Headers $postHeader
        }
        catch
        {
            Write-Host "Zatca service communication error:"
            Write-Host $_.Exception.Message 
            Write-Host "Please make sure the compliance check process has been done before obtaining a Production CSID (PCSID)."
            Write-Host "The process of obtaining a Production CSID (PCSID) is interrupted."
        }

        if ($response -ne $null)
        {
            $response = $response | ConvertFrom-Json
            $PCSIDbase64 = $response.binarySecurityToken
            Write-Host "Production CSID received from Zatca:"
            Write-Host $PCSIDbase64

            $PCSID = [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($PCSIDbase64))
            $PCSIDCertString = "-----BEGIN CERTIFICATE-----`n" + $PCSID + "`n" + "-----END CERTIFICATE-----"

            $PCSIDCertFileName = "PCSID.pem"
            $PCSIDCertFilePath = Get-Location
            $PCSIDCertFilePath = Join-Path $PCSIDCertFilePath $PCSIDCertFileName

            $Utf8NoBomEncoding = New-Object System.Text.UTF8Encoding $False
            [System.IO.File]::WriteAllLines($PCSIDCertFilePath, $PCSIDCertString, $Utf8NoBomEncoding)

            # Sandbox API will get error: openssl : No certificate matches private key
            openssl pkcs12 -inkey privatekey.pem -in PCSID.pem -export -passout pass:$password -out PCSID.pfx

            if (Test-Path -Path PCSID.pfx)
            {
                Write-Host "Certificate is saved to PCSID.pfx file."
                Write-Host "The process of obtaining a Production CSID (PCSID) is complete."
            }
            else
            {
                Write-Host "The process of obtaining a Production CSID (PCSID) is interrupted."
            }
        }
    } 
    ```

2. Save the output .pfx certificate file that is received in the key vault.

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
