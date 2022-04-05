---
# required metadata

title: Recruiting request status
description: This topic describes the Recruiting request status option set for Dynamics 365 Human Resources.
author: jaredha
ms.date: 02/05/2021
ms.topic: article
ms.prod: 
ms.technology: 

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

# Recruiting request status


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Recruiting request status option set for Dynamics 365 Human Resources.

Physical name: mshr_hcmrecruitingrequeststatus

This enumeration provides the option set for the status values of a RecruitingRequest.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Draft | The request is in draft and isn't ready for active recruiting. |
| 200000001 | In Review | The request has been submitted and is being routed for approval by workflow. Only available when workflow is enabled. |
| 200000002 | Pending | The request is pending workflow action. Only available when workflow is enabled. |
| 200000003 | Canceled | The request has been canceled. Only available when workflow is enabled. |
| 200000004 | Denied | The request has been denied. Only available when workflow is enabled. |
| 200000005 | Active | Any workflow is completed and approved, and the request is ready for active recruiting. |
| 200000006 | Closed | The recruiting request is closed. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Recruiting request](hr-admin-integration-ats-api-recruiting-request-example-query.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
