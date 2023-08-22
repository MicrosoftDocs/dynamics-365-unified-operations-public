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

1. Before you request a production environment, complete the [prerequisites for migrating a Human Resources production environment](hr-cust-migration.md#prerequisites-1).
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

    - Have the analysis, design and develop, and test phases in the Lifecycle Services methodology been completed to request a production environment?
    - Are you using a generic account as the environment's administrator?
    - Have the customer's key stakeholders been added to the Lifecycle Services project?
    - Confirm that the final version of the subscription estimator was uploaded into the Lifecycle Services project and marked as active.

    **User acceptance testing (UAT)**

    - Has the customer approved and signed off on the migration solution to confirm that it meets their business needs? If not, what's still pending, and what's the timeline for sign-off?
    - Confirm that user training or change management has been completed.

    **Cutover**

    - Do you have a cutover plan that includes the activity duration, responsibilities, dependencies, and a roll-back plan, and has the business signed off on it?
    - Please acknowledge your understanding that migrations to new environments will always be on the latest generally available (GA) release. Depending on your migration and testing plan, if the validation in the sandbox environment was done using a different version, we strongly recommend that you perform a regression validation using the release that your production environment will be in. You can find details about the release timeline for each release [here](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/public-preview-releases#targeted-release-schedule-dates-subject-to-change).
    - Please acknowledge your understanding that all standalone Human Resources environments will automatically be deleted 10 days after the successful migration of the production environment to the Finance and Operations infrastructure. And this has been considered in your rollback strategy.
    - Please acknowledge your understanding that the Human Resources migrated environments will be placed in the same region as the source standalone Human Resources environments. If there is requirement of geo to geo migration for the Lifecycle Services or environments, that would be a separate process and must be done once Human Resources sandbox and production migration is completed.

    **Continuous updates**

    - In standalone Human Resources, updates are managed by Microsoft with defined schedule. However, in Finance and Operations infrastructure, customer need to maintain application updates as per Microsoft One version policy. Please confirm you understand the continuous update policy for Finance and Operations which is documented [here](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/oneversion-overview?context=%2Fdynamics365%2Fcontext%2Fcommerce).
    
   
    **Integrations**

    - Are integrations in scope?

        > [!NOTE]
        > If the answer is "Yes," answer the below question in this section. Otherwise, move on to the next section.

    - Have you tested both the happy path and edge cases for each integration and signed off on all integrations that are in scope for go-live? If not, what's still pending, and what's the timeline for sign-off?

    **Dual-write**

    - Does the solution contain any dual-write integrations that are used to run processes across Dynamics 365 applications?
      
        > [!NOTE]
        > If the answer is "Yes," answer the below question in this section. Otherwise, move on to the next section.
        
    - Have all dual-write scenarios and flows been tested after migration, and have the acceptance criteria been met at the expected peak load? If not, what's still pending, and what's the timeline for sign-off?
  
    **Production support and maintenance**

    - Does the project team have a plan in place for regular, monitoring and maintenance of the production environment?
    - Is the project team familiar with the environment monitoring and diagnostics tool in Lifecycle Services?
    - Has the project team defined a process for post-go-live issue resolution and escalation?

3. The Dynamics 365 finance and operations go-live team replies to your email within two business days. A FastTrack team then works with you to assess the project's readiness for production deployment. The team also shares the potential risks, best practices, and recommendations for a successful go-live of the project.
4. After all critical risks have been addressed, and the review has been completed, Microsoft enables the production environment in the Lifecycle Services project. The customer/partner can then deploy the production environment.

For more information, see the following articles:

- [Dynamics 365 Human Resources customer migration](./hr-cust-migration.md)
- [Prepare for go-live](../fin-ops-core/fin-ops/imp-lifecycle/prepare-go-live.md)
