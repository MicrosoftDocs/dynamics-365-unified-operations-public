Career site functionality in Attract
====================================

This article provides an overview of the candidate facing career site
functionality in Microsoft Dynamics 365 for Talent: Attract and instructions
about how to set it up.

Attract provides one career site per environment within a tenant. For example,
if an organization has a development or test Attract environments, they each
will have their own career site provisioned. Each career site is **completely
isolated** with its own authentication mechanism and there is no sharing of jobs
or candidate profiles between career sites.

The career site is public by default. The candidates can view all jobs that are
marked as external without logging in. However for all other actions, the
candidate will be requested to login.

Career site management
----------------------

The following in the career site are currently controlled by a setting.

1.  Organization Name: This is displayed in the text in the navigation bar on
    top of the career site that takes the candidate to the list of all open
    jobs.

2.  Organization Logo: This image is displayed in the top left of the career
    site and takes the candidate to the list of all open jobs.

To set these values, please login as an administrator into the Attract
application and navigate to **Settings \> Admin center \> Company information**

> [!NOTE]
> The logo image in career site is shows with a fixed height of 20 px. The
images is scaled to fit and the width might change based on the image.

### Career Site URL

When you post a job for the first time, for external jobs, the
apply link can be copied from the Attract application. It will be in the
following format:
[https://jobs.talent.dynamics.com/jobs/\<companyname\>/\<environment_number\>/\<job_number\>/apply](https://jobs.talent.dynamics.com/jobs/%3ccompanyname%3e/%3cenvironment_number%3e/%3cjob_number%3e/apply)

The career site URL is a substring of this URL until the company name if the
rest of the URL is dropped. For the example above, the career site URL would
look like:
[https://jobs.talent.dynamics.com/jobs/\<companyname\>/](https://jobs.talent.dynamics.com/jobs/%3ccompanyname%3e/).

Authentication options
----------------------

The candidate has the following options to log into a Attract career site.

-   Personal Account

    -   LinkedIn

    -   Microsoft

    -   Google

    -   Facebook

-   Work or school account

    -   Azure active directory

Azure active directory (AAD) login is intended solely for internal candidates.
Hence, it only works for internal candidates who use their company AAD
credentials. For ex: If a candidate is currently an employee of “Contoso Ltd”
and wants to apply to a job in a unrelated company “Alpine Ski House” – if
he/she uses the AAD credential from “Contoso Ltd” to login, the login will fail.

Create and maintain profile
---------------------------

Once the candidate logs into the career site, they can click on “My profile” in
the navigation bar on the top of the page to create and maintain their profile.
The profile information includes personal information, work experiences,
education details, documents, link and skill sets. Once a profile has been
created, it can be used to apply for a job the candidate is interested in. The
profile also helps Attract recommend the right jobs to candidates.

Find the right job
------------------

Once candidates arrive at the job list page, they can search for a specific job.
The search today looks for the search term(s) across job title and job
description and shows relevant jobs as results. Furthermore, the candidate can
filter the results at any time based on job location or job function.

Additionally, candidates also get to see a set of recommended jobs in the career
site based on their past applications, profile and resumes.

> [!NOTE]
> For job recommendations to show, the career site should have at least 10
posted job and the candidate should have a complete profile.

Apply to jobs
-------------

Once candidate finds the right job, he/she can apply to the job using the apply
button on the job details page. At this point, the candidate is provided an
opportunity to either create a brand-new profile or review existing profile
information. In addition to that – he/she can upload a resume if needed and
submit the job application.

Check on application status
---------------------------

Once the candidate has applied for one or more job, he/she can click on
“Applications” in the navigation bar on the top of the page to view their open
applications as well as closed application. On opening an application, the
candidate can see the current stage and any action items that are pending from
their side. For example, If they need to provide potential dates for in person
interview, the options are shown here.

Internal Jobs
-------------

Jobs that are marked as internal and posted to the Attract career site, do not
show up in the career site today. They are accessible only via the direct apply
URL that can be copied from the Attract application.
