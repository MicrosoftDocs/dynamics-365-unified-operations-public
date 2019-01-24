---
title: Career site functionality in Attract
author: josaw
---

Career site functionality in Attract
====================================

[!include [banner](includes/banner.md)]

This article provides an overview of the candidate-facing career site
functionality in Microsoft Dynamics 365 for Talent: Attract. It also explains
how to set up this functionality.

Overview
--------

Attract provides one career site for each environment in a tenant. For example,
if an organization has a development environment and a test environment, one
career site is provisioned for the development environment, and another career
site is provisioned for the test environment. Each career site is **completely
isolated** and has its own authentication mechanism. Jobs and candidate profiles
aren't shared between career sites.

By default, the career site is public. Therefore, candidates can view all jobs
that are marked as external without having to sign in. However, all other
actions require that candidates sign in.

Career site managements
-----------------------

To set the values for the below items, sign in to Attract as an administrator,
select **Admin center** on the **Settings** menu (the gear symbol), and then
select the **Company information** tab.

-   **Organization name:** The organization name appears on the navigation bar
    at the top of the career site. By selecting the organization name,
    candidates go to a page that lists all open jobs.

-   **Organization logo:** An image of the organization's logo appears in the
    upper left of the career site. By selecting the logo image, candidates go to
    a page that lists all open jobs.

    >   [!NOTE] The logo image that appears on the career site has a fixed
    >   height of 20 pixels (px). The image that you add in the Admin center is
    >   scaled to fit. Therefore, depending on the image, the width might
    >   change.

To set the values for the below items, sign in to Attract as an administrator,
select **Admin center** on the **Settings** menu (the gear symbol), and then
select the **Career site management** tab.

-   **Search Engine Optimization:** If enabled, all jobs posted to Attract
    career site going forward will be searchable via popular search engines like
    Bing and Google.

    >   [!NOTE] You may see some delay between turning this setting on and
    >   search results lighting up, depending on the search engine you are
    >   using.

-   **Terms and conditions:** When candidates apply to a job through the Attract
    career site, organizations can setup terms and conditions to which the
    candidate must agree before submitting a job application. To set this up,
    first switch the terms and conditions option to on, then specify a short
    optional message and finally specify a link pointing candidates to your
    terms and conditions page. A preview of how this will be displayed to
    candidate is shown below the settings. Once setup, candidates have to
    mandatorily agree to the terms and conditions before submitting an
    application.

Career site URLs
----------------

The following are the commonly needed career sire URLs are how to access them.

-   **Career site home page URL:** To view the career site home page URL, sign
    in to Attract as an administrator, select Admin center on the Settings menu
    (the gear symbol), and then select the Career site management tab.

-   **Individual job post apply URL:** When you [post an external
    job](./Creating-jobs-Attract.md#postings) for the first time, you can copy
    the **Apply** link from the Attract application. The URL for this link will
    be in the following format:
    [https://jobs.talent.dynamics.com/jobs/\<company_name\>/\<environment_number\>/\<job_number\>/apply](https://jobs.talent.dynamics.com/jobs/%3ccompany_name%3e/%3cenvironment_number%3e/%3cjob_number%3e/apply)

-   **Individual job post URL:** The URL of the job post is a substring of the
    Apply URL. It consists of everything up through the job number. Therefore,
    for the preceding Apply URL, the job post URL is
    [https://jobs.talent.dynamics.com/jobs/\<company_name\>/\<environment_number\>/\<job_number\>](https://jobs.talent.dynamics.com/jobs/%3ccompany_name%3e/%3cenvironment_number%3e/%3cjob_number%3e)

Authentication options
----------------------

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
will be unsuccessful if the employee tries to use his or her Azure AD
credentials from Contoso Ltd.

Create and maintain a profile
-----------------------------

After candidates sign in to the career site, they can select **My profile** on
the navigation bar at the top of the page to create and maintain their profile.
The profile includes personal information, information about work experience,
education details, documents, links, and information about skill sets. After a
profile is created, it can be used to apply for jobs that the candidate is
interested in. Profiles also help Attract recommend the right jobs to
candidates.

>   [!NOTE] If a candidate uses an email id to login using one of the
>   authentication providers above, that email id is defaulted as the contact
>   email id associated with the profile. However, the latter can be changed at
>   any time is completely independent of the former. Attract will always use
>   the contact email id associate with your profile for all email
>   communications.

Find the right job
------------------

On the job list page, candidates can search for a specific job by entering
search terms. The search functionality looks for the search terms in job titles
and job descriptions, and shows relevant jobs as results. Candidates can filter
the results at any time, based on the job location or job function.

Candidates can also view a set of recommended jobs on the career site. The jobs
that are recommended to a candidate are based on the candidate's past
applications, profile, and resumes.

>   [!NOTE] Job recommendations are shown only if at least 10 jobs are posted on
>   the career site, and if the candidate has completed his or her profile.

Apply for jobs
--------------

After candidates find the right job, they can apply by using the **Apply**
button on the job details page. At this point, candidates can either create a
brand-new profile or review the information in their existing profile.
Candidates can also upload a resume, as required, and then submit the job
application.

Check application status
------------------------

After candidates apply for one or more jobs, they can select **Applications** on
the navigation bar at the top of the page to view their open and closed
applications. When candidates open one of their applications, they see the
current stage and any pending action items that they must complete. For example,
if a candidate must provide potential dates for an in-person interview, the page
shows his or her options.

Internal jobs
-------------

Currently, jobs that are marked as internal and posted to the Attract career
site don't appear on the career site. They are accessible only via the direct
**Apply** URL that can be copied from the Attract application.
