---
# required metadata

title: Onboarding agent for Human Resources managers (preview)
description: Learn how HR managers use the Onboarding agent in Microsoft Dynamics 365 Human Resources to onboard employees, review recommendations, and complete onboarding activities in Microsoft Teams.
author: ramagadu
ms.date: 06/22/2026
ms.reviewer: twheeloc
ms.topic: how-to
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ramagadu
ms.search.validFrom: 2026-06-22
ms.dyn365.ops.version: Human Resources

---

# Onboarding agent for Human Resources (preview)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

HR managers often perform a series of repetitive tasks when onboarding employees, such as:

- Creating worker records
- Assigning onboarding checklists
- Assigning leave plans
- Entering compensation information

The Onboarding agent for HR managers helps reduce manual effort by assisting with these activities and providing recommendations based on employee and organizational information.

The Onboarding agent can:

- Generate draft worker records.
- Recommend onboarding checklists.
- Recommend leave plans.
- Support onboarding multiple employees in a single workflow.
- Provide a consolidated view of onboarding progress.

Human resource managers review and confirm all recommendations before changes are committed to Dynamics 365 Human Resources.

## Configuration

Before Human resource managers can use the Onboarding agent, an administrator must enable and configure the experience.
To configure the Onboarding agent, follow these steps:

1. Go to **Human Resources** > **Setup** > **Human resources parameters**.
1. Open the **Agent** tab.
1. In the **HR manager experience** section, set **HR manager experience** to **Yes**.
1. Enter a value for **Trigger lead days**.

The **Trigger lead days** field determines how many days before an employee's joining date the onboarding process begins.

For more information, see [Set up the Dynamics 365 Human Resources Onboarding agent](hr-onboarding-agent-setup.md).

## How it works

After you configure the Onboarding agent, it reviews candidate records in Human Resources and identifies candidates whose joining date falls within the configured trigger lead days window.

For example, if you set the trigger lead days value to 20, the onboarding process includes candidates who are scheduled to join within the next 20 days.

The Onboarding agent sends a notification to the Human resource manager in Microsoft Teams that includes:

- Candidate name
- Hiring manager
- Joining date

Human resource managers can then complete onboarding activities directly from Microsoft Teams. During the onboarding process, the Onboarding agent can:

- Generate draft worker records.
- Recommend onboarding checklists.
- Recommend leave plans.
- Consolidate onboarding progress across multiple candidates.

Human resource managers review and confirm all information before the Onboarding agent writes changes to Dynamics 365 Human Resources and Finance.

## Onboard new hires

The following sections describe how Human resource managers onboard new hires by using the Onboarding agent in Microsoft Teams.

### Prerequisites

Before you begin:

- Install the Onboarding agent and make it available in Microsoft Teams.
- Assign yourself the appropriate Human Resources security role.
- Get permission to create worker records, assign positions, assign leave plans, and manage compensation information.

### Start onboarding

1. Open the onboarding notification in Microsoft Teams.

   The notification lists candidates who are ready for onboarding.
1. Select one or more candidates.
1. Select **Begin onboarding**.

### Review worker records and onboarding checklists

1. Review the draft worker records that the Onboarding agent generates for each candidate.
1. Verify the position assignments.
1. Review the recommended onboarding checklist.
1. Modify the checklist if needed.
1. Confirm the checklist assignment.

You don't commit worker records and checklist assignments until you confirm them.

> [!NOTE]
> If personnel actions are enabled for worker creation, the Onboarding agent submits the record for the workflow approval.

### Assign leave plans

1. Review the leave plans that the Onboarding agent recommends.
1. Modify the recommendations if needed.
1. Assign the leave plans.

The Onboarding agent can use information such as the employee's role, organization, manager, legal entity, and other onboarding details when generating recommendations.

> [!NOTE]
> The Onboarding agent provides leave plan recommendations to assist human resource managers during onboarding. Human resource managers should review all recommendations and make any necessary adjustments before confirming them.

### Enter compensation information

1. Select one or more employees.
1. Enter compensation information, including compensation plan, level, and pay rate.
1. Review the compensation details.
1. Confirm the compensation information.

### Review onboarding progress

1. The Onboarding agent provides the brief summary.
1. You can track the detailed onboarding activities in the **Onboarding agent** workspace in Dynamics 365 finance and operations.

The **Onboarding summary** provides a consolidated view of onboarding activities across all selected employees.

- The onboarding process is completed for one or more employees.
- Worker records, onboarding checklists, leave plans, and compensation information are reviewed and confirmed.
- The onboarding summary is used to track completion status and identify any remaining onboarding activities.

## Related information

- [Dynamics 365 Human Resources onboarding agent](hr-onboarding-agent-overview.md)
- [Set up the Dynamics 365 Human Resources onboarding agent](hr-onboarding-agent-setup.md)
- [Onboarding agent for new hires](hr-onboarding-agent-for-new-hires.md)
