---
# required metadata

title: Prepare for go-live
description: This topic describes how to prepare to go live with a project by using Microsoft Dynamics Lifecycle Services (LCS).
author: ClaudiaBetz-Haubold
ms.date: 10/27/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: July 2017 update
---

# Prepare for go-live

[!include [banner](../includes/banner.md)]

This article provides guidance about how to prepare for the go-live for Finance and Operations apps.

To ensure that the production environment is used for live operations, Microsoft provisions the production instance when the solution is ready and after readiness of the project is validated as part of the go-live readiness review with Microsoft. For more information about the environments in your subscription, see the [Licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

Refer to **[Go-live FAQ article](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/imp-lifecycle/go-live-faq)** to see answers to most common questions. 

The following table list key steps in the process and then each step is described in more detail.

|   | Step | Duration/When | Who | Notes |
|-|-|-|-|-|
| 1 | Validate prerequisites | When project is close to the end of testing phase and planning the Go-live review | Customer/Partner | See the first section after the table to understand Go-live Readiness Review prerequisites |
| 2 | Go-live Readiness Review with Microsoft | No later than 4 weeks before the Go-live | Customer/Partner submit answers to review questions on the **FastTrack for Dynamics 365 implementation portal**. Microsoft FastTrack provides review report | Follow the instructions provided in the "Go-live Readiness Review with Microsoft" section later in this article |
|   | Go-live review workshop with Microsoft *only for eligible projects* | Workshop is part of the Go-live readiness review | Microsoft-FastTrack Solution Architect with the project team. | This applies only to eligible projects with [FastTrack engagement](https://docs.microsoft.com/en-us/dynamics365/fasttrack/eligibility). Refer to [this article](https://docs.microsoft.com/en-us/dynamics365/fasttrack/go-live-workshops) for more details about workshop  
| 3 | Production deployment | Production deployment can be initiated as soon as Go-live readiness review is complete. After deployment is triggered it takes on average 30 minutes. | Customer/Partner trigger deployment in LCS | After the go-live review is successfully completed the Configure button in LCS is enabled for production environment and customer/partner will be able to [trigger production deployment](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/deployenvironment-newinfrastructure) | 
| 4 | Deployable package installation | An average of 30 minutes | Customer/Partner | Follow the instructions in [apply updates](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/updateenvironment-newinfrastructure#promote-an-update-to-production-environments). The packages must contain all the models and binaries consolidated in an [all-in-one](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/aio-deployable-packages) deployable package |
| 5 | Data migration to Production | Depends on the chosen method | Customer/Partner |  |
| 6 | Cutover activities | Depends on the project | Customer/Partner |  |
| 7 | Go-live |  | Customer/Partner |   |

## Go-live Readiness review prerequisites

Project team should validate solution readiness and below listed prerequisites before initiating the Go-live Readiness Review with Microsoft. 
Production environment can be deployed after successful completion of Go-live Readiness Review with Microsoft. 

1.	**UAT and performance testing is complete or almost complete** on a Tier 2 (or higher) environment. Tier-1 environments [must not be used for UAT or performance testing](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/imp-lifecycle/environment-planning#tier-1-vs-tier-2-and-higher). Refer to [this guidance](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/imp-lifecycle/environment-planning#selecting-the-correct-tier-2-or-higher-environment) to identify the right Sandbox environment tier based on your transaction volumes. 

During the UAT phase it is important to test all the business processes that you've implemented and any customizations that you've made. 
-	Test cases should cover the entire scope of requirements.
-	Use migrated data for testing. This data should include master data and opening balances, even if they aren't yet final.
-	Test by using the correct security roles (default roles and custom roles) that are assigned to users.
-	Make sure that the solution complies with any company-specific and industry-specific regulatory requirements.
-	Obtain sign-off from the customer.

Perfomance testing is a cricual part of validating readiness of your solution. We recommend reviewing [Performance Testing Techtalks](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/performance-testing-in-microsoft-dynamics-365-techtalk-series) for detailed guidance on the recommended practices. 

2.	The environment version planned for the Go-live is **compliant with the [Software lifecycle policy](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/versions-update-policy?toc=/dynamics365/commerce/toc.json)**. If you use Commerce Scale Units (CSU) the CSU version is in sync with the environment version as per [Dynamics 365 Commerce component versioning requirements](https://docs.microsoft.com/en-us/dynamics365/commerce/arch-component-versioning#component-dependencies). 

3.	**Key customer team members** are added to the LCS project.

4.	**Generic service account** is added to the LCS, which will be used to deploy Production environment.

5.	All **licenses needed for the Go-live** are purchased on the correct tenant. 

6.	**Final [Subscription Estimator](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/subscription-estimator)** is uploaded and activated in LCS (after all licences were purchased).

7.	[**Customisation analysis report (CAR)**](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/subscription-estimator) has been run and all critical issues have been addressed.

8.	Go-live date in LCS correctly represents the Go-live date you are targeting. This is the date when end users will start live operations, not cutover activities.

9.	All relevant **tasks and phases in [LCS methodology](https://docs.microsoft.com/lv-lv/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/lcs-works-lcs#methodologies)** are complete. It is possible to deploy Production only when all phases including the **Test phase**, are complete. 

To complete a phase in LCS, you must first complete every required step in that phase. When all the steps in a phase are completed, you can complete the whole phase. You can always reopen a phase later if you must make changes. The process of completing a step has two parts:
- Do the actual work, such as a fit-gap analysis or user acceptance testing (UAT).
-	Mark the corresponding step in the LCS methodology as completed.
It's good practice to complete the steps in the methodology as you make progress with the implementation. Don't wait until the last minute.

## Go-live Readiness review with Microsoft

> [!NOTE]
> In the middle of May 2022 the process has transitioned from word checklist to **FastTrack for Dynamics 365 implementation portal**. 
> 
> **Word Go-live checklists will not be accepted from June 15 2022**, Go-live review should be initiated on Portal only.
> 
> If you are already in process of working on Word checklist, you can continue (if you are planning to submit it before June 15th). However, questions on Portal are same as in the checklist, so we invite you to use Portal, if you are not too far with filling in Word document. 

All Finance and Operations apps customers **must complete a Go-live Readiness Review with [Microsoft FastTrack for Dynamics 365](https://docs.microsoft.com/en-us/dynamics365/fasttrack/) team before production environment can be deployed**. The key goal of the review is to assess project readiness and help you have a smooth and successful Go-live. LCS project users receive e-mail reminder about Go-live Readiness Review based on the Go-live date in LCS.

Please note that the review may take up to **3 business days** for the initial report, plus **additional time for risk mitigation**, if required. It is important that you plan when is the right time to start this review in order to meet Go-live timeline. 

Go-live readiness review is executed on the **FastTrack for Dynamics 365 implementation portal**. 

**How to initiate Go-live Readiness review?**
1.	Customer/partner should **send an e-mail to d365fogl@microsoft.com** 
-	Confirm that project is ready to start the Go-live Readiness review and **confirm project LCS ID**. 
-	Confirm which **users from the LCS project** will be Go-live Readiness Review particiants and **should be granted with access to Portal** for Go-ive Readiness review process.
-	Note, it is required that **key stakeholders from customer organization are participating in the review** and are **selected as Review participants on Portal**. 
2.	**Microsoft grants access** to Portal to requested LCS project users and will confirm this by responding to an e-mail.
3.	Customer/partner **start the review** on Portal by following guidance on this **[Portal Help article]( https://experience.dynamics.com/FTimplementationportal/help/help-details-page/?id=a275750e-2ffb-eb11-94ef-0022482594cd&searchtxt=)**. Users who will be granted with access to Portal will be able to access this article.

**How to submit the review?**
- Project team should provide **answers to all questions** in the Review. Review process on Portal supports multi-user scenario, multiple team members can be providing details for Go-live review at the same time. 
- When all answers to Go-live Readiness review questions are provided, please **submit the Review** to Microsoft by clicking on the Submit button. 

**What happens after review is submitted on Portal?**
- Microsoft FastTrack will review the project and provide a **report** that describes the potential **risks, best practices, and recommendations** for a successful go-live of the project. Review may take up to **3 business days** for the initial report, plus **additional time for risk mitigation** if required.
- Users who will be selected on the Portal as Review Participants will receive **email communication with updates about the review**. 
- When all critical risks are addressed **review will be complete**, Microsoft will **enable Production environment slot** in LCS and project and customer/partner will be able to **trigger Prodcution environment deployment**.

> [!NOTE]
> Note! If you face any issue with Portal please reach out to Portal Support team by following the guidance under **"Contact us" button** in the top right corner on the Portal or by sending an email to **ftd365ip-support@microsoft.com**. In the e-mail please specify LCS ID for your project and provide necessary details describing the issue you are facing.

## Production environment deployment

> [!NOTE]
> The production environment must be used exclusively for running your business operations and can not be used for testing/demo/training purposes. You will be able to perform the cutover, and if planned, to mock the cutover in production. To test the solution, you must use an appropriate sandbox environment, which is designed with the necessary elements and services for testing.

**We recommend that you select a service account** for environment deployment, for example a generic user account, as the Admin user of the environments that you deploy. If you use a named user account, you might not be able to access an environment if that user isn't available. Here are some scenarios where the Admin user must access an environment:

- **First sign-in to any environment after initial deployment** – In this case, the Admin user is the only user who can access the environment.
- **First sign-in to a sandbox environment after a database refresh from the production environment** – In this case, all user accounts except the Admin account are unable to sign in.

Production environment **should be deployed to the same datacenter where your sandbox environments are deployed** and where UAT and performance testing were executed. To understand network requirements and how to do latency testing please review [this article](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/system-requirements#network-requirements).

Production deployment lasts for approximately **30 minutes**, environment administrator will receive email notification when deployment is complete. 

Production environment is **sized** based on number of licences allocated to the LCS project and transaction volumes in the [Subscription Estimator](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/subscription-estimator). 

After Production is deployed project team can **apply deployable package** by following the process described in [this article](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/updateenvironment-newinfrastructure#promote-an-update-to-production-environments) and then **migrate data**. For data migration it is recommended to follow the aproach of preparing and validating data in non Production environment and then [copy Sandbox databse to Production](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/database/dbmovement-scenario-goldenconfig#copy-the-sandbox-database-to-production). 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
