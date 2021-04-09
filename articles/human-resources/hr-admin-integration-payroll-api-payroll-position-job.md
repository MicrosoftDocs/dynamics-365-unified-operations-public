---
# required metadata

title: Payroll position job
description: This topic provides details and an example query for the Payroll position job entity in Dynamics 365 Human Resources.
author: jcart
manager: tfehr
ms.date: 04/07/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Payroll position job

This topic provides details and an example query for the Payroll position job relationship entity in Dynamics 365 Human Resources.

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Job ID**<br>mshr_jobid<br>*String* | Readp-only<br>Required |The ID of the job. |
| **Valid from**<br>mshr_validto<br>*Date Time Offset* | Read-only <br>Required | Date the postion and job relationship is valid from. |
| **Valid to**<br>mshr_validto<br>*Date Time Offset* | Read-only <br>Required | Date the position and job relationship is valid to.  |
| **Position ID**<br>mshr_positionid<br>*String* | Read-only<br>Required | The ID of the position. |
| **Primary field**<br>mshr_primaryfield<br>*String* | Required<br>System generated |  |
| **Position job ID value**<br>_mshr_fk_positionjob_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key:mshr_PayrollPositionJobEntity of the mshr_payrollpositionjobentity |The ID of the job associated with the position.|
| **Fixed compensation plan ID value**<br>_mshr_fk_fixedcompplan_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_FixedCompPlan_id of mshr_payrollfixedcompensationplanentity  | The ID of the fixed compensation plan associated with the position. |
| **Payroll position job entity ID**<br>mshr_payrollpositionjobentityid<br>*Guid* | Required<br>System generated. | A system-generated GUID value to uniquely identify the job.  |

