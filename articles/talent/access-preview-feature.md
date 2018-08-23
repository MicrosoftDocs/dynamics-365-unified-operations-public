---
# required metadata

title: Access preview features in Talent
description: This topic describes how an administrator can enable the preview features, and it lists the features that are currently enabled for preview.
author: rschloma
manager: AnnBe
ms.date: 04/17/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2018-04-30
ms.dyn365.ops.version: AX 7.1.0, Talent April 2018 update

---

# Access preview features in Talent

[!include[banner](../includes/banner.md)]

As part of our continuous rollout of product capabilities, we want to let customers experience new features as soon as possible. Administrators can see and use preview features in their environments. These features are almost ready for general availability and have gone through extensive testing. We are just looking for a final round of customer feedback and validation before we generally release them.

This topic describes how an administrator can enable preview features, and it lists the features that are currently available for preview. This list will be updated as features are released to general availability and as new features are released to preview. No notification is given when new features are released to preview. Users will just start to see the features.

## Enable or disable preview features

You can use the **Preview Features** setting in the Microsoft Dynamics 365 for Talent admin center to enable or disable preview features. By default, the setting is turned off. The action of enabling or disabling preview features is environment-specific.

> [!IMPORTANT]
> By turning on the **Preview Features** setting, you enable preview features for all users in your organization who are in that environment. By turning off the setting, you disable preview features and make them inaccessible to your users. Preview features have limited support in Talent. They might use fewer privacy and security measures, and they aren't included in the Talent service level agreement. You should not use preview features to process personal data (that is, any information that could identify you), or to process other data that is subject to legal or regulatory compliance requirements.

### Enable or disable preview features for your organization

#### Attract

1. Sign in to Microsoft Dynamics 365 for Talent: Attract.
2. On the **Setup** menu (the gear symbol) in the upper-right corner, select **Admin settings**.
3. On the **Feature management** tab, select the option next to **Preview features** so that it turns blue.
4. Refresh your browser to start to see the new features. (Any users who are already signed in will see the features the next time that they sign in, or they can refresh their browser to see the features immediately.)

#### Core HR

1. Sign in to Talent. The core Human resources workspace will open, from which you'll complete the remaining steps. 
2. Select **System administration \> Links System parameters**.
3. On the **System Parameters page**, on the **Preview features** tab, set the **Enable preview mode for all users** option to **Yes** to make preview features available.

> [!NOTE]
> To disable preview features, use the same basic steps. When you disable preview features, they become inaccessible to your users, and errors might occur in processes that are associated with the features.

## Features that are currently in preview

### Attract

- **Job templates** – You can now create hiring process templates. Users can already customize the hiring process for a specific job. However, they can now create templates for the process and then select the appropriate template when a specific job is created. Therefore, this feature helps streamline the job setup process.
- **Career site** – The current version of the career site just lists all open jobs. However, more capabilities will be added to the site in the future. Jobs can be marked as either internal or external. Internal users who sign in to the site will see both internal jobs and external jobs. However, non-internal users and users who aren't signed in will see only external jobs.
- **Job posting** – You can now post jobs to the career site.
- **LinkedIn job posting** – You can now post jobs to LinkedIn.

    > [!NOTE]
    > Jobs that are posted are visible only to customers who subscribe to one or more LinkedIn job listing products. Otherwise, customers see a job only if they explicitly search for it. There is a delay when jobs are posted to LinkedIn. A job might take up to a few hours to appear after it's posted from Attract.

- **Candidate apply** – Both internal and external candidates can now apply directly from the job page on the career site.
- **Offer management** – Users can now create offer letters from templates that include placeholders. As candidates advance to the Offer stage, recruiters and hiring managers can use the Offer tool to prepare a candidate's formal offer via templates, send the offer for internal approval, and finally send the offer to the candidate for signature. Many new capabilities will be added to the Offer tool over time, and the preview feature will be updated with these capabilities as we are ready to release them to preview.

### Core HR

- **Open Enrollment** – Benefits open enrollment gives employees a simple, self-service experience for selecting their benefits. Human Resource (HR) administrators can configure the benefits open enrollment process for their organization, and the enrollment experience for employees, by using an easy-to-follow guided solution.

## Feedback

Regardless of whether the feedback is positive or negative, we want to hear from you about your use of the preview features. We encourage you to regularly post your feedback on the following sites as you use these or any other features.

- [Community](https://community.dynamics.com/enterprise/f/759?pi53869=0&category=Talent) – This site is a great resource where users can discuss use cases, ask questions, and get community help.
- Use the following sites to suggest product ideas. Let us know about features that you want to see in the product, and also any changes that you think should be made to existing features.

    - [Attract Ideas](https://powerusers.microsoft.com/t5/Ideas-for-Attract/idb-p/Attract)
    - [Core HR](https://powerusers.microsoft.com/t5/Ideas-for-Human-Resources/idb-p/HumanResources)

Don't include personal data (any information that could identify you) in your feedback or product review submissions. Information that is collected might be analyzed further, and it won't be used to answer requests under applicable privacy laws. Personal data that is collected separately under these programs is subject to the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

> [!TIP]
> Bookmark this topic, and check back often to stay up to date about new preview features as we release them.
