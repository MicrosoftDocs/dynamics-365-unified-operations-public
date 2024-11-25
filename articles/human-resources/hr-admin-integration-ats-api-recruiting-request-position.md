---
# required metadata

title: Recruiting request position
description: This article describes the Recruiting request position entity for Dynamics 365 Human Resources.
author: jaredha
ms.date: 07/09/2024
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
ms.author: ajitchandran
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: Human Resources
---

# Recruiting request position



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Recruiting request position entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmrecruitingrequestpositionentity

### Description

Describes the position or positions to fill for a recruiting request. Adding a position to the recruiting request is optional. The properties of the position are read-only, as the position properties shouldn't be different on the recruiting request than they are on the position master record. If the properties need to change, it should be done on the position master record before adding the position to the recruiting request.

### JSON representation
```json
{
    "mshr_recruitingrequestid": "String",
    "mshr_positionid": "String",
    "mshr_description": "String",
    "mshr_positiontypeid": "String",
    "mshr_status": Int,
    "mshr_departmentnumber": "String",
    "mshr_reportstopositionid": "String",
    "mshr_reportstopersonnelnumber": "String",
    "mshr_financialdimension": "String",
    "mshr_dataareaid": "String",
    "_mshr_dataareaid_id_value": "Guid",
    "mshr_primaryfield": "String",
    "_mshr_fk_recruitingrequest_id_value": "Guid",
    "_mshr_fk_position_id_value": "Guid",
    "_mshr_fk_positiontype_id_value": "Guid",
    "_mshr_fk_department_id_value": "Guid",
    "_mshr_fk_reportstoposition_id_value": "Guid",
    "_mshr_fk_reportstoworker_id_value": "Guid",
    "mshr_hcmrecruitingrequestpositionentityid": "Guid"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Recruiting Request Position Entity ID**<br>mshr_hcmrecruitingrequestpositionentityid<br>*GUID* | Read-only<br>Required |	System-generated identifier of the recruiting request position record. |
| **Recruiting Request ID**<br>mshr_recruitingrequestid<br>*String* | Write-once<br>Required | The user-readable unique identifier of the recruiting request. |
| **Recruiting Request ID Value**<br>_mshr_fk_recruitingrequest_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmrecruitingrequestentityid of mshr_hcmrecruitingrequestentity entity | System-generated identifier of the recruiting request to which the position is assigned. |
| **Position ID**<br>mshr_positionid<br>*String* | Write-once<br>Required | The user-readable unique identifier of the position. |
| **Position ID Value**<br>_mshr_fk_position_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmpositionv2entityid of mshr_hcmpositionv2entity entity | System-generated identifier of the position. |
| **Description**<br>mshr_description<br>*String* | Read-only<br>Required | The position description. |
| **Position Type ID**<br>mshr_positiontypeid<br>*String* | Read-only<br>Optional | The user-readable unique identifier of the position type for this position. |
| **Position Type ID Value**<br>_mshr_fk_positiontype_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmpositiontypeentityid of mshr_hcmpositiontypeentity entity | A system-generated unique identifier of the position type for this position. |
| **Status**<br>mshr_status<br>*RecruitingRequestPositionStatus* option set | Read/write<br>Required | Status of the position for the recruiting request. |
| **Department Number**<br>mshr_departmentnumber<br>*String* | Read-only<br>Optional<br> | The department number of the position. |
| **Department ID Value**<br>_mshr_fk_department_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_omdepartmententityid of mshr_omdepartmententity entity | System-generated unique identifier of the department of the position. |
| **Reports To Position ID**<br>mshr_reportstopositionid<br>*String* | Read-only<br>Required | The user-readable ID of the position to which the recruited position reports in the organizational hierarchy. |
| **Reports To Position ID Value**<br>_mshr_fk_reportstoposition_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmpositionv2entityid of mshr_hcmpositionv2entity entity | The system-generated ID of the position to which the recruited position reports. |
| **Reports To Personnel Number**<br>mshr_reportstopersonnelnumber<br>*String* | Read-only<br>Required | The worker ID of the worker to which the hired candidate will report. |
| **Reports To Worker ID Value**<br>_mshr_fk_reportstoworker_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmworkerbaseentityid of mshr_hcmworkerbaseentity entity | System-generated ID of the worker to which the hired candidate will report. |
| **Financial Dimension**<br>mshr_financialdimension<br>*String* | Read-only<br>Optional | The financial dimension (for example, cost center) assigned to the position. The financial dimension is assigned for each position per legal entity. Cost centers that are defined in dimensions are accessible through the mshr_dimattributeomcostcenterentity entity. |
| **Data Area ID**<br>mshr_dataareaid<br>*String* | Read/write<br>Optional | Specifies the legal entity (company) for the recruiting request position. |
| **Data Area ID Value**<br>_mshr_dataareaid_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: cdm_companyid of cdm_company entity | System-generated GUID value identifying the legal entity (company) for the recruiting request position. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Concatenation of Recruiting Request value and Position ID as another method to uniquely identify the record. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Recruiting request](hr-admin-integration-ats-api-recruiting-request-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
