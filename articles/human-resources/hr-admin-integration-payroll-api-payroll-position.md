---
# required metadata

title: Payroll details for Positions
description: This article provides details and an example query for the Payroll details for the Positions entity in Dynamics 365 Human Resources.
author: jcart
ms.date: 04/07/2021
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

# Payroll position



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Payroll Positions entity in Dynamics 365 Human Resources.

Physical name: mshr_payrollpositionentity.

### Description

This entity provides position-related information for a given employee.

Physical name: mshr_payrollpositionentity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Position ID**</br>mshr_positionid</br>*String* | Read-only | The ID of the position. |
| **Pay cycle ID**</br>mshr_paycycleid</br>*String* | Read-only | The pay cycle that is defined on the position. |
| **Annual regular hours**</br>annualregularhours</br>*Decimal* | Read-only | The annual regular hours that are defined on the position. |
| **Paid by legal entity**</br>paidbylegalentity</br>*String* | Read-only | The legal entity that is defined on the position and responsible for issuing payment. |
| **Valid to**</br>validto</br>*Date Time Offset* | Read-only | The date that the position details are valid to. |
| **Valid from**</br>validfrom</br>*Date Time Offset* | Read-only | The date that the position details are valid from. |
| **Primary field**</br>mshr_primaryfield</br>*String* | System generated | The primary field. |
| **Payroll position details entity ID**</br>payrollpositiondetailsentityid</br>*Guid* | Required</br>System generated. | A system-generated globally unique identifier (GUID) value to uniquely identify the position. |

## Relations

| Property value | Related entity | Navigation property | Collection type |
| --- | --- | --- | --- |
| _mshr_fk_fixedcompplan_id_value | [mshr_payrollfixedcompensationplanentity](hr-admin-integration-payroll-api-payroll-fixed-compensation-plan.md) | mshr_FK_FixedCompPlan_id | mshr_FK_PayrollFixedCompensationPlanEntity_PayrollPosition |
| _mshr_fk_hcmpositionhierarchy_id_value | mshr_hcmpositionhierarchyentity | mshr_FK_HcmPositionHierarchy_id | Not applicable |
| _mshr_fk_job_id_value | mshr_payrollpositionjobentity | mshr_FK_Job_id | mshr_FK_PayrollPositionJobEntity_Payroll |
| _mshr_fk_positionassignmentv2_id_value | mshr_hcmpositionworkerassignmentv2entity | mshr_FK_PositionAssignmentV2_id | Not applicable |

## Example query

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_payrollpositionentities?$filter=mshr_positionid eq @positionid and mshr_validfrom le @asofdate and mshr_validto ge @asofdate&@positionid='000276'&@asofdate=2021-04-01
```

**Response**

```json
{
    "mshr_positionid": "000276",
    "mshr_paycycleid": "w",
    "mshr_annualregularhours": 3000,
    "mshr_paidbylegalentity": "USMF",
    "mshr_validfrom": "2021-03-14T00:00:00Z",
    "mshr_validto": "2154-12-31T00:00:00Z",
    "mshr_primaryfield": "000276 | 3/14/2021",
    "_mshr_fk_job_id_value": "00010094-0000-0000-df00-014105000000",
    "_mshr_fk_fixedcompplan_id_value": "0000029f-0000-0000-d5ff-004105000000",
    "mshr_payrollpositionentityid": "00010097-0000-0000-df00-014105000000"
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
