---
# required metadata

title: LinkedIn integration FAQ
description: This topic answers questions that you might have about integration between LinkedIn and Microsoft Dynamics 365  Talent - Attract.
author: hasrivas
manager: AnnBe
ms.date: 07/08/2019
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
# ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: hasrivas
ms.search.validFrom: 2019-07-08
ms.dyn365.ops.version: Talent October 2018 update

---

# LinkedIn integration FAQ

[!include [banner](includes/banner.md)]

LinkedIn is the world's largest online professional network. Microsoft Dynamics Talent: Attract integrates with LinkedIn to give you access to the world's top talent. Attract lets you post jobs directly to LinkedIn, and it also lets you draw candidate information from LinkedIn into Attract.

## For recruiters and hiring managers

Here are answers to frequently asked questions about how to use Attract and LinkedIn together.

### What LinkedIn features do I get with Attract?

Attract's integration with LinkedIn lets you perform the following tasks:

- [Post jobs to LinkedIn](./attract-post-jobs-to-linkedin.md) (as free Limited Listings).
- [Source candidates with LinkedIn Recruiter in Microsoft Dynamics 365 Talent - Attract](./attract-linkedin-recruiter.md#export-linkedin-candidates-to-attract-with-one-click).
- [Set up integration with LinkedIn for Microsoft Dynamics 365 Talent - Attract](./attract-admin-linkedin.md#set-up-apply-with-linkedin-in-attract).

### What do I need before I can post jobs to LinkedIn?

Your admin must [configure LinkedIn integration in Attract](./attract-admin-linkedin.md#configure-job-posting-to-linkedin). After that, you're ready to go.

### How do I post jobs to LinkedIn from Attract?

After you create a job in Attract, you just have to select the **Post Now** button that corresponds to LinkedIn. For more information, see [Post jobs to LinkedIn from Microsoft Dynamics 365 Talent - Attract](./attract-post-jobs-to-linkedin.md#post-jobs-to-linkedin).

### Can I get candidate information from LinkedIn into Attract?

Yes. If you see a good candidate on LinkedIn, you can easily export that candidate's information into Attract. For more information, see [Source candidates with LinkedIn Recruiter in Microsoft Dynamics 365 Talent - Attract](attract-linkedin-recruiter.md).

### How can I get help accessing LinkedIn from Attract?

If you're having trouble signing in or posting jobs to LinkedIn from Attract, see [Troubleshooting integration with LinkedIn and Microsoft Dynamics 365 Talent - Attract](./attract-troubleshoot-linkedin.md).

For other issues with Attract, see [Get support for Microsoft Dynamics 365 Talent](./talent-support.md). For help with LinkedIn, see the [LinkedIn support page](https://www.linkedin.com/help).

## For admins and developers

Here are answers to frequently asked questions about how to configure integration between Attract and LinkedIn.

### How do I configure Attract so that recruiters and hiring managers can post jobs to LinkedIn?

You can configure the available options on the **LinkedIn Integration** tab in the Admin center. For more information, see [Set up integration with LinkedIn for Microsoft Dynamics 365 Talent - Attract](./attract-admin-linkedin.md).

### Can I export candidate information from LinkedIn?

Yes, but you must first configure integration with LinkedIn Recruiter. For more information, see [Set up integration with LinkedIn for Microsoft Dynamics 365 Talent - Attract](./attract-admin-linkedin.md).

### How can I post jobs to Premium Job Slots on LinkedIn?

Although Attract provides a powerful solution for posting jobs to LinkedIn, you might find that you need additional flexibility. For example, you might want to be able to post Premium Job Slots in addition to the free Limited Listings, or you might want LinkedIn to process your batch job posts more than once per day.

#### Types of LinkedIn job posts

LinkedIn offers the following types of job postings:

- **Limited Listing** – Free job postings that appear in search results when candidates search for jobs on LinkedIn and on a company's LinkedIn page. Limited Listings are targeted toward active job seekers. This type of listing is the type that Attract provides to LinkedIn. You can't promote Limited Listing jobs on LinkedIn. If you want to promote Limited Listings, you must work with LinkedIn to enable Job Wrapping. For more information about Job Wrapping, see [Limited Listings vs Premium Job Slots for Job Wrapping](https://www.linkedin.com/help/recruiter/answer/79049/limited-listings-vs-premium-job-slots-for-job-wrapping) and [Job Wrapping Plus - FAQs](https://www.linkedin.com/help/recruiter/answer/79050/job-wrapping-frequently-asked-questions).
- **Premium Job Slot** – Purchased postings that appear in various places across LinkedIn, such as the LinkedIn feed, emails, and the **Jobs You Might be Interested in** area. Premium Job Slots are targeted toward passive candidates, but they also appear in job searches.

Attract posts jobs to LinkedIn as Limited Listings. If you want to use Premium Job Slots, you must use Job Wrapping through LinkedIn Recruiter. Job Wrapping requires a job wrapping contract with LinkedIn. For more information, see [Job Wrapping through LinkedIn Recruiter - Overview](https://www.linkedin.com/help/recruiter/answer/79037).

#### Frequency of batch processing on LinkedIn

LinkedIn processes job posts in a batch through Attract once per day. Therefore, it can take up to 48 hours for jobs to appear on LinkedIn after they are posted through Attract. If you need jobs to appear sooner on LinkedIn, or if you need any additional flexibility, you can use the Recruiter System Connect application programming interface (API) from LinkedIn. For more information, see [Recruiter System Connect](https://docs.microsoft.com/linkedin/talent/recruiter-system-connect).

#### Table of options for job posting to LinkedIn

The following table describes the different options for posting jobs to LinkedIn. It includes the advantages of each option and additional information.

|  | Attract | Job Wrapping through LinkedIn Recruiter | Recruiter System Connect API |
|---|---|---|---|
| **Description** | Attract posts jobs to LinkedIn as an XML feed. | The company contracts with LinkedIn and provides an XML feed for posting jobs. | The customer uses the API to sync information between Attract and LinkedIn Recruiter. |
| **What type of job can I post?** | Limited Listing | Premium Job Slot or Limited Listing | Limited Listing |
| **Can I promote the job on LinkedIn?** | No | Premium Job Slots: Yes<br>Limited Listings: No | No |
| **How often does LinkedIn post jobs?** | Once per day | Once per day | Multiple times per day, as defined by the API |
| **Recommended by LinkedIn?** | No | Yes | No |
| **What do I need?** | Purchase of Attract | A job wrapping contract with LinkedIn and purchase of Premium Job Slots | An API agreement with LinkedIn | 
| **Where can I find more information?** | [Set up integration with LinkedIn for Microsoft Dynamics 365 Talent - Attract](./attract-admin-linkedin.md) | [Job Wrapping through LinkedIn Recruiter - Overview](https://www.linkedin.com/help/recruiter/answer/79037) | [Recruiter System Connect](https://docs.microsoft.com/linkedin/talent/recruiter-system-connect) |

> [!NOTE]
> You don't need a LinkedIn Recruiter System Connect license to post jobs to LinkedIn with Attract.

## See also

[Set up integration with LinkedIn for Microsoft Dynamics 365 Talent - Attract](./attract-admin-linkedin.md)

[Post jobs to LinkedIn from Microsoft Dynamics 365 Talent - Attract](./attract-post-jobs-to-linkedin.md)

[Source candidates with LinkedIn Recruiter in Microsoft Dynamics 365 Talent - Attract](./attract-linkedin-recruiter.md)

[Troubleshooting integration with LinkedIn and Microsoft Dynamics 365 Talent - Attract](./attract-troubleshoot-linkedin.md)
