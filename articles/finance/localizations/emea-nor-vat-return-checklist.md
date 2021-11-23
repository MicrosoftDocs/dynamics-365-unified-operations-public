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

The following type of processing is defined to support interoperation with Altinn.

| Processing | Name (Norwegian) | Description |
|--------------------|-------------|------------|
| NO VAT return | Momsoppgave med direkte innsending | The processing to prepare and submit VAT returns to Altinn. |

> [!IMPORTANT]
> You must define security roles for the processing to enable access to it at the record level for business users.

## Web applications

The **NO VAT return** processing use the following web applications.

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
