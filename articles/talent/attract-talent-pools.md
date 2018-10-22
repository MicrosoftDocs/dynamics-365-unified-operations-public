---
# required metadata

title: Source candidates by using talent pools
description: This topic explains how to create and set up talent pools in Attract.
author: 
manager: AnnBe
ms.date: 10/22/2018
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
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2018-22-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Source candidates by using talent pools

[!include[banner](../includes/banner.md)]


Recruiters and hiring managers can organize their candidates using the Talent pools functionality in Attract. Talent pools can help you keep track of and engage with all the candidates that apply for jobs at your company.

## Create and share a talent pool

Any user who has the ecruiter, hiring manager, or Attract administrator role can create talent pools. The owner of a talent pool can also share that pool with other users so that groups of users, especially recruiters, can look at a shared pool of candidates.

Contributors to a talent pool can view the list of candidates in that pool. They can also add candidates to the pool or remove candidates from it.

Follow the steps below to create and share a talent pool.

1. On the Attract home page, in the left navigation pane, select **Talent Pools**.

    The **My talent pools** tab shows all the talent pools that you have access to, with details about each. The details include the owner of the pool and the number of candidates in it.

1. In the upper right, select **+ New** to open the **Create talent pool** dialog box.
1. Enter a unique name for the talent pool.
1. To add people as contributors to the pool, find their names by using the people picker, and then add them to the list. You can share a talent pool only with users who have the recruiter, hiring manager, or Attract administrator role.
1. Select **Add** to create the talent pool.
> [!NOTE]
> You can also add contributors to a talent pool after you have created it. You can also manage access to a talent pool. For example, you can revoke a user's access to the talent pool.
> - To add contributors to an existing talent pool that you own, on the **My talent pools** tab, in the upper right of the talent pool card, select the ellipsis button (**…**), and then select **Edit**. Find the people by using the people picker, and add them to the list. 
> - To revoke a user's access to the talent pool, in the upper right of the talent pool card, select the ellipsis button (**…**), and then select **Edit**. On the **Manage access** tab, select the trash can button next to the user.

1. Select **Update** to complete and save the operation.

> [!NOTE]
> To create more than one talent pool, your organization must have the Comprehensive Hiring add-on.

## Add and remove candidates

The owner and contributors to the talent pool can add candidates to the talent pool, view the candidates in it, and remove candidates from it.

1. On the **My talent pools** tab, select a talent pool to open it.

    A list of the candidates who are part of the talent pool is shown.

1. To add candidates to the talent pool, select **+ New** in the upper right to open the **Add candidate** dialog box, and then do one of the following.

    - To add an internal candidate, you can search for the person by email address. After a successful search, the candidate's email address, first name, and last name are filled in. If you have the candidate's resume or any related documents about the candidate, you can upload them at this point. Then select **Add** to add the candidate to the talent pool.
    - To add an external candidate, manually enter his or her email address, first name, and last name. If you have the candidate's resume or any related documents, you can upload them at this point. Then select **Add** to add the candidate to the talent pool.
    - To add multiple candidates, select the **From Excel** tab. You can then download the appropriate Microsoft Excel template, enter the details for the candidates, save the Excel worksheet, and upload it to the application.

        If any errors are found in the worksheet, you will receive messages about them. You can then fix the errors and try to upload the worksheet again. When no more errors are found, select **Add** to upload the worksheet. The worksheet is processed in the background, and you'll be notified when all the candidates have been added to the talent pool.

1. To remove an existing candidate from the talent pool, in the **Action** column, select the trash can button for that candidate.

## Search and view candidate profiles

Users of a talent pool can view a candidate's profile, his or her LinkedIn information, related documents, or the candidate's whole application history. You can also search your whole candidate database for any candidate who has ever applied for any job in your organization, or who has ever been added to any talent pool.

1. Use the search field at the top of the **My talent pools** tab to search your whole candidate database.
1. Search among various profile attributes. Select the search attribute category, build a search query, and then select the right arrow button (**-\>**) to run the search.

    You can look up candidates by their name, the organization that they work for, the skills that they have been tagged for, their education history, their current job title, or the degree that they have earned, if this information is included in their profile.

    You can also create a search query that uses two or more of these attributes as criteria. Combine the criteria by using an **and** operator.

    If any candidates match your search query, they are listed in the search results.

1. To narrow down your results, you can update the search query by using the search field at the top.

    Alternatively, use the list of smart filters on the right. These smart filters are dynamically pulled in, based on the search results.

    The search results show the top 20 skills, schools, organization, and so on, that are most often found in the list of candidates. You can add more filters for any of these attributes to narrow down the search results even more.

1. After you've identified a candidate, select the row for that candidate to view his or her profile.

All users have a common view of candidate profiles. Select the row for a candidate in a set of search results or a talent pool to view his or her profile. The **Profile**  tab shows any information about skills, work experience, and educatoon that the candidate has updated from the career portal.

- You can view the contact details for the candidate. You can also edit or update the information as you require by using the **Edit details** button.

- You can add more skills tags to help identify a candidate's skills.

- You can view the candidate's whole application history. You can see all the jobs that the candidate has applied for in your organization and the status of those applications. If you're part of a job's hiring team, you can select **View** to look at the application in detail.

- The **Documents** tab shows any documents that the candidate has added from his or her profile or during job applications. This tab can be used to manage the candidate's resumes, cover letters, portfolio work, and so on. You can also use this tab to add documents.

    To view a document, select the document name in the list of documents. You can view Microsoft Word documents in the application by using Microsoft Office 365. You can also download the documents to your local computer by using the **Download** option for each document.

- The **LinkedIn** tab shows the candidate's LinkedIn information. To use this tab, you must connect your LinkedIn account in the user settings, and your environment's LinkedIn Recruiter connection must be established. For more information, see [Sourcing with LinkedIn Recruiter](./attract-linked-in-recruiter.md).

## Add candidates from a talent pool to a job

From the search results or a talent pool, you can push a candidate to any active job that you're hiring for. To push a candidate to a specific job, follow these steps.

1. Find the candidate by using the search option, and open his or her profile. Alternatively, open the talent pool from the **My talent pools** tab, search for the candidate in your talent pool, and then open his or her profile.
2. On the candidate's profile page, select **+ Add to job** in the upper right. A list of jobs that you belong to the hiring team for, as either a recruiter or a hiring manager, is shown.
3. Select the job to add the candidate to, and then select **Add**. You can also search for the job by using the search field at the top of the **Add candidate to job** dialog box.

    If prospecting was enabled for the job, the candidate is added to the Prospect stage.

    If prospecting wasn't enabled for the job, the candidate is added to the Apply stage. Depending on the job configuration, the candidate might also receive an email where they can view their application.

Add candidates from a job to a talent pool
---

Often, several good candidates for a job aren't selected. However, you don't want to lose track of them. In this case, you might want to add the candidates to a talent pool so that you can invite them to apply for other upcoming jobs.

1. Go to the job that you want to add a candidate from.
2. Select the candidate, and open his or her application.
3. On the application page, select **Add to talent pool**. A list of talent pools that you have access to is shown.
4. Select or search for the talent pool, and then select **Add** to add the candidate to that talent pool.
