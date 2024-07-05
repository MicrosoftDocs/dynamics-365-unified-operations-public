---
# required metadata

title: Applicants in the HR Recruiting app (preview)
description: This article describes applicants and activities in the HR Recruiting app in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 07/01/2024
ms.topic: article
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-12-03
ms.dyn365.ops.version: Human Resources

---

# Applicants in HR recruiting app (preview)

[This article is prerelease documentation and is subject to change.]

This article describes applicants and activities in the HR Recruiting app in Microsoft Dynamics 365 Human Resources. *Applicants* are candidates who submit applications for job vacancies. Recruiters can view applicants by going to **Job ads** \> **Applicants**.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## View the applications for a job

An application is created when a candidate applies for a job. The application includes the interview process for the candidate.

To view the applications for a job, follow these steps.

1. In the Recruiting app, select **Job ads**.
1. Select the job ad to view the applications for.
1. Select the **Applicant** tab.

## Application status

Every application has a status that indicates which phase of the application process it's currently in. There are two types of application status: *internal* and *external*.

- Internal application statuses reflect the internal process that's relevant to the recruiter. These statuses are hidden from the candidate.
- External application statuses inform the candidate about the status of their application.

The following table describes the statuses that are available.

| Scenario | Internal status | External status |
|----------|----------|----------|
| The application was submitted. | Applied | Submitted |
| The application is in progress. | In progress | In progress |
| The applicant was set to **Ready to hire**. | Ready to hire | In progress |
| The applicant was rejected. | Rejected | Rejected |
| The application was withdrawn. | Rejected | Withdrawn |

## Delete applicants

Recruiters can delete one or more applicants at a time.

To delete applicants, follow these steps.

1. Go to **Job ads** \> **Applicants** \> **Applicant**.
1. Select **Delete applicant**.

## Activities

Each application has its own activities to record information about the candidate's hiring process. Activities show the hiring template that was used when the job ad was created. Recruiters can use stages and steps to manage the application process. They can assign interviews for each stage or set of steps.

To view activities, go to **Job ads** \> **Applicants** \> **Applicant** \> **Activities**.
