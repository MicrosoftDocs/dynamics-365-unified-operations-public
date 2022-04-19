---
# required metadata

title: Person certificate
description: This topic describes the Person certificate entity for Dynamics 365 Human Resources.
author: jaredha
ms.date: 02/05/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: Human Resources
---

# Person certificate


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Person certificate entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmpersoncertificateentity

## Description

This entity describes the professional certificates of a candidate.

## JSON representation

```json
{
    "mshr_certificatetypeid": "String",
    "mshr_startdate": "Date",
    "mshr_enddate": "Date",
    "mshr_notes": "String",
    "mshr_partynumber": "String",
    "mshr_primaryfield": "String",
    "_mshr_fk_certificatetype_id_value": "Guid",
    "_mshr_fk_person_id_value": "Guid",
    "mshr_hcmpersoncertificateentityid": "Guid"
}
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Certificate Entity ID**<br>mshr_hcmpersoncertificateentityid<br>*GUID* | Read-only<br>Required | System-generated unique identifier for the person certificate entity record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read/write<br>Required | The party (person) ID of the candidate. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity | The system-generated identifier of the party (person) entity record. |
| **Certificate Type ID**<br>mshr_certificatetypeid<br>*String* | Read/write<br>Required | 	The identifier of the certificate type defined in Human Resources. |
| **Certificate Type ID Value**<br>_mshr_fk_certificatetype_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmcertificatetypeentityid of mshr_hcmcertificatetypeentity | System-generated unique identifier of the certificate type in the associated entity. |
| **Start Date**<br>mshr_startdate<br>*Datetime* | Read/write<br>Required | The date at which the certificate was issued. |
| **End Date**<br>mshr_enddate<br>*Datetime* | Read/write<br>Optional | The date at which the certificate will expire. |
| **Notes**<br>mshr_notes<br>*String* | Read/write<br>Optional | Notes for use by hiring managers and recruiters. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | 	Field to be used as an identifier of the entity record. Combination of party number, certificate type ID, and start date. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
