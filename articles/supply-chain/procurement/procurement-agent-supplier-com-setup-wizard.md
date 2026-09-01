---
title: Set up and configure supplier communications features of the Procurement Agent (production-ready preview)
description: Learn how to use the agent deployment wizard to set up and configure the supplier communications features of the Procurement Agent in Microsoft Dynamics 365 Supply Chain Management.
author: t-benebo
ms.author: benebotg
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

# Set up and configure supplier communications features of the Procurement Agent (production-ready preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how system administrators can use the [agent deployment wizard](../../fin-ops-core/dev-itpro/copilot/agent-deployment.md) from Copilot Hub to set up and configure the supplier communications features of the Procurement Agent.

## Prerequisites

Before you can use the supplier communications features of the Procurement Agent, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later, with all available quality updates.  
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Select **Check for updates** if the features don't appear on your system.

    - [*(Production ready Preview) Immersive Home*](../../fin-ops-core/fin-ops/copilot/immersive-home.md)
    - [*(Production ready preview) Agent management*](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md)
    - *(Production ready preview) Procurement Agent - Supplier Communications*
    - Optional: To have the agent send emails automatically, turn on the feature *(Production ready preview) Procurement Agent - Supplier Communications - automatically sending follow-up emails*. We recommend that you turn off this feature for sandbox environments because data (such as purchase orders) might not be up to date, or vendor email addresses might be missing.

    > [!TIP]
    > - If you don't see all of the features you're looking for in the **Feature management** workspace, select **Check for updates** to refresh the list of features.
    > - If you can't enable the *Agent management* feature, ensure that your environment fulfills all of the [prerequisites](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md), including version requirements and Copilot Studio billing.

- In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), ensure you're running the following versions of the following Dynamics 365 Apps in your Supply Chain Management environment. Install or update them in the following order:
    - First, install *Copilot for finance and operations apps* version 1.0.03048.2 or later. If it's already installed, update it to the latest version.
    - Then, install *Copilot in Microsoft Dynamics 365 Supply Chain Management* version 1.1.03510.1 or later. If it's already installed, update it to the latest version.

- Normally, the Microsoft Copilot Studio agents needed by supplier communications features are published automatically. However, data loss prevention (DLP) policies on your environment might prevent publishing these agents. To check if the agents are successfully published, go to [Copilot Studio](https://copilotstudio.microsoft.com/) and find your environment. Ensure that the following Microsoft Copilot Studio agents are published in that environment:
    - *Supplier communications Agent - inbound*
    - *Supplier Communications Agent - outbound*.

    If the two agents aren't published, see [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting).

## Video instructions

For video instructions on how to set up supplier communications, watch [Supplier Communications: Setup and configure via agent deployment wizard](https://www.youtube.com/watch?v=nb2UJxMza5A&t=3s).

The remaining sections in this article provide the same instructions in a text-based format.

## Understand the agent identity user

An *agent identity user* is a dedicated Microsoft Entra ID user account that the Procurement Agent uses to sign in to the systems it connects to. This account is distinct from a person who uses the mailbox day to day. Instead, it's a service-style identity that gives the agent the permissions it needs to access Dataverse, Microsoft Copilot Studio, Exchange, and Supply Chain Management while it reads and responds to supplier emails.

You create or select this user during setup because the agent must authenticate to multiple services before it can monitor mailboxes, classify incoming emails, and send follow-up messages. In the context of supplier communications, the identity user is the account that the wizard uses to connect the agent to the relevant mailboxes and background services. That connection lets the agent process incoming vendor emails and manage related actions in Supply Chain Management without requiring a human to sign in for each step.

## Run the agent deployment wizard

To set up the supplier communications features, follow these steps:

1. Open [Copilot Hub in Power Platform admin center](https://aka.ms/InstallD365Agents) and select **Dynamics 365**.
1. Select **Select environment** and choose your target environment.
1. In the **All agents** section, find the **Supplier Communications Agent** tile and select the **Add** button in that tile to launch the agent deployment wizard.
1. The **Overview** page opens, which provides a summary of the agent deployment wizard and its capabilities. Select **Next** to continue.
1. The **Check prerequisites** page opens. Make sure your environment meets all of the prerequisites for the agent. The prerequisites are organized into sections on this page, and you must meet all of the prerequisites in each section to continue. Here's how to review the prerequisites:
    - In the **Make sure the following apps are up to date with at least the versions noted** section, review this list of required apps and versions. Make sure that the apps listed are installed in your environment and that their versions are equal to or greater than the ones listed. For more information about the required apps and versions, see the [prerequisites](#prerequisites) section.
    - If any of the apps aren't installed or updated to the required version, install or update them before you continue. A link to the Power Platform admin center is provided to help you check the app versions and do the installations or updates if needed. Mark the **Complete** check after you've confirmed that all of the apps meet the requirements.
    - The remaining sections on this page automatically check whether all other required features and settings are enabled in your environment. If they are, green check marks are shown. If any of the features or settings aren't enabled, enable them before you continue. Links to the Power Platform admin center are provided in each section to help you enable the relevant features or settings if needed. Learn more in [Enable or disable Copilot features](/power-apps/maker/canvas-apps/ai-overview?WT.mc_id=ppac_inproduct_settings#enable-or-disable-copilot-features).
    - Each time you make changes to meet the prerequisites, go back to the agent deployment wizard and select the reload button at the right side of each section to let the wizard check the status of that section again. When all prerequisites are met, green check marks are shown for all sections.
    - Your environment might include data loss prevention (DLP) policies that prevent creating connections for the Procurement Agent. Ensure that your organization allows the required connections. For more information, see [Advanced connector policies](/power-platform/admin/advanced-connector-policies) and [Data Loss Prevention Policies](/power-platform/admin/wp-data-loss-prevention).

    When all prerequisites are met, select **Next** to continue.

1. The **Set up agent identity** page opens. Use this page to set up the *agent identity user* account that the agent uses to interact with Dataverse and Microsoft Copilot Studio. To set up your agent identity user, follow links and make settings in the following sections on this page:
    - **Create your agent's Entra user ID** – For security and ease of maintenance, use a dedicated identity for the agent. If you don't already have an eligible user available, select the link provided to open the Microsoft 365 admin center and create a new user that will be the agent identity user. Then select that user in the drop-down list provided.
    - **Set up identity in environment** - This section shows the required steps to configure the agent identity user in your Power Platform environment. Green check marks indicate which steps have been completed successfully. A link to the Power Platform admin center environment user settings is provided so that you can complete the required actions manually if needed.
    - **Assign required product licenses** – The Procurement Agent uses premium tier connectors, so the agent identity user you selected must have a license that permits those connectors. Learn more in [Power Platform licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq) or download the [Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130). Examples of sufficient licenses are listed in this section. Select the link provided to open the Microsoft 365 admin center, where you can review and assign licenses for the agent identity user.
    - **Set up identity in Finance and Operations** – The agent identity user must be added as a user in Supply Chain Management and assigned the security roles listed in this section. Make a note of the roles listed and then select the link provided to open the **Users** page of Supply Chain Management, where you can review and assign security roles for the agent identity user. Ensure that each of the required roles is assigned to the agent identity user, and then go back and continue to complete wizard.

    After you confirm all the required settings, select **Next** to continue.

1. The **Connect agent** page opens. To set up each of the required connections, make settings in the following sections on this page. The agent identity user you specified on the previous page is used to set up these connections.
    - **Connect the agent** – The agent uses the types of connections listed here. For each type, select an existing connection from the menu if one is available. If no connections are available, select the **+** button to create a new connection. Select **Connect the agent** to use the connections you selected, and wait until the agent is connected.
    - **Activate data flows and processes** – Select **Activate data flows** and wait for all of the flows listed to switch to the *Activated* state.

    When all connections and data flows are shown as successful, select **Next** to continue.

1. The **Configure mailboxes** page opens – To enable the email analysis and delivery features of the Procurement Agent, you must configure one or more mailboxes and synchronize them with Dataverse using server-side synchronization. You can choose to use shared mailboxes, private mailboxes, or both. At a minimum, you must configure at least one mailbox.

    - To use a shared mailbox, follow these steps:

        1. Select **Set up shared mailbox**.
        1. Enter the shared mailbox email address. Ensure the shared mailbox already exists in Exchange Server. Learn more in [Create a shared mailbox](/microsoft-365/admin/email/create-a-shared-mailbox).
        1. Select **Search** and then select **Set up**.
        1. Follow the on-screen instructions to approve and enable the configuration for the shared mailbox.

        This process associates the shared mailbox with a team in the Power Platform environment.

        > [!IMPORTANT]
        > Add all users who create agent configurations or review agent results related to this mailbox as members of the associated team.

    - To set up a private mailbox, follow these steps:

        1. Select **Set up private mailbox**.
        1. Search for a user. If the user doesn't appear, see [Add users to environment](/power-platform/admin/add-users-to-environment).
        1. Select the mailbox associated with the selected user.
        1. Select **Set up**.
        1. Follow the on-screen instructions to approve and enable the configuration. This process enables synchronization between the email server and Dataverse for the selected mailbox.

        > [!IMPORTANT]
        > Only the owner of a private mailbox can create agent configurations and review agent results related to that mailbox. The owner must have [permissions](#user-permissions) to manage the agent configuration and review agent results.

        Learn more in [Set up server-side synchronization of email](/power-platform/admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks).

1. The **Enable agent** page opens. To enable the agent, follow links and make settings in the following sections on this page:
    - **Publish Copilot Studio agents** – Normally, the Microsoft Copilot Studio agents needed for the Procurement Agent to run are published automatically. But there might be data loss prevention (DLP) policies in your environment that prevent the publishing of these agents (learn more in [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting)). This section lists the agents that must be published. Select the link provided here to go to Copilot Studio, where you can check whether these agents are published and publish them if necessary. Learn more in [Key concepts - Publish and deploy your agent](/microsoft-copilot-studio/publication-fundamentals-publish-channels).
    - **Enable agent related features** – This section lists the features that must be turned on in Supply Chain Management. Make a note of the features listed here and then select the link provided to open the Feature [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace, where you can enable each of the features.

    > [!TIP]
    >
    > - The *(Production ready preview) Procurement Agent - Supplier communications - automatically sending follow-up emails* feature is optional. It allows the agent to send emails automatically. Turn off this feature for sandbox environments because data there (such as purchase orders) might not be be current, or vendor email addresses might be missing.
    > - If you don't see all of the features listed on this page, select **Check for updates** to refresh the list of features.
    > - If you can't enable the *Agent management* feature, ensure that your environment fulfills all of the [prerequisites](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md), including version requirements and Copilot Studio billing.

    After you complete all of the settings on this page, select **Next** to continue.

1. The final page of the wizard opens. Select **Finish** to complete the setup.

<a name="user-permissions"></a>

## Assign user permissions

After you run the setup wizard, set up user permissions for the users who manage the agent configuration and review agent results. The permissions differ for users who manage the agent configuration and users who review agent results. The following sections describe these differences.

If you need to create new users in your environment to manage the agent configuration or review agent results, learn how to [Create users](/power-platform/admin/create-users).

### Required permissions for users who manage the agent configuration

The following permissions are required for users who create and manage the agent configuration:

- Required Dataverse user roles:
    - *Basic User*
    - *Finance and Operations Agent Configuration Manager*
    - *Finance and Operations Basic User*

- Required Supply Chain Management user roles:
    - *System user*
    - *Purchasing manager* and/or *Purchasing agent*

### Required permissions for users who review agent results

Users who review the agent results need the following permissions:

- Required Dataverse user roles:
    - *Basic User*
    - *Finance and Operations Basic User*

- Required Supply Chain Management user roles:
    - *System user*
    - *Purchasing agent*

## Troubleshooting

### Issues with setting up supplier communications features of the Procurement Agent

For help with problems that might occur when setting up supplier communications features of the Procurement Agent, go to [Solve common problems when setting up supplier communications features](procurement-agent-supplier-com-setup-faq.md).

### Issues with server-side synchronization

Learn how to fix common issues that are related to server-side synchronization in [Troubleshooting and monitoring](/power-platform/admin/troubleshooting-monitoring-server-side-synchronization).
