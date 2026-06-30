---
# required metadata

title: Set up the Dynamics 365 Human Resources Onboarding agent (preview)
description: This article explains how to set up the Onboarding agent for HR and the Onboarding agent for new hires in Microsoft Dynamics 365 Human Resources.
author: Pranjal-Sinha
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
ms.author: pranjalsinha
ms.search.validFrom: 2026-06-17
ms.dyn365.ops.version: Human Resources

---

# Set up the Dynamics 365 Human Resources Onboarding agent (preview)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)].

This article explains how to set up the Onboarding agent in Microsoft Dynamics 365 Human Resources for both the Onboarding agent for HR and the Onboarding agent for new hires. Before you begin, complete the prerequisites. For more information, see [prerequisites for the onboarding agent](hr-onboarding-agent-prerequisites.md).

## Common setup steps

### Enable the Onboarding agent (preview) feature

To enable the Onboarding agent, follow these steps:

1. In Dynamics 365 Human Resources, open the **Feature management** workspace.
1. Select **Check for updates**.
1. Search for the **Onboarding agent (preview)** feature.
1. Select the feature, and then select **Enable now**.

### Install the solution from the Power Platform admin center (PPAC)

To install the solution, follow these steps:

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), and select the environment where you want to install the app.
1. In the left pane, select **Resources** \> **Dynamics 365 apps**.
1. Select **Install app**, and search for **Dynamics 365 Human Resources onboarding agent (preview)** in the list.
1. Select **Next**, agree to the terms of service, and then install the app.

## Onboarding agent for HR

Before you begin this section, complete the **Common setup steps**.

### Enable Onboarding agent for HR

To enable the Onboarding agent for HR, follow these steps:

1. In Dynamics 365 Human Resources, open the **Human resources parameters** page.
1. On the **Agent** tab, set the **HR manager experience** option to **Yes**, and then set the trigger lead days.

> [!NOTE]
> If you receive an error message when you enable the **HR manager experience** option, go to the **Recruitment** tab, set the **Recruitment enabled** option to **Yes**. Set the **Recruitment experience** field to **HR Recruitment**. Then enable the **HR manager experience** option again.

### Set up connection references and turn on the Human Resources flows

To set up connection references, follow these steps:

1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/) using administrator credentials, and select your environment.
1. In the left pane, select **Solutions**, and then select the **Managed** tab.
1. On the **Managed** tab, find and open the **HcmAdminOnboardingAgent** solution, and then select **Cloud flows**.
1. To set the connection references, select on each flow, and then select **Edit**. Sign in by using administrator credentials, and then select **Save**.
1. To turn on each flow, select the more options (**...**) menu for the flow, and then select **Turn on**. Repeat this step for all flows.

### Publish Onboarding agent for HR to Teams

To publish the Onboarding agent for HR, follow these steps:

1. In the maker portal, select the **Agents** tab, and open **Onboarding agent for HR**.
1. Select **Publish**.
1. Select the **Channels** tab.
1. Select **Teams and Microsoft 365 Copilot**, and select **Add channel**.
1. Select **Availability options**. In **Availability options**, you can also change the name and other settings.
1. Select **Submit for admin approval**. The request is submitted to the Teams administrator for approval.

### Approve and publish the HR app in Teams admin center

A Teams administrator must complete the following steps in the Teams admin center.

1. Go to the [Teams admin center](https://admin.teams.microsoft.com/), search for the app, and select it.
1. Publish the app.
1. (Optional) Go to **Manage policies**, and add the Onboarding agent so that it's installed by default.
1. Optionally, pin the app by adding it to the pinned apps section.

After the app is published, HR administrators who want to use the app can install it in Teams, in the **Built for your org** section.

## Onboarding agent for new hires

Before you begin this section, complete all steps in **Common setup steps**.

### Enable for Onboarding agent for new hires

1. In Dynamics 365 Human Resources, open the **Human resources parameters** page.
1. On the **Agent** tab, set the **Employee experience** option to **Yes**. Then add a welcome message or set up links.

### Configure checklist for Onboarding agent for new hires

1. Go to **Human Resources** > **Task management** > **Links** > **Onboarding checklists**, and create a new checklist.
1. Under the new checklist, select **Create tasks**.
1. For each task, enter a name, set **Assignment type** to **Employee self service**, and set **Use onboarding agent** to **Yes**.
1. In the **Agent tasks** section, set the required onboarding activity to **Yes**, such as **Personal details**, **Identification numbers**, **Addresses**, **Contacts**, or **Draft an email**.
1. Select **OK** to create the task.

> [!TIP]
> Although a single checklist task can include multiple enabled **Agent tasks**, using separate checklist tasks for distinct onboarding activities can improve visibility into onboarding progress and simplify task management.

### Set up connection references and turn on the new-hire flows

1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/) using administrator credentials, and select your environment.
1. In the left pane, select **Solutions**, and then select the **Managed** tab.
1. On the **Managed** tab, find and open the **HcmEmployeeOnboardingAgent** solution, and then select **Cloud flows**.
1. To set the connection references, select each flow, and then select **Edit**. Sign in by using administrator credentials, and then select **Save**.
1. To turn on each flow, select the more options (**...**) menu for the flow, and then select **Turn on**. Repeat this step for all flows.

### Assign the security role to a team or user

1. In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), select the sandbox environment.
1. Under **Access**, select **Security roles**.
1. Select **See all**.
1. On the new page, search for **HcmEmployeeOnboardingAgent Role**.
1. In the list, select the ellipsis (**...**) menu for the role, and then select **Members**.
1. Add the individual users or groups who should use onboarding agent for new hires.

For information about creating and managing Dataverse teams, see [Microsoft Dataverse teams management](/power-platform/admin/manage-teams).

### Publish the Onboarding agent for new hires to Teams

1. In the maker portal, select the **Agents** tab, and then select **Onboarding agent for new hires**.
1. Select **Publish**.
1. Select the **Channels** tab.
1. Select **Teams and Microsoft 365 Copilot**, and then select **Add channel**.
1. Select **Availability options**. In **Availability options**, you can also change the name and other settings.
1. Select **Submit for admin approval**. The request is submitted to the Teams administrator for approval.

### Approve and publish the new-hire app in Teams admin center

A Teams administrator should complete the following steps in the Teams admin center.

1. Go to the [Teams admin center](https://admin.teams.microsoft.com/), search for the app, and then select it.
1. Publish the app.
1. If needed, go to **Manage policies**, and add the onboarding agent for new hires so that it's installed by default.
1. Optionally, pin the app by adding it to the pinned apps section.

After the app is published, employees who want to use the app can install it in Teams, in the **Built for your org** section.
