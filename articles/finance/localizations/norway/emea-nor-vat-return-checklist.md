---
title: Checklist for Electronic messages setup for VAT returns with direct submission to Altinn
description: Access a checklist for setting up Electronic messages functionality for VAT returns of Norway, including an outline on web applications.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: article
ms.date: 02/09/2024
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Norway
ms.search.validFrom: 2021-11-18
ms.dyn365.ops.version: AX 10.0.22
---

# Checklist for Electronic messages setup for VAT returns with direct submission to Altinn

[!include [banner](../../includes/banner.md)]

This article provides information about how the [Electronic messages](../../general-ledger/electronic-messaging.md) functionality is set up to support the processing of value-added tax (VAT) returns with direct submission to Altinn in Norway. You can use the information in this article to determine whether the Electronic messages functionality is correctly set up.

Although this article includes the most important information about the setup, it doesn't include information about all the data. We recommend that you use a package of data entities that contains a predefined setup of the functionality, and that includes all the data that is required to set up the processing for interoperation with Altinn.

- Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic messages processing**, and review your setup. The following type of processing is defined to support interoperation with Altinn.

    | Processing | Name (Norwegian) | Description |
    |---|---|---|
    | NO VAT return | Momsoppgave med direkte innsending | The processing to prepare and submit VAT returns to Altinn. |

    > [!IMPORTANT]
    > To enable access at the record level for business users, you must define security roles for the processing.

## Web applications

- Go to **Tax** \> **Setup** \> **Electronic messages** \> **Web applications**, and review your setup. The **NO VAT return** processing uses the following web applications.

    | Application name | Description |
    |---|---|
    | NO Altinn | Web application for interoperation with Altinn application programming interfaces (APIs). |
    | NO ID-Porten | Web application for interoperation with the integration point that you created in ID-porten. |

The following table shows the web application parameters that the **NO VAT return** processing uses to interoperate with the ***sandbox APIs*** that the Norwegian Tax Administration provides.

| Parameter | Value for NO Altinn | Value for NO ID-Porten |
|---|---|---|
| Base URL | `https://platform.tt02.altinn.no/authentication/api/v1/exchange/id-porten` | **Blank** |
| Authorization URL path | Blank | `https://login.test.idporten.no/authorize` |
| Token URL path | Blank | `https://test.idporten.no/token` |
| Redirect URL | Blank | Set up the value according to the information in [Set up the internet address of ID-porten and Altinn web services](emea-nor-vat-return-setup.md#internet-address). |
| Authorization format mapping | **Altinn VAT authorization format (NO)** | **Altinn VAT authorization format (NO)** |
| Import token model mapping | **Altinn VAT import Altinn token format (NO)** | **Altinn VAT import ID-Porten token format (NO)** |
| Accept | Blank | Blank |
| Content type | **application/json** | **application/x-www-form-urlencoded** |

> [!IMPORTANT]
> To enable access to the access token and interoperation with ID-porten and Altinn APIs for business users, you must define security roles for both web applications.

Internet addresses (base URLs, Authorization URL path, and Token URL path) are subject to change by the Norwegian Tax Administration. We recommend that you check for actual internet addresses on the official Altinn and ID-porten website. For actual internet addresses of the sandbox setup of the **NO ID-Porten** web application, go to <https://test.idporten.no/.well-known/openid-configuration>. For the production setup of the **NO ID-Porten** web application, go to <https://idporten.no/.well-known/openid-configuration>.

## Web service settings

- Go to **Tax** \> **Setup** \> **Electronic messages** \> **Web service settings**, and review your setup. The **NO VAT return** processing uses the following web services:

    - NO Altinn GET attachments
    - NO Altinn GET JSON
    - NO Altinn POST JSON
    - NO Altinn POST XML
    - NO Altinn PUT JSON
    - NO Altinn PUT XML
    - NO Validate VAT return

The following tables show the parameters and parameter values for the web services that the **NO VAT return** processing uses to interoperate with the *sandbox APIs* that the Norwegian Tax Administration provides.

### Web service: NO Altinn GET attachments

| Parameter name | Parameter value |
|---|---|
| Web service | **NO Altinn GET attachments** |
| Description | **Altinn web service for GET attachments downloaded (XML, PDF)** |
| Internet address | Blank |
| Web application | **NO Altinn** |
| Use proxy server | **No** |
| Use advanced parameters | Blank |
| Certificate | Blank |
| The response type – XML | **No** |
| Request method | **GET** |
| Accept | Blank |
| Accept encoding | Blank |
| Request headers | Blank |
| Content type | Blank |
| Request header format mapping | **Altinn VAT web request headers format (NO)** |
| Successful response code | **200** |

### Web service: NO Altinn GET JSON

| Parameter name | Parameter value |
|---|---|
| Web service | **NO Altinn GET JSON** |
| Description | **Altinn web service for GET requests of JSON type of content** |
| Internet address | `https://skd.apps.tt02.altinn.no/skd/mva-melding-innsending-etm2/instances` |
| Web application | **NO Altinn** |
| Use proxy server | **No** |
| Use advanced parameters | Blank |
| Certificate | Blank |
| The response type – XML | **No** |
| Request method | **GET** |
| Accept | **application/json** |
| Accept encoding | Blank |
| Request headers | Blank |
| Content type | Blank |
| Request header format mapping | **Altinn VAT web request headers format (NO)** |
| Successful response code | **200** |

For *production* interoperation, use the following internet address: `https://skd.apps.altinn.no/skd/mva-melding-innsending-v1/instances`.

### Web service: NO Altinn POST JSON

| Parameter name | Parameter value |
|---|---|
| Web service | **NO Altinn POST JSON** |
| Description | **Altinn web service for POST requests of JSON type of content** |
| Internet address | `https://skd.apps.tt02.altinn.no/skd/mva-melding-innsending-etm2/instances` |
| Web application | **NO Altinn** |
| Use proxy server | **No** |
| Use advanced parameters | Blank |
| Certificate | Blank |
| The response type – XML | **No** |
| Request method | **POST** |
| Accept | Blank |
| Accept encoding | Blank |
| Request headers | Blank |
| Content type | **application/json** |
| Request header format mapping | **Altinn VAT web request headers format (NO)** |
| Successful response code | **201** |

For *production* interoperation, use the following internet address: `https://skd.apps.altinn.no/skd/mva-melding-innsending-v1/instances`.

### Web service: NO Altinn POST XML

| Parameter name | Parameter value |
|---|---|
| Web service | **NO Altinn POST XML** |
| Description | **Altinn web service for POST requests of XML type of content** |
| Internet address | `https://skd.apps.tt02.altinn.no/skd/mva-melding-innsending-etm2/instances` |
| Web application | **NO Altinn** |
| Use proxy server | **No** |
| Use advanced parameters | Blank |
| Certificate | Blank |
| The response type – XML | **No** |
| Request method | **POST**|
| Accept | Blank |
| Accept encoding | Blank |
| Request headers | Blank |
| Content type | **text/xml** |
| Request header format mapping | **Altinn VAT web request headers format (NO)** |
| Successful response code | **201** |

For *production* interoperation, use the following internet address: `https://skd.apps.altinn.no/skd/mva-melding-innsending-v1/instances`.

### Web service: NO Altinn PUT JSON

| Parameter name | Parameter value |
|---|---|
| Web service | **NO Altinn PUT JSON** |
| Description | **Altinn web service for PUT requests of JSON type of content** |
| Internet address | `https://skd.apps.tt02.altinn.no/skd/mva-melding-innsending-etm2/instances` |
| Web application | **NO Altinn** |
| Use proxy server | **No** |
| Use advanced parameters | Blank |
| Certificate | Blank |
| The response type – XML | **No** |
| Request method | **PUT** |
| Accept | Blank |
| Accept encoding | Blank |
| Request headers | Blank |
| Content type | **application/json** |
| Request header format mapping | **Altinn VAT web request headers format (NO)** |
| Successful response code | **200** |

For *production* interoperation, use the following internet address: `https://skd.apps.altinn.no/skd/mva-melding-innsending-v1/instances`.

### Web service: NO Altinn PUT XML

| Parameter name | Parameter value |
|---|---|
| Web service | **NO Altinn PUT XML** |
| Description | **Altinn web service for PUT requests of XML type of content** |
| Internet address | `https://skd.apps.tt02.altinn.no/skd/mva-melding-innsending-etm2/instances` |
| Web application | **NO Altinn** |
| Use proxy server | **No** |
| Use advanced parameters | Blank |
| Certificate | Blank |
| The response type – XML | **No** |
| Request method | **PUT** |
| Accept | Blank |
| Accept encoding | Blank |
| Request headers | Blank |
| Content type | **application/xml** |
| Request header format mapping | **Altinn VAT web request headers format (NO)** |
| Successful response code | **201** |

For *production* interoperation, use the following internet address: `https://skd.apps.altinn.no/skd/mva-melding-innsending-v1/instances`.

### Web service: NO Validate VAT return

| Parameter name | Parameter value |
|---|---|
| Web service | **NO Validate VAT return** |
| Description | **Web service of Tax Administration to validate VAT return** |
| Internet address | `https://mp-test.sits.no/api/mva/grensesnittstoette/mva-melding/valider` |
| Web application | **NO ID-Porten** |
| Use proxy server | **No** |
| Use advanced parameters | Blank |
| Certificate | Blank |
| The response type – XML | **No** |
| Request method | **POST** |
| Accept | Blank |
| Accept encoding | Blank |
| Request headers | Blank |
| Content type | **application/xml** |
| Request header format mapping | **Altinn VAT web request headers format (NO)** |
| Successful response code | **200** |

For *production* interoperation, use the following internet address: `https://idporten.api.skatteetaten.no/api/mva/grensesnittstoette/mva-melding/valider`.

## Additional fields

- Go to **Tax** \> **Setup** \> **Electronic messages** \> **Additional fields**, and review your setup. The **NO VAT return** processing uses the following additional fields.

    | Field | Description (Norwegian) | User edit | Counter | Hidden |
    |---|---|---|---|---|
    | NO VAT Data GUID | Data GUID | No | No | Yes |
    | NO VAT Instance GUID | Instans-GUID | No | No | Yes |
    | NO VAT Note for VAT return | Merknad på meldingsnivå: har en kan velge mellom en predefinert liste av merknader eller fylle ut fritekst | Yes | No | No |
    | NO VAT Party ID | Part ID | No | No | Yes |
    | NO VAT Payment information | Betalingsinformasjon | No | No | Yes |
    | NO VAT Receipt | Kvittering | No | No | Yes |
    | NO VAT Validation result | Valideringsresultat | No | No | Yes |
    | Tax registration number | Skatteregistreringsnummer | No | No | Yes |
    | NO VAT Payment ID | KundeIdentifikasjonsnummer. Nummer som brukes ved regningsbetaling i Norge for å identifisere kunden og fakturaen, KID-nummer. | Yes | No | No |

    > [!NOTE]
    > The user can't change the setting of any of these fields.

## Electronic message item types

- Go to **Tax** \> **Setup** \> **Electronic messages** \> **Message item types**, and review your setup. The **NO VAT return** processing uses one type of electronic message item: **NO VAT return**.

## Electronic message item statuses

- Go to **Tax** \> **Setup** \> **Electronic messages** \> **Message item statuses**, and review your setup. The **NO VAT return** processing uses the following electronic message item statuses.

    | Status | Description | Allow delete |
    |---|---|---|
    | NO VAT Collected | Sales tax payment record included for VAT return (Momsregistrering inkludert for mva-retur). | Yes |
    | NO VAT Excluded | Sales tax payment excluded from VAT return (Innbetaling av merverdiavgift ekskludert fra mva ). | Yes |
    | To be reported | Sales tax payment record ready for VAT return (Momsregistrering er klar for merverdiavgift). | No |

## Electronic message statuses

- Go to **Tax** \> **Setup** \> **Electronic messages** \> **Message statuses**, and review your setup. The **NO VAT return** processing uses the following electronic message statuses.

    | Status | Description (Norwegian) | Response type | Allow delete |
    |---|---|---|---|
    | NO VAT Error completion of VAT return submission | Feil ved gjennomføring av innsending av mva | TechnicalError | No |
    | NO VAT Error file download | Feil nedlasting av fil | TechnicalError | No |
    | NO VAT Error generation of instance request | Feil generering av forespørsel | TechnicalError | No |
    | NO VAT Error generation of VAT return submission | Feil generering av momsoppgave | TechnicalError | No |
    | NO VAT Error importing create instance response | Feil under import av opprettelsesforekomster | TechnicalError | No |
    | NO VAT Error importing of feedback | Tilbakemelding ved importfeil | TechnicalError | No |
    | NO VAT Error importing of feedback status response | Feil ved import av tilbakemeldingsstatusrespons | TechnicalError | No |
    | NO VAT Error importing of final validation result | Feil ved import av endelig valideringsresultat | TechnicalError | No |
    | NO VAT Error importing VAT return validation result | Feil under import av mva-returvalideringsresultat | TechnicalError | No |
    | NO VAT Error of data filling completion | Feil ved fullføring av data | TechnicalError | No |
    | NO VAT Error of instance creation | Feil ved opprettelse av forekomst | BusinessError | No |
    | NO VAT Error sending request for feedback | Feil ved sending av forespørsel om tilbakemelding | TechnicalError | No |
    | NO VAT Error sending request for status of feedback | Feil ved sending av forespørsel om status for tilbakemelding | TechnicalError | No |
    | NO VAT Error sending request to create an instance | Feil ved sending av forespørsel for å opprette en forekomst | TechnicalError | No |
    | NO VAT Error sending VAT return validation request | Feil ved sending av forespørsel om validering av mva | TechnicalError | No |
    | NO VAT Error validation of uploaded VAT return | Feilvalidering av opplastet MVA-melding | BusinessError | No |
    | NO VAT Error VAT return generation | Mva-returgenereringsfeil | TechnicalError | Yes |
    | NO VAT Error VAT return uploading | Melding om opplasting av mva | TechnicalError | No |
    | NO VAT Error VAT return validation | Mva-returvalideringsfeil | BusinessError | No |
    | NO VAT Feedback imported | Tilbakemeldinger importert | Successful | No |
    | NO VAT Feedback not provided | Tilbakemelding tilbys ikke | Successful | No |
    | NO VAT Feedback provided | Tilbakemelding tilbys | Successful | No |
    | NO VAT Instance created | Forekomst opprettet | Successful | No |
    | NO VAT New message created | Ny elektronisk melding opprettet | Successful | Yes |
    | NO VAT Ready to generate VAT return | Klar til å generere mva | Successful | No |
    | NO VAT Return received by Tax Authority | Mva-meldingen er levert og mottatt av Skatteetaten | Successful | No |
    | NO VAT Return submission completed | Mva-returnering fullført | Successful | No |
    | NO VAT Return submission request generated | Mva-returinnleveringsforespørsel generert | Successful | No |
    | NO VAT Return submission uploaded successfully | Innlevering av merverdiavgift ble lastet opp | Successful | No |
    | NO VAT Return submission uploading error | Melding om returopplastingsfeil | TechnicalError | No |
    | NO VAT Return uploaded | Mva-retur lastet opp | Successful | No |
    | NO VAT Return validated and ready to upload | Momsangivelsen ble godkjent av Skatteetaten og klar til å lastes opp til Altinn | Successful | No |
    | NO VAT Return validation passed successfully | Mva-returvalidering bestått | Successful | No |
    | NO VAT Return XML generated | Mva-retur er vellykket generert i XML-format | Successful | Yes |
    | NO VAT Sent request for feedback | Sendt forespørsel om tilbakemelding | Successful | No |
    | NO VAT Sent request for status of feedback | Sendt forespørsel om status for tilbakemelding | Successful | No |
    | NO VAT Sent VAT return validation request | Returvalideringsforespørsel sendt | Successful | No |
    | NO VAT Successful download of final validation | Vellykket nedlasting av endelig validering | Successful | No |
    | NO VAT Successful file download | Last ned filen vellykket | Successful | No |
    | NO VAT Successful sending create instance request | Sendingen oppretter forespørsel om vellykket sending | Successful | No |
    | NO VAT SUCCESSFUL VAT return submission to the Tax Administr | MVA-meldingen lastet opp til Skatteetaten ble validert | Successful | No |

## Action populate records

- Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**, and review your setup. The **NO VAT return** processing uses one **NO VAT Collect sales tax payments** populate records action.

The following table shows the setup of the data source for the **NO VAT Collect sales tax payments** populate records action that the **NO VAT return** processing uses.

| Property | Value |
|---|---|
| Name | NO VAT return |
| Message item type | NO VAT return |
| Account type | All |
| Master table name | TaxReportVoucher |
| Document number field | Voucher |
| Document date field | TransDate |
| Document account field | TaxPeriod |
| User query | Yes |

> [!IMPORTANT]
> Define the settlement period by selecting **Edit query**. For more information, see [Define a sales tax settlement period](emea-nor-vat-return-setup.md#settlement-period).

## Electronic message actions

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**, and review your setup. The **NO VAT return** processing uses the following electronic message actions.

    | Order | Action | Description (Norwegian) | Inseparable sequence | Run separately |
    |---|---|---|---|---|
    | 1 | NO VAT Create message | Lag melding | Blank | **No** |
    | 2 | NO VAT Collect sales tax payments | Samle momsregistreringer for merverdiavgift | Blank | **No** |
    | 3 | NO VAT Ready to generate VAT return | Klar til å generere mva | Blank | **Yes** |
    | 4 | NO VAT Not ready to generate VAT return | Elektronisk melding er ikke klar til å generere merverdiavgi | Blank | **Yes** |
    | 5 | NO VAT Preview VAT return in Excel | Forhåndsvis mva-retur i Excel | Blank | **Yes** |
    | 6 | NO VAT Generate VAT return | Generer merverdiavgift i XML | **NO VAT Validation** | **Yes** | 
    | 7 | NO VAT Send validation request | Send forespørsel om validering | **NO VAT Validation** | **Yes** | 
    | 8 | NO VAT Import validation response | Import validering svar | **NO VAT Validation** | **No** |
    | 9 | NO VAT Generate request for instance | Generer forespørsel om å opprette forekomst | **NO VAT Validation** | **No** |
    | 10 | NO VAT Send request to create instance | Send forespørsel for å opprette forekomst | **NO VAT Submission** | **Yes** |
    | 11 | NO VAT Import instance creation response | Importer opprettelsessvar for forekomst | **NO VAT Submission** | **No** |
    | 12 | NO VAT Generate VAT return submission | Generer innsending av mva | **NO VAT Submission** | **No** |
    | 13 | NO VAT Upload VAT return submission | Last opp innsending av merverdiavgift | **NO VAT Submission** | **No** |
    | 14 | NO VAT Upload VAT return | Last opp mva-retur | **NO VAT Submission** | **No** |
    | 15 | NO VAT Complete data filling | Fullstendig datafylling | **NO VAT Submission** | **No** |
    | 16 | NO VAT Complete VAT return submission | Fullfør momsoppgaven | **NO VAT Submission** | **No** |
    | 17 | NO VAT Send feedback status request | Send statusforespørsel om tilbakemelding | **NO VAT Submission** | **No** |
    | 18 | NO VAT Import feedback status response | Importer tilbakemeldingsstatusrespons | **NO VAT Submission** | **No** |
    | 19 | NO VAT Send feedback request | Send forespørsel om tilbakemelding | **NO VAT Submission** | **No** |
    | 20 | NO VAT Import feedback response | Importer tilbakemeldingssvar | **NO VAT Submission** | **No** |
    | 21 | NO VAT Download validation result | Last ned valideringsresultat | **NO VAT Submission** | **No** |
    | 22 | NO VAT Import final validation result | Import endelig valideringsresultat | **NO VAT Submission** | **No** |
    | 23 | NO VAT Download payment information | Last ned betalingsinformasjon | Blank | **Yes** |
    | 24 | NO VAT Download receipt | Last ned kvittering | Blank | **Yes** |
    | 25 | NO VAT Exclude from VAT return | Innbetaling av merverdiavgift ekskludert fra mva | Blank | **Yes** |
    | 26 | NO VAT Include to VAT return | Inkluder betaling av omsetningsavgift til mva | Blank | **Yes** |

2. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Message processing actions**, and review your setup. The following parameters must be defined for the actions.

    | Action | Action type | Parameters |
    |---|---|---|
    | NO VAT Create message | Create message | <ul><li>**From statuses:** No</li><li>**To statuses:** NO VAT New message created</li></ul> |
    | NO VAT Collect sales tax payments | Populate records | <ul><li>**Populate records action:** NO VAT Collect sales tax payments</li><li>**From statuses:** NO VAT New message created</li><li>**To statuses:** NO VAT Collected</li></ul> |
    | NO VAT Ready to generate VAT return | Message level user processing | <ul><li>**From statuses:** NO VAT New message created</li><li>**To statuses:** NO VAT Ready to generate VAT return</li></ul> |
    | NO VAT Not ready to generate VAT return | Message level user processing | <ul><li>**From statuses:** NO VAT Ready to generate VAT return, NO VAT Return validated and ready to upload, NO VAT Return XML generated</li><li>**To statuses:** NO VAT New message created</li></ul> |
    | NO VAT Preview VAT return in Excel | Electronic reporting export message | <ul><li>**Message item type:** NO VAT return</li><li>**Format mapping:** VAT Declaration Excel (NO)</li><li>**From statuses:** NO VAT Error VAT return generation, NO VAT Error VAT return validation, NO VAT Ready to generate VAT return</li><li>**To statuses:** NO VAT Error VAT return generation, NO VAT Ready to generate VAT return</li></ul> |
    | NO VAT Generate VAT return | Electronic reporting export message | <ul><li>**File name:** mvamelding</li><li>**Message item type:** NO VAT return</li><li>**Format mapping:** VAT Declaration XML (NO)</li><li>**From statuses:** NO VAT Error sending VAT return validation request, NO VAT Error validation of uploaded VAT return, NO VAT Error VAT return generation, NO VAT Error VAT return validation, NO VAT Ready to generate VAT return, NO VAT Return XML generated</li><li>**To statuses:** NO VAT Return XML generated, NO VAT Error VAT return generation</li></ul> |
    | NO VAT Send validation request | Web service | <ul><li>**Web service:** NO Validate VAT return</li><li>**File name:** valideringsresultat.xml</li><li>**File name to send:** mvamelding.xml</li><li>**From statuses:** NO VAT Error sending VAT return validation request, NO VAT Error VAT return validation, NO VAT Return XML generated</li><li>**To statuses:** NO VAT Error sending VAT return validation request, NO VAT Sent VAT return validation request</li></ul> |
    | NO VAT Import validation response | Electronic reporting import | <ul><li>**Model mapping:** Altinn VAT import validation result format (NO)</li><li>**From statuses:** NO VAT Error importing VAT return validation result, NO VAT Sent VAT return validation request</li><li>**To statuses:** NO VAT Error importing VAT return validation result, NO VAT Error VAT return validation, NO VAT Return validation passed successfully</li></ul> |
    | NO VAT Generate request for instance | Electronic reporting export message | <ul><li>**File name:** createInstanceRequest.json</li><li>**Format mapping:** Altinn VAT interoperation (NO)</li><li>**From statuses:** NO VAT Error generation of instance request, NO VAT Error of instance creation, NO VAT Error sending request to create an instance, NO VAT Return validation passed successfully</li><li>**To statuses:** NO VAT Error generation of instance request, NO VAT Return validated and ready to upload</li></ul> |
    | NO VAT Send request to create instance | Web service | <ul><li>**File name:** createInstanceResponse.json</li><li>**Web service:** NO Altinn POST JSON</li><li>**From statuses:** NO VAT Error sending request to create an instance, NO VAT Return validated and ready to upload</li><li>**To statuses:** NO VAT Error sending request to create an instance, NO VAT Successful sending create instance request</li></ul> |
    | NO VAT Import instance creation response | Electronic reporting import | <ul><li>**Model mapping:** Altinn VAT import instance format (NO)</li><li>**From statuses:** NO VAT Error importing create instance response, NO VAT Successful sending create instance request</li><li>**To statuses:** NO VAT Error importing create instance response, NO VAT Error of instance creation, NO VAT Instance created</li></ul> |
    | NO VAT Generate VAT return submission | Electronic reporting export message | <ul><li>**File name:** konvolutt.xml</li><li>**Format mapping:** VAT Declaration XML (NO)</li><li>**From statuses:** NO VAT Error generation of VAT return submission, NO VAT Instance created</li><li>**To statuses:** NO VAT Error generation of VAT return submission, NO VAT Return submission request generated</li></ul> |
    | NO VAT Upload VAT return submission | Web service | <ul><li>**Format mapping for URL path:** Altinn VAT interoperation (NO)</li><li>**Web service:** NO Altinn PUT XML</li><li>**File name:** uploadVATReturnSubmissionResponse.json</li><li>**From statuses:** NO VAT Return submission request generated, NO VAT Return submission uploading error</li><li>**To statuses:** NO VAT Return submission uploaded successfully, NO VAT Return submission uploading error</li></ul> |
    | NO VAT Upload VAT return | Web service | <ul><li>**Format mapping for URL path:** Altinn VAT interoperation (NO)</li><li>**Web service:** NO Altinn POST XML</li><li>**File name:** uploadVATReturnResponse.json</li><li>**File name to send:** mvamelding.xml</li><li>**From statuses:** NO VAT Error VAT return uploading, NO VAT Return submission uploaded successfully</li><li>**To statuses:** NO VAT Error VAT return uploading, NO VAT Return uploaded</li></ul> |
    | NO VAT Complete data filling | Web service | <ul><li>**Format mapping for URL path:** Altinn VAT interoperation (NO)</li><li>**Web service:** NO Altinn PUT JSON</li><li>**File name:** completeDataFillingResponse.json</li><li>**File name to send:** *Not applicable*</li><li>**From statuses:** NO VAT Error of data filling completion, NO VAT Return uploaded</li><li>**To statuses:** NO VAT Data filling completed, NO VAT Error of data filling completion</li></ul> |
    | NO VAT Complete VAT return submission | Web service | <ul><li>**Format mapping for URL path:** Altinn VAT interoperation (NO)</li><li>**Web service:** NO Altinn PUT JSON</li><li>**File name:** completeVATReturnSubmissionResponse.json</li><li>**File name to send:** *Not applicable*</li><li>**From statuses:** NO VAT Data filling completed, NO VAT Error completion of VAT return submission</li><li>**To statuses:** NO VAT Error completion of VAT return submission, NO VAT Return submission completed</li></ul> |
    | NO VAT Send feedback status request | Web service | <ul><li>**Format mapping for URL path:** Altinn VAT interoperation (NO)</li><li>**Web service:** NO Altinn GET JSON</li><li>**File name:** feedbackStatusResponse.json</li><li>**File name to send:** *Not applicable*</li><li>**From statuses:** NO VAT Error sending request for status of feedback, NO VAT Feedback not provided, NO VAT Return submission completed</li><li>**To statuses:** NO VAT Error sending request for status of feedback, NO VAT Sent request for status of feedback</li></ul> |
    | NO VAT Import feedback status response | Electronic reporting import | <ul><li>**Model mapping:** Altinn VAT import feedback status format (NO)</li><li>**From statuses:** NO VAT Error importing of feedback status response, NO VAT Sent request for status of feedback</li><li>**To statuses:** NO VAT Error importing of feedback status response, NO VAT Feedback not provided, NO VAT Feedback provided</li></ul> |
    | NO VAT Send feedback request | Web service | <ul><li>**Format mapping for URL path:** Altinn VAT interoperation (NO)</li><li>**Web service:** NO Altinn GET JSON</li><li>**File name to send:** *Not applicable*</li><li>**File name:** feedbackResponse.json</li><li>**From statuses:** NO VAT Error sending request for feedback, NO VAT Feedback provided</li><li>**To statuses:** NO VAT Error sending request for feedback, NO VAT Sent request for feedback</li></ul> |
    | NO VAT Import feedback response | Electronic reporting import | <ul><li>**Model mapping:** Altinn VAT import instance format (NO)</li><li>**From statuses:** NO VAT Error importing of feedback, NO VAT Sent request for feedback</li><li>**To statuses:** NO VAT Error importing of feedback, NO VAT Feedback imported, NO VAT Return received by Tax Authority</li></ul> |
    | NO VAT Download validation result | Web service | <ul><li>**Format mapping for URL path:** Altinn VAT interoperation (NO)</li><li>**Web service:** NO Altinn GET attachments</li><li>**File name:** valideringsresultat.xml</li><li>**File name to send:** *Not applicable*</li><li>**From statuses:** NO VAT Error file download, NO VAT Feedback imported, NO VAT Return received by Tax Authority, NO VAT Successful file download, NO VAT SUCCESSFUL VAT return submission to the Tax Administr</li><li>**To statuses:** NO VAT Error file download, NO VAT Successful download of final validation</li></ul> |
    | NO VAT Import final validation result | Electronic reporting import | <ul><li>**Model mapping:** Altinn VAT import validation result format (NO)</li><li>**From statuses:** NO VAT Error importing of final validation result, NO VAT Successful download of final validation</li><li>**To statuses:** NO VAT Error importing of final validation result, NO VAT Error validation of uploaded VAT return, NO VAT SUCCESSFUL VAT return submission to the Tax Administr</li></ul> |
    | NO VAT Download payment information | Web service | <ul><li>**Format mapping for URL path:** Altinn VAT interoperation (NO)</li><li>**Web service:** NO Altinn GET attachments</li><li>**File name:** vbetalingsinformasjon.xml</li><li>**File name to send:** *Not applicable*</li><li>**From statuses:** NO VAT Error file download, NO VAT Successful file download, NO VAT SUCCESSFUL VAT return submission to the Tax Administr</li><li>**To statuses:** NO VAT Error file download, NO VAT Successful file download</li></ul> |
    | NO VAT Download receipt | Web service | <ul><li>**Format mapping for URL path:** Altinn VAT interoperation (NO)</li><li>**Web service:** NO Altinn GET attachments</li><li>**File name:** kvittering.pdf</li><li>**File name to send:** *Not applicable*</li><li>**From statuses:** NO VAT Error file download, NO VAT Successful file download, NO VAT SUCCESSFUL VAT return submission to the Tax Administr</li><li>**To statuses:** NO VAT Error file download, NO VAT Successful file download</li></ul> |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
