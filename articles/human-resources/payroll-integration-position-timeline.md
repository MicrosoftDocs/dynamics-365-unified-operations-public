---
# required metadata

title: Position Timeline entity
description: This article provides details and an example query for the HCM Position Timeline entity in Microsoft Dynamics 365 Human Resources.
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

# Position Timeline entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Position Timeline entity (PayIntV1HcmPositionTimelineEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the hcm position timeline.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Jobfunctionid | mserp_jobfunctionid | String | Read-only |
| Marketminimumpay | mserp_marketminimumpay | Real | Read-only |
| Positionworkerassignmentvalidto | mserp_positionworkerassignmentvalidto | Date time offset | Read-only |
| Marketmaximumpay | mserp_marketmaximumpay | Real | Read-only |
| Jobdetailcreateddatetime | mserp_jobdetailcreateddatetime | Date time offset | Read-only |
| Jobdetailmodifieddatetime | mserp_jobdetailmodifieddatetime | Date time offset | Read-only |
| Jobdetailvalidfrom | mserp_jobdetailvalidfrom | Date time offset | Read-only |
| Marketsource | mserp_marketsource | String | Read-only |
| Jobdetailmodifiedby | mserp_jobdetailmodifiedby | String | Read-only |
| Payrollnormalhours | mserp_payrollnormalhours | Real | Read-only |
| Marketcontrolpay | mserp_marketcontrolpay | Real | Read-only |
| Note | mserp_note | String | Read-only |
| Jobdetailvalidto | mserp_jobdetailvalidto | Date time offset | Read-only |
| Payrollpositiondetailsvalidto | mserp_payrollpositiondetailsvalidto | Date time offset | Read-only |
| Payrollpositiondetailsvalidfrom | mserp_payrollpositiondetailsvalidfrom | Date time offset | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Jobtypeid | mserp_jobtypeid | String | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Jobid | mserp_jobid | String | Read-only |
| Departmentnumber | mserp_departmentnumber | String | Read-only |
| Jobdetaildescription | mserp_jobdetaildescription | String | Read-only |
| Defaultfulltimeequivalency | mserp_defaultfulltimeequivalency | Real | Read-only |
| Positionid | mserp_positionid | String | Read-only |
| Compensationlevelid | mserp_compensationlevelid | String | Read-only |
| Availableforassignment | mserp_availableforassignment | Date time offset | Read-only |
| Positiontypeid | mserp_positiontypeid | String | Read-only |
| Externalsurveycode | mserp_externalsurveycode | String | Read-only |
| Titleid | mserp_titleid | String | Read-only |
| Paycycleid | mserp_paycycleid | String | Read-only |
| Description | mserp_description | String | Read-only |
| Positionworkerassignmentmodifiedby | mserp_positionworkerassignmentmodifiedby | String | Read-only |
| Surveycompanyid | mserp_surveycompanyid | String | Read-only |
| Positioncreateddatetime | mserp_positioncreateddatetime | Date time offset | Read-only |
| Reasoncodeid | mserp_reasoncodeid | String | Read-only |
| Positioncreatedby | mserp_positioncreatedby | String | Read-only |
| Positiondetailvalidto | mserp_positiondetailvalidto | Date time offset | Read-only |
| Positionworkerassignmentcreatedby | mserp_positionworkerassignmentcreatedby | String | Read-only |
| Positiondetailcreateddatetime | mserp_positiondetailcreateddatetime | Date time offset | Read-only |
| Positionmodifieddatetime | mserp_positionmodifieddatetime | Date time offset | Read-only |
| Positiondetailcreatedby | mserp_positiondetailcreatedby | String | Read-only |
| Validto | mserp_validto | Date time offset | Read-only |
| Positiondetailmodifieddatetime | mserp_positiondetailmodifieddatetime | Date time offset | Read-only |
| Positionworkerassignmentcreateddatetime | mserp_positionworkerassignmentcreateddatetime | Date time offset | Read-only |
| Positiondetailmodifiedby | mserp_positiondetailmodifiedby | String | Read-only |
| Positionworkerassignmentvalidfrom | mserp_positionworkerassignmentvalidfrom | Date time offset | Read-only |
| Positionmodifiedby | mserp_positionmodifiedby | String | Read-only |
| Jobdetailcreatedby | mserp_jobdetailcreatedby | String | Read-only |
| Positionworkerassignmentmodifieddatetime | mserp_positionworkerassignmentmodifieddatetime | Date time offset | Read-only |
| Positiondetailvalidfrom | mserp_positiondetailvalidfrom | Date time offset | Read-only |
| Fulltimeequivalency | mserp_fulltimeequivalency | Real | Read-only |
| Complocationid | mserp_complocationid | String | Read-only |
| Paidbylegalentityid | mserp_paidbylegalentityid | String | Read-only |

## Example query for PayIntV1HcmPositionTimelineEntity

Entity name: mserp_payintv1hcmpositiontimelineentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpositiontimelineentities
```

**Response**

```JSON
{  
    "mserp_jobdetailcreatedby": "",
    "mserp_positionworkerassignmentcreatedby": "",
    "mserp_positionworkerassignmentmodifieddatetime": null,
    "mserp_positionworkerassignmentcreateddatetime": null,
    "mserp_defaultfulltimeequivalency": 0,
    "mserp_positiontypeid": "",
    "mserp_marketmaximumpay": 0,
    "mserp_positionworkerassignmentmodifiedby": "",
    "mserp_positiondetailcreatedby": "",
    "mserp_validfrom": "2005-01-01T00:00:00Z",
    "mserp_positioncreateddatetime": "2016-09-11T19:08:16Z",
    "mserp_surveycompanyid": "",
    "mserp_positiondetailvalidto": null,
    "mserp_compensationlevelid": "",
    "mserp_paidbylegalentityid": "USMF",
    "mserp_titleid": "",
    "mserp_positioncreatedby": "MIA",
    "mserp_jobdetailvalidto": null,
    "mserp_jobdetaildescription": "",
    "mserp_positionworkerassignmentvalidfrom": null,
    "mserp_externalsurveycode": "",
    "mserp_marketminimumpay": 0,
    "mserp_positiondetailmodifiedby": "",
    "mserp_payrollpositiondetailsvalidto": "2154-12-31T00:00:00Z",
    "mserp_positionid": "000001",
    "mserp_marketsource": "",
    "mserp_positiondetailvalidfrom": null,
    "mserp_positionmodifieddatetime": "2016-09-11T19:08:16Z",
    "mserp_positiondetailcreateddatetime": null,
    "mserp_reasoncodeid": "",
    "mserp_personnelnumber": "",
    "mserp_marketcontrolpay": 0,
    "mserp_payrollnormalhours": 2080,
    "mserp_note": "",
    "mserp_availableforassignment": null,
    "mserp_fulltimeequivalency": 0,
    "mserp_positionmodifiedby": "MIA",
    "mserp_jobfunctionid": "",
    "mserp_validto": "2004-12-31T23:59:59Z",
    "mserp_paycycleid": "w",
    "mserp_jobdetailmodifiedby": "",
    "mserp_jobdetailvalidfrom": null,
    "mserp_positionworkerassignmentvalidto": null,
    "mserp_jobid": "",
    "mserp_positiondetailmodifieddatetime": null,
    "mserp_description": "",
    "mserp_jobtypeid": "",
    "mserp_jobdetailcreateddatetime": null,
    "mserp_jobdetailmodifieddatetime": null,
    "mserp_complocationid": "",
    "mserp_payrollpositiondetailsvalidfrom": "2005-01-01T00:00:00Z",
    "mserp_departmentnumber": ""
}
```
