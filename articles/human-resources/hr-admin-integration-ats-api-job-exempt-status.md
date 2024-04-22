---
# required metadata

title: Job exempt status
description: This article describes the Job exempt status option set for Dynamics 365 Human Resources.
author: jaredha
ms.date: 02/05/2021
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
ms.author: jaredha
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: Human Resources
---

# Job exempt status



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Job exempt status option set for Dynamics 365 Human Resources.

Physical name: cdm_jobexemptstatus

This enumeration specifies the option set for FLSA job exempt status values. This is provided in the existing cdm_jobexemptstatus option set.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Exempt | The job has an exempt status based on FLSA guidelines. |
| 200000001 | Non-Exempt | The job has a nonexempt status based on FLSA guidelines. |
| 200000002 | Does Not Apply | FLSA status guidelines don't apply to the job. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Recruiting request](hr-admin-integration-ats-api-recruiting-request-example-query.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
