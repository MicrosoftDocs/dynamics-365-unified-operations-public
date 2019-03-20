---

# required metadata

title:  Career site functionality in Attract
description: This topic provides an overview of the candidate-facing career site functionality in Attract.
author: hasrivas
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
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: hasrivas
ms.search.validFrom: 2019-02-12
ms.dyn365.ops.version: AX 7.1.0, Talent April 2018 update


---

# Career site functionality in Attract

[!include[banner](../includes/banner.md)]

This topic provides an overview of the candidate-facing career site
functionality in Microsoft Dynamics 365 for Talent: Attract. It also explains
how to set up this functionality.

Attract provides one career site for each environment in a tenant. For example,
if an organization has a development environment and a test environment, one
career site is provisioned for the development environment, and another career
site is provisioned for the test environment. Each career site is completely
isolated and has its own authentication mechanism. Jobs and candidate profiles
aren't shared between career sites.

By default, the career site is public. Therefore, candidates can view all jobs
that are marked as external without having to sign in. However, all other
actions require that candidates sign in.

## Career site management

To set the values for the following items, sign in to Attract as an administrator,
select **Admin center** on the **Settings** menu (the gear symbol), and then
select the **Company information** tab.

-   **Organization name** - The organization name appears on the navigation bar
    at the top of the career site. By selecting the organization name,
    candidates go to a page that lists all open jobs.

-   **Organization logo** - An image of the organization's logo appears in the
    upper left of the career site. By selecting the logo image, candidates go to
    a page that lists all open jobs.

    >   [!NOTE] 
    >   The logo image that appears on the career site has a fixed
    >   height of 20 pixels (px). The image that you add in the Admin center is
    >   scaled to fit. Therefore, depending on the image, the width might
    >   change.
 
To set the values for the following items, sign in to Attract as an administrator,
select **Admin center** on the **Settings** menu, and then
select the **Career site management** tab.

-   **Search Engine Optimization** - When enabled, all public jobs posted to
    Attract career site will be searchable using search engines like Bing
    and Google.

    >   [!NOTE] 
    >   There might be a delay between turning this setting on and search
    >   results appearing, depending on the search engine that you are using.
         
## Career site URLs

The following list contains the commonly used career site URLs and how to access them.

-   **Career site home page URL** - To view the career site home page URL, sign
    in to Attract as an administrator, select **Admin center** on the **Settings** menu, and then select the **Career site management** tab.

-   **Individual job post apply URL** - When you [post an external
    job](Creating-jobs-Attract.md#postings) for the first time, you can copy
    the **Apply** link from the Attract application. The URL for this link will
    be in the following format: 
    [https://jobs.talent.dynamics.com/jobs/\<company_name\>/\<environment_number\>/\<job_number\>/apply](https://jobs.talent.dynamics.com/jobs/%3ccompany_name%3e/%3cenvironment_number%3e/%3cjob_number%3e/apply)

-   **Individual job post URL** - The URL of the job post is a substring of the
    Apply URL. It consists of everything up through the job number. Therefore,
    for the preceding Apply URL, the job post URL is
    [https://jobs.talent.dynamics.com/jobs/\<company_name\>/\<environment_number\>/\<job_number\>](https://jobs.talent.dynamics.com/jobs/%3ccompany_name%3e/%3cenvironment_number%3e/%3cjob_number%3e)

## Authentication options

Candidates have the following sign-in options for an Attract career site:

-   Personal account:

    -   LinkedIn

    -   Microsoft

    -   Google

    -   Facebook

-   Work or school account:

    -   Microsoft Azure Active Directory (Azure AD)

Azure AD sign-in is intended only for internal candidates. Therefore, it works
only for internal candidates who use their company Azure AD credentials. For
example, a candidate who is currently an employee of Contoso Ltd wants to apply
for a job in an unrelated company, Alpine Ski House. In this case, the sign-in
will be unsuccessful if the employee tries to use Azure AD
credentials from Contoso Ltd. 

Candidates are mandated to sign-in using Azure AD if the job they are trying to view/apply is listed as internal only. 

## Create and maintain a profile

After candidates sign in to the career site, they can select **My profile** on
the navigation bar at the top of the page to create and maintain their profile.
The profile includes personal information, information about work experience,
education details, documents, links, and information about skill sets. After a
profile is created, it can be used to apply for jobs that the candidate is
interested in. Profiles also help Attract recommend the right jobs to
candidates.

>   [!NOTE]
>   If a candidate uses an email ID to sign in using one of the
>   authentication providers listed above, that email ID will default to the contact
>   email ID associated with the profile. However, the latter can be changed at
>   any time and is completely independent of the former. Attract will always use
>   the contact email ID to associate with your profile for all email
>   communications.

## Find the right job

On the job list page, candidates can search for a specific job by entering
search terms. The search functionality looks for the search terms in job titles
and job descriptions, and shows relevant jobs as results. Candidates can filter
the results at any time, based on the job location or job function.

Candidates can also view a set of recommended jobs on the career site. The jobs
that are recommended to a candidate are based on the candidate's past
applications, profile, and resumes.

>   [!NOTE] 
>   Job recommendations are shown only if at least 10 jobs are posted on
>   the career site, and if the candidate has completed a profile.

Internal candidates are also able to view who the hiring manager and/or the recruiter for the job is in case they want to contact them further. External candidates, on the other hand, have no visibility into who are the hiring team members for any job. 

## Contact the hiring team
The ability to contact the hiring team is only available for internal candidates for all jobs, internal only or publicly posted. Candidates can choose to **Contact hiring team**  to express interest or know more about the posted job. They can pick any of the listed hiring team memebers (hiring manager or recruriters) to send the message to, along with an optional resume if they choose to attach one. Alternatively, they can also pick an existing resume document already uploaded as part of their profile.  

Once an internal candidate reaches out to the hiring team member(s), a mail is sent to the chosen recepients on candidate's behalf. At the same time, the candidate's profile is also added to the prospect stage if it's enabled for that job. Recruiters or Hiring managers will have all such candidates who reached out to them organized for them under the Prospect stage, they can they review the profiles and invite potential candidates to apply. 

Candidates are able to Apply for the job they have already contacted the hiring team member for. Once applied, they do not have the ability to contact the hiring team via the career site any more. 


## Apply for jobs

After candidates find the right job, they can apply by using the **Apply**
button on the **Job details** page. At this point, candidates can either create a
new profile or review the information in their existing profile.
Candidates can also upload a resume, as required, and then submit the job
application.

## Check application status

After candidates apply for one or more jobs, they can select **Applications** on
the navigation bar at the top of the page to view their open and closed
applications. When candidates open one of their applications, they see the
current stage and any pending action items that they must complete. For example,
if a candidate must provide potential dates for an in-person interview, the page
shows the available options.

## Internal jobs

Currently, jobs that are marked as internal and posted to the Attract career
site don't appear on the career site. They are only accessible using the direct
**Apply** URL that can be copied from the Attract application.
