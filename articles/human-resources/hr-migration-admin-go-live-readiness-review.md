# required metadata

title: Human Resources migration go-live readiness review
description: This page provides guidance on go-live readiness review for Dynamics 365 Human Resources migration to finance and operations infrastructure.
author: Priyanka Sinha
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
ms.author: prsinha
ms.search.validFrom: 2023-8-7
ms.dyn365.ops.version: Human Resources

---

# Human Resources migration go-live readiness review

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Go-Live Readiness review steps for Dynamics 365 Human Resources migration to finance and operations infrastructure.

## Human Resources migration go-live readiness review process

**1**. Before requesting the production environment, ensure that all prerequisites called out in [Prerequisites for migrating a Human Resources production environment](https://learn.microsoft.com/en-us/dynamics365/human-resources/hr-cust-migration#prerequisites-1) are completed.

**2**. Send an email to Dynamics 365 FO Go-Live (d365fogl@microsoft.com) with subject "**[Customer name]: Human Resources migration go-live readiness review**".
   
To ensure that the process will run smoothly, provide the following details in the email,
  - Customer name:
  - Key customer contact(s) e-mail(s) and role(s): 
  - Partner: 
  - Migration LCS project URL:
  - Go-Live date (live transactions):
  - Date when Production will be requested: 

Additionally, copy the following list to your email, and then answer all of the information line by line.

#### LCS
- Is the Go-Live milestone date in LCS methodology matching the planned Go-Live date? Please make sure that Go-Live date in LCS in reflecting the real Go-Live   plans when users will start live operations in Production.
- Are you using a generic account as the environment’s administrator?
- Have the customer key stakeholders been added to the LCS project?
- Are Analysis, Design and Develop, and Test phases in the LCS methodology completed to request Production Environment?
- Is the final version of the Subscription estimator uploaded to LCS project and marked as active?

#### User Acceptance Testing
- Provide the start date and end date of the UAT in the migrated sandbox environment.
- On which environment was UAT performed? Please provide the environment name.
- If you need user training or change management to be conducted, please confirm this has been completed?
- Has the entire solution approved, and signed off by the customer to confirm that it meets their business needs? If no, please share what is pending and what is the timeline for getting sign-off.

#### Cutover
- Do you have a cutover plan that contains activity duration, responsibilities, dependencies, and a roll-back plan, signed off by the business?
- Please confirm that you are aware that migration to environments will always be on the latest generally available (GA) version. Depending on your migration and testing plan, if your migration validation for sandbox environments was on a different version, we recommend that you validate a sandbox migration on the same version as your production environment.
- Please confirm that you are aware that all remaining standalone Human Resources environments will automatically be deleted ten days after the successful migration of the production environment to the finance and operations infrastructure. 

#### Continuous Updates
- Is the team familiar with the Continuous Updates policy?
- Have you reviewed the Continuous Updates settings in your LCS project and made adjustments as needed?
- Briefly describe your organization’s plan for Continuous Updates

#### Integrations
- Are integrations in scope?

> [!NOTE]
> If yes, continue and complete below section. If No, go to the next section.

- Have you tested both happy path and edge cases for each integration?
- Have all integrations in scope for the Go-live been signed off by the customer? If no, please share what is pending and what is the timeline for getting sign-off.

#### Dual Write
- Does the solution contain any dual-write integrations to run processes across Dynamics 365 applications?

> [!NOTE]
> If yes, continue and complete below section. If No, go to the next section.

- Are you planning to integrate two finance and operations environments?
- Are both finance and operations environments in the same Azure tenant and in the same Azure region?
- Are you planning to have multiple Dataverse (formerly CDS) instances or multiple Finance and Operations apps instances?
- Have all dual-write flows been tested and have the acceptance criteria been met at expected peak load?
- Are you using managed solutions to follow application lifecycle management (ALM) best practices for your Dataverse (formerly CDS) custom entities and extensions
- Are notifications set up to alert users about any dual-write failures?
- Please confirm that you have read and understood the limitations for implementing dual-write in [System requirements for dual-write document](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-system-req).
  
 #### Production Support and Maintenance 
- Does the project team have a plan in place for regular Production environment monitoring and maintenance routine?
- Is the project team familiar with the LCS environment monitoring and diagnostics tool?
- Has the project team defined post Go-live issue resolution and escalation process?

**3**. When answers have been provided to all the questions, the Dynamics 365 FO Go-Live team will reply to you within two business days and a FastTrack team will work with you on the assessment of the project readiness for production deployment and will share the potential risks, best practices, and recommendations for a successful go-live of the project.
   
**4**. When all critical risks have been addressed, and the review has been completed, Microsoft enables the production environment slot in the Lifecycle Services project. The customer/partner can then trigger the production environment deployment.

## See also

[Dynamics 365 Human Resources customer migration](https://learn.microsoft.com/en-us/dynamics365/human-resources/hr-cust-migration)

[Prepare for go-live](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/imp-lifecycle/prepare-go-live)

[Go-live FAQ](hr-admin-go-live-faq.md)
