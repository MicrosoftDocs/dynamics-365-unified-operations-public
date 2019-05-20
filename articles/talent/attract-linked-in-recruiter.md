---
# required metadata

title: Source candidates with LinkedIn Recruiter
description: Use the LinkedIn integration provided by Microsoft Dynamics 365 for Talent - Attract to source job candidates through LinkedIn Recruiter.
author: andreabichsel
manager: AnnBe
ms.date: 05/20/2019
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
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Source candidates with LinkedIn Recruiter
[!include[banner](../includes/banner.md)]

LinkedIn is the world’s largest talent database and often the primary system that recruiters use to find, communicate with, and source candidates for their positions. Integration between Dynamics 365 for Talent: Attract and LinkedIn Recruiter makes it easier for recruiters to find and hire top candidates, and to sync data between Attract and LinkedIn.


## Using LinkedIn Recruiter capabilities






After LinkedIn Recruiter capabilities has been enabled by the Attract Admin it is available for hiring managers and recruiters to access. To use these capabilities, connect your LinkedIn account under **User Settings**. Several capabilities will be available after both the Admin and User settings have been connected.

### In-ATS profile widget

You can view the candidate’s LinkedIn profile in Attract. The LinkedIn widget will display the candidate profile when the ATS information matches the LinkedIn information of its users.

To view a profile, go the candidate profile either from a job or talent pool. In the candidate profile, select the **LinkedIn** tab and the profile widget will load. You can also save the candidate to your LinkedIn Recruiter projects from this page.
1. If LinkedIn found the match based on email and LinkedIn member ID (exact match), the candidate's profile will be shown. The user still has an option to link/unlink the profile.

2. If LinkedIn cannot find the candidate based on their email or member ID, it will show a list of possible candidate matches based on candidate name and the user can choose one of them and link the profile.  

3. If LinkedIn cannot find any candidate based on the name, it will return that no match was found.

### 1-click export 

While sourcing candidates in LinkedIn, you can 1-click export the candidate to
the jobs that you currently have open. Complete the following steps for a 1-click export. Before you complete these steps, verify that you are a assigned the role of Hiring manager or Recruiter for the job and that the job has a **Prospect** stage.

1.  Create the job, assign the appropriate roles, and activate the job.

2.  When the job is activated, navigate to LinkedIn Recruiter.

3.  Find the candidate that you are looking for and go to their profile.

4.  Using the job search box in the contact card, find the job using the title or the Job ID that was activated in Attract. If you don’t find the job, click **Change ATS** to find the correct Attract instance.

5. After the job is selected, click **Export**. The candidate is now fetched by Attract.

6.  Go to Attract and open the respective job. You will find the candidate that you just exported in the **Prospect** stage of the job.

### In-ATS indicator 

Using LinkedIn recruiter, you can track whether a candidate has applied to other jobs in your organization, look at where they are in different stages of job applications, and view the feedback and comments from Attract in LinkedIn Recruiter.

1.  Open LinkedIn Recruiter and locate the candidate profile that you are looking for.

2.  Scroll down to view the **In-ATS** section on the candidate’s profile.

3.  You can use this widget to view all of the information about the candidate that’s present in Attract from within the LinkedIn Recruiter view.

4.  Select the **Jobs & Statuses** tab to see jobs they are part of, the latest status, and how they have been moving against each job.

5.  Select the **Interview Feedback** tab to see feedback that the interviewers have submitted in Attract.

6.  Select the **Notes** tab to see notes that have been captured for this applicant in Attract.

> [!NOTE]
> Candidate and application data will not be synced to LinkedIn Recruiter if the candidate hasn't moved past the prospect stage.

### InMail history

The LinkedIn InMail history is available with contract-level access with LinkedIn Recruiter. When it is enabled, you can view your entire InMail history with the candidate. You can also see who else from your organization has exchanged InMail with the candidate, 
however you can't view the messages between them.

To view InMail history, go to a candidate’s profile, go to the **LinkedIn** tab and scroll to the bottom of the page to view the history. You can view InMail history if you have had a discussion with the candidate. The messages from InMail will sync with
Attract every couple of hours.

### Notes history 

The LinkedIn notes history is available with contract-level access with LinkedIn Recruiter. When it is enabled, you can view the notes that have been captured about the candidate by different recruiters from your organization.

To view Notes history, go to a candidate’s profile, go to the **LinkedIn** tab
and scroll to the bottom of the page to view the history. You can view all the
notes about the candidate from LinkedIn Recruiter.

### InMail stub profile

The InMail stub profile is available with contract-level access with LinkedIn Recruiter. If candidates agree to share their LinkedIn profiles with any user in your organization, you can track the candidates in Attract and a new candidate record will be created for each candidate. You can view candidate's email address if the candidate already exists in the system with an email address or has chosen to share their address with the recruiter.

To view the list of candidates, go to **Talent pools** to see a system-created LinkedIn talent pool. This talent pool contains the list candidates and their stub profiles as received from LinkedIn, showing the candidate's first name and last name. The candidate’s email ID will be displayed if the candidate had chosen to share their email address.

## See also

[Set up integration with LinkedIn](./attract-admin-linkedin.md)
[Create jobs](./creating-jobs-attract.md)
[Post jobs to external sites from Attract](./posting-jobs-external.md)