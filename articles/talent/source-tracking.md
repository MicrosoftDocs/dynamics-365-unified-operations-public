---
# required metadata

title: Source tracking
description: This topic provides information about tracking the source for candidate profiles and applications. 
author: hachandr
manager: AnnBe
ms.date: 03/18/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Source tracking 
================

[!include[banner](../includes/banner.md)]

> [!NOTE] 
> Process templates are available with the Comprehensive hiring add-on.

> [!NOTE] 
> This feature is currently under preview. To enable it, please ask an administrator to enable it via Feature Management in Attract’s Admin Center.

With source tracking, your organization can identify how your candidates first
land in Attract and how an applicant discovered the job they applied to. This
information is therefore available in the candidate profile as well as the
application. You can view the source of an application in the Application
activity details under the Activity tab as well as part of the application
history available under Profile in talent pools. The candidate profile source
can be found among the candidate details under the Profile tab in both
applications and talent pools.

We have a pre-configured list of common sources already set up, therefore once
you enable this feature, recruiters and hiring managers will be able to add
source information while manually adding a candidate to a job or a talent pool.

In addition, whenever a candidate applies, we will track the source of their
application automatically. This will help your organization see a breakdown of
where most applicants discover jobs and what source populates the most candidate
profiles in Attract. We will be releasing reports that show this data in
aggregate shortly.

Job boards and Social media are two types of sources that also have additional
source details. For instance, Social media breaks down into as Facebook and
Twitter. The Referral source type allows for an internal employee to be
specified as the referrer. A full breakdown of pre-configured sources is
available below.

## Pre-configured sources

-   Attract career site

-   Agency

-   Career Fair

-   Company Marketing

-   Conferences & Trade shows

-   Professional Association

-   Job board

    -   Indeed

    -   Seek

    -   CareerBuilder

    -   Google Jobs

    -   Xing

    -   Glassdoor

    -   Monster Jobs

-   Magazines & Publications

-   Social Network

    -   Facebook

    -   Twitter

-   University Recruiting

-   LinkedIn

-   Classifieds

-   Referral

-   Added by Recruiter

-   Other

## Customizing the source list 
As your organization may have other sources you would like to capture, we have
made the source list an option set that can be extended. If you would like to
customize this list, you can follow the instructions available
[here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/extensibility-attract#extending-option-sets-in-attract)
and make edits to the TalentSource entity. Please do not edit or delete the
TalentCategory enum values (not name) for Referral, LinkedIn and Other as this
will impact the UI. You need to simply extend the TalentSource enum to add other
types of sources.
