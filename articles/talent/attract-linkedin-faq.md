---
# required metadata

title: Microsoft Dynamics 365 for Talent - Attract integration with LinkedIn FAQ
description: This topic answers questions you may have about integration between LinkedIn and Microsoft Dynamics 365 for Talent - Attract.
author: hasrivas
manager: AnnBe
ms.date: 06/06/2019
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
ms.search.industry: 
ms.author: hasrivas
ms.search.validFrom: 2019-06-06
ms.dyn365.ops.version: Talent October 2018 update

---

# LinkedIn FAQ

[!include [banner](includes/banner.md)]

LinkedIn is the world's largest online professional network. Microsoft Dynamics for Talent: Attract integrates with LinkedIn to give you access to the world's top talent. Attract allows you to post jobs directly into LinkedIn, and it also allows you to draw candidate information from LinkedIn into Attract.

## For recruiters and hiring managers

Here are answers to frequently asked questions about how to use Attract and LinkedIn together.

### What LinkedIn features do I get with Attract?

Attract's integration with LinkedIn lets you do the following:

- Post jobs to LinkedIn (as free Limited Limited Listings).

- Export candidate information from LinkedIn to Attract.

- Allow job candidates to apply to your jobs with LinkedIn.

### What do I need before I can post jobs to LinkedIn?

Your admin needs to [configure LinkedIn integration in Attract](./attract-admin-linkedin.md#configure-job-posting-to-linkedin). After that, you're ready to go!

### How do I post jobs to LinkedIn from Attract?

After you create a job in Attract, all you need to do is select the **Post Now** button that corresponds with LinkedIn. For more information, see [Post jobs to LinkedIn from Attract](./attract-post-jobs-to-linkedin.md#post-jobs-to-linkedin).

### Can I get candidate information from LinkedIn into Attract?

Yes! If you see a good candidate in LinkedIn, you can easily port that candidate's information into Attract. For more information, see [Source candidates with LinkedIn Recruiter](attract-linkedin-recruiter.md).

## For admins and developers

Here are answers to frequently asked questions about how to configure integration between Attract and LinkedIn.

### How do I configure Attract so recruiters and hiring managers can post jobs to LinkedIn?

You can configure both of these options on the **LinkedIn Integration** tab in the **Admin center**. For more information, see [Set up integration with LinkedIn](./attract-admin-linkedin.md).

### Can I export candidate information from LinkedIn?

Yes! First, you'll need to configure integration with LinkedIn Recruiter. For more information, see [Set up integration with LinkedIn](./attract-admin-linkedin.md).

### How can I post jobs to Premium Job Slots in LinkedIn?

While Attract provides a powerful solution for posting jobs to LinkedIn, you might find you need additional flexibility. For example, you might want to be able to post Premium Job Slots as well as the free Limited Listings, or you might want LinkedIn to process your batch job posts more than once per day.

#### Types of LinkedIn job posts

LinkedIn offers the following types of job postings:

- **Limited Listing** - free job postings that appear in search results when candidates search for jobs on LinkedIn and on a company's LinkedIn page. Limited Listings are targeted toward active job seekers. This is the type of listing that Attract provides to LinkedIn. You can't promote Limited Listing jobs on LinkedIn. If you want to promote Limited Listings, you need to work with LinkedIn to enable Job Wrapping. For more information about Job Wrapping, see [Limited Listings vs Premium Job Slots for Job Wrapping](https://www.linkedin.com/help/recruiter/answer/79049/limited-listings-vs-premium-job-slots-for-job-wrapping) and [Job Wrapping Plus - FAQs](https://www.linkedin.com/help/recruiter/answer/79050/job-wrapping-frequently-asked-questions).

- **Premium Job Slot** - purchased postings that appear in various places across LinkedIn, including the LinkedIn feed, emails, and the **Jobs You Might be Interested in** area. Premium Job Slots are targeted toward passive candidates, but also appear in job searches.

Attract posts jobs to LinkedIn as Limited Listings. If you want to use Premium Job Slots, you need to use Job Wrapping through LinkedIn Recruiter, which requires a job wrapping contract through LinkedIn. For more information, see [Job Wrapping through LinkedIn Recruiter - Overview](https://www.linkedin.com/help/recruiter/answer/79037).

#### Frequency of batch processing in LinkedIn

LinkedIn processes job posts in batch through Attract and other Applicant Tracking Systems (ATSs) once per day. This means it could take up to 24 hours for jobs to appear on LinkedIn after being posted through Attract. If you need jobs to appear sooner on LinkedIn, or any additional flexibility, you can use the Recruiter System Connect API from LinkedIn. For more information, see [Recruiter System Connect](https://docs.microsoft.com/en-us/linkedin/talent/recruiter-system-connect).

#### Table of options for job posting to LinkedIn

The following table lists each option for posting jobs to LinkedIn, along with their advantages and additional information.

|  | Attract | Job Wrapping through LinkedIn Recruiter | Recruiter System Connect API |
|---|---|---|---|
| Description | Attract posts jobs to LinkedIn as an XML feed. | Company contracts with LinkedIn and provides XML feed for posting jobs. | Customer uses API to synchronize information between Attract and LinkedIn Recruiter. |
| What type of job can I post? | Limited Listing | Premium Job Slot or Limited Listing | Limited Listing |
| Can I promote the job on LinkedIn? | No | Premium Job Slots - yes; Limited Listings - no | No |
| How often does LinkedIn post jobs? | Once per day | Once per day | Multiple times per day, as defined by API |
| Recommended by LinkedIn? | No | Yes | No |
| What do I need? | Purchase of Attract | Job wrapping contract with LinkedIn and purchase of Premium Job Slots | API agreement with LinkedIn | 
| Where can I find more information? | [Set up integration with LinkedIn](./attract-admin-linkedin.md) | [Job Wrapping through LinkedIn Recruiter - Overview](https://www.linkedin.com/help/recruiter/answer/79037) | [Recruiter System Connect](https://docs.microsoft.com/en-us/linkedin/talent/recruiter-system-connect) |

>[!NOTE]
>You don't need a LinkedIn Recruiter System Connect license to post jobs to LinkedIn with Attract.

## See also

[Set up integration with LinkedIn](./attract-admin-linkedin.md)<p></p>
[Post jobs to LinkedIn from Attract](./attract-post-jobs-to-linkedin.md)<p></p>
[Source candidates with LinkedIn Recruiter](./attract-linkedin-recruiter.md)<p></p>
[Troubleshoot integration with LinkedIn](./attract-troubleshoot-linkedin.md)