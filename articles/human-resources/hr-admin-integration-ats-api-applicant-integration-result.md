---
# required metadata

title: Applicant integration result
description: This topic describes the Applicant integration result option set for Dynamics 365 Human Resources.
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

# Applicant integration result


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Applicant integration result option set for Dynamics 365 Human Resources.

Physical name: mshr_hcmapplicantintegrationresult

This enumeration provides status for a candidate record.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Not processed | Candidate is still under consideration. |
| 200000001 | Hired | The candidate has been hired. |
| 200000002 | Not hired | Decision was made to not hire the candidate. |
| 200000003 | Dismissed | The candidate was dismissed from consideration. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
