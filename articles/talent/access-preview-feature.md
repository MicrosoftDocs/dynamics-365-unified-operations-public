---
# required metadata

title: Access preview features in Dynamics 365 for Talent: Attract description: This topic describes how an administrator can enable the preview features and lists the features that are currently enabled for preview. 
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

# Access preview features in Dynamics 365 for Talent 
 
As part of our continuous rollout of product capabilities we want to let customers experience new features as soon as possible.  Administrators can see and use of preview features in their environment. These features are nearly ready for general availability and have gone through extensive testing. We are just looking for a final round of customer feedback and validation before we generally release them. 

This topic describes how an administrator can enable the preview features, and lists the features that are currently enabled for preview. This list will be maintained as features are released to general availability and when new features are released to preview. No notification is made when new features are delivered to preview; users will simply start seeing the features. 

## Enable or disable preview features

The **Preview Features** setting in the Dynamics 365 for Talent admin center lets you enable or disable previews. This setting is disabled by default. Enabling or disabling preview features is environment specific.   

> [!Important]
> By selecting the **Preview Features** setting you are enabling previews for all users in your organization in this environment.  Clearing this setting disables previews, making them inaccessible to your users. Preview features have limited support in Dynamics 365 for Talent. They may utilize less privacy and security measures and are not included in the Dynamics 365 for Talent service level agreement. You should not use previews to process personal data (any information that could identify you) or other data that is subject to legal or regulatory compliance requirements. 

### To enable or disable preview features for your organization

 **Attract**
 
 1. Log in to Microsoft Dynamics 365 for Talent: Attract.
 
 2. Open the **Setup** menu, designated by the gear icon, in the upper-right corner, and the select **Admin settings**. 
 
 3. Select the **Feature management** tab on the left. 
 
 4. Click the switch next to **Preview features** so that it turns blue. 
 
 5. Refresh your browser to begin seeing the new features. (Any user who is already logged in will see them the next time they log in, or they can see them immediately by also refreshing their browser.)
 
**Core HR** 
 
 1. Log into Core HR.
 
 2. Select **System administration > Links System parameters**.
 
 3. On the **System Parameters page**, choose the **Preview features** tab. 
 

## Managing Preview Features 

The enabling of preview features is environment specific. To enable the features an administrator of Attract will need to perform the following steps: 

1. Log in to Attract. 

2. Select the ‘gear’ menu in the upper right-hand corner, and select **Admin settings**. 

3. Select the **Feature management** tab on the left. 

4. Click the switch next to **Preview features** so that it turns blue. 

5. Refresh your browser to begin seeing the new features. (Any user who is logged in will see them the next time they login, or they can see them immediately by refreshing their browser.) 

> [!NOTE] 
> Follow same steps to disable the preview capabilities. When disabling them, note that existing processes could have potential issues. In most cases existing processes will continue to use the preview features. New processes created after disabling the preview features will not use any of the preview features. 
 


## Current Features in Preview 

### Attract

**Job templates** – Ability to create hiring process templates. Currently users can customize the hiring process for a given job.  With this feature they can first create a template of the process and then select the appropriate template at the time of job creation, thus streamlining the job setup process. 

 **Career site** – The current version of the career site simply lists all open jobs. This will be expanded in the future with additional capabilities. Jobs can be marked as internal or external and thus if an internal user logs into the site they will see the internal and external jobs.  Otherwise non-internal users or non-logged in users will only see external jobs. 
Job Posting – Ability to post jobs to the career site. 

 **Job posting** - Ability to post jobs to the career site. 

 **LinkedIn job posting** – Ability to post jobs to LinkedIn. 

> [!Note]
> Customers will need to be subscribers to one or more of LinkedIn’s job listing products for the job to be visible.  Otherwise the job will only show when you explicitly search for it.  Posting to LinkedIn does have a delay and it can take up to a few hours for a job to appear after posting it from Attract. 

 **Candidate apply** – Candidates (Internal or External) can now apply directly from the job page of the career site. 

 **Assessments** – As part of the configurable hiring process (on a job or using a job template) users now have access to a new **Assessment** activity type.  From here users can use the Project: "Gauge" (part of Dynamics 365 for Talent) to build basic assessments to send to candidates. Project: "Gauge" is also in public preview. Additional providers will be added in the future. 
 
 **Project: "Gauge"** - Project: "Gauge" is another app in Dynamics 365 for Talent which allows users to create simple assessments or surveys. 

 **Offer management** – Offer management provides the ability for users to build templatized offer letters with placeholders.  As a candidate advances to the Offer stage, recruiters and hiring managers can now use Offer to prepare the candidates formal offer via the templates, send for internal approval, and finally send the offer for signature to the candidate. Many new features will come to the Offer tool over time and the preview will be updated with these capabilities as we are ready to release them to preview. 
 
### Core HR

 **Open Enrollment** – Benefits open enrollment provides employees with a simple, self-service experience for selecting their benefits. Human Resource administrators can configure their organization’s benefits open enrollment process, as well as the employee enrollment experience, using an easy-to-follow guided solution.

## Feedback

Good or bad, we want to hear from you regarding your use of these preview features. Please post your feedback on the following sites regularly as you use these or any other features. 

 - [Community](https://community.dynamics.com/enterprise/f/759?pi53869=0&category=Talent) - This site is a great tool for users to discuss use cases, ask questions and get community help. 
  - Use these sites for suggesting product ideas. Let us know about features you'd like to see in the product, as well sa any changes you think we should make to existing features. 
  
      - [Attract Ideas](https://powerusers.microsoft.com/t5/Ideas-for-Attract/idb-p/Attract)
      - [Core HR](https://powerusers.microsoft.com/t5/Ideas-for-Human-Resources/idb-p/HumanResources)

Do not include personal data (any information that could identify you) in your feedback or product review submissions. Information collected could be further analyzed and it will not be used to answer requests under applicable privacy laws.  Personal data collected separately under these programs is subject to the [Microsoft Privacy Statement](https://privacy.microsoft.com/en-us/privacystatement).

> [!Tip]
> Bookmark this page and check back often to keep up to date on new preview features as we release them. 
