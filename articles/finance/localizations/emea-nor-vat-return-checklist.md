---
# required metadata

title: Checklist for Electronic messages setup for VAT return
description: This topic contains checklist for Electronic messages setup for VAT return of Norway.
author: liza-golub
ms.date: 11/18/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 2021-11-18
ms.dyn365.ops.version: AX 10.0.22

---

# Checklist for Electronic messages setup for VAT return with direct submission to Altinn

This topic provides information about how the [Electronic messages](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/electronic-messaging) functionality should be set up so that it supports VAT return of Norway with direct submission to Altinn processing. Use this information to determine whether the Electronic messages functionality is correctly set up.

Although this topic includes the most important information about the setup, it doesn't include information about all the data. We recommend that you use a package of data entities that provides a predefined setup of the functionality and that includes all the data that is required to set up the processing for interoperation with Altinn.

Go to **Tax** > **Setup** > **Electronic messages** > **Electronic messages processing** and check your setup. The following type of processing is defined to support interoperation with Altinn.

| Processing | Name (Norwegian) | Description |
|--------------------|-------------|------------|
| NO VAT return | Momsoppgave med direkte innsending | The processing to prepare and submit VAT returns to Altinn. |

> [!IMPORTANT]
> You must define security roles for the processing to enable access to it at the record level for business users.

## Web applications

Go to **Tax** > **Setup** > **Electronic messages** > **Web applications** and check your setup. The **NO VAT return** processing uses the following web applications.

| Application name                 | Description |
|----------------------|-------------|
| NO Altinn | Web application to interoperate with Altinn APIs. |
| NO ID-Porten        | Web application to interoperate with integration point created in ID-porten. |

The following table shows the parameters of the web applications.

| Parameter                             | Value for **NO Altinn** | Value for **NO ID-Porten** |
|---------------------------------------|-------|--------------|
| Base URL | `https://platform.tt02.altinn.no/authentication/api/v1/exchange/id-porten` | `https://oidc-ver2.difi.no/idporten-oidc-provider` |
| Authorization URL path                | empty | `/authorize` |
| Token URL path                        | empty | `/token` |
| Redirect URL                          | empty | Set up here your value according to [Set up the internet address of ID-porten and Altinn web services](emea-nor-vat-return-setup.md#internet-address)
| Authorization format mapping          | Altinn VAT authorization format (NO) | Altinn VAT authorization format (NO)|
| Import token model mapping            | Altinn VAT import Altinn token format (NO) | Altinn VAT import ID-Porten token format (NO) |
| Accept                                | empty | empty |
| Content type                          | application/json | application/x-www-form-urlencoded |

> [!IMPORTANT]
> You must define security roles for both web applications to enable access to the access token and interoperation with ID-porten and Altinn APIs for business users.

Internet addresses (base URL) are subject to change by the Tax Administration. Therefore, we recommend that you check for actual internet addresses on the official web site of the Altinn and ID-porten. 

## Web service settings

Go to **Tax** > **Setup** > **Electronic messages** > **Web service settings** and check your setup. The **NO VAT return** processing uses the following web services.

| Parameter name | Parameter value |
|-------|-----------|
| Web service  | **NO Altinn GET attachments**|
| Description | Altinn web service for GET attachments downloaded (XML, PDF)|
| Internet address | empty|
| Web application |  **NO Altinn**|
| Use proxy server | No |
| Use advanced parameters | empty |
| Certificate | empty |
| The response type – XML | No |
| Request method | **GET**|
| Accept | empty|
| Accept encoding| empty |
| Request headers | empty |
| Content type | empty|
| Request header format mapping | **Altinn VAT web request headers format (NO)**|
| Successful response code |**200**|

| Parameter name | Parameter value |
|-------|-----------|
| Web service  | **NO Altinn GET JSON**|
| Description | Altinn web service for GET requests of JSON type of content |
| Internet address | `https://skd.apps.tt02.altinn.no/skd/mva-melding-innsending-etm2/instances` |
| Web application |  **NO Altinn** |
| Use proxy server | No |
| Use advanced parameters | empty |
| Certificate | empty |
| The response type – XML | No |
| Request method | **GET**|
| Accept | **application/json** |
| Accept encoding| empty |
| Request headers | empty |
| Content type | empty |
| Request header format mapping | **Altinn VAT web request headers format (NO)**|
| Successful response code |**200**|

| Parameter name | Parameter value |
|-------|-----------|
| Web service  | **NO Altinn POST JSON**|
| Description | Altinn web service for POST requests of JSON type of content |
| Internet address | `https://skd.apps.tt02.altinn.no/skd/mva-melding-innsending-etm2/instances` |
| Web application |  **NO Altinn**|
| Use proxy server | No |
| Use advanced parameters | empty |
| Certificate | empty |
| The response type – XML | No |
| Request method | **POST**|
| Accept | empty|
| Accept encoding| empty |
| Request headers | empty |
| Content type | **application/json** |
| Request header format mapping | **Altinn VAT web request headers format (NO)**|
| Successful response code |**201** |

| Parameter name | Parameter value |
|-------|-----------|
| Web service  | **NO Altinn POST XML**|
| Description | Altinn web service for POST requests of XML type of content |
| Internet address | `https://skd.apps.tt02.altinn.no/skd/mva-melding-innsending-etm2/instances` |
| Web application |  **NO Altinn**|
| Use proxy server | No |
| Use advanced parameters | empty |
| Certificate | empty |
| The response type – XML | No |
| Request method | **POST**|
| Accept | empty|
| Accept encoding| empty |
| Request headers | empty |
| Content type | **text/xml** |
| Request header format mapping | **Altinn VAT web request headers format (NO)**|
| Successful response code |**201** |

| Parameter name | Parameter value |
|-------|-----------|
| Web service  | **NO Altinn PUT JSON**|
| Description | Altinn web service for PUT requests of JSON type of content |
| Internet address | `https://skd.apps.tt02.altinn.no/skd/mva-melding-innsending-etm2/instances` |
| Web application |  **NO Altinn**|
| Use proxy server | No |
| Use advanced parameters | empty |
| Certificate | empty |
| The response type – XML | No |
| Request method | **PUT**|
| Accept | empty|
| Accept encoding| empty |
| Request headers | empty |
| Content type | **application/json** |
| Request header format mapping | **Altinn VAT web request headers format (NO)**|
| Successful response code |**200** |

| Parameter name | Parameter value |
|-------|-----------|
| Web service  | **NO Altinn PUT XML**|
| Description | Altinn web service for PUT requests of XML type of content |
| Internet address | `https://skd.apps.tt02.altinn.no/skd/mva-melding-innsending-etm2/instances` |
| Web application |  **NO Altinn**|
| Use proxy server | No |
| Use advanced parameters | empty |
| Certificate | empty |
| The response type – XML | No |
| Request method | **PUT**|
| Accept | empty|
| Accept encoding| empty |
| Request headers | empty |
| Content type | **application/xml** |
| Request header format mapping | **Altinn VAT web request headers format (NO)**|
| Successful response code |**201** |

| Parameter name | Parameter value |
|-------|-----------|
| Web service  | **NO Validate VAT return**|
| Description | Web service of Tax Administration to validate VAT return |
| Internet address | `https://mp-test.sits.no/api/mva/grensesnittstoette/mva-melding/valider` |
| Web application |  **NO ID-Porten**|
| Use proxy server | No |
| Use advanced parameters | empty |
| Certificate | empty |
| The response type – XML | No |
| Request method | **POST**|
| Accept | empty|
| Accept encoding| empty |
| Request headers | empty |
| Content type | **application/xml** |
| Request header format mapping | **Altinn VAT web request headers format (NO)**|
| Successful response code |**200** |

## Additional fields

Go to **Tax** > **Setup** > **Electronic messages** > **Additional fields** and check your setup. The **NO VAT return** processing uses the following additional fields.

> [!NOTE]
> None of these fields can be changed by the user.

| Field                   | Description (Norwegian) | User edit | Counter | Hidden |
|-------------------------|-------------|-----------|---------|---|
| NO VAT Data GUID | Data GUID  | No | No | Yes |
| NO VAT Instance GUID | Instans-GUID  | No | No | Yes |
| NO VAT Note for VAT return | Merknad på meldingsnivå: har en kan velge mellom en predefinert liste av merknader eller fylle ut fritekst  | Yes | No | No |
| NO VAT Party ID | Part ID  | No | No | Yes |
| NO VAT Payment information | Betalingsinformasjon  | No | No | Yes |
| NO VAT Receipt | Kvittering  | No | No | Yes |
| NO VAT Validation result | Valideringsresultat  | No | No | Yes |
| Tax registration number | Skatteregistreringsnummer  | No | No | Yes |

## Electronic message item types

Go to **Tax** > **Setup** > **Electronic messages** > **Message item types** and check your setup. The **NO VAT return** processing uses one type of electronic message item: **NO VAT return**.

## Electronic message item statuses

Go to **Tax** > **Setup** > **Electronic messages** > **Message item statuses** and check your setup. The **NO VAT return** processing uses the following electronic message item statuses.

| Status           | Description | Allow delete |
|------------------|-------------|---------------------------------------|
| NO VAT Collected | Sales tax payment record included for VAT return (Momsregistrering inkludert for mva-retur). | Yes |
| NO VAT Excluded  | Sales tax payment excluded from VAT return (Innbetaling av merverdiavgift ekskludert fra mva ). | Yes |
| To be reported   | Sales tax payment record ready for VAT return (Momsregistrering er klar for merverdiavgift). | No |

## Electronic message statuses

Go to **Tax** > **Setup** > **Electronic messages** > **Message statuses** and check your setup. The **NO VAT return** processing uses the following electronic message statuses.

| Status                            | Description (Norwegian) | Response type | Allow delete |
| --- | --- | --- | --- |
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
| NO VAT Feedback imported | Tilbakemeldinger importert | Successfull | No |
| NO VAT Feedback not provided | Tilbakemelding tilbys ikke | Successfull | No |
| NO VAT Feedback provided | Tilbakemelding tilbys | Successfull | No |
| NO VAT Instance created | Forekomst opprettet | Successfull | No |
| NO VAT New message created | Ny elektronisk melding opprettet | Successfull | Yes |
| NO VAT Ready to generate VAT return | Klar til å generere mva | Successfull | No |
| NO VAT Return received by Tax Authority | Mva-meldingen er levert og mottatt av Skatteetaten | Successfull | No |
| NO VAT Return submission completed | Mva-returnering fullført | Successfull | No |
| NO VAT Return submission request generated | Mva-returinnleveringsforespørsel generert | Successfull | No |
| NO VAT Return submission uploaded successfully | Innlevering av merverdiavgift ble lastet opp | Successfull | No |
| NO VAT Return submission uploading error | Melding om returopplastingsfeil | TechnicalError | No |
| NO VAT Return uploaded | Mva-retur lastet opp | Successfull | No |
| NO VAT Return validated and ready to upload | Momsangivelsen ble godkjent av Skatteetaten og klar til å lastes opp til Altinn | Successfull | No |
| NO VAT Return validation passed successfully | Mva-returvalidering bestått | Successfull | No |
| NO VAT Return XML generated | Mva-retur er vellykket generert i XML-format | Successfull | Yes |
| NO VAT Sent request for feedback | Sendt forespørsel om tilbakemelding | Successfull | No |
| NO VAT Sent request for status of feedback | Sendt forespørsel om status for tilbakemelding | Successfull | No |
| NO VAT Sent VAT return validation request | Returvalideringsforespørsel sendt | Successfull | No |
| NO VAT Successful download of final validation | Vellykket nedlasting av endelig validering | Successfull | No |
| NO VAT Successful file download | Last ned filen vellykket | Successfull | No |
| NO VAT Successful sending create instance request | Sendingen oppretter forespørsel om vellykket sending | Successfull | No |
| NO VAT SUCCESSFUL VAT return submission to the Tax Administr | MVA-meldingen lastet opp til Skatteetaten ble validert | Successfull | No |

## Action populate records

Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions** and check your setup. The **NO VAT return** processing uses one **NO VAT Collect sales tax payments** populate records action. The following table shows the setup of the data source for this action.

| Property               | Value |
|------------------------|-------|
| Name                   | NO VAT return |
| Message item type      | NO VAT return |
| Account type           | All |
| Master table name      | TaxReportVoucher |
| Document number field  | Voucher |
| Document date field    | TransDate |
| Document account field | TaxPeriod |
| User query             | Yes |

> [!IMPORTANT]
> Define the settlement period by using the **Edit query** button. For more information, see [Define a sales tax settlement period](emea-nor-vat-return-setup.md#settlement-period).

## Electronic message actions

Go to **Tax** > **Setup** > **Electronic messages** > **Electronic message processing** and check your setup. The **NO VAT return** processing uses the following electronic message actions.

| Order | Action                       | Description (Norwegian) | Inseparable sequence | Run separately |
|-------|------------------------------|-------------------------|----------------------|---------|
| 1 | NO VAT Create message | Lag melding | empty | No |
| 2 | NO VAT Collect sales tax payments | Samle momsregistreringer for merverdiavgift | empty |No |
| 3 | NO VAT Ready to generate VAT return | Klar til å generere mva | empty | Yes |
| 4 | NO VAT Not ready to generate VAT return | Elektronisk melding er ikke klar til å generere merverdiavgi | empty | Yes |
| 5 | NO VAT Preview VAT return in Excel | Forhåndsvis mva-retur i Excel | empty | Yes |
| 6 | NO VAT Generate VAT return | Generer merverdiavgift i XML | NO VAT Validation | Yes | 
| 7 | NO VAT Send validation request | Send forespørsel om validering | NO VAT Validation | Yes | 
| 8 | NO VAT Import validation response | Import validering svar | NO VAT Validation |No |
| 9 | NO VAT Generate request for instance | Generer forespørsel om å opprette forekomst  | NO VAT Validation |No |
| 10 | NO VAT Send request to create instance | Send forespørsel for å opprette forekomst  | NO VAT Submission |Yes |
| 11 | NO VAT Import instance creation response | Importer opprettelsessvar for forekomst  | NO VAT Submission |No |
| 12 | NO VAT Generate VAT return submission | Generer innsending av mva  | NO VAT Submission |No |
| 13 | NO VAT Upload VAT return submission | Last opp innsending av merverdiavgift  | NO VAT Submission |No |
| 14 | NO VAT Upload VAT return | Last opp mva-retur  | NO VAT Submission |No |
| 15 | NO VAT Complete data filling | Fullstendig datafylling  | NO VAT Submission |No |
| 16 | NO VAT Complete VAT return submission | Fullfør momsoppgaven |  NO VAT Submission |No |
| 17 | NO VAT Send feedback status request | Send statusforespørsel om tilbakemelding | NO VAT Submission | No |
| 18 | NO VAT Import feedback status response | Importer tilbakemeldingsstatusrespons | NO VAT Submission | No |
| 19 | NO VAT Send feedback request | Send forespørsel om tilbakemelding | NO VAT Submission | No |
| 20 | NO VAT Import feedback response | Importer tilbakemeldingssvar  | NO VAT Submission | No |
| 21 | NO VAT Download validation result | Last ned valideringsresultat  | NO VAT Submission | No |
| 22 | NO VAT Import final validation result | Import endelig valideringsresultat | NO VAT Submission | No |
| 23 | NO VAT Download payment information | Last ned betalingsinformasjon | empty | Yes |
| 24 | NO VAT Download receipt | Last ned kvittering | empty |Yes |
| 25 | NO VAT Exclude from VAT return | Innbetaling av merverdiavgift ekskludert fra mva | empty | Yes |
| 26 | NO VAT Include to VAT return | Inkluder betaling av omsetningsavgift til mva | empty | Yes |

Go to **Tax** > **Setup** > **Electronic messages** > **Message processing actions** and check your setup. The following table shows parameters of the actions that must be defined.

| Action | Action type | Parameters |
|--------|-------------|------------|
| NO VAT Create message | Create message | <ul><li>**From statuses:** No</li><li>**To statuses:** NO VAT New message created</li></ul> |
| NO VAT Collect sales tax payments | Populate records | <ul><li>**Populate records action:** NO VAT Collect sales tax payments</li><li>**From statuses:** NO VAT New message created</li><li>**To statuses:** NO VAT Collected</li></ul>|
| NO VAT Ready to generate VAT return | Message level user processing | <ul><li>**From statuses:** NO VAT New message created</li><li>**To statuses:** NO VAT Ready to generate VAT return</li></ul> |
| NO VAT Not ready to generate VAT return | Message level user processing | <ul><li>**From statuses:** NO VAT Ready to generate VAT return, NO VAT Return validated and ready to upload, NO VAT Return XML generated</li><li>**To statuses:** NO VAT New message created</li></ul> |
| NO VAT Preview VAT return in Excel | Electronic reporting export message | <ul><li>**Message item type:** NO VAT return</li><li>**Format mapping:** VAT Declaration Excel (NO)</li><li>**From statuses:** NO VAT Error VAT return generation, NO VAT Error VAT return validation, NO VAT Ready to generate VAT return</li><li>**To statuses:** NO VAT Error VAT return generation, NO VAT Ready to generate VAT return</li></ul> |
| NO VAT Generate VAT return | Electronic reporting export message | <ul><li>**File name:** mvamelding</li><li>**Message item type:** NO VAT return</li><li>**Format mapping:** VAT Declaration XML (NO)</li><li>**From statuses:** NO VAT Error sending VAT return validation request, NO VAT Error validation of uploaded VAT return, NO VAT Error VAT return generation, NO VAT Error VAT return validation, NO VAT Ready to generate VAT return, NO VAT Return XML generated</li><li>**To statuses:** NO VAT Return XML generated, NO VAT Error VAT return generation</li></ul> |
| NO VAT Send validation request | Web service | <ul><li>**Web service:** NO Validate VAT return</li><li>**File name:** `valideringsresultat.xml`</li><li>**File name to send:** `mvamelding.xml`</li><li>**From statuses:** NO VAT Error sending VAT return validation request, NO VAT Error VAT return validation, NO VAT Return XML generated</li><li>**To statuses:** NO VAT Error sending VAT return validation request, NO VAT Sent VAT return validation request</li></ul>|
| NO VAT Import validation response | Electronic reporting import | <ul><li>**Model mapping:** Altinn VAT import validation result format (NO)</li><li>**From statuses:** NO VAT Error importing VAT return validation result, NO VAT Sent VAT return validation request</li><li>**To statuses:** NO VAT Error importing VAT return validation result, NO VAT Error VAT return validation, NO VAT Return validation passed successfully</li></ul> |
| NO VAT Generate request for instance | Electronic reporting export message | <ul><li>**File name:** createInstanceRequest.json</li><li>**Format mapping:** Altinn VAT interoperation (NO)</li><li>**From statuses:** NO VAT Error generation of instance request, NO VAT Error of instance creation, NO VAT Error sending request to create an instance, NO VAT Return validation passed successfully</li><li>**To statuses:** NO VAT Error generation of instance request, NO VAT Return validated and ready to upload</li></ul>|
