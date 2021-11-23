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
| Redirect URL                          | empty | Set up here your value according to [Set up the internet address of ID-porten and Altinn web services](emea-nor-vat-return-setup#internet-address)
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

The setup of electronic messages for both the **UK MTD VAT TEST** processing and the **UK MTD VAT returns** processing uses one type of electronic message item: **VAT return**.
