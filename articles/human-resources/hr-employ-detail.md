---
# required metadata

title: Employee detail entity
description: This article provides details and an example query for the Employee detail entity in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 05/22/2024
ms.topic: article
ms.reviewer: twheeloc

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

# Employee detail entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.


This article describes the Job type entity (payintv1employmentdetailentity) for Dynamics 365 Human Resources.

Physical name: mserp_payintv1employmentdetailentity

## Description

This entity provides information about the employee details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| mserp_AdjustedWorkerStartDate AdjustedWorkerStartDate|Date Time Offset | Read-only |
| mserp_EmployerQuantity EmployerNoticeAmount|Int | Read-only |
| mserp_EmployerUnit|EmployerUnit|Enum | Read-only |
| mserp_LastDateWorked LastDateWorked|Date Time Offset | Read-only |
| mserp_TerminationDate|TransitionDate|Date Time Offset | Read-only |
| mserp_Effective|Effective|Date Time Offset | Read-only |
| mserp_Expiration|Expiration|Date Time Offset | Read-only |
| mserp_WorkerNoticeAmount WorkerNoticeAmount|Int | Read-only |
| mserp_WorkerStartDate WorkerStartDate|Date Time Offset | Read-only |
| mserp_WorkerUnitOfNotice WorkerUnitOfNotice|Enum | Read-only |
| mserp_Status|Status|Enum | Read-only |
| mserp_EmploymentStartDate EmploymentStartDate|Date Time Offset | Read-only |
| mserp_EmploymentEndDate EmploymentEndDate|Date Time Offset | Read-only |
| mserp_Company|Company|String | Read-only |
| mserp_PersonnelNumber PersonnelNumber|String | Read-only |
| mserp_WorkerType|WorkerType|Enum | Read-only |
| mserp_BenifitsEmploymentType BenefitsEmploymentType|String | Read-only |
| mserp_EmploymentCategory EmploymentCategory|String | Read-only |
| mserp_ReasonCodeId|ReasonCodeId|Int64 | Read-only |


## Example query for employment detail entity

Entity Name: mserp_payintv1employmentdetailentity

**Request**

```HTTPCopy
GET \[Organizaton URI\]/api/data/v9.1/payintv1employmentdetailentity
```

**Response**

```JSON
{
"mserp_employerquantity": 0,
"mserp_employerunit": 200000000,
"mserp_effective": "2012-09-11T20:30:58Z",
"mserp_expiration": "2154-12-31T23:59:59Z",
"mserp_workernoticeamount": 0,
"mserp_workerstartdate": "2010-02-01T08:00:00Z",
"mserp_workerunitofnotice": 200000000,
"mserp_status": 200000000,
"mserp_employmentstartdate": "2006-02-01T08:00:00Z",
"mserp_employmentenddate": "2154-12-31T23:59:59Z",
"mserp_company": "USMF",
"mserp_personnelnumber": "000001",
"mserp_workertype": 200000000,
"mserp_benifitsemploymenttype": "",
"mserp_employmentcategory": "",
"mserp_reasoncodeid": 0,
"mserp_reasoncodeid_bigint": 0,
"mserp_adjustedworkerstartdate": null,
"mserp_terminationdate": null,
"mserp_lastdateworked": null,
}
```
