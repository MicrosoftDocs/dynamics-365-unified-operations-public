---
# required metadata

title: Job function entity
description: This article provides details and an example query for the Job function entity in Dynamics 365 Human Resources.
author: jcart
ms.date: 04/04/2024
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
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Job function entity


This article describes the entity **PayIntV1HcmJobFunctionEntity** for Dynamics 365 Human Resources.

Physical name: mserp_PayIntV1HcmJobFunctionEntity

### Description

This entity provides information about the job function.

### Properties

| Property</br>**Physical name**</br>***Type***| Use | Description |
| --- | --- | --- |
| Description<br>mserp_Description<br>*String* | Read-only | Description of the Job function. |
| JobFunctionId<br>mserp_JobFunctionId<br>*String* | Read-only | ID of the job function. |
| RegulatoryJobCategory<br>mserp_RegulatoryJobCategory<br>*Enum* | Read-only | Category of the job. |

## Example query for PayIntV1HcmJobFunctionEntity

**Request**

Entity Name: mserp_payintv1hcmjobfunctionentities

```http 
GET \[Organizaton URI\]/api/data/v9.1/mserp_payintv1hcmjobfunctionentities_
```

**Response**

```json
{  
      "mserp_description": "Officials and Manager",  
      "mserp_jobfunctionid": "0100",  
      "mserp_regulatoryjobcategory": 200000000,  
    }
```
