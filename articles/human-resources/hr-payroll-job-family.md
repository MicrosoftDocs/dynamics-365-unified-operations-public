---
# required metadata

title: Job family entity
description: This article provides details and an example query for the Job family entity in Dynamics 365 Human Resources.
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

# Job family

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

### Description
This entity provides information about the job family. 

## Properties

| **Property**<br><br>Physical name<br><br>_Type_ | **Use** | **Description** |
| --- | --- | --- |
| JobFamilyId<br><br>mserp_JobFamilyId<br><br>*String* | Read-only | ID of the Job family. |
| Description<br><br>mserp_Description<br><br>*String* | Read-only | Description of the job family. |

## Example query for PayIntV1HcmJobFamilyEntity

Entity Name: mserp_payintv1hcmjobfamilyentities

**Request**

```http
GET \[Organizaton URI\]/api/data/v9.1/mserp_payintv1hcmjobfamilyentities_
```

**Response**

```json

{  
      "mserp_jobfamilyid": "Finance Jobs",  
      "mserp_description": "Accounting, Payroll",  
          }

```
