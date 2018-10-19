---
# required metadata

title: Career site functionality in Attract
description: This article provides an overview of the candidate-facing career site functionality in Microsoft Dynamics 365 for Talent - Attract. It also explains how to set up this functionality.
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

This article provides an overview of the candidate-facing career site functionality in Microsoft Dynamics 365 for Talent: Attract. It also explains how to set up this functionality.

## Overview

Attract provides one career site for each environment in a tenant. For example, if an organization has a development environment and a test environment, one career site is provisioned for the development environment, and another career site is provisioned for the test environment. Each career site is **completely isolated** and has its own authentication mechanism. Jobs and candidate profiles aren't shared between career sites.

By default, the career site is public. Therefore, candidates can view all jobs that are marked as external without having to sign in. However, all other actions require that candidates sign in.

## Career site management

The following items on the career site are controlled by settings:

- **Organization name:** The organization name appears on the navigation bar at the top of the career site. By selecting the organization name, candidates go to a page that lists all open jobs.
- **Organization logo:** An image of the organization's logo appears in the upper left of the career site. By selecting the logo image, candidates go to a page that lists all open jobs.

To set the values for the organization name and logo, sign in to Attract as an administrator, select **Admin center** on the **Settings** menu (the gear symbol), and then select the **Company information** tab.

> [!NOTE]
> The logo image that appears on the career site has a fixed height of 20 pixels (px). The image that you add in the Admin center is scaled to fit. Therefore, depending on the image, the width might change.

## Career site URL

When you [post an external job](./Creating-jobs-Attract.md#postings) for the first time, you can copy the **Apply** link from the Attract application. The URL for this link will be in the following format: `https://jobs.talent.dynamics.com/jobs/<company_name>/<environment_number>/<job_number>/apply`

The URL of the career site is a substring of the **Apply** URL. It consists of everything up through the company name. Therefore, for the preceding **Apply** URL, the career site URL is `https://jobs.talent.dynamics.com/jobs/<company_name>/`.

## Authentication options

Candidates have the following sign-in options for an Attract career site:

- Personal account:

    - LinkedIn
    - Microsoft
    - Google
    - Facebook

- Work or school account:

    - Microsoft Azure Active Directory (Azure AD)

Azure AD sign-in is intended only for internal candidates. Therefore, it works only for internal candidates who use their company Azure AD credentials. For example, a candidate who is currently an employee of Contoso Ltd wants to apply for a job in an unrelated company, Alpine Ski House. In this case, the sign-in will be unsuccessful if the employee tries to use his or her Azure AD credentials from Contoso Ltd.

## Create and maintain a profile

After candidates sign in to the career site, they can select **My profile** on the navigation bar at the top of the page to create and maintain their profile. The profile includes personal information, information about work experience, education details, documents, links, and information about skill sets. After a profile is created, it can be used to apply for jobs that the candidate is interested in. Profiles also help Attract recommend the right jobs to candidates.

## Find the right job

On the job list page, candidates can search for a specific job by entering search terms. The search functionality looks for the search terms in job titles and job descriptions, and shows relevant jobs as results. Candidates can filter the results at any time, based on the job location or job function.

Candidates can also view a set of recommended jobs on the career site. The jobs that are recommended to a candidate are based on the candidate's past applications, profile, and resumes.

> [!NOTE]
> Job recommendations are shown only if at least 10 jobs are posted on the career site, and if the candidate has completed his or her profile.

## Apply for jobs

After candidates find the right job, they can apply by using the **Apply** button on the job details page. At this point, candidates can either create a brand-new profile or review the information in their existing profile. Candidates can also upload a resume, as required, and then submit the job application.

## Check application status

After candidates apply for one or more jobs, they can select **Applications** on the navigation bar at the top of the page to view their open and closed applications. When candidates open one of their applications, they see the current stage and any pending action items that they must complete. For example, if a candidate must provide potential dates for an in-person interview, the page shows his or her options.

## Internal jobs

Currently, jobs that are marked as internal and posted to the Attract career site don't appear on the career site. They are accessible only via the direct **Apply** URL that can be copied from the Attract application.
