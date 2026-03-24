---
title: Prepare for go-live
description: Learn about how to prepare for the go-live for finance and operations apps, including a table that lists the key steps in the go-live process.
author: alejandra-cabrales
ms.date: 09/30/2025
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: alcabral
ms.search.validFrom: 2018-01-31
ms.search.form: 
ms.dyn365.ops.version: July 2017 update
---

# Prepare for go-live

[!include [banner](../../../finance/includes/banner.md)]

This article provides guidance about how to prepare for the go-live for finance and operations apps in Lifecycle Services if you already have a project there.

To ensure that the production environment is used for live operations, Microsoft provisions the production instance when the solution is ready and after project readiness is validated as part of the Go-live Readiness Review with Microsoft. For more information about the environments in your subscription, see the [Licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

> [!NOTE]
> Most projects are **required** to use the **FastTrack for Dynamics 365 implementation portal** for their Go-live Readiness Review with Microsoft.
> If you have a Microsoft FastTrack Solution Architect assigned to your implementation project, reach them before creating a new project to avoid duplicate projects/reviews being created. The Microsoft FastTrack Solution Architect can work with you on the Go-Live review and guides you on the process to follow.

For answers to common questions about go-live, see the [Go-live FAQ](go-live-faq.md).

The following table lists the key steps in the go-live process.

| Step | Duration/When | Who | Notes |
|---|---|---|---|
| Validation of prerequisites | A project is close to the end of the testing phase, and you're planning the go-live review. | Customer/Partner | For more information, see the [Go-live Readiness Review prerequisites](#prerequisites) section. |
| Go-live Readiness Review with Microsoft | No later than four weeks before the go-live | Customer/Partner submits answers to review questions in the FastTrack for Dynamics 365 implementation portal. Microsoft FastTrack provides a review report. | For more information, see the [Go-live Readiness Review with Microsoft](#readiness) section. |
| Go-live review workshop with Microsoft (only for eligible projects) | The workshop is part of the Go-live Readiness Review. | Microsoft FastTrack together with the project team | This step applies only to eligible projects that have [FastTrack engagement](/dynamics365/fasttrack/eligibility). For more information about the workshop, see [Go-live Readiness workshops](/dynamics365/fasttrack/go-live-workshops). |
| Production deployment | Production deployment can be initiated as soon as the Go-live Readiness Review is completed. After deployment is triggered, production deployment takes approximately 30 minutes. | Customer/Partner triggers the deployment in Microsoft Dynamics Lifecycle Services. | After the go-live review is successfully completed, the **Configure** button is enabled for the production environment. Selection of this button [triggers the production deployment](../deployment/deployenvironment-newinfrastructure.md). |
| Deployable package installation | An average of 30 minutes | Customer/Partner | Follow the instructions in [Promote an update to production environments](../deployment/updateenvironment-newinfrastructure.md#promote-an-update-to-production-environments). The packages must contain all the models and binaries consolidated into [all-in-one deployable packages](../dev-tools/aio-deployable-packages.md). |
| Data migration to production | The duration/time depends on the method that is used. | Customer/Partner | |
| Cutover activities | The duration/time depends on the project. | Customer/Partner | |
| Go-live | | Customer/Partner | |

## <a name="prerequisites"></a>Go-live Readiness Review prerequisites

The project team should validate solution readiness. The following prerequisites must be met before the Go-live Readiness Review with Microsoft can be initiated. The production environment can be deployed after the Go-live Readiness Review with Microsoft is successfully completed.

- User acceptance testing (UAT) and performance testing is complete or almost completed in a Tier-2 (or higher) environment. Tier-1 environments must not be used for UAT or performance testing. For more information, see [Tier-1 vs. Tier-2 and higher](environment-planning.md#tier-1-vs-tier-2-and-higher). For information about how to identify the correct sandbox environment tier, based on your transaction volumes, see [Selecting the correct Tier-2 or higher environment](environment-planning.md#selecting-the-correct-tier-2-or-higher-environment).

    During the UAT phase, test all the business processes that you've implemented and any customizations that you made.

    - Test cases should cover the entire scope of requirements.
    - Use migrated data for testing. This data should include master data and opening balances, even if they aren't yet final.
    - Use the correct security roles for testing, including default roles and custom roles that are assigned to users.
    - Make sure that the solution complies with any company-specific and industry-specific regulatory requirements.
    - Obtain approval from the customer.

    Performance testing is a crucial part of validating the readiness of your solution. For detailed guidance about the recommended practices, review the [Performance Testing Techtalks](https://community.dynamics.com/blogs/post/?postid=88afa660-b640-4206-a163-500964a1a331).

- The environment version that is planned for the go-live complies with the [Software lifecycle policy](../migration-upgrade/versions-update-policy.md). If you use Commerce Scale Units (CSU), the CSU version must be in sync with the environment version. For more information, see [Component dependencies](../../../commerce/dev-itpro/arch-component-versioning.md#component-dependencies).
- Key customer team members are added to the Lifecycle Services project.*
- A generic service account that's used to deploy the production environment is added to Lifecycle Services.
- All licenses that are required for go-live were purchased in the correct tenant.
- After all licenses are purchased, the final subscription estimator is uploaded and activated in Lifecycle Services. For more information, see [Subscription estimator in Lifecycle Services](../lifecycle-services/subscription-estimator.md).*
- The Customization analysis report (CAR) is run, and critical issues are addressed. For more information, see [Customization Analysis Report (CAR)](../dev-tools/customization-analysis-report.md).
- The go-live date in Lifecycle Services correctly represents the go-live date that you're targeting. This date is the date when end users start live operations, not cutover activities.*
- All relevant tasks and phases in the [Lifecycle Services methodology](../lifecycle-services/lcs-works-lcs.md#methodologies) are complete. Production can be deployed only after all phases, including the Test phase, are complete*. To complete a phase in Lifecycle Services, first complete every required step in that phase. When all the steps in a phase are complete, you can complete the whole phase. You can always reopen a phase later if you must make changes. The process of completing a step has two parts:

    - Do the actual work, such as a fit-gap analysis or UAT.
    - Mark the corresponding step in the Lifecycle Services methodology as you complete it.

    Complete the steps in the methodology as you make progress with the implementation. Don't wait until the last minute.

You must complete all steps that we marked with an asterisk (*) before you submit the project for review in the portal. The project shows as blocked for review until you mark those steps as completed. When you update a setting in Lifecycle Services, it takes about 15 minutes before the the status of review readiness changes.
    
## <a name="readiness"></a>Go-live Readiness Review with Microsoft

The implementation project in Lifecycle Services must complete a Go-live Readiness Review with the [Microsoft FastTrack for Dynamics 365](/dynamics365/guidance/fasttrack/overview) team before you can deploy production environments. The main purpose of the review is to assess project readiness and help you have a smooth and successful go-live experience. Lifecycle Services project users receive an email reminder about the Go-live Readiness Review, based on the go-live date in Lifecycle Services. For most projects, the Go-live Readiness Review is done in the Dynamics 365 implementation portal. Learn more at [What is the Dynamics 365 Implementation Portal?](/dynamics365/guidance/implementation-portal/overview).

If a project opts in for an AI review when you submit the request for review, the review process is autonomously managed by AI. The review process completes on the same day, and the stakeholders are notified by email. Any risks or issues are highlighted and shared in the Dynamics 365 Implementation Portal. The customer stakeholders added to the project can review the risks and mitigate them, and the production slot is automatically released in Lifecycle Services within few minutes.

For projects that opt out of the AI review, the familiar manual review process follows. The manual reviews can take up to three business days for the initial report, plus more time for any risk mitigation that is required. Determine an appropriate time to start this review, so that you can meet the go-live timeline.

> [!NOTE]
> There are **four exceptions** that don't use the FastTrack for Dynamics 365 implementation portal:
>1. **GCC, GCC High, and Department of Defense projects** - Projects that are in the **[United States (US) Government Community Cloud (GCC)](../../fin-ops/deployment/us-gcc-deployment.md)** or **US Government Community Cloud High (GCC High)** or **US Department of Defense (DoD)**. - [Download the Go-live checklist](https://aka.ms/d365fogolivechecklist), fill in all necessary details, and send it via email to <d365fogccglr@microsoft.com> to start the Go-Live process. Always include a key stakeholder from the customer and the implementation partner on the email. Microsoft FastTrack reviews the project and follows up.
>1. **Tenant moves** - For projects that are already live, but planning to move the live solution to a new tenant if the solution is not changing, completing a new Go-live Readiness review is not necessary. Follow the steps described in [Move your production environment to the new tenant](../get-started/move-lcs-implementation-project-tenant.md#move-your-production-environment-to-the-new-tenant) to get the production slot enabled on the new tenant.
>2. The following steps apply to Lifecycle Services projects. These steps do no apply to implementations that you manage in the Power Platform admin center.

### Initiate the Go-live readiness review in the portal

> [!NOTE]
> If you have a Microsoft FastTrack Solution Architect assigned to your implementation project, reach them before creating a new project using following steps in the portal to avoid duplicate projects/reviews being created. The Microsoft FastTrack Solution Architect can work with you on the Go-Live review and guides you on the process to follow.

#### Self-service create/join the project in the Dynamics 365 Implementation Portal

Submitting the Go-live readiness review can be performed by partners and customer in the Dynamics 365 Implementation portal without involving Microsoft. The Onboarding Wizard in the Implementation portal has simplified the steps to create the project, add the admin and users, and submitting the Go-Live review for self-service.

1. Create the project in Implementation portal. For more information about creating and joining the project, see [Create or join a project in the Implementation Portal](/dynamics365/guidance/implementation-portal/onboard-project).
1. Ensure that the project admin on the project is from the **customer** organization. This user from the customer organization can then add more users and serve as the key participant in the Go-live readiness review. For more information about adding users, see [Admin](/dynamics365/guidance/implementation-portal/manage-projects#admin) section.
1. Once the project is created, the project team can create and perform the Go-live readiness review in the portal using the guidance in the [Portal Help article](https://implementationportal.dynamics.com/). All users who have registered on portal can access this article. 

> [!NOTE]
> If you encounter any issue with the portal, contact the portal Support team by selecting **Contact us** in the upper-right corner of the portal or sending an email to the [Support team](mailto:ftd365ip-support@microsoft.com). In the email, specify the ID of your project in Lifecycle Services, and provide details that describe the issue.

### Submit the review

- The project team should provide answers to all questions in the review. The review process in the portal supports multi-user scenarios. Multiple team members can provide details for the go-live review at the same time.
- When answers are provided to all the questions in the Go-live Readiness Review, submit the review to Microsoft by selecting **Submit for review**.
- If all the prerequisites are met, you can choose the key review participants and submit the review.
  - In this dialog box, there's an option to opt out of the AI review. If you choose this option, a manual review process follows, and the corresponding SLA (3 days) applies.
  - If you don't choose to opt out, the autonomous AI review process starts so that that the review completes on the same day.

### After the review is submitted in the portal

#### Manual review process (opted-out of AI review)
- Microsoft FastTrack reviews the project and provides a report that describes the potential risks, best practices, and recommendations for a successful go-live of the project. **The review might require up to three business days for the initial report, plus more time for any risk mitigation that is required.**
- Users who are selected as **Review participants** in the portal receive email communication that provides updates about the review.
- When all critical risks are addressed, and the review is completed, Microsoft enables the production environment slot in the Lifecycle Services project. The customer/partner can then trigger the production environment deployment.

#### Automated review process (not opted-out of AI review)
- An AI system conducts the review. When the review completes, users who are selected as **Review participants** in the portal receive an email that provides updates about the review. The review completes within a few minutes after you submit the project for review.
- The stakeholders can use the link in the email to access the Implementation Portal where they can review any potential risks, best practices, and recommendations for a successful go-live of the project. It's highly recommended to take corrective action on all the risks/issues for a successful go-live.
- Only the people who are added to the review as key participants get a button with the label **Resolve/Mitigate all risks** in the Implementation Portal. If they choose that button, they confirm the mitigation of the relevant risks.
- When all critical risks are mitigated/accepted by the stakeholder in the Implementation Portal, the review is marked as completed, and the production environment slot in the Lifecycle Services project becomes available 15 minutes. A person from the organization or the implementation partner can then choose the **Configure** button in Lifecycle Services to configure the production environment.

## Production environment deployment

> [!NOTE]
> The production environment must be used exclusively to run your business operations. Don't use it for testing, demo, or training purposes. You are able to do the cutover, and mock the cutover (if a mock cutover is planned), in production. To test the solution, use an appropriate sandbox environment that is designed so that it includes all the elements and services that are required for testing.

We recommend that you select a service account for environment deployment. For example, select a generic user account as the admin user of the environments that you deploy. If you select a named user account, you might not be able to access an environment if that user is unavailable. Here are some examples of scenarios where the admin user must access an environment:

- **First sign-in to any environment after initial deployment** – The admin user is the only user who can access the environment.
- **First sign-in to a sandbox environment after a database refresh from the production environment** – No user accounts except the admin account can sign in.

The production environment should be deployed to the same datacenter where your sandbox environments are deployed, and where UAT and performance testing were done. For information about network requirements and how to do latency testing, see [Network requirements](../get-started/system-requirements.md#network-requirements).

Production deployment takes approximately 30 minutes. When deployment is completed, an email notification is sent to the environment administrator.

The production environment is sized based on the number of licenses that are allocated to the Lifecycle Services project and the transaction volumes in the [Subscription estimator](../lifecycle-services/subscription-estimator.md).

After production is deployed, the project team can apply the deployable package by following the instructions in [Promote an update to production environments](../deployment/updateenvironment-newinfrastructure.md#promote-an-update-to-production-environments) and then migrate the data. For data migration, we recommend that you prepare and validate data in a nonproduction environment and then [copy the sandbox database to production](../database/dbmovement-scenario-goldenconfig.md#copy-the-sandbox-database-to-production).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

