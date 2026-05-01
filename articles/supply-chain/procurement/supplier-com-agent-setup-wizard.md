---
title: Use the agent deployment wizard to set up the Supplier Communications Agent (preview)
description: Learn how to use the agent deployment wizard to set up and configure the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 03/13/2026
ms.custom:
  - bap-template
---

# Use the agent deployment wizard to set up the Supplier Communications Agent (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how system administrators can use the [agent deployment wizard](../../fin-ops-core/dev-itpro/copilot/agent-deployment.md) from Copilot Hub to set up and configure the Supplier Communications Agent.

> [!IMPORTANT]
> The agent deployment wizard (preview) is an alternative to the manual setup process described in [Set up and configure the Supplier Communications Agent](supplier-com-agent-setup.md). It provides a guided experience for setting up an agent and automatically configures many of the required settings for you. You don't need to run the wizard if you already set up the Supplier Communications Agent manually.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Run the agent deployment wizard

To use the agent deployment wizard to set up the Supplier Communications Agent, follow these steps:

1. Open [Copilot Hub in Power Platform admin center](https://aka.ms/InstallD365Agents) and select **Dynamics 365**.
1. Select **Select environment** and choose your target environment.
1. In the **All agents** section, find the **Supplier Communications Agent** tile and select the **Add** button in that tile to launch the agent deployment wizard.
1. The **Overview** page opens, which provides a summary of the agent deployment wizard and its capabilities. Select **Next** to continue.
1. The **Check prerequisites** page opens. Make sure your environment meets all of the prerequisites for the agent. The prerequisites are organized into sections on this page, and you must meet all of the prerequisites in each section to continue. Here's how to review the prerequisites:
    - In the **Make sure the following apps are up to date with at least the versions noted** section, review this list of required apps and versions. Make sure that the apps listed are installed in your environment and that their versions are equal to or greater than the ones listed. If any of the apps aren't installed or updated to the required version, install or update them before you continue. A link to the Power Platform admin center is provided to help you check the app versions and do the installations or updates if needed. Mark the **Complete** check after you've confirmed that all of the apps meet the requirements.
    - The remaining sections on this page automatically check whether all other required features and settings are enabled in your environment. If they are, green check marks are shown. If any of the features or settings aren't enabled, enable them before you continue. Links to the Power Platform admin center are provided in each section to help you enable the relevant features or settings if needed. Learn more in [Enable or disable Copilot features](/power-apps/maker/canvas-apps/ai-overview?WT.mc_id=ppac_inproduct_settings#enable-or-disable-copilot-features).
    - Each time you make changes to meet the prerequisites, go back to the agent deployment wizard and select the reload button at the right side of each section to let the wizard check the status of that section again. When all prerequisites are met, green check marks are shown for all sections.
    - Your environment might include data loss prevention (DLP) policies that prevent creating connections for the Supplier Communications Agent. Make sure that the required connections are allowed in your organization. For more information, see [Advanced connector policies](/power-platform/admin/advanced-connector-policies) and [Data Loss Prevention Policies](/power-platform/admin/wp-data-loss-prevention).

    When all prerequisites are met, select **Next** to continue.

1. The **Set up agent identity** page opens. Use this page to set up the *agent identity user* account that the agent uses to interact with Dataverse and Microsoft Copilot Studio. To set up your agent identity user, follow links and make settings in the following sections on this page:
    - **Create your agent's Entra user ID** – For security and ease of maintenance, use a dedicated identity for the agent. If you don't already have an eligible user available, select the link provided to open the Microsoft 365 admin center and create a new user that will be the agent identity user. Then select that user in the drop-down list provided.
    - **Set up identity in environment** - This section shows the required steps to configure the agent identity user in your Power Platform environment. Green check marks indicate which steps have been completed successfully. A link to the Power Platform admin center environment user settings is provided so that you can complete the required actions manually if needed.
    - **Assign required product licenses** – The Supplier Communications Agent uses premium tier connectors, so the agent identity user you selected must have a license that permits those connectors. Learn more in [Power Platform licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq) or download the [Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130). Examples of sufficient licenses are listed in this section. Select the link provided to open the Microsoft 365 admin center, where you can review and assign licenses for the agent identity user.
    - **Set up identity in Finance and Operations** – The agent identity user must be added as a user in Supply Chain Management and assigned the security roles listed in this section. Make a note of the roles listed and then select the link provided to open the **Users** page of Supply Chain Management, where you can review and assign security roles for the agent identity user. Make sure that each of the required roles is assigned to the agent identity user, and then go back and continue to complete wizard.

    When you've confirmed all the required settings, select **Next** to continue.

1. The **Connect agent** page opens. To set up each of the required connections, make settings in the following sections on this page. The agent identity user you specified on the previous page is used to set up these connections.
    - **Connect the agent** – The agent uses the types of connections listed here. For each type, select an existing connection from the menu if one is available. If no connections are available, select the **+** button to create a new connection. Select **Connect the agent** to use the connections you selected, and wait until the agent is connected.
    - **Activate data flows and processes** – Select **Activate data flows** and wait for all of the flows listed to switch to the *Activated* state.

    When all connections and data flows are shown as successful, select **Next** to continue.

1. The **Configure mailboxes** page opens – To enable the email analysis and delivery features of the Supplier Communications Agent, you must configure one or more mailboxes and synchronize them with Dataverse using server-side synchronization. You can choose to use shared mailboxes, private mailboxes, or both. At a minimum, you must configure at least one mailbox.

    - To use a shared mailbox, follow these steps:

        1. Select **Set up shared mailbox**.
        1. Enter the shared mailbox email address. Make sure the shared mailbox already exists in Exchange Server. Learn more in [Create a shared mailbox](/microsoft-365/admin/email/create-a-shared-mailbox).
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
        > Only the owner of a private mailbox can create agent configurations and review agent results related to that mailbox. The owner must have permissions to [manage the agent configuration](supplier-com-agent-setup.md#permissions-for-users-who-manage-the-agent-configuration) and [review agent results](supplier-com-agent-setup.md#permissions-for-users-who-review-agent-results).

        Learn more in [Set up server-side synchronization of email](/power-platform/admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks).

1. The **Enable agent** page opens. To enable the agent, follow links and make settings in the following sections on this page:
    - **Publish Copilot Studio agents** – Normally, the Microsoft Copilot Studio agents needed for the Supplier Communications Agent to run are published automatically. But there might be data loss prevention (DLP) policies in your environment that prevent the publishing of these agents (learn more in [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting)). This section lists the agents that must be published. Select the link provided here to go to Copilot Studio, where you can check whether these agents are published and publish them if necessary. Learn more in [Key concepts - Publish and deploy your agent](/microsoft-copilot-studio/publication-fundamentals-publish-channels).
    - **Enable agent related features** – This section lists the features that must be turned on in the in Supply Chain Management. Make a note of the features listed here and then select the link provided to open the Feature [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace, where you can enable each of the features.

    > [!TIP]
    >
    > - The *(Preview) Send follow-up emails to vendors with Supplier Communications Agent - automatically sending emails* feature is optional. It allows the agent to send emails automatically. We recommend that you turn off this feature for sandbox environments because data there (such as purchase orders) might not be up to date, or vendor email addresses might be missing.
    > - If you don't see all of the features listed on this page, select **Check for updates** to refresh the list of features.
    > - If you can't enable the *Agent management* feature, make sure that all of the [prerequisites](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md) are fulfilled, including version requirements and Copilot Studio billing.

    When you've completed all of the settings on this page, select **Next** to continue.

1. The final page of the wizard opens. Select **Finish** to complete the setup.

## Assign user permissions

After you run the setup wizard, you must set up user permissions for the users who will manage the agent configuration and review agent results. The permissions are different for users who manage the agent configuration and users who review agent results, as described in the following sections.

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

The following permissions are required for users who review the agent results:

- Required Dataverse user roles:
    - *Basic User*
    - *Finance and Operations Basic User*

- Required Supply Chain Management user roles:
    - *System user*
    - *Purchasing agent*

## Refresh data on sandbox environments (optional)

After you enable the Supplier Communications Agent in a sandbox environment, refresh the data. By refreshing the data, you can use the same data in the sandbox environment as you have in the production environment for testing. Learn how to do a database refresh in [Refresh database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh).

## <a name="own-email"></a>Set your email address as a vendor contact for testing

When you use the [review and apply purchase order changes received in vendor emails](supplier-com-agent-apply-email-changes.md) feature, the agent only reads emails from vendor domains. This limitation means that when you're testing the system and want to send or forward vendor emails from your own email account, you must add your email address as a vendor contact. To add your email address, follow these steps:

1. Go to **Procurement and sourcing** \> **Vendors** \> **All vendors**.
1. Create or select a vendor.
1. On the **Contact information** FastTab, add a row with your own email address (the one you'll send or forward test messages from).

## Troubleshooting

### Issues with setting up Supplier Communications Agent

For help with problems that might occur when setting up the Supplier Communications Agent, go to [FAQ and solving typical issues when setting up and configure the Supplier Communications Agent](supplier-com-agent-setup-faq.md).

### Issues with server-side synchronization

Learn how to fix common issues that are related to server-side synchronization in [Troubleshooting and monitoring](/power-platform/admin/troubleshooting-monitoring-server-side-synchronization).
