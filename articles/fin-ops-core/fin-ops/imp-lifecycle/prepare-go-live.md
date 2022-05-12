---
# required metadata

title: Prepare for go-live
description: This topic describes how to prepare to go live with a project by using Microsoft Dynamics Lifecycle Services (LCS).
author: ClaudiaBetz-Haubold
ms.date: 05/12/2022
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

This topic provides guidance about how to prepare for the go-live for Dynamics 365 Finance and Operations apps.

To ensure that the production environment is used for live operations, Microsoft provisions the production instance when the solution is ready, and after the project readiness is validated as part of the go-live readiness review with Microsoft. For more information about the environments in your subscription, see the [Licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

For answers to common questions about go-live, see the [Go-live FAQ](go-live-faq.md). 

The following table lists the key steps in the go-live process.

| Step | Duration/When | Who | Notes |
|-|-|-|-|
| Validate prerequisites | When a project is close to the end of the testing phase and you are planning the go-live review. | Customer/Partner | See the section, [Go-live readiness review prerequisites](#prerequisites) for more information. |
| Go-live readiness review with Microsoft | No later than four weeks before the go-live. | Customer/Partner submits answers to review questions on the **FastTrack for Dynamics 365 implementation portal**. Microsoft FastTrack provides a review report. | See the section [Go-live readiness review with Microsoft](#readiness)for more information.  |
| Go-live review workshop with Microsoft (only for eligible projects) | The workshop is part of the go-live readiness review. | Microsoft FastTrack solution architect with the project team | This applies only to eligible projects with [FastTrack engagement](/dynamics365/fasttrack/eligibility). For more information about the workshop, see [Go-live Readiness workshops](/dynamics365/fasttrack/go-live-workshops).  
| Production deployment | Production deployment can be initiated as soon as the go-live readiness review is complete. After deployment is triggered, production deployment takes approximately 30 minutes. | Customer/Partner triggers the deployment in Lifecycle Services (LCS). | After the go-live review is successfully completed, the **Configure** button is enabled for the production environment. Selecting this button [triggers the production deployment](../../dev-itpro/deployment/deployenvironment-newinfrastructure). | 
| Deployable package installation | An average of 30 minutes | Customer/Partner | Follow the instructions in the topic, [Promote an update to production environments](../../dev-itpro/deployment/updateenvironment-newinfrastructure.md#promote-an-update-to-production-environments). The packages must contain all the models and binaries consolidated in [all-in-one deployable packages](../../dev-itpro/dev-tools/aio-deployable-packages.md). |
| Data migration to production | Depends on the chosen method | Customer/Partner | &nbsp; |
| Cutover activities | Depends on the project | Customer/Partner | &nbsp; |
| Go-live |&nbsp;  | Customer/Partner | &nbsp;  |

## <a name="prerequisites"></a> Go-live readiness review prerequisites

The project team should validate solution readiness. The following prerequisites must be met before initiating the Go-live Readiness Review with Microsoft. The production environment can be deployed after the Go-live Readiness Review with Microsoft has been successfully completed. 

- UAT and performance testing is complete or almost complete on a Tier-2 (or higher) environment. Tier-1 environments must not be used for UAT or performance testing. For more information, see [Tier-1 vs. Tier-2 and higher](environment-planning.md#tier-1-vs-tier-2-and-higher). To identify the correct sandbox environment tier based on your transaction volumes, see [Selecting the correct Tier-2 or higher environment](environment-planning.md#selecting-the-correct-tier-2-or-higher-environment). 

  During the UAT phase, test all the business processes that you've implemented and any customizations that you've made. 
  
    -	Test cases should cover the entire scope of requirements.
    -	Use migrated data for testing. This data should include master data and opening balances, even if they aren't yet final.
    -	Use the correct security roles for testing, including default roles and custom roles that are assigned to users.
    -	Make sure that the solution complies with any company-specific and industry-specific regulatory requirements.
    -	Obtain sign-off from the customer.

  Perfomance testing is a crucial part of validating the readiness of your solution. For detailed guidance on the recommeded practices, review the [Performance Testing Techtalks](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/performance-testing-in-microsoft-dynamics-365-techtalk-series). 

- The environment version planned for the go-live is compliant with the [Software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md). If you use Commerce Scale Units (CSU), the CSU version must be in sync with the environment version. For more information, see [Dynamics 365 Commerce component versioning requirements](/commerce/arch-component-versioning.md#component-dependencies). 
- Key customer team members are added to the LCS project.
- A generic service account is added to LCS, which will be used to deploy the production environment.
- All licenses that are needed for go-live are purchased on the correct tenant. 
- The final subscription estimator is uploaded and activated in LCS, after all licences were purchased. For more information, see [Subscription estimator in Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/subscription-estimator.md).
- The Customization analysis report (CAR) has been run and critical issues have been addressed. For more information, see [Customization Analysis Report (CAR)](../../dev-itpro/dev-tools/customization-analysis-report.md).
- The go-live date in LCS correctly represents the go-live date you are targeting. This is the date when end users will start live operations, not cutover activities.
- All relevant tasks and phases in the [LCS methodology](../../dev-itpro/lifecycle-services/lcs-works-lcs.md#methodologies) are complete. It is possible to deploy production only when all phases including the **Test phase**, are complete. To complete a phase in LCS, first complete every required step in that phase. When all the steps in a phase are completed, you can complete the whole phase. You can always reopen a phase later if you must make changes. The process of completing a step has two parts:

    - Do the actual work, such as a fit-gap analysis or user acceptance testing (UAT).
    -	Mark the corresponding step in the LCS methodology as you complete it.
   
   Complete the steps in the methodology as you make progress with the implementation. Don't wait until the last minute.

## <a name="readiness"></a> Go-live Readiness Review with Microsoft

> [!IMPORTANT]
> In May 2022, the process has transitioned from a Microsoft Word checklist to the FastTrack for Dynamics 365 implementation portal. 
> 
> As of June 15, 2022, Word Go-live checklists will no longer be accepted. Go-live reviews should be only be initiated in the portal.
> 
> If you are already in the process of using a Word checklist, you can continue if you plan to submit the Word checklist before June 15th. However, questions on the portal are the same as in the checklist, so we invite you to use the portal. 

All Finance and Operations apps customers must complete a Go-live Readiness Review with the [Microsoft FastTrack for Dynamics 365](/dynamics365/fasttrack/) team before production environment can be deployed. The key goal of the review is to assess project readiness and help you have a smooth and successful go-live experience. LCS project users will receive an e-mail reminder about the Go-live Readiness Review based on the go-live date in LCS.

The review may take up to three business days for the initial report, plus additional time for risk mitigation, if required. Determine the right time to start this review to meet the go-live timeline. 

The Go-live Readiness Review is executed on the FastTrack for Dynamics 365 implementation portal. 

### Initiate the Go-live Readiness Review

1.	The customer/partner should send an e-mail to d365fogl@microsoft.com that:

    -	Confirms the project is ready to start the Go-live Readiness Review.
    -	Confirm the project LCS ID. 
    -	Confirm which users from the LCS project will be Go-live Readiness Review particiants and should be granted with access to the portal for the Go-live Readiness Review process.

    > [!NOTE]
    > Key stakeholders from the customer organization that are participating in the review must be selected as **Review participants** on the portal. 

2. Microsoft grants portal access to the requested LCS project users and confirms this by responding to an e-mail.
3. The customer/partner starts the review on the portal by following the guidance provided in the [Portal Help article]( https://experience.dynamics.com/FTimplementationportal/help/help-details-page/?id=a275750e-2ffb-eb11-94ef-0022482594cd&searchtxt=). Users who have access to the portal can access this article.

### Submit the review
- The project team should provide answers to all questions in the review. The review process on the portal supports multi-user scenarios. Multiple team members can provide details for the go-live review at the same time. 
- When all answers to the Go-live Readiness Review questions are provided, submit the review to Microsoft by selecting **Submit**. 

### After the review is submitted in the portal
- Microsoft FastTrack reviews the project and provides a report that describes the potential risks, best practices, and recommendations for a successful go-live of the project. The review may take up to three business days for the initial report, plus additional time for risk mitigation, if required.
- Users who are selected in the portal as **Review participants** will receive e-mail communication with updates about the review. 
- When all critical risks are addressed and the review is complete, Microsoft will enable the production environment slot in LCS and the project. The customer/partner can now trigger the prodcution environment deployment.

> [!NOTE]
> If you face any issue with the portal, reach out to the portal Support team by selecting **Contact us** in the top-right corner of the portal or by sending an email to **ftd365ip-support@microsoft.com**. In the email, specify the LCS ID for your project and provide details describing the issue.

## Production environment deployment

> [!NOTE]
> The production environment must be used exclusively to run your business operations. Do not use the production environment for testing, demo, or training purposes. You will be able to perform the cutover and if planned, mock the cutover in production. To test the solution, use an appropriate sandbox environment, which is designed with the necessary elements and services for testing.

We recommend that you select a service account for environment deployment. For example, as the admin user of the environments that you deploy, select a generic user account. If you select a named user account, you might not be able to access an environment if that user isn't available. There are some scenarios where the admin user must access an environment. For example:

- **First sign-in to any environment after initial deployment** – The Admin user is the only user who can access the environment.
- **First sign-in to a sandbox environment after a database refresh from the production environment** – All user accounts except the admin account are unable to sign in.

The production environment should be deployed to the same datacenter where your sandbox environments are deployed and where UAT and performance testing were executed. To understand network requirements and how to perform latency testing, see [Network requirements](../get-started/system-requirements.md#network-requirements).

Production deployment lasts for approximately 30 minutes. An email notification is sent to the environment administrator when deployment is complete. 

The production environment is sized based on number of licences allocated to the LCS project and the transaction volumes in the [Subscription estimator](../../dev-itpro/lifecycle-services/subscription-estimator.md). 

After production is deployed, the project team can apply the deployable package by following the process described in the topic, [Update an environment](../../dev-itpro/deployment/updateenvironment-newinfrastructure.md#promote-an-update-to-production-environments) and then migrate the data. For data migration, we recommend that you prepare and validate data in a non-production environment and then [copy the sandbox databse to production](../../dev-itpro/database/dbmovement-scenario-goldenconfig.md#copy-the-sandbox-database-to-production). 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
