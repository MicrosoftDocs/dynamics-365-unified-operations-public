---
# required metadata

title: Job base entity
description: This article provides details and an example query for the Job base entity in Dynamics 365 Human Resources.
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

# Job base

[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

### Description

This entity is the base entity that provides information about the job.

### Properties

| **Property**<br><br>Physical name<br><br>_Type_ | **Use** | **Description** |
| --- | --- | --- |
| JobId<br><br>mserp_JobId<br><br>_String_ | Read Only | The ID of the job. |
| MaximumPositions<br><br>mserp_MaximumPositions<br><br>_Integer_ | Read Only | Maximum allowed positions for a job. |
| AllowUnlimitedPositions<br><br>mserp_AllowUnlimitedPositions<br><br>_NoYes_ | Read Only | Allow unlimited positions for a job. |

## Example query for PayIntV1HcmJobBaseEntity

**Request**

Entity Name: mserp_payintv1hcmjobbaseentities_

```http 
GET \[Organizaton URI\]/api/data/v9.1/mserp_payintv1hcmjobbaseentities_
```

**Response**
```json
{  
      "mserp_jobid": "VP of Operations",  
      "mserp_maximumnumberofpositions": 2147483647,  
      "mserp_allowunlimitedpositions": 200000001,_

}
```

