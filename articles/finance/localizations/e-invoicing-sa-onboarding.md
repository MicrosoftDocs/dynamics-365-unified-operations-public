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

Onboarding is mandatory for all taxpayers who are subjects to electronic invoicing in Saudi Arabia. As the result of onboarding process, taxpayers will obtain Cryptographic Stamp Identifiers (**CSID**) which are required for integration with electronic invoicing portal managed by Saudi Arabian Tax authority (**ZATCA**) and further electronic invoices submission.
This topic provides information about onboarding process for taxpayers and their electronic invoicing software by Saudi Arabian tax authorities.

## Prerequisites

- The legal entity must be registered as a Taxpayer in Saudi Arabia and have a valid VAT registration number.
- The legal entity must have the access to Saudi Arabian Taxation Portal - [ERAD](https://fatoora.zatca.gov.sa/) 

## Onboarding process

Onboarding process consist of 2 parts:
1. Obtaining Compliance CSID (**CCSID**) which is initially assigned by ZATCA to perform compliance checks of Electronic invoices Generation Solutions (**EGS**).
2. Obtaining Production CSID (**PCSID**) which is finally assigned by ZATCA to compliant electronic invoices generation solutions.

### Obtaining Compliance CSID

1. In the Taxation Portal (**ERAD**), navigate to the Onboarding and Management Portal by clicking on the relevant tile.
2. On the main landing page of the Onboarding and Management Portal select the **Onboard new solution unit/device** tile and then click on 
**Generate OTP code**.
3. Choose to the number of **OTP** (*on-time password*) codes to be generated. The number depends on how many e-invoicing generation units (devices) will be used.
4. Save the generated OTP codes to be used on the next steps.
5. Prepare a configuration file for Certificate Signing Request in a form of a plain text file which should contain the following data:

    ```powershell
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
    SN=MSD365Finance10028
    UID=310122393500003
    title=1100
    registeredAddress= MyAddress
    businessCategory=Industry
    ```

    In the configuration file, update the **emailAddress** and the following specific data:

    | Code                             | Description | Specification |
    |----------------------------------|-------------|-------------|
    | C                    | Country code | 2 letter code (ISO 3166 Alpha-2)  |
    | OU                    | Organization Unit name| Free text in the case of normal taxpayer; in the case of VAT Groups identify this through the 11th digit of Organization Identifier being ‘1’. Run a validation that the input is a 10-digit TIN |
    | O                    | Organization/Taxpayer Name  | Free text |
    | CN                    | Unique Name of the Solution or Unit | Free text |
    | SN                    | Unique identification code for the solution | Free text |
    | UID                   | VAT Registration Number of the Taxpayer | 15 digits; begins with 3 and ends with 3 |
    | title                 | The document type that the Taxpayer’s solution unit will be issuing | 4-digit numerical input using 0 & 1 mapped to “TSCZ”: 0 = False/Not supported, 1= True/Supported. T= Tax invoice (Standard), S = Simplified Tax Invoice, C= “for future use”, Z = “for future use” |
    | registeredAddress     | The address of the Branch or location where the device or solution unit is primarily situated | Free text |
    | businessCategory | Industry or sector for which the device or solution will generate invoices| Free text|

### Obtaining Production CSID
Text [Customer certificates and secrets](e-invoicing-customer-certificates-secrets.md). 

> [!NOTE]
> Some .

   ![Property type added on the Electronic document property types page.](media/e-invoicing-pol-parameters.jpg)
   
   
## Onboarding script

1. Use the following Windows PowerShell script to obtain CCSID and PCSID.

    ```powershell
    param($otp, $csrconfig)
    $env:path = $env:path + ";C:\Program Files\Git\usr\bin"
    Invoke-Expression "openssl ecparam -name secp256k1 -genkey -noout -out privatekey.pem"
    Write-Host "Private key generated"
    Invoke-Expression "openssl ec -in privatekey.pem -pubout -conv_form compressed -out publickey.pem"
    Write-Host "Public key generated"
    Invoke-Expression "openssl base64 -d -in publickey.pem -out publickey.bin"
    Invoke-Expression "openssl req -new -sha256 -key privatekey.pem -extensions v3_req -config <csrconfig> -out .\taxpayer.csr".replace('<csrconfig>', $csrconfig)
    Invoke-Expression "openssl base64 -in taxpayer.csr -out text.txt"
    $Text = Get-Content -path text.txt -Raw
    $Text = $Text -replace "`n",""
    $postParams = @{"csr"=$Text} | ConvertTo-Json
    
    $postHeader = @{
	    "Accept"="application/json"
	    "OTP"=$otp
	    "Content-Type"="application/json"}
	    
    $response = Invoke-WebRequest -Uri 'https://gw-apic-gov.gazt.gov.sa/e-invoicing/developer-portal/compliance' -Method POST -Body $postParams -Headers $postHeader 
    
    if ($response.StatusCode -eq 200)
    {
	    $response = $response | ConvertFrom-Json
	    $requestId = $response.requestID
	    $bst = $response.binarySecurityToken
	    
	    $postHeader = @{
		    "Accept"="application/json"
		    "Authentication-Certificate"=$bst
		    "Accept-Language"="en"
		    "Content-Type"="application/json"}
		    
	    $invoiceText = Get-Content -path invoice.txt -Raw
	    $invoiceText = $invoiceText -replace "`n",""
	    $uuid = "3cf5ee18-ee25-44ea-a444-2c37ba7f28be" #[guid]::NewGuid().ToString()
	    $postParams = @{"invoiceHash"="9ZUyaT5frZko5fHO09jYj0T2A/Kd77sIn1V3knLVAso=";"uuid"=$uuid;"invoice"=$invoiceText} | ConvertTo-Json
	    #$response = Invoke-WebRequest -Uri 'https://gw-apic-gov.gazt.gov.sa/e-invoicing/developer-portal/compliance/invoices' -Method POST -Body $postParams -Headers      $postHeader 
	
	if (1 -eq 1) #$response.StatusCode -eq 200)
	{
		Write-Host "Successfully submitted test invoice."
		Write-Host "Requesting for production BST."
		
		$postHeader = @{
			"Accept"="application/json"
			"currentCCSID"=$bst
			"Content-Type"="application/json"}
		$postParams = @{"compliance_request_id"=$requestID} | ConvertTo-Json
		$response = Invoke-WebRequest -Uri 'https://gw-apic-gov.gazt.gov.sa/e-invoicing/developer-portal/production/csids' -Method POST -Body $postParams -Headers    $postHeader 
		
		   if ($response.StatusCode -eq 200)
		   {
			   Write-Host "Successfully obtained production BST:"
			   $response = $response | ConvertFrom-Json
			   Write-Host $response.binarySecurityToken
		   }
			   else
		   {
			   Write-Host "Production BST request failed."
			   Write-Host $response.StatusCode
			   Write-Host $response.StatusDescription
		   }
	   }
	   else
	   {
		   Write-Host "Test invoice submission failure."
		   Write-Host $response.StatusCode
		   Write-Host $response.StatusDescription
	   }
   }
   else
   {
	   Write-Host $response.StatusCode
	   Write-Host $response.StatusDescription
   }
    ```

2. Save the .pfx certificate file to the key vault.

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
