---
# required metadata

title: Human Resources migration go-live readiness review
description: This article provides guidance on go-live readiness review for Dynamics 365 Human Resources migration to finance and operations infrastructure.
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

This article describes the go-live readiness review steps for Dynamics 365 Human Resources migration to finance and operations infrastructure.

## Human Resources migration go-live readiness review process

1. Before requesting the production environment, complete the prerequisites that are listed in [Prerequisites for migrating a Human Resources production environment](hr-cust-migration.md#prerequisites).
2. Email d365fogl@microsoft.com with the subject "[Customer name]: Human Resources migration go-live readiness review".
Provide the following information in the email:
 - Customer name
 - Key customer contact(s) e-mail(s) and role(s)
 - Partner
 - Migration LCS project URL
 - Go-live date (live transactions)
 - Date when production is requested 

In addition, copy the following list into the email, and fill in the following information:

#### LCS
- Does the go-live milestone date in LCS methodology matching the planned go-live date? Confirm that the go-live date in LCS reflects the actual go-live date when users start working in production.
- Are you using a generic account as the environment’s administrator?
- Have the customer key stakeholders been added to the LCS project?
- Is the analysis, design and develop, and test phases in the LCS methodology completed to request a production environment?
- Confirm that the final version of the subscription estimator uploaded to LCS project and marked as active.

#### User Acceptance Testing
- Provide the start date and end date of the UAT in the migrated sandbox environment.
- Which environment was UAT performed? 
- Confirm that user training or change management has been completed.
- Has the entire solution been approved and signed off by the customer to confirm that it meets their business needs? If not, what is pending and what is the timeline for sign-off?

#### Cutover
- Do you have a cutover plan that contains activity duration, responsibilities, dependencies, and a roll-back plan, signed off by the business?
- Confirm that migration to environments will always be on the latest generally available (GA) version. Depending on your migration and testing plan, if your migration validation for sandbox environments was on a different version, we recommend that you validate a sandbox migration on the same version as your production environment.
- Confirm that all remaining standalone Human Resources environments will automatically be deleted 10 days after the successful migration of the production environment to the finance and operations infrastructure. 

#### Continuous Updates
- Is the team familiar with the continuous updates policy?
- Have you reviewed the continuous updates settings in your LCS project and made adjustments as needed?
- Briefly describe your organization’s plan for continuous updates.

#### Integrations
- Are integrations in scope?

> [!NOTE]
> If yes, complete the following section. If no, go to the next section.

- Have you tested both happy path and edge cases for each integration?
- Are all integrations that are in scope for go-live signed off by the customer? If no, what is pending and what is the timeline for getting sign-off?

#### Dual Write
- Does the solution contain any dual-write integrations to run processes across Dynamics 365 applications?

> [!NOTE]
> If yes, complete the following section. If no, go to the next section.

- Are you planning to integrate two finance and operations environments?
- Are both finance and operations environments in the same Azure tenant and in the same Azure region?
- Are you planning to have multiple Dataverse (formerly CDS) instances or multiple finance and operations apps instances?
- Have all dual-write flows been tested and have the acceptance criteria been met at expected peak load?
- Are you using managed solutions to follow application lifecycle management (ALM) best practices for your Dataverse (formerly CDS) custom entities and extensions?
- Are notifications set up to alert users about any dual-write failures?
- Confirm that you have read and understood the limitations for implementing dual-write: [System requirements for dual-write document](../fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-system-req.md).
  
 #### Production Support and Maintenance 
- Does the project team have a plan in place for regular production environment monitoring and maintenance routine?
- Is the project team familiar with the LCS environment monitoring and diagnostics tool?
- Has the project team defined post go-live issue resolution and escalation process?

3. After emailing the answers to the previous questions, the Dynamics 365 finance and operations go-live team will reply to you within two business days. A FastTrack team works with you on the assessment of the project readiness for production deployment and share the potential risks, best practices, and recommendations for a successful go-live of the project.
   
4. After all critical risks have been addressed and the review has been completed, Microsoft will enable the production environment in the Lifecycle Services project. The customer/partner can then deplay the production environment.

For more information, see: 
[Dynamics 365 Human Resources customer migration](./hr-cust-migration.md)
[Prepare for go-live](../fin-ops-core/fin-ops/imp-lifecycle/prepare-go-live.md)
