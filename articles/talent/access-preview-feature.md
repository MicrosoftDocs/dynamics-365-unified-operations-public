---
# required metadata

title: Access preview features in Microsoft Dynamics 365 for Talent
description: This topic describes how an administrator can enable preview features in Microsoft Dynamics 365 for Talent, and it lists the features that are currently enabled for preview.
author: tracykeya
manager: AnnBe
ms.date: 05/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
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
# ms.search.industry: 
ms.author: trkeya
ms.search.validFrom: 2018-04-30
ms.dyn365.ops.version: AX 7.1.0, Talent April 2019 update

---

# Access preview features in Talent

[!include[banner](../includes/banner.md)]

As part of our continuous rollout of human capital management (HCM) capabilities for Microsoft Dynamics 365 for Talent, we want to let customers experience new features as soon as possible. Administrators can see and use preview features in their environments. These features are almost ready for general availability and have gone through extensive testing. We're just looking for a final round of customer feedback and validation before we release them for general availability.

This topic describes how an administrator can enable preview features, and it lists the features that are currently available for preview. This list will be updated as features are released to general availability and as new features are released to preview. No notification is given when new features are released to preview. Users will just start to see the features.

## Enable or disable preview features

To access preview features, you must first enable them in your environment. The action of enabling or disabling preview features is environment-specific.

> [!IMPORTANT]
> By turning on the **Preview Features** setting, you enable preview features for all users in your organization who are in that environment. By turning off the setting, you disable preview features and make them inaccessible to your users. Preview features have limited support in Talent. They might use fewer privacy and security measures, and they aren't included in the Talent service level agreement. You should not use preview features to process personal data (that is, any information that could identify you), or to process other data that is subject to legal or regulatory compliance requirements.

### Attract

1. Sign in to Microsoft Dynamics 365 for Talent: Attract.
2. On the **Setup** menu (the gear symbol) in the upper-right corner, select **Admin center**.
3. On the **Feature management** tab, select the option next to **Preview features** so that it turns blue and says **On**.
4. Select or deselect individual preview features. If you do nothing, all available preview features are enabled.
5. Refresh your browser to start to see the new features. (Any users who are already signed in will see the features the next time they sign in, or they can refresh their browser to see the features immediately.)

> [!NOTE]
> Some preview features might require additional configuration. Follow the links next to the preview feature to complete the setup for it.

### Core HR

1. Sign in to Talent.
2. Select **System administration**, select the **Links** tab, and then select **System parameters**.
3. On the **System parameters**, select the **Preview features** tab.
4. Under **Enable preview mode for all users**, change the toggle to **Yes** to make preview features available.

> [!NOTE]
> To disable preview features, use the same steps, setting **Enable preview mode for all users** to **No**. When you disable preview features, they become inaccessible to your users, and errors might occur in processes that are associated with the features.

### Onboard

There are no preview features available for Onboard at this time.

## Features that are currently in preview

### Attract

- [Candidate recommendation](./intelligent-recommendations.md#candidate-recommendations) – If more than ten candidates have resumes or complete profiles, the candidates who most closely meet a job's requirements appear in the **Applicants to consider** section on that job's page.

- [Job recommendation](./intelligent-recommendations.md#job-recommendations) – If there are more than ten jobs posted on your career site, Attract provides job recommendations to prospects.

- [Broadbean integration](./posting-jobs-external.md#post-jobs-to-broadbean) – You can post jobs from Attract to Broadbean, an external job posting site. After enabling this preview feature, you'll need to complete the setup by entering your Broadbean username, client ID, and encryption token.

- [Analytics](./analytic-reports.md) – Hiring teams can view key metrics for a single job with Job Analytics or aggregated metrics accross all jobs in the Analytics Hub.

- EEO – New activity types enable the use of a predefined form for the collection of Equal Employment Opportunity  (EEO) and Office of Federal Contract Compliance Program (OFCCP) data from the candidate.  This is a predefined form and is not editable.

- [Prospect recommendation](./intelligent-recommendations.md#prospect-recommendations) – Attract reviews past applicants and current candidates to provide you with a list of prospects who are a good match for your job.

- [Relevance search](./attract-talent-pools#search-and-view-candidate-profiles) – Search your entire candidate database for particular skills, names, or educational background. Attract searches the entire profile and highlights all the matches found. Attract also searches all documents that are available for a candidate and intelligently ranks the search results.

- [Activity audience](./whats-new-talent-march-20#setting-the-audience-on-activities) – Set the audience for activities (such as Interview, Schedule, or Feedback) to All candidates, Internal candidates, or External candidates. You can deliver customer activities, such as YouTube videos, web content, and Microsoft Forms, to All candidates, Internal candidates, External candidates, or the hiring team. 

- [Apply with LinkedIn](./career-site#enable-applying-for-jobs-with-linkedin-profiles) – You can set up on option on your Attract career site to allow job candidates to apply with LinkedIn. This streamlines the application process for your candidates by letting them use their LinkedIn profile to auto-fill their applications on your career site.

- [Source tracking](./source-tracking) – Attract tracks the source of candidate applications, which provides you with valuable information that helps you target your recruiting efforts. You can also select an application source when you're adding a candidate to a job or talent pool.

- [Silver medalist](./whats-new-talent-march-20#designate-silver-medalists-to-assign-high-value-applicants-for-future-positions) – You can designate candidates who are a great fit for your organization but who you didn't extend an offer to for your current position as silver medalists. This helps reduce your time to hire the next time you have a similar position available.



### Core HR

- [Validate position hierarchy data](./whats-new-talent-may-13-2019#new-page-to-validate-position-hierarchy-data) – Validate the managerial hierarchy for circular references that might have been imported inadvertently.

- [Specify reason codes on leave types](./whats-new-talent-may-13-2019#specify-reason-codes-on-leave-types) – You can specify reason codes for leave types.

- [Require reason codes on time-off requests](./whats-new-talent-may-13-2019#require-reason-codes-for-specific-leave-types-on-time-off-requests) – In addition to specifying reason codes for leave types, you can require reason codes for time-off requests.

- [Provide a leave and absence transaction list for HR](./whats-new-talent-may-13-2019#provide-a-leave-and-absence-transaction-list-for-hr) – You can view a list of leave and absence transactions to help provide insights into time-off balances.


### Onboard

There are no preview features available for Onboard at this time.

## Feedback

Regardless of whether the feedback is positive or negative, we want to hear from you about your use of the preview features. We encourage you to regularly post your feedback on the following sites as you use these or any other features.

- [Community](https://community.dynamics.com/enterprise/f/759?pi53869=0&category=Talent) – This site is a great resource where users can discuss use cases, ask questions, and get community help.
- Use the following sites to suggest product ideas. Let us know about features that you want to see in the product, and also any changes that you think should be made to existing features.

    - [Attract Ideas](https://powerusers.microsoft.com/t5/Ideas-for-Attract/idb-p/Attract)
    - [Core HR](https://powerusers.microsoft.com/t5/Ideas-for-Human-Resources/idb-p/HumanResources)

Don't include personal data (any information that could identify you) in your feedback or product review submissions. Information that is collected might be analyzed further, and it won't be used to answer requests under applicable privacy laws. Personal data that is collected separately under these programs is subject to the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

> [!TIP]
> Bookmark this topic, and check back often to stay up to date about new preview features as we release them.
