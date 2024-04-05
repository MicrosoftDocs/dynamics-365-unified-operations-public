---
# required metadata

title: Job type entity
description: This article provides details and an example query for the Job type entity in Dynamics 365 Human Resources.
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

# Job type

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the entity PayIntV1HcmJobTypeEntity for Dynamics 365 Human Resources.

### Description
This entity provides information about the job type. 

### Properties
| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
|Description</br>mserp_description </br>*String*|	Read-only|	Description of the job type.   |
|exemptstatus</br>mserp_exemptstatus</br>*Enum*|	Read-only|	Indicates whether the job type is exempt or non-exempt from the Fair labor standards Act (FLSA) coverage or indicate that the act doesn't apply 
to the job type.|
|JobTypeId</br>mserp_jobtypeid</br>*String*|Read-only|	ID of the job type.|
|PaidHourly</br>mserp_PaidHourly</br>*Enum*|	Read-only	|Indicate if the job is paid hourly.|
|CreatedBy</br>mserp_System_CreatedBy</br>*Date time offset*|	Read-only|	Details of the job type created by.|
|CreatedDateTime</br>mserp_System_CreatedDateTime</br>*Date time offset*|	Read-only|	The date and time the job type created.|
|ModifiedBy</br>mserp_System_ModifiedBy</br>*Date time offset*|	Read-only|	Job type modified by.|
|ModifiedDateTime</br>mserp_System_ModifiedDateTime</br>*Date time offset*|	Read-only|	The data and time the job type was modified.|

## Example query for PayIntV1HcmJobTypeEntity

**Request**

Entity name: mserp_payintv1hcmjobtypeentities

```http 
GET [Organizaton URI]/api/data/v9.1/mserp_payintv1hcmjobtypeentities
```

**Response**
```json
{
      "mserp_description": "Clerical",
      "mserp_exemptstatus": 200000002,
      "mserp_jobtypeid": "Clerical",
      "mserp_paidhourly": 200000000,
      "mserp_system_createdby": "JACOB",
      "mserp_system_createddatetime": "2016-09-14T14:38:59Z",
      "mserp_system_modifiedby": "JACOB",
      "mserp_system_modifieddatetime": "2016-09-14T14:38:59Z",
    }
```




