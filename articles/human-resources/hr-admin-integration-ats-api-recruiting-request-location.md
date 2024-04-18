---
# required metadata

title: Recruiting request location
description: This article describes the Recruiting request location entity for Dynamics 365 Human Resources.
author: jaredha
ms.date: 02/05/2021
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
ms.author: jaredha
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: Human Resources
---

# Recruiting request location



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Recruiting request location entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmrecruitingrequestlocationentity

### Description

The list of locations defined as locations where recruited employees will work upon hiring. These are locations created across legal entities.

### JSON representation

```
{
    "mshr_recruitingrequestlocationid": "String",
    "mshr_locationid": "String",
    "mshr_description": "String",
    "mshr_countryregionid": "String",
    "mshr_zipcode": "String",
    "mshr_street": "String",
    "mshr_city": "String",
    "mshr_state": "String",
    "mshr_county": "String",
    "mshr_telephone": "String",
    "mshr_email": "String",
    "mshr_internetaddress": "String",
    "_mshr_dataareaid_id_value": "Guid",
    "mshr_dataareaid": "String",
    "_mshr_fk_countryregion_id_value": "Guid",
    "mshr_hcmrecruitingrequestlocationentityid": "Guid"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Location ID**<br>mshr_locationid<br>*String* | Write-once<br>Required | The system-generated, user-readable identifier for the recruiting location. |
| **Recruiting Request Location**<br>mshr_recruitingrequestlocationid<br>*String* | Write-once<br>Required | User-defined unique identifier for the recruiting location. |
| **Recruiting Request Location Entity ID**<br>mshr_hcmrecruitingrequestlocationentityid<br>*GUID* | Read-only<br>Required | System-generated unique identifier for the recruiting request location record. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | Description of the location. |
| **Country/Region ID**<br>mshr_countryregionid<br>*String* | Read-only<br>Optional | Specifies the country or region where the candidate has citizenship. |
| **Country/Region ID Value**<br>_mshr_fk_countriregion_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_logisticaddresscountryregionentityid of mshr_logisticsaddresscountryregionentity | System-generated unique identifier of the country/region of the address. |
| **ZipCode**<br>mshr_zipcode<br>*String* | Read-only<br>Optional | Zip/postal code. |
| **Street**<br>mshr_street<br>*String* | Read-only<br>Optional | Street address. |
| **City**<br>mshr_city<br>*String* | Read-only<br>Optional | City. |
| **State**<br>mshr_state<br>*String* | Read-only<br>Optional | State or province. |
| **County**<br>mshr_county<br>*String* | Read-only<br>Optional | County. |
| **Telephone**<br>mshr_telephone<br>*String* | Read/write<br>Optional | Telephone number for the location. |
| **Email**<br>mshr_email<br>*String* | Read/write<br>Optional | Email address. |
| **InternetAddress**<br>mshr_internetaddress<br>*String* | Read/write<br>Optional | URL for the location website. |
| **Data Area ID**<br>mshr_dataareaid<br>*String* | Read/write<br>Optional | Specifies the legal entity (company). |
| **Data Area ID Value**<br>_mshr_dataareaid_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: cdm_companyid of cdm_company entity | System-generated GUID value identifying the legal entity (company). |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Recruiting request](hr-admin-integration-ats-api-recruiting-request-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
