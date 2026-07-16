---
title: Manage recruiting processes
description: Learn about manage recruiting, a concept that recruiters can use to track the steps in a recruiting process, including an overview on recruitment projects.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 06/25/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: HRMApplication, HRMRecruitingTable
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 1ad725bf-20e2-42a1-8068-111f7ddddad9
---

# Manage recruiting processes

> [!IMPORTANT]
> This article refers to the recruiting functionality as Recruitment projects. It focuses on applicants, applications, and recruitment projects.

This article describes a concept that recruiters can use to track the steps in a recruiting process. These steps include efforts to advertise open positions and recruit applicants, tracking applicant and application information, interviewing applicants, and selecting one or more candidates to fill the open positions in your organization.

## Overview

Recruitment projects can help you organize the steps you complete when filling open positions in a legal entity. An applicant is a person who applies for employment to your enterprise. An application is an applicant's expression of interest in being employed by a company. You can tie an application to a recruitment project to express interest in a specific opening. A single applicant can have multiple applications within the same legal entity or across multiple companies in your organization.

## Recruitment projects

Recruitment projects help recruiters track progress toward filling one or more open positions. The recruitment project identifies the department and job for which one or more positions are open. Recruitment projects also track the following information for open positions:

- The specific number of open positions
- The hiring manager and an alternative contact for the position
- The date that the requisition was approved
- The application deadline
- The estimated start date

The recruitment project contains the **Job ad** value that you use on the **Employee self service** page to advertise the opening. You can show the opening to employees only if the recruitment project has a **Job ad** value, the **Display on employee self service** field is set to **Yes**, the **Application deadline** field is set to a future date, and the recruitment project has a **Project status** value of **Started**. The following table lists the possible recruitment project statuses and their description.

| Status    | Description                                                                         |
|-----------|-----------------------------------------------------------------------------------------|
| Scheduled | Recruiting efforts are being prepared. Recruiting isn't yet started for this project. |
| Started   | Applications are now being accepted for the openings in this project.                   |
| Finished  | All openings for this project are filled.                                         |
| Canceled  | Recruiting is canceled for this project.                                          |

Recruiters can also record the **Media** used to advertise the opening through external outlets and track **Developments** against the project or applications.

## Applicants

An applicant is a person who applies for a job in your enterprise. All legal entities in your organization share applicants, so you have a large pool of talent to search. You can maintain competencies, references, accommodation requests, and personal information for applicants. When you create an applicant record, you also create a person record for that applicant in the global address book. Use the **Applicant** page to update the following global address book information for people who are applicants:

- Address information
- Contact information
- Identification information
- Name details
- Personal information

## Applications

Use the **Application** page to record information from employment applications that you receive. The application is the applicant's expression of interest in a job opening in your organization. To create an application, the applicant must already exist as an applicant or person in your system.

Employment applications that applicants submit on the web are either solicited applications that applicants enter in response to a job ad, or unsolicited applications. Solicited applications automatically associate with the recruitment project that the job ad created. Unsolicited applications associate with the recruitment project that you specify in the **Recruitment** area of the **Human resources parameters** page.

### Application status

The application status indicates where an application is in the recruitment process. The following table lists the possible application statuses and their description.

| Status    | Description                                                                              |
|-----------|-------------------------------------------------------------------------------------------|
| Received  | The application was received.                                                             |
| Confirmed | A notice can be sent to the applicant to confirm receipt of their application.            |
| Interview | An interview invitation can be sent to the applicant.                                     |
| Rejection | A rejection letter can be sent to the applicant.                                          |
| Canceled  | A withdrawal confirmation can be sent to the applicant. This status is assigned manually. |
| Employed  | An employment offer can be sent to the applicant.                                         |

### Correspondence actions

An application's correspondence action determines the document or email template that you use to communicate with the applicant who submitted the application. By associating **application bookmarks** with correspondence actions, you can use values from the **Application**, **Applicant**, **Interview**, and **Recruitment project** pages in your communications with applicants. By creating **application email templates** for the correspondence actions, you can quickly send emails to applicants whose applications have a specific combination of a status and a correspondence action. For example, you can send a confirmation email to all applications that have a **Status** value of **Received** and a **Correspondence action** value of **Received**. After you send the email, you have the option to automatically update the status of the applications.

## Application routing

If an application must be reviewed by several workers, use the **Application routing** page to create a worker circulation list to manage the process.

## Interviews

You can schedule **applicant interviews** from the **Applications** page. Use the **Send meeting information** button to send a calendar file with the interview schedule information to the applicant and interviewer.

## Skill mapping

Use **Skill mapping** and **Skill mapping profiles** to identify candidates who might be a good fit for an opening.

## Hiring applicants

Use the **Applications** page to hire an applicant. When you hire an applicant, the application record has a status of **Employed** and the applicant's global address book person record associates with the new worker record. Modifications to the global address book information for the new worker record also display in the applicant record. This information can help reduce data entry if the new worker ever applies for a different job within your enterprise. To hire an existing worker into a new position, select **Change position** in the **Application status** dropdown to initiate the transfer process.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
