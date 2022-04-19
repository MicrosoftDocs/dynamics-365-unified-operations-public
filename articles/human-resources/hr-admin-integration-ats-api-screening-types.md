---
# required metadata

title: Screening types
description: This topic describes the Screening types entity for Dynamics 365 Human Resources.
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

# Screening types


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Screening types entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmscreeningtypeentity

## Description

This entity describes the screening types set up by the company for pre-employment and ongoing employee screening processes.

## JSON representation

```json
{
    "mshr_description": "String",
    "mshr_frequencyunit": Int,
    "mshr_generatefrom": Int,
    "mshr_frequencyinterval": Int,
    "mshr_screeningtypeid": "String",
    "mshr_hcmscreeningtypeentityid": "Guid"
}
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Screening Type Entity ID**<br>mshr_hcmscreeningtypeentityid<br>*GUID* | Read-only<br>Required<br>System-generated | Unique primary identifier for the screening type record. |
| **Screening Type ID**<br>mshr_screeningtypeid<br>*String* | Read/write<br>Required | User-defined unique identifier for the screening type. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | The description of the screening type. |
| **Frequency Unit**<br>mshr_frequencyunit<br>*mshr_hcmfrequencyunit option set* | Read/write<br>Required | Describes the frequency with which the screening must be completed for the assigned person. |
| **Generate From**<br>mshr_generatefrom<br>*mshr_hcmfrequencygeneratefrom option set* | Read-write<br>Required | If the Frequency value is any value other than “One-time only”, the GenerateFrom value determines the date from which to calculate the next screening event. |
| **Frequency Interval**<br>mshr_frequencyinterval<br>*Integer* | Read-write<br>Required | If the Frequency value is any value other than “One-time only”, you must define an interval for the units of time between each screening event. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
