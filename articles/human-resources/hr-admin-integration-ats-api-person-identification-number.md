---
# required metadata

title: Person identification number
description: This topic describes the Person identification number entity for Dynamics 365 Human Resources.
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

# Person identification number


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Person identification number entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmpersonidentificationnumberentity

## Description

This entity describes the identification numbers for the candidate. It enables the API consumer to write identification numbers, like Social Security numbers or passport numbers, to the candidate record. Identification numbers are surfaced on the worker record, but not on the candidate record. An integrating application can write the values to the Human Resources database, but the numbers won’t be visible in Human Resources until the candidate's worker record is created.

## JSON representation

```json
{
    "mshr_entrytype": "String",
    "mshr_description": "String",
    "mshr_expirationdate": "Datetime",
    "mshr_isprimary": Int,
    "mshr_identificationnumber": "String",
    "mshr_partynumber": "String",
    "mshr_identificationtypeid": "String",
    "mshr_issuingagencyid": "String",
    "mshr_primaryfield": "String",
    "_mshr_fk_person_id_value": "Guid",
    "_mshr_fk_issuingagency_id_value": "Guid",
    "_mshr_fk_identificationtype_id_value": "Guid",
    "mshr_hcmpersonidentificationnumberentityid": "Guid",
    "mshr_issueddate": "Datetime"
}
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Identification Number Entity ID**<br>mshr_hcmpersonidentificationnumberentityid<br>*GUID* | Read-only<br>Required<br>System-generated | Unique primary identifier for the person identification number record. |
| **Entry Type**<br>mshr_entrytype<br>*String* | Read-write<br>Optional | Free value to reference the type of entry for the identification number. |
| **Description**<br>mshr_description<br>*String* | Read-write<br>Optional | The description of the identification number. |
| **Expiration Date**<br>mshr_expirationdate<br>*Datetime* | Read-write<br>Optional | The date on which the identification number or associated document expires. |
| **Is Primary**<br>mshr_isprimary<br>*mshr_noyes option set* | Read-write<br>Optional | Defines whether the identification number is the primary record for the person for this identification type. |
| **Identification Number**<br>mshr_identificationnumber<br>*String* | Read-write<br>Required | The identification number. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read-write<br>Required | The identifier of the party (person) owning the identification number. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity entity | The unique identifier of the party (person). |
| **Identification Type ID**<br>mshr_identificationtypeid<br>*String* | Read-write<br>Required | The type of identification number. |
| **Identification Type ID Value**<br>_mshr_fk_identificationtype_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmidentificationtypeentityid of mshr_hcmidentificationtypeentity entity | System-generated unique identifier of the identification type. |
| **Issuing Agency ID**<br>mshr_issuingagencyid<br>*String* | Read-write<br>Optional | The agency or organization issuing the identification number. |
| **Issuing Agency ID Value**<br>_mshr_fk_issuingagency_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmissuingagencyentityid of mshr_hcmissuingagencyentity entity | System-generated unique identifier of the agency issuing the identification number. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field to be used as an identifier of the entity record. Combination of party number, identification type ID, and identification number. |
| **Issue Date**<br>mshr_issuedate<br>*Date* | Read-write<br>Optional | The date the identification number was issued. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
