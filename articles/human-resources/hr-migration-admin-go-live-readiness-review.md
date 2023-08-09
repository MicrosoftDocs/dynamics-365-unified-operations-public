---
# required metadata

title: Human Resources migration go-live readiness review
description: This article provides guidance about the go-live readiness review for Microsoft Dynamics 365 Human Resources migration to the finance and operations infrastructure.
author: priyankasinha77
ms.author: prsinha
ms.date: 8/7/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.search.validFrom: 2023-8-7
ms.dyn365.ops.version: Human Resources

---

# Human Resources migration go-live readiness review

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the steps of the go-live readiness review for Microsoft Dynamics 365 Human Resources migration to the finance and operations infrastructure.

## Human Resources migration go-live readiness review process

1. Before you request a production environment, complete the [prerequisites for migrating a Human Resources production environment](hr-cust-migration.md#prerequisites).
2. Send an email to <d365fogl@microsoft.com>. Use the following subject line: **\<*Customer name*\>: Human Resources migration go-live readiness review**. (Replace **\<*Customer name*\>** with the name of the customer.)

    In the body of the email, provide the following information:

    - Customer name
    - Email addresses and roles of key customer contacts
    - Partner
    - URL of the Microsoft Dynamics Lifecycle Services Migration project
    - Go-live date (live transactions)
    - Date when production is requested

    In addition, copy the following list into the email, and provide the appropriate information.

    **Lifecycle Services**

    - Does the go-live milestone date in the Lifecycle Services methodology match the planned go-live date? Confirm that the go-live date in Lifecycle Services reflects the actual go-live date when users start to work in production.
    - Are you using a generic account as the environment's administrator?
    - Have the customer's key stakeholders been added to the Lifecycle Services project?
    - Have the analysis, design and develop, and test phases in the Lifecycle Services methodology been completed to request a production environment?
    - Confirm that the final version of the subscription estimator was uploaded into the Lifecycle Services project and marked as active.

    **User acceptance testing (UAT)**

    - Provide the start date and end date of the UAT in the migrated sandbox environment.
    - Which environment was UAT performed on? 
    - Confirm that user training or change management has been completed.
    - Has the customer approved and signed off on the whole solution to confirm that it meets their business needs? If not, what's still pending, and what's the timeline for sign-off?

    **Cutover**

    - Do you have a cutover plan that includes the activity duration, responsibilities, dependencies, and a roll-back plan, and has the business signed off on it?
    - Confirm that migration to environments will always be on the latest generally available (GA) version. Depending on your migration and testing plan, if your migration validation for sandbox environments was done on a different version, we recommend that you validate a sandbox migration on the same version as your production environment.
    - Confirm that all remaining standalone Human Resources environments will automatically be deleted 10 days after successful migration of the production environment to the finance and operations infrastructure. 

    **Continuous updates**

    - Is the team familiar with the continuous updates policy?
    - Have you reviewed the continuous updates settings in your Lifecycle Services project and made any required adjustments?
    - Briefly describe your organization's plan for continuous updates.

    **Integrations**

    - Are integrations in scope?

        > [!NOTE]
        > If the answer is "Yes," answer the remaining questions in this section. Otherwise, move on to the next section.

    - Have you tested both the happy path and edge cases for each integration?
    - Has the customer signed off on all integrations that are in scope for go-live? If not, what's still pending, and what's the timeline for sign-off?

    **Dual-write**

    - Does the solution contain any dual-write integrations that are used to run processes across Dynamics 365 applications?

        > [!NOTE]
        > If the answer is "Yes," answer the remaining questions in this section. Otherwise, move on to the next section.

    - Are you planning to integrate two finance and operations environments?
    - Are both finance and operations environments in the same Azure tenant and in the same Azure region?
    - Are you planning to have multiple instances of Dataverse (formerly named Common Data Service) or multiple instances of finance and operations apps?
    - Have all dual-write flows been tested, and have the acceptance criteria been met at the expected peak load?
    - Are you using managed solutions to follow Application Lifecycle Management (ALM) best practices for your Dataverse custom entities and extensions?
    - Are notifications set up to alert users about any dual-write failures?
    - Confirm that you've read and understood the limitations for implementing dual-write in [System requirements for dual-write document](../fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-system-req.md).

    **Production support and maintenance**

    - Does the project team have a plan in place for regular, monitoring and maintenance of the production environment?
    - Is the project team familiar with the environment monitoring and diagnostics tool in Lifecycle Services?
    - Has the project team defined a process for post-go-live issue resolution and escalation?

3. The Dynamics 365 finance and operations go-live team replies to your email within two business days. A FastTrack team then works with you to assess the project's readiness for production deployment. The team also shares the potential risks, best practices, and recommendations for a successful go-live of the project.
4. After all critical risks have been addressed, and the review has been completed, Microsoft enables the production environment in the Lifecycle Services project. The customer/partner can then deploy the production environment.

For more information, see the following articles:

- [Dynamics 365 Human Resources customer migration](./hr-cust-migration.md)
- [Prepare for go-live](../fin-ops-core/fin-ops/imp-lifecycle/prepare-go-live.md)
