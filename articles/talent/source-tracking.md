---
# required metadata

title: Track candidate sources in Attract
description: This topic provides information about tracking the source for candidate profiles and applications. 
author: hachandr
manager: AnnBe
ms.date: 03/18/2019
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
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Track candidate sources in Attract

[!include [banner](includes/banner.md)]

> [!NOTE] 
> Functionality noted in this topic is available as part of a preview review release. The content and the functionality are subject to change. To use this feature, ask an administrator to enable it using the **Admin settings** in Attract. A future release will provide source tracking reports. For more information, see [Access preview features in Talent](https://docs.microsoft.com/dynamics365/unified-operations/talent/access-preview-feature).

When candidates apply for a job, Attract automatically tracks the source of their applications, providing you with valuable information to help you target your recruiting efforts. Recruiters and hiring managers can also select an application source while manually adding a candidate to a job or talent pool.

You can view the application source in the application activity details under the **Activity** tab, as well as in the application history available under **Profile** in talent pools. You can find a candidate's profile source in the candidate details under the **Profile** tab in both applications and talent pools.

> [!NOTE] 
> You can find process templates in the [Comprehensive hiring add-on](https://docs.microsoft.com/dynamics365/unified-operations/talent/attract-comprehensive-hiring).

## Pre-configured sources

The default source list contains common application sources. Some source types, like **Job board** and **Social Network**, have additional source details. For example, **Social Network** includes Facebook and Twitter. The **Referral** source type allows you to specify an internal employee as the referrer. The default source list includes the following pre-configured sources:

-   Attract career site

-   Agency

-   Career Fair

-   Company Marketing

-   Conferences & Trade shows

-   Professional Association

-   Job board

    -   Indeed

    -   Seek

    -   CareerBuilder

    -   Google Jobs

    -   Xing

    -   Glassdoor

    -   Monster Jobs

-   Magazines & Publications

-   Social Network

    -   Facebook

    -   Twitter

-   University Recruiting

-   LinkedIn

-   Classifieds

-   Referral

-   Added by Recruiter

-   Other

## Customize the source list 

You can extend the source list to include additional application sources. To customize this list, follow the instructions in [Extending Option Sets in Attract](https://docs.microsoft.com/dynamics365/unified-operations/talent/extensibility-attract#extending-option-sets-in-attract). Edit the **TalentSource** entity to include additional sources. 

To avoid negatively impacting the user interface (UI), don't edit or delete the **TalentCategory** enum values (not names) for the following:

- **Referral**
- **LinkedIn**
- **Other**

Instead, you can extend the **TalentSource** enum to add other types of sources.
