---
# required metadata

title: Onboarding agent for new hires (preview)
description: This article describes the Onboarding agent for new hires in Microsoft Dynamics 365 Human Resources, including how new hires complete their day-one onboarding.
author: Pranjal-Sinha
ms.date: 06/22/2026
ms.topic: how-to
ms.reviewer: twheeloc
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
ms.search.validFrom: 2026-06-22
ms.dyn365.ops.version: Human Resources

---

# Onboarding agent for new hires (preview)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)].

The Onboarding agent for new hires helps employees complete day-one onboarding activities in Microsoft Teams. The agent provides a guided onboarding experience that includes personalized tasks, onboarding resources, and assistance with entering employee information. You can use information collected during recruitment and information extracted from uploaded documents to reduce manual data entry.

## Configuration

Before employees can use the Onboarding agent, an administrator must enable and configure the experience.

1. Go to **Human Resources** > **Setup** > **Human resources parameters**.
1. Open the **Agent** tab.
1. In the **Employee experience** section, set **Enable employee experience** to **Yes**.
1. Enter the welcome message that employees see when they begin onboarding.
1. Configure links to documents, learning materials, and other resources that employees should access during onboarding.

For more information, see [Set up the Dynamics 365 Human Resources onboarding agent](hr-onboarding-agent-setup.md).

## How it works

After an employee joins the organization, the Onboarding agent sends a welcome notification in Microsoft Teams. The notification includes a link to the employee onboarding workspace.

The onboarding workspace contains:

- A personalized onboarding checklist.
- Documents, learning materials, and organizational resources.
- Guided activities for completing employee information.

As employees complete onboarding activities, the agent can use information from recruitment records and uploaded documents to help populate required information. Employees should review all suggested information and make corrections before saving.

> [!NOTE]
> Information extracted from uploaded documents might require review and correction before it's saved.

## Complete onboarding

The following sections describe how to complete onboarding activities in Microsoft Teams.

### Prerequisites

Before you begin:

- You join the organization.
- You have access to Microsoft Teams.
- The Onboarding agent is enabled for your organization.

### Start onboarding

1. Open the welcome notification from the Onboarding agent in Microsoft Teams.
1. Select **Get Started** to begin your onboarding.
1. The onboarding agent displays your onboarding details together with links, learning materials, and resources.
1. Select **Begin onboarding**.

### Review personal details

1. Open the **Personal details** activity.
1. Review the information that the recruitment process imported.
1. Make any necessary changes.
1. Select **Confirm**.

You complete the activity, and you can continue to the next activity.

### Add identification details

1. Open the **Identification details** activity.
1. Select **Add document**.
1. Upload an image of your identification document.

   The Onboarding agent extracts information from the document and creates a draft identification record.
1. Review the extracted information.
1. Correct any information as needed.
1. Select **Save all**.

### Add your address

You can provide your address in one of two ways.

#### Use the address from your identification document

1. Review the address that the system extracts from your identification document.
1. Confirm that the address is correct.
1. Save the address.

#### Enter an address manually

1. Enter your address in natural language.
1. Select **Submit**.

   The Onboarding agent structures the address automatically.
1. Review the address details.
1. Make any necessary corrections.
1. Save the address.

### Confirm contact details

1. Open the **Employee contacts** activity.

   The system automatically displays contact information that it collected during recruitment, such as email addresses and phone numbers.
1. Review the existing contact information.
1. To add a contact, select **Add**, enter the required information, and save the record.
1. Confirm the contact details.

### Create and send a self-introduction email

1. Open the **Self-introduction** activity.
1. Provide the information requested by the onboarding agent.

   The Onboarding agent generates a draft introduction email.
1. Open the draft email in Outlook.
1. Review and edit the email as needed.
1. Send the email.
1. Mark the activity as completed.

### Review onboarding status

1. Open the **Onboarding summary** activity.

   The summary displays the onboarding activities that you completed, including:

   - Personal details
   - Identification details
   - Address information
   - Contact information
   - Self-introduction email
1. Select **Continue** to check for any remaining onboarding tasks.

If no onboarding tasks remain, you can view other assigned activities in **My Tasks** in **Employee self service** in Dynamics 365 finance and operations.

## Result

You completed your onboarding activities. You reviewed and confirmed your personal information, created your onboarding records, and sent your self-introduction email. You can view any remaining work items in **My Tasks** in Dynamics 365 finance and operations.

## Related information

- [Dynamics 365 Human Resources onboarding agent](hr-onboarding-agent-overview.md)
- [Onboarding agent for HR](hr-onboarding-agent-for-hr.md)
