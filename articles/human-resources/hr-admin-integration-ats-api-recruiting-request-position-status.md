---
# required metadata

title: Recruiting request position status
description: This article describes the Recruiting request position status option set for Dynamics 365 Human Resources.
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

# Recruiting request position status



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Recruiting request position status option set for Dynamics 365 Human Resources.

Physical name: mshr_hcmrecruitingrequestpositionstatus

This enumeration provides the option set for the status values of each position a recruiting request in the RecruitingRequestPosition entity.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Open | The position in the recruiting request is open for recruiting. This does not indicate that there is no currently active position assignment for the position. There may be an employee in the position at the time of recruiting. It indicates only that the position is available for recruiting in the context of the recruiting request. |
| 200000001 | Filled | A worker has been selected for assignment to the position. |
| 200000002 | Canceled | The request to recruit for this position has been canceled. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Recruiting request](hr-admin-integration-ats-api-recruiting-request-example-query.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
