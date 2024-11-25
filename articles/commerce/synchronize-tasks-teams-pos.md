---
title: Synchronize task management between Microsoft Teams and Dynamics 365 Commerce POS
description: This article describes how to synchronize task management between Microsoft Teams and Dynamics 365 Commerce point of sale (POS).
author: ritakimani
ms.date: 07/29/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: josaw
ms.search.region: Global
ms.author: ritakimani
ms.search.validFrom: 2021-01-15
ms.dyn365.ops.version: 10.0.18
---

# Synchronize task management between Microsoft Teams and Dynamics 365 Commerce POS

[!include [banner](includes/banner.md)]

This article describes how to synchronize task management between Microsoft Teams and Dynamics 365 Commerce point of sale (POS).

One of the main purposes of Teams integration is to enable the synchronization of task management between the POS application and Teams. In this way, store employees can use either the POS application or Teams to manage tasks, and don't have to switch applications.

Because Planner is used as a repository for tasks in Teams, there must be a link between Teams and Dynamics 365 Commerce. This link is established by using a specific plan ID for a given store team.

The following procedures show how to set up task management synchronization between the POS and Teams applications.

## Link POS and Teams for task management

To link the POS and Microsoft Teams applications for task management in Commerce headquarters, follow these steps.

> [!NOTE]
> Before you try to integrate task management with Teams, make sure that you've enabled [Dynamics 365 Commerce and Microsoft Teams integration](enable-teams-integration.md). 

1. Go to **Retail and Commerce \> Task management \> Tasks integration with Microsoft Teams**.
1. On the Action Pane, select **Edit**.
1. Set the **Enable Task Management Integration** option to **Yes**.
1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Setup task management**. You should receive a notification that indicates that a batch job that's named **Teams provision** is being created.
1. Go to **System administration \> Inquiries \> Batch jobs**, and find the most recent job that has the description **Teams provision**. Wait until this job is finished running.
1. Run the **CDX job 1070** to publish the plan ID and store references to Retail Server.

## Publish a test task list in Teams

The following procedure assumes that your store teams are using Microsoft Teams task management integration with Commerce for the first time.

To publish a test task list in Teams, follow these steps.

1. Sign in to Teams as a communications manager. Typically, communications managers are users who have the **Regional manager** role in Commerce.
1. In the left navigation pane, select **Tasks by Planner**.
1. On the **Published lists** tab, select **New list** in the lower left, and name the new list **Test task list**.
1. Select **Create**. The new list appears under **Drafts**.
1. Under **Task title**, give the first task the title **Testing Teams integration**. Then select **Enter**.
1. In the **Drafts** list, select the task list. Then select **Publish** in the upper-right corner.
1. In the **Select who to publish to** dialog box, select the teams that should receive the test task list.
1. Select **Next** to review your publication plan. If you must make changes, select **Back**. 
1. Select **Confirm to proceed**, and then select **Publish**.
1. After publishing is completed, a message at the top of the **Published lists** tab indicates whether your task list was successfully delivered.

For more information, see [Publish task lists to create and track work in your organization](https://support.microsoft.com/office/publish-task-lists-to-create-and-track-work-in-your-organization-095409b3-f5af-40aa-9f9e-339b54e705df).

> [!NOTE]
> After the task list is published successfully in Teams, the tasks will be displayed in POS. POS managers and cashiers then need to turn on Microsoft Entra login in POS. For more information, refer to the [Enable Microsoft Entra authentication for POS sign-in](aad-pos-logon.md) article. 

## Additional resources

[Dynamics 365 Commerce and Microsoft Teams integration overview](commerce-teams-integration.md)

[Enable Dynamics 365 Commerce and Microsoft Teams integration](enable-teams-integration.md)

[Provision Microsoft Teams from Dynamics 365 Commerce](provision-teams-from-commerce.md)

[Manage user roles in Microsoft Teams](manage-user-roles-teams.md)

[Map stores and teams if there are pre-existing teams in Microsoft Teams](map-stores-existing-teams.md)

[Dynamics 365 Commerce and Microsoft Teams integration FAQ](teams-integration-faq.md)
