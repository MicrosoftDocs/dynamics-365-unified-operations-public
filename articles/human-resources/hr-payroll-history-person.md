---
# required metadata

title: Historical person name entity
description: This article provides details and an example query for the Historical person name entity in Dynamics 365 Human Resources.
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

>[Note!]
>The functionality noted in this article is available starting in Dynamics 365 Human Resources version 10.0.39.

# Historical person name 


[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the entity PayIntV1DirPersonNameHistoricalEntity for Dynamics 365 Human Resources.

### Description
This entity provides information about the Person name history. 

### Properties
| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
|FirstName</br>mserp_ FirstName</br>*String*|	Read-only|First name of the person.|
|LastNamePrefix</br>mserp_ LastNamePrefix</br>*String*|	Read-only|	Last name prefix of the person.|
|LastName</br>mserp_LastName</br>*String*|	Read-only|	Last name of the person.| 
|MiddleName</br>mserp_MiddleName</br>*String*|	Read-only|Middle name of the person.|
|ValidFrom</br>mserp_ValidFrom</br>*Date time offset*| 	Read-only|	The starting date the person's name is valid. |
|ValidTo</br>mserp_ValidTo</br>*Date time offset*| 	Read-only|	The ending date the person's name is valid.|
|PartyNumber</br>mserp_PartyNumber</br>*String*|	Read-only|	Unique identifier for the party. |

## Example query for PayIntV1DirPersonNameHistoricalEntity

**Request**

Entity name: mserp_payintv1dirpersonnamehistoricalentities

```http 
GET [Organizaton URI]/api/data/v9.1/mserp_payintv1dirpersonnamehistoricalentities
```

**Response**
```json
{
      "mserp_firstname": "Jodi",
      "mserp_lastnameprefix": "",
      "mserp_lastname": "Christiansen",
      "mserp_middlename": "",
      "mserp_validto": "2154-12-31T23:59:59Z",
      "mserp_partynumber": "000000032",
      "mserp_validfrom": null
    }
```






