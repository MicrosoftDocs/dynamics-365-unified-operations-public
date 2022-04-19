---
# required metadata

title: Person address
description: This topic describes the Person address entity for Dynamics 365 Human Resources.
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

# Person address


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Person address entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmpersonaddressentities

## Description

This entity contains the list of postal addresses for candidate records.

## JSON representation

```json
{
    "mshr_partynumber": "String",
    "mshr_locationid": "String",
    "mshr_description": "String",
    "mshr_roles": "String",
    "mshr_countryregionid": "String",
    "mshr_zipcode": "String",
    "mshr_street": "String",
    "mshr_city": "String",
    "mshr_state": "String",
    "mshr_county": "String",
    "mshr_isprimary": Int,
    "mshr_isprivate": Int,
    "mshr_primaryfield": "String",
    "_mshr_fk_person_id_value": "Guid",
    "_mshr_fk_countryregion_id_value": "Guid",
    "mshr_hcmpersonaddressentityid": "Guid"
}
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Address Entity ID**<br>mshr_hcmpersonaddressentityid<br>*String* | Read-only<br>Required | System-generated unique identifier for the entity record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read/write<br>Required | The ID of the associated party (person) record. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity | The system-generated identifier of the party (person) entity record. |
| **Location ID**<br>mshr_locationid<br>*String* | Read/write<br>Required | The location ID of the address record. Set up in mshr_logisticspostaladdresslocationcdsentity entity. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | A description of the candidate’s address. |
| **Roles**<br>mshr_roles<br>*String* | Read/write<br>Required | The roles assigned for this address. More than one role can be assigned. Each role should be separated by a semicolon. Valid values contained in the mshr_logisticslocationroleentity entity. |
| **Street**<br>mshr_street<br>*String* | Read/write<br>Optional | The street number. |
| **City**<br>mshr_city<br>*String* | Read/write<br>Optional | The city of the address. Set up in mshr_logisticsaddresscityentity entity. |
| **State**<br>mshr_state<br>*String* | Read/write<br>Optional | The state of the address. Set up in mshr_logisticsaddressstateentity entity. |
| **County**<br>mshr_county<br>*String* | Read/write<br>Optional | The county of the address. Set up in mshr_logisticsaddresscountyentity entity. |
| **Zip Code**<br>mshr_zipcode<br>*String* | Read/write<br>Optional | The zip/postal code of the address. Set up in mshr_logisticsaddresspostalcodeentity entity. |
| **Country Region ID**<br>mshr_countryregionid<br>*String* | Read/write<br>Optional | The country or region of the address. |
| **Country/Region ID Value**<br>_mshr_fk_countriregion_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_logisticaddresscountryregionentityid of mshr_logisticsaddresscountryregionentity | System-generated unique identifier of the country/region of the address. |
| **Is Primary**<br>mshr_isprimary<br>*mshr_noyes option set* | Read/write<br>Required | Identifies whether this address is the primary address for the person of the defined role. |
| **Is Private**<br>mshr_isprivate<br>*mshr_noyes option set* | Read/write<br>Required | Identifies whether this address is a private address for the person. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field used as a primary identifier of the entity record. Combination of party number and location ID. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
