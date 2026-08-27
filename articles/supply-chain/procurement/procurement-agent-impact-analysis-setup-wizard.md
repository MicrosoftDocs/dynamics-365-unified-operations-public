---
title: Set up and configure impact analysis features of the Procurement Agent (production-ready preview)
description: Learn how to use the agent deployment wizard to set up impact analysis features for the Procurement Agent. Follow this guided setup to configure agents quickly.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 08/26/2026
ms.update-cycle: 180-days
ms.collection:
  - bap-ai-copilot
ms.custom:
  - bap-template
---
# Set up and configure impact analysis features of the Procurement Agent (production-ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how system administrators can use the [agent deployment wizard](../../fin-ops-core/dev-itpro/copilot/agent-deployment.md) from Copilot Hub to set up and configure the impact analysis features of the Procurement Agent, regardless of whether you're also using the supplier communications features of the agent.

If you're already using supplier communications, you can choose to keep the same Entra ID and connections you created in the supplier communications set-up, or you can create new ones.

## Prerequisites

To use the impact analysis features of the Procurement Agent, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.48 build 10.39.2117 or later. If you're running 10.0.48, ensure you're running the newest available build.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Select **Check for updates** if the features don't appear on your system.

    - [*Immersive Home*](../../fin-ops-core/fin-ops/copilot/immersive-home.md)
    - [*Agent management*](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md)
    - *(Production-ready preview) Procurement Agent - Impact analysis*

    > [!TIP]
    > - If you don't see all of the features you're looking for in the **Feature management** workspace, select **Check for updates** to refresh the list of features.
    > - If you can't enable the *Agent management* feature, ensure that your environment fulfills all of the [prerequisites](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md), including version requirements and Copilot Studio billing.

- In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), ensure you're running the following versions of the following Dynamics 365 Apps in your Supply Chain Management environment. It's important that you install or update them in the following order:
    - First, install *Copilot for finance and operations apps* version 1.0.03048.2 or later. If it's already installed, update it to the latest version.
    - Then, install *Copilot in Microsoft Dynamics 365 Supply Chain Management* version 1.1.03510.1 or later. If it's already installed, update it to the latest version.

- Normally, the Microsoft Copilot Studio agent needed for impact analysis to run is published automatically. But there might be data loss prevention (DLP) policies on your environment that prevent the publishing of this agent. To check if the agents are successfully published, go to [Copilot Studio](https://copilotstudio.microsoft.com/) and find your environment. Ensure that the following Microsoft Copilot Studio agent is published in that environment: *Procurement Agent - Impact Analysis*. If the agent isn't published, you can find help in [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting).

## Understand the agent identity user

An *agent identity user* is a dedicated Microsoft Entra ID user account that the Procurement Agent uses to sign in to the systems it connects to. This account isn't a person account for day-to-day business use. Instead, it's a service-style identity that gives the agent the permissions it needs to access Dataverse, Microsoft Copilot Studio, and Supply Chain Management while it performs its work.

You create or select this user during setup because the agent must authenticate to several services and components before it can run impact analysis. The identity user is what allows the agent to read incoming vendor change requests, review the related purchase orders and downstream data, and trigger the processes that evaluate the impact of those changes. The agent deployment wizard uses this identity user as the foundation for the connection and authorization steps you complete to enable impact analysis.

## Run the agent deployment wizard

To use the agent deployment wizard to set up the impact analysis features, follow these steps:

1. Open [Copilot Hub in Power Platform admin center](https://aka.ms/InstallD365Agents) and select **Dynamics 365 agents** in the **Manage** section.
1. Select **Select environment** and choose your target environment.
1. In the **All agents** section, find the **Procurement agent - Impact analysis (Preview)** tile and select the **Add** button in that tile to launch the agent deployment wizard.
1. The **Overview** page opens, which provides a summary of the agent deployment wizard and its capabilities. Select **Next** to continue.
1. The **Check prerequisites** page opens. This step makes sure your environment meets all of the prerequisites for the agent.
    - The deployment wizard automatically checks most of these prerequisites for you. It shows a green check mark for each fulfilled prerequisite. If any of the features or settings aren't enabled, enable them before you continue. Each section provides links to the Power Platform admin center to help you enable the relevant features or settings. Learn more in [Enable or disable Copilot features](/power-apps/maker/canvas-apps/ai-overview?WT.mc_id=ppac_inproduct_settings#enable-or-disable-copilot-features).
    - In the **Make sure the following apps are up to date with at least the versions noted** section, review this list of required apps and versions. Make sure that the apps listed are installed in your environment and that their versions are equal to or greater than the ones listed. For more information about the required apps and versions, see the [prerequisites](#prerequisites) section.
    - Each time you make changes to meet the prerequisites, go back to the agent deployment wizard and select the **Reload** button at the right side of each section to let the wizard check the status of that section again. When all prerequisites are met, green check marks are shown for all sections.
    - Your environment might include data loss prevention (DLP) policies that prevent it from creating connections for the Procurement Agent. Ensure that the required connections are allowed in your organization. Learn more in [Advanced connector policies](/power-platform/admin/advanced-connector-policies) and [Data Loss Prevention Policies](/power-platform/admin/wp-data-loss-prevention).

    When all prerequisites are met, select **Next** to continue.

1. The **Set up agent identity** page opens. Use this page to set up the *agent identity user* account that the agent uses to interact with Dataverse and Microsoft Copilot Studio. To set up your agent identity user, follow links and make settings in the following sections on this page:
    - **Create your agent's Entra user ID** – For security and ease of maintenance, use a dedicated identity for the agent. If you don't already have an eligible user available, select the link provided to open the Microsoft 365 admin center and create a new user that will be the agent identity user. Then select that user in the drop-down list provided. Select **Set up**. This action triggers the wizard to check the required roles in the next section, **Set up identity in environment**.
    - **Set up identity in environment** – This section shows the steps required to configure the agent identity user in your Power Platform environment. Green check marks indicate which steps are completed successfully. A link to the Power Platform admin center environment user settings is provided so that you can complete the required actions manually if needed.
    - **Assign required product licenses** – The Procurement Agent uses premium tier connectors, so the agent identity user you selected must have a license that permits those connectors. You must check this license manually in the Power Platform admin center. Learn more in [Power Platform licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq) or download the [Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130). Examples of sufficient licenses are listed in this section. Select the link provided to open the Microsoft 365 admin center, where you can review and assign licenses for the agent identity user. Once you verify that the licenses are in place, check **Complete**.
    - **Set up identity in Finance and Operations** – Add the agent identity user as a user in Supply Chain Management and assign the security roles listed in this section. You must check this setting manually in Supply Chain Management. Make a note of the roles listed and then select the link provided to open the **User settings** page of Supply Chain Management, where you can review and assign security roles for the agent identity user. Ensure that each of the required roles is assigned to the agent identity user, and then go back and continue to complete wizard. Once you verify that the roles are in place, check **Complete**.

    After you confirm all the required settings, select **Next** to continue.

1. The **Connect agent** page opens. The agent identity user you specified on the previous page is used to set up these connections.
    - **Connect the agent** – The agent uses the types of connections listed here. For each type, select an existing connection from the menu if one is available. If no connections are available, select the **+** button to create a new connection. Select **Connect agent** to use the connections you selected, and wait until the agent is connected.
    - **Activate data flows and processes** – Select **Activate flows** and wait for all of the flows listed to switch to the *Activated* state.

    When all connections and data flows are shown as successful, select **Next** to continue.

1. The **Set up user permissions** page opens. Add users who can interact with the agent and specify if they can configure it or only view results.
    - In the **Add a user** search field, search for a user. In the **Select a role** dropdown, assign the *Agent manager* or *Agent user* role. The *Agent manager* role grants the user permission to enable and edit configurations of the agent, while the *Agent user* role only grants the user permission to view impact analysis results. Users assigned the *Agent manager* role can also view results of the agent.
    - If you need to create new users in your environment to manage the agent configuration or review agent results, see [Create users](/power-platform/admin/create-users).

    After you assign permissions to users, select **Next** to continue.

1. The **Enable agent** page opens.
    - **Publish Copilot Studio agents** – The wizard automatically publishes the Microsoft Copilot Studio agents needed for the Procurement Agent to run. If this action succeeds, the **Deploy** button is greyed out and shows the help text *All agents are already published*. If the agent isn't automatically published, it might be because data loss prevention (DLP) policies in your environment prevent this action. Learn more in [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting). Select the **Microsoft Copilot Studio: Agents** link provided here to go to Copilot Studio, where you can check whether these agents are published and publish them if necessary. Learn more in [Key concepts - Publish and deploy your agent](/microsoft-copilot-studio/publication-fundamentals-publish-channels).
    - **Enable Immersive Home and agent features in Finance and Operations** – This section lists the features that you must turn on in Supply Chain Management. Make a note of the features listed here and then select the link provided to open the **Feature management** workspace, where you can enable each of the features.

    > [!TIP]
    >
    > - If you don't see all of the features you're looking for in the **Feature management** workspace, select **Check for updates** to refresh the list of features.
    > - If you can't enable the *Agent management* feature, ensure that your environment fulfills all of the [prerequisites](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md), including version requirements and Copilot Studio billing.

    Select **Next** to continue.

1. The final page of the wizard opens. Select **Finish** to complete the setup.

<a name="trigger-impact-analysis"></a>

## Configure sources that automatically trigger impact analysis

To use impact analysis on incoming change requests received through emails or the vendor collaboration interface, first enable the relevant sources. Learn more in [Supplier communications features of the Procurement Agent](procurement-agent-supplier-com-overview.md) and [Vendor collaboration with external vendors](vendor-collaboration-work-external-vendors.md).

To enable impact analysis to run based on change requests coming through one or both sources, follow these steps:

1. Sign in to the Supply Chain Management environment as a user who has permissions to manage the agent configuration.
1. Go to **Agents** > **Agents**.
1. Open the **Library** tab.
1. Find the *Show impact of changes in purchase orders - Impact analysis - Procurement Agent* tile and select **Select** for that tile.
1. Open the **Source** dropdown list and select one or both of the following options:
    - *Vendor emails* – Select this option if you're using supplier communications features of the Procurement Agent to receive and classify emails from vendors.
    - *Vendor collaboration module* – Select this option if you're using the vendor collaboration interface to receive and manage vendor responses.
1. Select **Activate**.

If you're using impact analysis with supplier communications, impact analysis only runs on configurations set for the *Updates from vendors (reading vendor emails)* feature (see [Configure the agent to track your email](procurement-agent-supplier-com-apply-email-changes.md)). If you set up a configuration for the Procurement Agent to read and review emails from all vendors, impact analysis runs on all change requests received from all vendors. If you set up a configuration for the Procurement Agent to read and review only emails from certain vendors, impact analysis only runs on change requests received from those specific vendors. If your organization sets up multiple configurations, for example to accommodate different purchasers responsible for their own vendors, the impact analysis configuration applies to all of them. Impact analysis runs for all change requests received from all specified vendors in all configurations.
