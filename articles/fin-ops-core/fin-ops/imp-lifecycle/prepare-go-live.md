---
# required metadata

title: Prepare for go-live
description: This article provides guidance about how to prepare for the go-live for finance and operations apps.
author: alejandra-cabrales
ms.date: 05/19/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: alcabral
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: July 2017 update
---

# Prepare for go-live

[!include [banner](../includes/banner.md)]

This article provides guidance about how to prepare for the go-live for finance and operations apps.

To ensure that the production environment is used for live operations, Microsoft provisions the production instance when the solution is ready and after project readiness has been validated as part of the Go-live Readiness Review with Microsoft. For more information about the environments in your subscription, see the [Licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

> [!Note]
> Most projects are **required** to use the **FastTrack for Dynamics 365 implementation portal** for their Go-live Readiness Review with Microsoft.


For answers to common questions about go-live, see the [Go-live FAQ](go-live-faq.md).

The following table lists the key steps in the go-live process.

| Step | Duration/When | Who | Notes |
|---|---|---|---|
| Validation of prerequisites | A project is close to the end of the testing phase, and you're planning the go-live review. | Customer/Partner | For more information, see the [Go-live Readiness Review prerequisites](#prerequisites) section. |
| Go-live Readiness Review with Microsoft | No later than four weeks before the go-live | Customer/Partner submits answers to review questions in the FastTrack for Dynamics 365 implementation portal. Microsoft FastTrack provides a review report. | For more information, see the [Go-live Readiness Review with Microsoft](#readiness) section. |
| Go-live review workshop with Microsoft (only for eligible projects) | The workshop is part of the Go-live Readiness Review. | Microsoft FastTrack together with the project team | This step applies only to eligible projects that have [FastTrack engagement](/dynamics365/fasttrack/eligibility). For more information about the workshop, see [Go-live Readiness workshops](/dynamics365/fasttrack/go-live-workshops). |
| Production deployment | Production deployment can be initiated as soon as the Go-live Readiness Review is completed. After deployment is triggered, production deployment takes approximately 30 minutes. | Customer/Partner triggers the deployment in Microsoft Dynamics Lifecycle Services (LCS). | After the go-live review is successfully completed, the **Configure** button is enabled for the production environment. Selection of this button [triggers the production deployment](../../dev-itpro/deployment/deployenvironment-newinfrastructure.md). |
| Deployable package installation | An average of 30 minutes | Customer/Partner | Follow the instructions in [Promote an update to production environments](../../dev-itpro/deployment/updateenvironment-newinfrastructure.md#promote-an-update-to-production-environments). The packages must contain all the models and binaries consolidated into [all-in-one deployable packages](../../dev-itpro/dev-tools/aio-deployable-packages.md). |
| Data migration to production | The duration/time depends on the method that is used. | Customer/Partner | |
| Cutover activities | The duration/time depends on the project. | Customer/Partner | |
| Go-live | | Customer/Partner | |

## <a name="prerequisites"></a>Go-live Readiness Review prerequisites

The project team should validate solution readiness. The following prerequisites must be met before the Go-live Readiness Review with Microsoft can be initiated. The production environment can be deployed after the Go-live Readiness Review with Microsoft has been successfully completed.

- User acceptance testing (UAT) and performance testing have been completed or almost completed in a Tier-2 (or higher) environment. Tier-1 environments must not be used for UAT or performance testing. For more information, see [Tier-1 vs. Tier-2 and higher](environment-planning.md#tier-1-vs-tier-2-and-higher). For information about how to identify the correct sandbox environment tier, based on your transaction volumes, see [Selecting the correct Tier-2 or higher environment](environment-planning.md#selecting-the-correct-tier-2-or-higher-environment).

    During the UAT phase, test all the business processes that you've implemented and any customizations that you've made.

    - Test cases should cover the entire scope of requirements.
    - Use migrated data for testing. This data should include master data and opening balances, even if they aren't yet final.
    - Use the correct security roles for testing, including default roles and custom roles that are assigned to users.
    - Make sure that the solution complies with any company-specific and industry-specific regulatory requirements.
    - Obtain sign-off from the customer.

    Performance testing is a crucial part of validating the readiness of your solution. For detailed guidance about the recommended practices, review the [Performance Testing Techtalks](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/performance-testing-in-microsoft-dynamics-365-techtalk-series).

- The environment version that is planned for the go-live complies with the [Software lifecycle policy](../../dev-itpro/migration-upgrade/versions-update-policy.md). If you use Commerce Scale Units (CSU), the CSU version must be in sync with the environment version. For more information, see [Component dependencies](../../../commerce/arch-component-versioning.md#component-dependencies).
- Key customer team members have been added to the LCS project.
- A generic service account that will be used to deploy the production environment has been added to LCS.
- All licenses that are required for go-live have been purchased in the correct tenant.
- After all licenses have been purchased, the final subscription estimator has been uploaded and activated in LCS. For more information, see [Subscription estimator in Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/subscription-estimator.md).
- The Customization analysis report (CAR) has been run, and critical issues have been addressed. For more information, see [Customization Analysis Report (CAR)](../../dev-itpro/dev-tools/customization-analysis-report.md).
- The go-live date in LCS correctly represents the go-live date that you're targeting. This date is the date when end users will start live operations, not cutover activities.
- All relevant tasks and phases in the [LCS methodology](../../dev-itpro/lifecycle-services/lcs-works-lcs.md#methodologies) have been completed. Production can be deployed only after all phases, including the Test phase, have been completed. To complete a phase in LCS, first complete every required step in that phase. When all the steps in a phase have been completed, you can complete the whole phase. You can always reopen a phase later if you must make changes. The process of completing a step has two parts:

    - Do the actual work, such as a fit-gap analysis or UAT.
    - Mark the corresponding step in the LCS methodology as you complete it.

    Complete the steps in the methodology as you make progress with the implementation. Don't wait until the last minute.

## <a name="readiness"></a>Go-live Readiness Review with Microsoft

All finance and operations apps customers must complete a Go-live Readiness Review with the [Microsoft FastTrack for Dynamics 365](/dynamics365/fasttrack/) team before production environments can be deployed. The main purpose of the review is to assess project readiness and help you have a smooth and successful go-live experience. LCS project users will receive an email reminder about the Go-live Readiness Review, based on the go-live date in LCS.

The review might require up to three business days for the initial report, plus additional time for any risk mitigation that is required. Determine an appropriate time to start this review, so that you can meet the go-live timeline.

For most projects, the Go-live Readiness Review is done in the FastTrack for Dynamics 365 implementation portal.

> [!Note]
> There are only **two exceptions** that will not use the FastTrack for Dynamics 365 implementation portal:
> - Projects that are in **[United States (US) Government Community Cloud (GCC)](../../dev-itpro/deployment/us-gcc-deployment.md)**. Please [download the Go-live checklist](https://aka.ms/d365fogolivechecklist), fill in all necessary details, and send it via email to <d365fogccglr@microsoft.com>. Always include a key stakeholder from the customer and the implementation partner on the email. Microsoft FastTrack will review the project and follow up.
> - For projects that are already live, but planning to move the live solution to a new tenant if the solution is not changing, completing a new Go-live Readiness review is not necessary. Please follow the steps described in [Move your production environment to the new tenant](../get-started/move-lcs-implementation-project-tenant.md#move-your-production-environment-to-the-new-tenant) to get the production slot enabled on the new tenant.

### Initiate the Go-live Readiness Review in the portal

1. The project team decides who from the **customer** organisation will be the admin for the project on Portal and a key participant of the Go-live Readiness review. Admin access to the project on Portal can be grnated only to the member of the customer organisation. Microsoft will grant access to this user and this user will manage access for other team mmembers. 

2. Project team sends an e-mail to d365fogl@microsoft.com and includes the following information:

    - Confirmation that the project is ready to start the Go-live Readiness Review. Please carefully review prerequisites for the Go-live readiness review which are described in the earlier section of this article.
    - Confirmation of the LCS project ID or LCS project URL.
    - Confirmation of the planned Go-live date (when live operations will start in Production). Please make sure this date is reflected in the LCS correctly.
    - Confirmation by when it is required to have Production environment deployed. Building a cutover plan allows to deptermine by which date environment should be available. 
    - Confirmation who should be granted admin access for this project on Portal. It is required that admin access is granted to the member of the customer organsation (unless it is an internal implementation by the partner). 
    - Please also indicate in the e-mail if it is an internal implementation for a partner organisation. 

3. Microsoft grants the key review participant from the customer organization admin access to the project and confirms that this task has been completed by responding to the email.
4. The admin adds additional project team members.
5. Project team creates the review in the portal by following the guidance in the [Portal Help article](https://experience.dynamics.com/FTimplementationportal/help/help-details-page/?id=a275750e-2ffb-eb11-94ef-0022482594cd&searchtxt=). All users who have registred on portal can access this article. 

### Submit the review

- The project team should provide answers to all questions in the review. The review process in the portal supports multi-user scenarios. Multiple team members can provide details for the go-live review at the same time.
- When answers have been provided to all the questions in the Go-live Readiness Review, submit the review to Microsoft by selecting **Submit**.

### After the review is submitted in the portal

- Microsoft FastTrack reviews the project and provides a report that describes the potential risks, best practices, and recommendations for a successful go-live of the project. **The review might require up to three business days for the initial report, plus additional time for any risk mitigation that is required.**
- Users who have been selected as **Review participants** in the portal receive email communication that provides updates about the review.
- When all critical risks have been addressed, and the review has been completed, Microsoft enables the production environment slot in the LCS project. The customer/partner can then trigger the production environment deployment.

> [!NOTE]
> If you encounter any issue with the portal, contact the portal Support team by selecting **Contact us** in the upper-right corner of the portal or sending an email to <ftd365ip-support@microsoft.com>. In the email, specify the ID of your project in LCS, and provide details that describe the issue.

## Production environment deployment

> [!NOTE]
> The production environment must be used exclusively to run your business operations. Don't use it for testing, demo, or training purposes. You will be able to do the cutover, and mock the cutover (if a mock cutover is planned), in production. To test the solution, use an appropriate sandbox environment that has been designed so that it includes all the elements and services that are required for testing.

We recommend that you select a service account for environment deployment. For example, select a generic user account as the admin user of the environments that you deploy. If you select a named user account, you might not be able to access an environment if that user is unavailable. Here are some examples of scenarios where the admin user must access an environment:

- **First sign-in to any environment after initial deployment** – The admin user is the only user who can access the environment.
- **First sign-in to a sandbox environment after a database refresh from the production environment** – No user accounts except the admin account can sign in.

The production environment should be deployed to the same datacenter where your sandbox environments are deployed, and where UAT and performance testing were done. For information about network requirements and how to do latency testing, see [Network requirements](../get-started/system-requirements.md#network-requirements).

Production deployment takes approximately 30 minutes. When deployment has been completed, an email notification is sent to the environment administrator.

The production environment is sized based on the number of licenses that have been allocated to the LCS project and the transaction volumes in the [Subscription estimator](../../dev-itpro/lifecycle-services/subscription-estimator.md).

After production has been deployed, the project team can apply the deployable package by following the instructions in [Promote an update to production environments](../../dev-itpro/deployment/updateenvironment-newinfrastructure.md#promote-an-update-to-production-environments) and then migrate the data. For data migration, we recommend that you prepare and validate data in a non-production environment and then [copy the sandbox database to production](../../dev-itpro/database/dbmovement-scenario-goldenconfig.md#copy-the-sandbox-database-to-production).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

