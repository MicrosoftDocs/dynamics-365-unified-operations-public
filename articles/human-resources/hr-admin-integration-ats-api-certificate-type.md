---
# required metadata

title: Certificate type
description: This article describes the Certificate type entity for Dynamics 365 Human Resources.
author: jaredha
ms.date: 07/02/2024
ms.topic: article
# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: Human Resources
---

# Certificate type



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Certificate type entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmcertificatetypeentity

## Description

This entity defines the list of professional certificate types set up in Human Resources. The entity isn't specific to a legal entity (company).

## JSON representation

```json
{
    "mshr_certificatetype": "String",
    "mshr_description": "String",
    "mshr_requirerenewal": Int,
    "mshr_hcmcertificatetypeentityid": "Guid"
}
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Certificate Type Entity ID**<br>mshr_hcmcertificatetypeentityid<br>*GUID* | Read-only<br>Required 
System-generated | Unique primary identifier for the certificate type. |
| **Certificate Type**<br>mshr_certificatetype<br>*String* | Read/write<br>Required | Unique user-readable identifier for the certificate type. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | Description of the certificate type. |
| **Require Renewal**<br>mshr_requirerenewal<br>*mshr_noyes option set* | Read/write<br>Optional | Indicates whether renewal is required for the certificate. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
