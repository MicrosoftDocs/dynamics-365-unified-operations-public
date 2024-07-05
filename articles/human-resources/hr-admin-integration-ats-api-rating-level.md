---
# required metadata

title: Rating level
description: This article describes the Rating level entity for Dynamics 365 Human Resources.
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

# Rating level



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Rating level entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmratinglevelentity

## Description

This entity provides the available rating levels for skills. Rating levels apply across all legal entities.

## JSON representation

```json
{
    "mshr_description": "String",
    "mshr_factor": Int,
    "mshr_note": "String",
    "mshr_ratinglevelid": "String",
    "mshr_ratingmodelid": "String",
    "mshr_primaryfield": "String",
    "_mshr_fk_ratingmodelentity_id_value": "Guid",
    "mshr_hcmratinglevelentityid": "Guid"
}
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Rating Level Entity ID**<br>mshr_hcmratinglevelentityid<br>*GUID* | Read-only<br>Required<br>System-generated | The system-generated unique identifier for the level. |
| **Rating Level ID**<br>mshr_ratinglevelid<br>*String* | Read/write<br>Required | User-readable unique identifier for the level. |
| **Rating Model ID**<br>mshr_ratingmodelid<br>*String* | Read/write<br>Required | The rating model to which the rating level belongs. |
| **Rating Model Entity ID**<br>_mshr_fk_ratingmodelentity_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmratingmodelentityid of mshr_hcmratingmodelentity | The system-generated identifier for the rating model to which the rating level belongs. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | The description of the rating level. |
| **Factor**<br>mshr_factor<br>*Integer* | Read/write<br>Required | The factor for the rating level. When you compare items with a different number of rating levels, the factor is used to normalize the scores. The value must be an integer between 0 and 9. |
| **Note**<br>mshr_note<br>*String* | Read/write<br>Optional | Any notes associated with the rating level. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field to be used as an identifier of the entity record. Combination of rating level ID and rating model ID. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
