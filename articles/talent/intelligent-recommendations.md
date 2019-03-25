---
# required metadata

title: Intelligent recommendations
description: This topic explains how machine learning can be used to provide recommendations for jobs and job candidates.
author: andreabichsel
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
ms.reviewer: anbichse
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Intelligent recommendations

[!include[banner](../includes/banner.md)]

Machine learning can help recruiters and hiring managers quickly identify top candidates for a position. It can also help prospects find the position that best suits their profile and interests. As these features are used, and feedback is provided, recommendations will improve.

> [!NOTE] 
> - The intelligent recommendation features are available only with the [Comprehensive hiring add-on](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/attract-comprehensive-hiring).
> - This feature is currently in preview. If you want to try it out, please ask an administrator to [enable it in Attract's **Admin settings**](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/access-preview-feature). Set **Candidate recommendation**, **Job recommendation**, and **Prospect recommendation** to **On**.


## Candidate recommendations

Because job postings might attract hundreds of applicants, it can be difficult for recruiters and hiring managers to find the candidates whose skills and background best match the position. By analyzing the correlation between the job description and requirements, and data from the candidates' resumes and profiles, machine learning can be used to produce candidate recommendations. Candidate recommendations can help recruiters and hiring managers identify the top talent and move them to the interview stage faster. For any job, if there are more than ten candidates or prospects who have resumes or complete profiles, the candidates or prospects who most closely meet the job's requirements appear in the **Applicants to consider** section on the **Job** page.

For any recommended candidate, you can select **View candidate** on the candidate card to review the candidate's profile and take action on his or her application. You can use the ellipsis button (**...**) to open the candidate's profile on a new tab. You can also use the ellipsis button to provide feedback about the recommendation. In this way, you help fine-tune the recommendation engine and improve future recommendations. Any recommendations that you don't like are removed from the **Applicants to consider** section when you refresh the **Job** page. You can use the feedback card to indicate why you didn't find the recommendation useful.

## Job recommendations 

When a prospective employee uses the career site to apply to a job, Attract recommends other open positions at the organization. These recommendations are based on past applications and the resume or candidate profile of the prospect. Therefore, job recommendations help prospects quickly identify the jobs that are the best fit for them. Job recommendations are provided to prospects if more than ten jobs are posted on the career site. Prospects can open the details of a job posting from the recommendation card. They can also provide feedback about a recommendation to help improve future recommendations.

## Prospect recommendations 

When a new position becomes available, looking through all your past applicants and your entire talent network can take a while. Why not let Attract help you? Using intelligent machine learning algorithms, Attract looks at all the candidates and suggests those who are a good matach as soon as you create the job. To see these recommendations, you need to enable the **Prospect** stage for the job. It may take up to a minute for Attract to scour through your entire candidate database to make recommendations.

The recommendations appear as cards in the **Prospects** tab of any job that has the **Prospect** stage enabled. These cards list the skills found in the prospect's profile, as well as any education qualification information. If you see a recommendation you like, you can add the candidate as a prospect for that job.

If you recently started using Attract, you’ll need to wait until you have 10 or more applicants who have full profiles or resumes before you can use this capability.

To avoid bias in the recommendations, Attract only scans candidate profiles and looks for skills, qualifications and
other keywords that match the job description. In addition, Attract removes  personally identifying information from candidate profiles prior to evaluating them.

