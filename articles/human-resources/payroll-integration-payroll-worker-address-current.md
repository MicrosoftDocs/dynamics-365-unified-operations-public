---
# required metadata

title: Payroll Worker Address Current entity
description: This article provides details and an example query for the Payroll Worker Address Current entity in Microsoft Dynamics 365 Human Resources.
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

# Payroll Worker Address Current entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Payroll Worker Address Current entity (PayIntV1PayrollWorkerAddressCurrentEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the current address for payroll worker.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Islivedinaddress | mserp_islivedinaddress | Enum | Read-only |
| Street | mserp_street | String | Read-only |
| Zipcode | mserp_zipcode | String | Read-only |
| Postaladdressvalidfrom | mserp_postaladdressvalidfrom | Date time offset | Read-only |
| City | mserp_city | String | Read-only |
| State | mserp_state | String | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Postaladdressvalidto | mserp_postaladdressvalidto | Date time offset | Read-only |
| Assignmentdate | mserp_assignmentdate | Date time offset | Read-only |
| County | mserp_county | String | Read-only |
| Locationid | mserp_locationid | String | Read-only |
| Isworkedinaddress | mserp_isworkedinaddress | Enum | Read-only |
| Countryregionid | mserp_countryregionid | String | Read-only |

## Example query for PayIntV1PayrollWorkerAddressCurrentEntity

Entity name: mserp_payintv1payrollworkeraddresscurrententities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1payrollworkeraddresscurrententities
```

**Response**

```JSON
{  
    "mserp_islivedinaddress": 200000000,
    "mserp_street": "123 Ash Street",
    "mserp_zipcode": "94115",
    "mserp_postaladdressvalidfrom": "2024-01-01T00:00:00Z",
    "mserp_city": "Oakland",
    "mserp_state": "CA",
    "mserp_personnelnumber": "000001",
    "mserp_postaladdressvalidto": "2024-01-01T00:00:00Z",
    "mserp_assignmentdate": "2024-01-01T00:00:00Z",
    "mserp_county": "SAN FRANCI",
    "mserp_locationid": "000000551",
    "mserp_isworkedinaddress": 200000001,
    "mserp_countryregionid": "USA"
}
```
