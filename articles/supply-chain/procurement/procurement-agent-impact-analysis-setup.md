---
title: Set up impact analysis (production ready preview)
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

# Set up impact analysis (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article describes how to set up impact analysis as a standalone Procurement Agent capability for use with the Vendor Collaboration Module and/or manual simulation. If you want to use both supplier communications and impact analysis together, and already have set up supplier communications, you will need to adhere to the following additional prerequisites:

- Later Microsoft Dynamics 365 Supply Chain Management version
- Turn on specific feature for impact analysis in feature management
<!-- - Triggering power automate flow for impact analysis - LS: Will updated shortly after public preview date -->

## Prerequisites

Before you can use impact analysis, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.48 or later, with all available quality updates.  
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Select **Check for updates** if the features aren't shown on your system.

    - [*(Production ready Preview) Immersive Home*](../../fin-ops-core/fin-ops/copilot/immersive-home.md)
    - [*(Production ready preview) Agent management*](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md)
    - *(Production ready preview) Procurement Agent - Impact analysis*
        - Once this feature is enabled, you can use the [Impact simulation](procurement-agent-impact-analysis-simulation.md) feature without any further configuration.

    > [!TIP]
    > If you can't enable the *Agent management* features, make sure that all of the [prerequisites](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md) are fulfilled, such as version requirements and Copilot Studio billing enablement.

- In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), make sure you're running the following versions of the following Dynamics 365 Apps in your Supply Chain Management environment. It's important that you install or update them in the following order:
    - First, install *Copilot for finance and operations apps* version 1.0.03048.2<!-- LS: Will updated shortly after public preview date --> or later. If it's already installed, update it to the latest version.
    - Then, install *Copilot in Microsoft Dynamics 365 Supply Chain Management* version 1.1.03071.1<!-- LS: Will updated shortly after public preview date --> or later. If it's already installed, update it to the latest version.
- Normally, the Microsoft Copilot Studio agent needed for impact analysis to run is published automatically. But there might be data loss prevention (DLP) policies on your environment that prevent the publishing of this agent. To check if the agents were successfully published, go to [Copilot Studio](https://copilotstudio.microsoft.com/) and find your environment. Make sure that the following Microsoft Copilot Studio agents are published in that environment:
    - *Procurement Agent - Impact Analysis*

    If the agent isn't published, you can find help in [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting).

## <a name="set-up-agent-identity"></a>Set up an agent identity

The Procurement Agent impact analysis interacts with Dataverse and Microsoft Copilot Studio to do its work. Select the identity that the agent uses for these interactions and create the required connections.

> [!TIP]
> For security and ease of maintenance, use a dedicated identity for the agent.

### Set up agent identity users and assign security roles

Use the user management features for your tenant to create an *agent identity user*. Then assign the licenses and security roles described in the following subsections to that user.

#### License requirements

Impact analysis uses premium tier connectors, so the agent identity user must have a license that permits those connectors. Learn more in [Power Platform licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq) or download the [Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130).

Examples of sufficient licenses include *Power Apps Premium*, *Power Automate Premium*, or *Dynamics 365 Supply Chain Management*.

Use the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?referrer=entra#/licenses) to assign the required licenses.

#### Required security roles

Add the agent identity user both to the Dataverse environment and to Supply Chain Management. Assign the agent identity user the security roles shown in the following lists.

- Required Dataverse user roles:

    - *Finance and Operation Basic User*
    - *Supplier Communications Agent* <!-- LS: Will be changed shortly after public preview date to "Procurement Agent" -->
    - *Environment Maker*

- Required Supply Chain Management user roles:

    - *(Preview) Supplier Communications Agent* <!-- LS: Will be changed shortly after public preview date to "Procurement Agent" -->
    - *System user*
    - *System agent*

> [!NOTE]
> The *System agent* role in Supply Chain Management exempts the agent identity user from license enforcement. This means that you don't need to allocate a user license to the agent.

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

### <a name="trigger-flows"></a>Activate the triggering Power Automate flows

<!-- LS: The engineers caught this part too late so we will not be able to have it available by April 24th. Either we leave it knowing it will not be there right away (but soon after), or we leave it blank and saying "coming soon" or "to be updated soon"? I know this is not ideal -->

To finish setting up the agent identity, you must activate the triggering Power Automate flows. Follow these steps to use a Canvas app and finish the setup.

1. Sign in to the [Power Apps Maker portal](https://make.powerapps.com) as an environment administrator user.
1. Select your environment from the **Environment** drop-down list in the page header.
1. In the left pane, select **Solutions**.
1. Open the **Managed** tab.
1. Find and open the solution with a **Display name** of *Copilot in Supply Chain Management solution*.
1. On the **Objects** pane, select **Apps**.
1. Select the app with a **Display name** of *(Production ready preview) Setup Procurement Agent - Impact analysis*.
1. If **Play** is disabled on the command bar, select **Share**, add your name, and select **Share**.
1. Select the *(Production ready preview) Setup Procurement Agent - Impact analysis* app again and then select **Play** on the command bar.
1. Under **Connections**, select the connections you created in the previous section for both *Microsoft Dataverse* and *Microsoft Copilot Studio*.
1. Select **Apply** at the bottom-right of the page and wait for all of the flows listed under **Agent trigger flows status** to switch to a state of *Activated*.

## Assign permissions to users working with the agent

All Dynamics 365 Supply Chain Management users working with the agent must also be created as Dataverse users (if they aren't already). To learn how, go to [Create users](/power-platform/admin/create-users).

Additionally, assign the roles described in the following subsections.

### Permissions for users who manage the agent configuration

- Required Dataverse user roles:

    - *Basic User*
    - *Finance and Operations Agent Configuration Manager*
    - *Finance and Operations Basic User*

- Required Supply Chain Management user roles:

    - *System user*
    - *Purchasing manager* and/or *Purchasing agent*

### Permissions for users who review agent results

- Required Dataverse user roles:

    - *Basic User*
    - *Finance and Operations Basic User*

- Required Supply Chain Management user roles:

    - *System user*
    - *Purchasing agent*

## Refresh data (optional)

After you enable impact analysis in a sandbox environment, we recommend that you do a data refresh. In this way, when you do testing in the sandbox environment, you can use the same data that you have in the production environment. Learn how to do a database refresh in [Refresh database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh).
