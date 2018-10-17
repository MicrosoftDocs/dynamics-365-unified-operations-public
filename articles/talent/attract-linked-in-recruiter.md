---
# required metadata

title: Sourcing with LinkedIn Recruiter
description: This topic provides information about using machine learning to get job and job candidate recommendations.
author: 
manager: AnnBe
ms.date: 10/15/2018
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
Attract Admin view to start LinkedIn Recruiter integration# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Sourcing with LinkedIn Recruiter
[!include[banner](../includes/banner.md)]

LinkedIn is the world’s largest talent database and often the primary system that recruiters use to find, communicate with, and source candidates for the jobs that recruiters are looking to fill. LinkedIn Recruiter integration with Dynamics 365 for
Talent: Attract makes it easier for users to hire using the Attract and keep the data in sync between their two systems of choice.

> [!NOTE]
> You need the Comprehensive Hiring Add-On along with LinkedIn Recruiter seats
to be able to use LinkedIn Recruiter integration with Attract.

## Set up LinkedIn Recruiter with Attract 

Before you can use the LinkedIn Recruiter capabilities, you must configure Contract-level or Company-level access with your Attract instance. To complete the configuration process, you also need to work with the user who is an Admin on your LinkedIn Recruiter contract. Steps to configure LinkedIn Recruiter with Attract are as follows:

1.  Log in to Attract as an Attract Admin and navigate to Admin Settings

2.  Go to the **LinkedIn Integration** tab from the left navigation panel.

[![Attract Admin view to start LinkedIn Recruiter integration](./media/LinkedInConnect.png)](./media/LinkedInConnect.png)

3.  Use the **Connect** button to start setting up the integration. You will be
    taken through a LinkedIn Sign-in process.

4.  If you have seat(s) on multiple LinkedIn Contracts, select the one that you
    would like to connect to the attract system. If you have a seat on only one
    LinkedIn contract, this step will be skipped.

5.  The LinkedIn widget will now load in your Admin Settings with the list of
    integrations shown. Click “Request” under Recruiter System Connect.

[![Attract Admin view to Request LinkedIn Recruiter integration](./media/RequestLinkedInRSC.png)](./media/RequestLinkedInRSC.png)

6.  Once the integration has been requested from Attract, it will show as
    “Partner ready” and is ready to be turned on from Recruiter Admin Settings.
    If you see “Notify partner” on this page, wait a few second and click the
    “Notify partner” button and refresh the page. It should now show as “Partner
    ready”

[![Attract Admin view to indicate Attract side of requests have been completed](./media/PartnerReadyRSC.png)](./media/PartnerReadyRSC.png)

6.  To complete the next step, you need to have an Admin privilege on your
    LinkedIn Recruiter Contract as well.

7.  Log in to LinkedIn using the Admin account, navigate to LinkedIn Recruiter
    on top right and go to Admin Settings under the More menu at the top.

8.  Click on the ATS Tab.

9.  You will see your Attract system listed there showing a couple of options
    which can be turned on.

10. Choose the Company-level access if you want to enable only 1-Click Export,
    In-ATS indicator and the In-ATS Profile Widget. You can choose the
    Contract-level access if you want to enable all of Company-level access
    features plus InMail history, Notes history and the InMail stub profile
    access as well.

11.  Turn on the desired access level from your LinkedIn Recruiter Admin-ATS
    settings

[![Turn on Attract integration from LinkedIn Recruiter Admin view](./media/EnableRSC.png)](./media/EnableRSC.png)

12. Navigate back to Attract Admin Settings as an AttractAdmin and go to the
    LinkedIn integration tab. You should now see the LinkedIn widget load
    showing **Enabled** with the kind of access level turned on.

[![LinkedIn Recruiter integration complete](./media/RSCSetupComplete.png)](./media/RSCSetupComplete.png)

## Using LinkedIn Recruiter capabilities

Once LinkedIn Recruiter capabilities has been enabled by the Attract Admin – it
is now available for hiring managers and recruiters as well. To use these
capabilities, connect your LinkedIn account under **User Settings**. There are
several capabilities available, once both the Admin and User settings have been
connected.

### In-ATS profile widget

You can view the candidate’s LinkedIn profile within Attract. The LinkedIn
widget will display the candidate profile when the ATS information matches the
LinkedIn information of its users.

To view this, go the Candidate profile either from a job or Talent Pools. Once
in the candidate profile, navigate to the LinkedIn tab and the profile widget
will load. Using the profile widget, you can indicate if this is indeed the
right match, if not find the correct person. You can also save the candidate to
your LinkedIn Recruiter projects from this page.

### 1-Click export 

While sourcing candidates in LinkedIn, you can 1-click export the candidate to
the jobs that you currently have open as well. Steps to follow for 1-click
export are as follows:

1.  Ensure that you are either a Hiring Manager or a recruiter on the job and
    the job has a prospect stage.

2.  Create the job, assign the right roles and activate the job.

3.  Once the job is activated, navigate to LinkedIn Recruiter.

4.  Find the candidate that you are looking for and go to their profile.

5.  Using the job search box in the contact card, find the job using the title
    or the Job ID that was activated in Attract.

6.  If you don’t find the job, click **Change ATS** to find the right Attract
    instance.

7.  Once the right job is selected, click Export

8.  The candidate is now fetched by Attract.

9.  Go to Attract and open the respective job.

10. You will find the candidate you just exported in the Prospect stage of the
    job.

### In-ATS indicator 

Using LinkedIn recruiter, you can also track whether a candidate has applied to
other jobs in your organization, look at where they are in different stages of
jobs and view the feedback and comments from Attract in LinkedIn Recruiter.

1.  Open LinkedIn Recruiter

2.  Find the candidate profile you are looking for

3.  Scroll down to view the **In-ATS** section on the candidate’s profile.

4.  You can use this widget to view all the information about the candidate
    that’s present in Attract from within the LinkedIn Recruiter view itself.

5.  View the **Jobs & Statuses** tab to see the jobs they are part of the latest
    status and how they have been moving against each job.

6.  View the **Interview Feedback** tab to see the feedback that the interviewers
    may have submitted in Attract.

7.  View the **Notes** tab to see the notes that may have been captured for this
    applicant in Attract.

### InMail history

The LinkedIn InMail history is available with Contract-level access with
LinkedIn Recruiter. Once enabled, you can view your entire InMail history with the candidate. 
You can also see who else from your organization has exchanged InMail with the candidate. 
However, you cannot see the messages between them.

To view InMail history, go to a candidate’s profile, navigate to the LinkedIn
tab and scroll to the bottom of the page to view the history. You can view the
InMail history only if the candidate has responded to your request and chosen to
share their profile with you in LinkedIn. The messages from InMail sync with
Attract every couple of hours.

### Notes history 

The LinkedIn Notes history is available with Contract-level access with LinkedIn
Recruiter. Once enabled, you can view the notes that have been captured about
the candidate by different recruiters over in LinkedIn from your organization.

To view Notes history, go to a candidate’s profile, navigate to the LinkedIn tab
and scroll to the bottom of the page to view the history. You can view all the
notes about the candidate from LinkedIn Recruiter.

### InMail stub profile

The InMail Stub profile is available with Contract-level access with LinkedIn
Recruiter. Once a candidate has consented to share their profile via LinkedIn
with any user in your organization, you can keep track of all these candidates
in Attract and a new candidate record is created for these candidates.

To view this list of candidates, go to Talent pools and you will have a
system-created LinkedIn Talent Pool. This talent pool contains the list of all
the candidates and their stub profiles as received from LinkedIn which will have
their first name and last name. The candidate’s email id will be displayed if
the candidate had chosen to share their email address with the user as well.
