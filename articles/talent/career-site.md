---
# required metadata

title: Career site functionality in Attract
description: This article provides an overview of the candidate facing career site functionality in Microsoft Dynamics 365 for Talent and instructions about how to set it up.
author: josaw
manager: AnnBe
ms.date: 10/18/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2018-10-18
ms.dyn365.ops.version: AX 7.0.0

---
# Career site functionality in Attract

[!include [banner](includes/banner.md)]

This article provides an overview of the candidate-facing career site
functionality in Microsoft Dynamics 365 for Talent: Attract, and provides instructions
for how to set up the career site.

## Overview

Attract provides one career site per environment within a tenant. For example,
if an organization has a development and a test environment, they each
will have their own career site provisioned. Each career site is **completely
isolated** with its own authentication mechanism and there is no sharing of jobs
or candidate profiles between career sites.

By default, the career site is public. A candidate can view all jobs that are
marked as external without having to log in. However, for all other actions, the
candidate will be required to login.

## Career site management

The following items on the career site are controlled by settings.

1.  Organization Name: The organization name is displayed in the text in the navigation bar on
    top of the career site and takes the candidate to the list of all open
    jobs.

2.  Organization Logo: The logo image is displayed in the top left of the career
    site and takes the candidate to the list of all open jobs.

To set the values above, log in to Attract as an administrator and navigate to **Settings \> Admin center \> Company information**.

> [!NOTE]
> The logo image in career site is shown with a fixed height of 20 px. The image is scaled to fit and the width might change based on the image.

## Career Site URL

When you [post an external job](./Creating-jobs-Attract.md#postings) for the first time, the **Apply** link can be copied from the Attract application. It will be in the following format:
[https://jobs.talent.dynamics.com/jobs/\<companyname\>/\<environment_number\>/\<job_number\>/apply](https://jobs.talent.dynamics.com/jobs/%3ccompanyname%3e/%3cenvironment_number%3e/%3cjob_number%3e/apply).

The career site URL is a substring of this URL: up to the company name (if everything in the URL after the company name is dropped). For the example above, the career site URL would be:
[https://jobs.talent.dynamics.com/jobs/\<companyname\>/](https://jobs.talent.dynamics.com/jobs/%3ccompanyname%3e/).

## Authentication options

The candidate has the following options for logging into an Attract career site.

-   Personal Account

    -   LinkedIn

    -   Microsoft

    -   Google

    -   Facebook

-   Work or school account

    -   Azure active directory

Azure active directory (AAD) login is intended solely for internal candidates. Therefore, it only works for internal candidates who use their company AAD credentials. For example, if a candidate is currently an employee of “Contoso Ltd” and wants to apply to a job in an unrelated company “Alpine Ski House”, the login will fail if the employee uses the AAD credential from “Contoso Ltd” to login.

## Create and maintain a profile

Once the candidate logs into the career site, they can click n **My profile** in the navigation bar on the top of the page to create and maintain their profile. The profile information includes personal information, work experiences, education details, documents, link and skill sets. Once a profile has been created, the profile can be used to apply for a job the candidate is interested in. The profile also helps Attract recommend the right jobs to candidates.

## Find the right job

Once a candidate arrives at the job list page, they can search for a specific job. The search looks for the search term(s) across job title and job description, and shows relevant jobs as results. Additionally, the candidate can filter the results at any time based on job location or job function.

The candidate can also view a set of recommended jobs in the careersite based on their past applications, profile, and resumes.

> [!NOTE]
> For job recommendations to show, the career site should have at least 10 posted jobs, and the candidate should have a completed profile.

## Apply for jobs

Once the candidate finds the right job, they can apply to the job using the **Apply** button on the job details page. At this point, the candidate is provided an opportunity to either create a brand-new profile or review existing profile information. The candidate can also  upload a resume if needed, andthen submit the job application.

## Check on application status

Once the candidate has applied for one or more job, they can click **“Applications** in the navigation bar on the top of the page to view their open and closed applications. On opening an application, the candidate can see the current stage and any action items that are pending from their side. For example, if they need to provide potential dates for an in-person interview, they will see their options on the page.

## Internal Jobs

Jobs that are marked as internal and posted to the Attract career site don't appear on the career site yet. They are accessible only via the direct **Apply** URL that can be copied from the Attract application.
