---
# required metadata

title: Payroll Employee entity
description: This article provides details and an example query for the Payroll Employee entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 02/20/2026
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
ms.author: twheeloc
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Payroll Employee entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Payroll Employee entity (PayIntV1PayrollEmployeeEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the payroll employee.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Legalentity | mserp_legalentity | Real | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Identificationnumber | mserp_identificationnumber | String | Read-only |
| Person | mserp_person | Real | Read-only |
| Birthdate | mserp_birthdate | Date time offset | Read-only |
| Legalentity Bigint | mserp_legalentity_bigint | Int64 | Read-only |
| Employmentstartdate | mserp_employmentstartdate | Date time offset | Read-only |
| Employmenttype | mserp_employmenttype | Enum | Read-only |
| Partynumber | mserp_partynumber | String | Read-only |
| Dataareaid | mserp_dataareaid | String | Read-only |
| Gender | mserp_gender | Enum | Read-only |
| Legalentityid | mserp_legalentityid | String | Read-only |
| Person Bigint | mserp_person_bigint | Int64 | Read-only |
| Identificationtypeid | mserp_identificationtypeid | String | Read-only |
| Readytopay | mserp_readytopay | Enum | Read-only |
| Employmentenddate | mserp_employmentenddate | Date time offset | Read-only |
| Employmentid | mserp_employmentid | String | Read-only |

## Example query for PayIntV1PayrollEmployeeEntity

Entity name: mserp_payintv1payrollemployeeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1payrollemployeeentities
```

**Response**

```JSON
{  
    "mserp_employmentenddate": "2154-12-31T23:59:59Z",
    "mserp_personnelnumber": "000813",
    "mserp_dataareaid": "USRT",
    "mserp_person": 68719522942,
    "mserp_birthdate": "1994-05-24T00:00:00Z",
    "mserp_identificationnumber": "",
    "mserp_employmentstartdate": "2024-02-01T00:00:00Z",
    "mserp_partynumber": "000002780",
    "mserp_legalentity_bigint": 22565422586,
    "mserp_employmenttype": 200000000,
    "mserp_gender": 200000002,
    "mserp_legalentityid": "USRT",
    "mserp_readytopay": 200000000,
    "mserp_identificationtypeid": "",
    "mserp_person_bigint": 68719522942,
    "mserp_legalentity": 22565422586,
    "mserp_employmentid": "000006821"
}
```
