---
# required metadata

title: What's new or changed in Dynamics 365 Talent (March 20, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 03/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-03-20
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (March 20, 2019)

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.

## Changes in Attract

### Setting the audience on activities
Activities in the system can now have the audience defined. Process-related activities (such as Interview, Schedule, Feedback, and EEO) can be set to All candidates, Internal candidates, and External candidates. Custom activities, such as Microsoft Forms, YouTube videos, and web content can be delivered to All candidates, Internal candidates, External candidates, or the hiring team.  

### Improve career site job discoverability: Search Engine Optimization
This feature enables search engine crawlers to reach and index job postings on the Attract career site. This helps candidates find jobs posted to the Attract career site using popular search engines.

### Show login hint to candidates who forgot their credentials
If a candidate forgot the social credentials they used to apply to a job while opening a link that was saved or emailed to them, they will now see a hint with the provider name and user name (obfuscated). This helps them use the correct credentials to access their job application.

### Help internal candidates explore internal jobs
An issue has been fixed where external candidates could see the name of the recruiter or the hiring manager of a job. Now only internal candidates can see the hiring team members for a job. 
It’s also easier for internal candidates to view and apply to internal only jobs. When a candidate tries to access the link to view or apply to an internal-only job, they are forced to authenticate with Azure Active Directory credentials. Internal candidates also have the ability to contact the hiring team member to express interest in or to know more about the job. This capability is available for all jobs for only internal candidates. For more information, see [Set up your career site in Microsoft Dynamics 365 Talent - Attract](./career-site.md).

### Designate silver medalists to assign high value applicants for future positions
Recruiters and hiring managers often keep a running list of applicants who were a good fit for the position but could not be extended an offer as the position was already filled. Such applicants, termed silver medalists, are valuable as they can help reduce the time to hire the next time a similar position opens up. Attract now allows recruiters and hiring managers to designate silver medalists on the applicants list if the applicant is advanced to the Offer stage. The silver medalist designation will appear on the applicants list for the job, but also in the talent pool view when these applicants are members of any of the recruiter's or hiring manager's pools. Additionally, the designation will appear in the job history as part of the talent pool profile of a candidate. You can preview this feature by having an administrator turn it on using [Feature Management in the Admin Center](https://docs.microsoft.com/dynamics365/unified-operations/talent/access-preview-feature).

### Add applicants to talent pools
It is now easier to add applicants to talent pools by surfacing a new action on the Applicants list. By selecting the **Add to talent pool** icon, the recruiter or hiring manager can choose from their list of talent pools and easily add applicants to talent pools right from the Applicants list on a job.

### Configure whether a resume is required to apply for a particular job
Based on customer feedback, recruiters can now configure whether a resume, in the form of an uploaded file, is required when applying for a particular job. This configuration is part of the Application activity, accessible in the hiring process. When enabled, every potential applicant will be prompted to upload a resume as they apply for this position. The application will not be considered complete unless a resume is uploaded. This helps reduce the noise in the applicant pool by ensuring that every applicant provides enough information to allow the recruiter to triage them.

### Candidates can apply to a job using their LinkedIn profile
Candidates who already have their current updated profile on LinkedIn can apply to jobs with just a single click using that profile.

### Track how a candidate profile originated in the system and where your applicants discover the jobs they applied for
You can now find out how a particular candidate's profile originated in Attract by looking at the profile source under candidate details on the **Profile** page of an application or talent pool profile. Similarly, you can find out how any applicant discovered the job by looking at the application source provided in the **Application activity** in the application activity feed. This information is also available in the job history in the talent pool profile. When recruiters or hiring managers add candidates manually, they will also be prompted to designate the source of the application or candidate profile. When a candidate applies for the first time, their profile source will be the same as the origin of their application. You can preview this feature by having an administrator turn it on using [Feature Management in the Admin Center](https://docs.microsoft.com/dynamics365/unified-operations/talent/access-preview-feature). Note that existing candidates and applicants won't have any source information. However, recruiters can add this information manually.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2195

### Attract integration throws duplicate record error for Applications
In this update, an issue with duplicate records has been fixed. This issue is surfaced when opening the **Personnel management** workspace.

### Unable to close form when editing name sequence
Changes have been made to correct an issue when editing the name sequence on the worker form.

## Coming soon

###  Advanced compensation security (fixed and variable)
In many organizations, the compensation and benefits managers might only have access to certain compensation records. These could be for executives or regional employees. With this change, HR can manage and maintain the compensation plans for different employee groups in the organization. You can assign security roles to fixed and variable plans that determine access to the plans and the employee data related to the plans, such as salary or bonus records. Only the roles with the access granted can process compensation for those employees.

###  Email support for alerts
With Platform update 24 for Finance and Operations, users can create alert rules that automatically dispatch email notifications to contacts when triggered by an event.

### Duplicate employee check: Interface changes
With this change, duplicates are detected as you enter name fields, and a status displays the number of duplicates found. You can select the provided link to open a new page to evaluate whether to use the detected match. The duplicates form doesn't automatically open, to avoid interrupting data entry.


