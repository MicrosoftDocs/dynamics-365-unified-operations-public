---
# required metadata

title: Onboarding agent FAQ (preview)
description: This article provides answers to frequently asked questions about the Onboarding agent in Microsoft Dynamics 365 Human Resources.
author: Pranjal-Sinha
ms.date: 06/23/2026
ms.reviewer: twheeloc
ms.topic: faq
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: pranjalsinha
ms.search.validFrom: 2026-06-23
ms.dyn365.ops.version: Human Resources

---

# Dynamics 365 HR Onboarding agent FAQ (preview)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article provides answers to frequently asked questions about the Onboarding agent in Microsoft Dynamics 365 Human Resources.

## What is the Onboarding agent?

The Onboarding agent is a guided experience in Microsoft Teams that helps HR managers and new hires complete onboarding activities. It automates routine onboarding tasks, provides recommendations based on employee and organizational information, and writes confirmed information back to Dynamics 365 Human Resources.

## What experiences does the Onboarding agent provide?

The Onboarding agent provides two experiences that work together:

- **Onboarding agent for HR managers** – Helps HR managers create worker records, assign onboarding checklists and leave plans, enter compensation, and track onboarding progress.
- **Onboarding agent for new hires** – Helps new hires complete day-one activities, such as reviewing personal details, adding identification and address information, confirming contacts, and sending a self-introduction email.

## Where do I use the Onboarding agent?

Both experiences run in Microsoft Teams. HR managers and new hires complete their onboarding activities in the flow of work, without switching to another application.

## What do I need before I can use the Onboarding agent?

An administrator must complete the prerequisites and set up the agent before HR managers and new hires can use it. For more information, see [Prerequisites for the onboarding agent](hr-onboarding-agent-prerequisites.md) and [Set up the Dynamics 365 Human Resources onboarding agent](hr-onboarding-agent-setup.md).

## What are trigger lead days?

Trigger lead days determine how many days before an employee's joining date the onboarding process begins. For example, if the trigger lead days value is 20, candidates who are scheduled to join within the next 20 days are included in the onboarding process.

## How does the Onboarding agent select candidates for onboarding?

After you configure the agent, it reviews candidate records in Human Resources and identifies candidates whose joining date falls within the configured trigger lead days window. The agent then notifies the HR manager in Microsoft Teams with the candidate's name, hiring manager, and joining date.

## Does the Onboarding agent make changes automatically?

No. The Onboarding agent generates drafts and recommendations, but HR managers and new hires review and confirm the information before any changes are committed to Dynamics 365 Human Resources.

## What information can the Onboarding agent prefill or extract?

The agent can use information collected during recruitment to prefill details, and it can extract information from documents that a new hire uploads, such as an identification document. New hires review the extracted information and make corrections before saving.

## Can HR managers onboard more than one candidate at a time?

Yes. HR managers can select one or more candidates and onboard them in a single workflow. The **Onboarding summary** provides a consolidated view of onboarding progress across all selected employees.

## How are onboarding checklist and leave plan recommendations generated?

The Onboarding agent generates recommendations by using information such as the employee's role, organization, manager, legal entity, and other onboarding details. HR managers can review and adjust the recommendations before they confirm them.

## Does compensation information flow to payroll?

After an HR manager confirms compensation information, the records are available in Dynamics 365 Human Resources, which helps prepare new hires for payroll processing.

## Is the Onboarding agent generally available?

The onboarding agent is available in public preview. Preview features aren't meant for production use and might have restricted functionality.

## Related information

- [Dynamics 365 Human Resources onboarding agent](hr-onboarding-agent-overview.md)
- [Onboarding agent for HR managers](hr-onboarding-agent-for-hr.md)
- [Onboarding agent for new hires](hr-onboarding-agent-for-new-hires.md)
