---
# required metadata

title: Job Detail entity
description: This article provides details and an example query for the Hcm Job Detail entity in Microsoft Dynamics 365 Human Resources.
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

# Job Detail entity

> [!NOTE]
> The functionality that is noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Job Detail entity (PayIntV1HcmJobDetailEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about job detail.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Marketpricesource | mserp_marketpricesource | String | Read-only |
| Compensationlevelid | mserp_compensationlevelid | String | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Jobid | mserp_jobid | String | Read-only |
| Compensationreferencejob | mserp_compensationreferencejob | String | Read-only |
| Marketpricelowthreshold | mserp_marketpricelowthreshold | Real | Read-only |
| Marketpricecontrolpoint | mserp_marketpricecontrolpoint | Real | Read-only |
| Titleid | mserp_titleid | String | Read-only |
| Paidhourly | mserp_paidhourly | Enum | Read-only |
| Description | mserp_description | String | Read-only |
| Marketpricehighthreshold | mserp_marketpricehighthreshold | Real | Read-only |
| Jobtypeid | mserp_jobtypeid | String | Read-only |
| Compensationsurveycompanyid | mserp_compensationsurveycompanyid | String | Read-only |
| Jobfamilyid | mserp_jobfamilyid | String | Read-only |
| Jobdescription | mserp_jobdescription | String | Read-only |
| Fulltimeequivalent | mserp_fulltimeequivalent | Real | Read-only |
| Validto | mserp_validto | Date time offset | Read-only |
| Functionid | mserp_functionid | String | Read-only |

## Example query for PayIntV1HcmJobDetailEntity

Entity name: mserp_payintv1hcmjobdetailentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobdetailentities
```

**Response**

```JSON
{  
    "mserp_marketpricesource": "",
    "mserp_compensationlevelid": "G05",
    "mserp_validfrom": "2024-01-01T00:00:00Z",
    "mserp_jobid": "Sales Associate",
    "mserp_compensationreferencejob": "",
    "mserp_marketpricelowthreshold": 0,
    "mserp_marketpricecontrolpoint": 0,
    "mserp_titleid": "Sales Associate",
    "mserp_paidhourly": 200000000,
    "mserp_description": "Sales Associate",
    "mserp_marketpricehighthreshold": 0,
    "mserp_jobtypeid": "Hourly",
    "mserp_compensationsurveycompanyid": "",
    "mserp_jobfamilyid": "",
    "mserp_jobdescription": "",
    "mserp_fulltimeequivalent": 1,
    "mserp_validto": "2024-01-01T00:00:00Z",
    "mserp_functionid": "0400"
}
```
