---
# required metadata

title: Job entity
description: This article provides details and an example query for the Hcm Job entity in Microsoft Dynamics 365 Human Resources.
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

# Job entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Job entity (PayIntV1HcmJobEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the job.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Function Bigint | mserp_function_bigint | Int64 | Read-only |
| Description | mserp_description | String | Read-only |
| Jobfamilyid | mserp_jobfamilyid | String | Read-only |
| Expiration | mserp_expiration | Date time offset | Read-only |
| Jobdescription | mserp_jobdescription | String | Read-only |
| Compensationreferencejob | mserp_compensationreferencejob | String | Read-only |
| Compensationlevelid | mserp_compensationlevelid | String | Read-only |
| Maximumnumberofpositions | mserp_maximumnumberofpositions | Enum | Read-only |
| Jobfamily | mserp_jobfamily | Real | Read-only |
| Titleid | mserp_titleid | String | Read-only |
| Compensationsurveycompanyid | mserp_compensationsurveycompanyid | String | Read-only |
| Marketpricelowthreshold | mserp_marketpricelowthreshold | Real | Read-only |
| Jobtypeid | mserp_jobtypeid | String | Read-only |
| Functionid | mserp_functionid | String | Read-only |
| Jobid | mserp_jobid | String | Read-only |
| Title | mserp_title | Real | Read-only |
| Compensationsurveycompany | mserp_compensationsurveycompany | Real | Read-only |
| Jobtype | mserp_jobtype | Real | Read-only |
| Function | mserp_function | Real | Read-only |
| Fulltimeequivalent | mserp_fulltimeequivalent | Real | Read-only |
| Compensationlevel | mserp_compensationlevel | Real | Read-only |
| Jobfamily Bigint | mserp_jobfamily_bigint | Int64 | Read-only |
| Paidhourly | mserp_paidhourly | Enum | Read-only |
| Effective | mserp_effective | Date time offset | Read-only |
| Marketpricesource | mserp_marketpricesource | String | Read-only |
| Allowunlimitedpositions | mserp_allowunlimitedpositions | Enum | Read-only |
| Compensationlevel Bigint | mserp_compensationlevel_bigint | Int64 | Read-only |
| Marketpricecontrolpoint | mserp_marketpricecontrolpoint | Real | Read-only |
| Title Bigint | mserp_title_bigint | Int64 | Read-only |
| Compensationsurveycompany Bigint | mserp_compensationsurveycompany_bigint | Int64 | Read-only |
| Marketpricehighthreshold | mserp_marketpricehighthreshold | Real | Read-only |
| Jobtype Bigint | mserp_jobtype_bigint | Int64 | Read-only |

## Example query for PayIntV1HcmJobEntity

Entity name: mserp_payintv1hcmjobentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobentities
```

**Response**

```JSON
{  
    "mserp_compensationsurveycompany_bigint": 11290923053,
    "mserp_fulltimeequivalent": 1,
    "mserp_compensationlevel_bigint": 16928090052,
    "mserp_jobtypeid": "Hourly",
    "mserp_jobtype_bigint": 16928090032,
    "mserp_effective": "2016-07-08T16:53:32Z",
    "mserp_compensationsurveycompany": 11290923053,
    "mserp_jobfamily_bigint": 0,
    "mserp_jobfamilyid": "",
    "mserp_function": 16928090041,
    "mserp_maximumnumberofpositions": 2147483647,
    "mserp_paidhourly": 200000000,
    "mserp_title_bigint": 22565424510,
    "mserp_jobtype": 16928090032,
    "mserp_compensationlevelid": "S2",
    "mserp_description": "Sales Assotiate - Russia",
    "mserp_compensationlevel": 16928090052,
    "mserp_titleid": "Sales Assotiate - Russia",
    "mserp_jobfamily": 0,
    "mserp_jobid": "Sales Assotiate - Russia",
    "mserp_allowunlimitedpositions": 200000001,
    "mserp_expiration": "2154-12-31T23:59:59Z",
    "mserp_compensationsurveycompanyid": "Industry1",
    "mserp_functionid": "0400",
    "mserp_marketpricecontrolpoint": 0,
    "mserp_marketpricehighthreshold": 0,
    "mserp_title": 22565424510,
    "mserp_compensationreferencejob": "Sales Associate",
    "mserp_marketpricelowthreshold": 0,
    "mserp_function_bigint": 16928090041,
    "mserp_jobdescription": "",
    "mserp_marketpricesource": ""
}
```
