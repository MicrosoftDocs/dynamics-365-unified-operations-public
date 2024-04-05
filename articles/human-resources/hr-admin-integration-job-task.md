---
# required metadata

title: Job task entity
description: This article provides details and an example query for the Job task entity in Dynamics 365 Human Resources.
author: 
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

# Job task


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the entity PayIntV1HcmJobTaskEntity for Dynamics 365 Human Resources.

### Description
This entity provides information about the job task. 

### Properties
| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
|Description</br>mserp_Description</br>*String*|	Read-only|	Description of the job task|
|JobTaskId </br>mserp_JobTaskId</br>*String*	|Read-only|	ID of the job task |
|Note</br>mserp_Note</br>*String*|	Read-only|	Notes for a job task|

## Example query for Job task entity

**Request**

Entity Name: mserp_payintv1hcmjobtaskentities

```http 
GET [Organizaton URI]/api/data/v9.1/mserp_payintv1hcmjobtaskentities
```

**Response**
```json
{
      "mserp_description": "Customer calls",
      "mserp_jobtaskid": "Customer calls",
      "mserp_note": "This job includes communication with the customers, and stakeholders.",
    }
```

