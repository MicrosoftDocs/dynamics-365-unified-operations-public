---
title: Set up impact analysis (production-ready preview)
description: Learn how to configure features, assign permissions, and activate Power Automate flows in Dynamics 365.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/24/2026
ms.custom:
  - bap-template
---

# Set up impact analysis (production-ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article describes how to set up impact analysis together with supplier communications or as a standalone Procurement Agent capability for use with the vendor collaboration interface and/or manual simulation.

## If you're already using supplier communications

If you're already using the supplier communications capabilities of the Procurement Agent (previously known as the Supplier Communications Agent), you don't need to follow all of the steps in this article to add the impact analysis features because you've already completed most of the required steps. Just do the following steps:

- Make sure you're running Microsoft Dynamics 365 Supply Chain Management version 10.0.48 or later.
- Install *Copilot in Microsoft Dynamics 365 Supply Chain Management* version 1.1.03413.1 or later.
- Make sure that the following Microsoft Copilot Studio agent is published in that environment: *Procurement Agent - Impact Analysis*.
- Turn on the *(Production-ready preview) Procurement Agent - Impact analysis* feature in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Select **Check for updates** if the feature isn't shown on your system.
- Add the following security user role: *Procurement User Role (Preview)*.
- [Activate the triggering Power Automate flows for impact analysis](#impact-analysis-trigger-flows), as described later in this article.

## If you will use impact analysis without supplier communications

### Prerequisites

To use impact analysis, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.48 or later, with all available quality updates.  
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Select **Check for updates** if the features aren't shown on your system.

    - [*Immersive Home*](../../fin-ops-core/fin-ops/copilot/immersive-home.md)
    - [*Agent management*](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md)
    - *(Production-ready preview) Procurement Agent - Impact analysis*

    > [!TIP]
    > If you can't enable the *Agent management* feature, make sure that all of its [prerequisites](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md) are fulfilled, such as version requirements and Copilot Studio billing enablement.

- In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), make sure you're running the following versions of the following Dynamics 365 Apps in your Supply Chain Management environment. It's important that you install or update them in the following order:
    - First, install *Copilot for finance and operations apps* version 1.0.03048.2 or later. If it's already installed, update it to the latest version.
    - Then, install *Copilot in Microsoft Dynamics 365 Supply Chain Management* version 1.1.03413.1 or later. If it's already installed, update it to the latest version.

- Normally, the Microsoft Copilot Studio agent needed for impact analysis to run is published automatically. But there might be data loss prevention (DLP) policies on your environment that prevent the publishing of this agent. To check if the agents are successfully published, go to [Copilot Studio](https://copilotstudio.microsoft.com/) and find your environment. Make sure that the following Microsoft Copilot Studio agent is published in that environment: *Procurement Agent - Impact Analysis*. If the agent isn't published, you can find help in [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting).

<a name="set-up-agent-identity"></a>

### Set up an agent identity

The Procurement Agent impact analysis features interact with Dataverse and Microsoft Copilot Studio. Follow the instructions in the following subsections to create the required connections and set up the *agent identity* that the agent uses for these interactions.

> [!TIP]
> For security and ease of maintenance, use a dedicated identity for the agent.

#### Set up agent identity users and assign security roles

Use the user management features for your tenant to create an *agent identity user*. Then assign the licenses and security roles described in the following subsections to that user.

##### License requirements

Impact analysis uses premium tier connectors, so the agent identity user must have a license that permits those connectors. Learn more in [Power Platform licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq) or download the [Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130).

Examples of sufficient licenses include *Power Apps Premium*, *Power Automate Premium*, or *Dynamics 365 Supply Chain Management*.

Use the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?referrer=entra#/licenses) to assign the required licenses.

##### Required security roles

Add the agent identity user both to the Dataverse environment and to Supply Chain Management. Assign the agent identity user the security roles shown in the following lists. Some user roles are common for the Procurement Agent - supplier communications and impact analysis.

- Required Dataverse user roles:

    - *Finance and Operation Basic User*
    - *Supplier Communications Agent*
    - *Environment Maker*

- Required Supply Chain Management user roles:

    - *System user*
    - *System agent*

> [!NOTE]
> The *System agent* role in Supply Chain Management exempts the agent identity user from license enforcement. This means that you don't need to allocate a user license to the agent.

### Assign permissions to users working with the agent

All Dynamics 365 Supply Chain Management users working with the agent must also be created as Dataverse users (if they aren't already). To learn how, go to [Create users](/power-platform/admin/create-users).

Additionally, assign the roles described in the following subsections.

#### Permissions for users who manage the agent configuration

Users who manage the agent configuration must have the following roles:

- Required Dataverse user roles:
    - *Basic User*
    - *Finance and Operations Agent Configuration Manager*
    - *Finance and Operations Basic User*

- Required Supply Chain Management user roles:
    - *System user*
    - *Purchasing manager* and/or *Purchasing agent*

#### Permissions for users who review agent results

Users who review the agent results must have the following roles:

- Required Dataverse user roles:
    - *Basic User*
    - *Finance and Operations Basic User*
    - *Procurement User Role (Preview)*

- Required Supply Chain Management user roles:
    - *System user*
    - *Purchasing agent*

### Create the required connections

To create the required connections, follow these steps:

1. Open the [Power Apps Maker portal](https://make.powerapps.com) and sign in as an environment administrator user.
1. Use the **Environment** drop-down list in the page header to select the environment associated with your finance and operations apps.
1. In the left navigator, select **Connections**.
1. At the top of the page, select **New connection**.
1. Use the **Search** field at the right side of the page to find the connection with a **Name** of *Microsoft Dataverse* (if you see two, use the one with the green icon). Select **Create** for that row and follow the instructions on your screen. Sign in with the intended *agent identity user* when prompted.
1. You return to the **Connections** list. Your new connector is now shown at the bottom of the list and is named after the agent identity you signed in with when creating it.
1. At the top of the page, select **New connection**.
1. Find the connection with a **Name** of *Microsoft Copilot Studio*. Select **Create** for that row and follow the instructions on your screen. Sign in as the intended agent identity when prompted.
1. You return to the **Connections** list. Your new connector is now shown at the bottom of the list and is named after the agent identity you signed in with when creating it.

    :::image type="content" source="media/sca-connections-setup.png" alt-text="Example connections setup" lightbox="media/sca-connections-setup.png":::

<a name="trigger-flows"></a>

### Activate the triggering Power Automate flows

#### For the Procurement Agent

To finish setting up the agent identity, first activate the triggering common Procurement Agent Power Automate flows, and then activate the triggering impact analysis specific flows.

1. Sign in to the [Power Apps Maker portal](https://make.powerapps.com) as an environment administrator user.
1. Select your environment from the **Environment** drop-down list in the page header.
1. In the left pane, select **Solutions**.
1. Open the **Managed** tab.
1. Find and open the solution with a **Display name** of *Copilot in Supply Chain Management solution*.
1. On the **Objects** pane, select **Apps**.
1. Select the app with a **Display name** of *(Production ready preview) Setup Supplier Communications Agent*. This step applies for both the supplier communications and impact analysis features of the Procurement Agent.
1. Select **Play**. If **Play** is disabled on the command bar, select **Share**, add your name, and select **Share**.
1. Select the *(Production ready preview) Setup Supplier Communications Agent* app again and then select **Play** on the command bar.
1. Under **Connections**, select the connections you created in the previous section for both *Microsoft Dataverse* and *Microsoft Copilot Studio*.
1. Select **Apply** at the bottom-right of the page and wait for all of the flows listed under **Agent trigger flows status** to switch to a state of *Activated*.

<a name="impact-analysis-trigger-flows"></a>

#### For impact analysis

Next, activate the specific impact analysis Power Automate flow.

1. Sign in to the [Power Apps Maker portal](https://make.powerapps.com) as an environment administrator user.
1. Select your environment from the **Environment** drop-down list in the page header.
1. In the left pane, select **Solutions**.
1. Find the solution with a **Display name** of *Copilot in Supply Chain Management solution*.
1. On the left pane, select **Objects**.
1. On the objects pane, select **Cloud Flows**.
1. Select the cloud flow with the **Display name** of *Procurement Agent - Impact analysis (Preview)*.
1. Select **Turn on** in the top navigation bar.
