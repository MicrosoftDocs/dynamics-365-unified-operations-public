---
title: Set up and configure the Supplier Communications Agent (production ready preview)
description: Learn how to set up and configure the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management to streamline vendor communications.
author: BogdanaBotez
ms.author: andbot
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 16/01/2026
ms.custom:
  - bap-template
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:04/24/2025
---

# Set up and configure the Supplier Communications Agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how system administrators can set up and configure the Supplier Communications Agent, by using the [Agent deployment wizard](../../fin-ops-core/dev-itpro/copilot/agent-deployment) from Copilot Hub.

## Access the agent deployment wizard

To access the agent deployment wizard, follow these steps:

1. Open [Copilot Hub in Power Platform admin center and select Dynamics 365](https://aka.ms/InstallD365Agents).
1. Select the target environment.
1. Choose **Supplier Communications Agent**.
1. Select **Add** to launch the agent deployment wizard.

## Check Prerequisites

Before you can use the Supplier Communications Agent, your system must meet the following requirements:

- Validate that the apps listed in the wizard are installed with a version equal or greater than the ones listed.
- Confirm that [Copilot is enabled](/power-apps/maker/canvas-apps/ai-overview?WT.mc_id=ppac_inproduct_settings#enable-or-disable-copilot-features).
- Confirm message consumption settings and billing for Copilot. You can manage these settings [on the **Licenses** page in Power Platform admin center](https://admin.preview.powerplatform.microsoft.com/billing/licenses/copilotStudio/overview).
- Normally, the Microsoft Copilot Studio agents needed for the Supplier Communications Agent to run are published automatically. But there might be data loss prevention (DLP) policies on your environment that prevent the publishing of these agents. To check if the agents were successfully published, go to [Copilot Studio](https://copilotstudio.microsoft.com/) and find your environment. Make sure that the following Microsoft Copilot Studio agents are published in that environment:
    - *Supplier Communications Agent - inbound*
    - *Supplier Communications Agent - outbound*.

If the two agents aren't published, you can find help in [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting). 

When done, choose Next to advance to the following wizard step.

## Set up agent identity

The Supplier Communications Agent interacts with Dataverse and Microsoft Copilot Studio to do its work. 

> [!TIP]
> For security and ease of maintenance, use a dedicated identity for the agent.

Use the user management features for your tenant to create an *agent identity user*.

### Create your agent's Entra user ID

Activate the selection field to choose an eligible user. If no such user exists, follow the instructions on the screen to create one.

### Assign product licenses

The Supplier Communications Agent uses premium tier connectors, so the agent identity user must have a license that permits those connectors. Learn more in [Power Platform licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq) or download the [Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130).

Examples of sufficient licenses include *Power Apps Premium*, *Power Automate Premium*, or *Dynamics 365 Supply Chain Management*.

Use the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?referrer=entra#/licenses) to assign the required licenses.

### Add agent user to environment, assign required security roles

Add the agent identity user to the Dataverse environment. Assign the agent identity user the following security roles:

- Required Dataverse user roles:

    - *Finance and Operation Basic User*
    - *Supplier Communications Agent*
    - *Environment Maker*

### Add agent user to Finance and Operations, assign required security roles

- Required Supply Chain Management user roles:

    - *(Preview) Supplier Communications Agent*
    - *System user*

<!-- Bogdana - this is how far I've got to writing the new wizard setup doc -->




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

> [!NOTE]
> This section describes one of two ways to activate the triggering Power Automate flows. The other way is to use a PowerShell script, which is described in the [Activate the triggering Power Automate flows by using a PowerShell script](#sample-script) section later in this article. You don't need to do both methods. Choose the method that you prefer.

To finish setting up the agent identity, you must activate the triggering Power Automate flows. Follow these steps to use a Canvas app and finish the setup.

1. Sign in to the [Power Apps Maker portal](https://make.powerapps.com) as an environment administrator user.
1. Select your environment from the **Environment** drop-down list in the page header.
1. In the left pane, select **Solutions**.
1. Open the **Managed** tab.
1. Find and open the solution with a **Display name** of *Copilot in Supply Chain Management solution*.
1. On the **Objects** pane, select **Apps**.
1. Select the app with a **Display name** of *(Production ready preview) Setup Supplier Communications Agent*.
1. If **Play** is disabled on the command bar, select **Share**, add your name, and select **Share**.
1. Select the *(Production ready preview) Setup Supplier Communications Agent* app again and then select **Play** on the command bar.
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

## Synchronize mailboxes with Dataverse

To enable the email analysis and delivery features of the Supplier Communications Agent, you must set up targeted mailboxes so that they're synchronized with Dataverse at the server level.

### Private mailbox

> [!IMPORTANT]
> Only the owner of a private mailbox can create an agent configuration and review agent results related to it. The owner must have permissions to [manage the agent configuration](./supplier-com-agent-setup.md#permissions-for-users-who-manage-the-agent-configuration) and [review agent results](./supplier-com-agent-setup.md#permissions-for-users-who-review-agent-results).

To set up a private mailbox, follow these steps:

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as a user with the system administrator security role. (Although users without an administrator role can enable synchronization for their own mailboxes, administrator approval might be required.)
1. Select the environment that you want to set up.
1. On the command bar, select **Settings**.
1. On the **Settings** page, under **Email**, select **Mailboxes**.
1. On the **Select a view** dropdown menu at the top of the page, select **Active Mailboxes**.
1. Select the check box for each mailbox that you want to use with the Supplier Communications Agent.
1. On the command bar, select **Test & enable mailbox** to enable synchronization for the selected mailboxes.

After you set up a private mailbox, the user who owns it must update the personalization settings to specify that all emails should be tracked.

To enable tracking of all emails for a private mailbox that you own, follow these steps:

1. On the **Active Mailboxes** page, select the **Settings** button (gear symbol) in the upper right, and then select **Personalization Settings**.
1. In the **Set Personal Options** dialog, on the **Email** tab, in the **Track** field, select *All email messages*.
1. Select **OK**.

### Shared mailbox

If you use a shared mailbox, follow these steps:

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as a user who has a system administrator security role.
1. Select the environment that you want to set up.
1. On the command bar, select **Settings**.
1. On the **Settings** page, under **Users + permissions**, select **Teams**.
1. On the command bar, select **Create team**.
1. In the **New team** dialog, specify a name (for example *My Mail Team*), business unit, and administrator as required. Set the **Team type** field to *Owner*.
1. Select **Next**.
1. In the **Add team members** dialog, add all the users who should have access to the shared mailbox.

    > [!IMPORTANT]
    > Add all users who create an agent configuration and review agent results that are related to this mailbox as team members.

1. Select **Next**.
1. In the **Manage security roles** dialog, select *Basic User* and *Finance and Operations Basic User*, and then select **Save**.
1. You return to the list of teams. Find the newly created team, and open it.
1. In the upper-right corner, find the **Default Queue** associated with the team and open it. The queue has the same name as the team, set within angle brackets (for example: *\<My Mail Team\>*).
1. A mailbox should be shown in the **Email settings** section. Select the mailbox name.
1. On the mailbox details page, select **Activate** on the command bar and then select **Activate** in the dialog.
1. In the section **Mailbox Information**, enter the shared **Email address** and save.
1. On the command bar, select **Test & Enable Mailboxes**.

    > [!TIP]
    > If this operation fails, review the **Alerts** section for the mailbox. If it includes an error message that states that approval is required, you must ask your global or Exchange admin to approve the mailbox. Learn more in [Approve email](/power-platform/admin/connect-exchange-online#approve-email).

1. Ensure that no other mailboxes that have the same email address are set up and active.

    1. Return to the **Settings** page for your environment.
    1. Under **Email**, select **Mailboxes**.
    1. On the **Select a view** dropdown menu at the top of the page, select **Active Mailboxes**.
    1. If any other mailboxes have the same email address as the shared mailbox email address, deactivate them.

Get detailed instructions in [Set up server-side synchronization of email](/power-platform/admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks).

### Troubleshooting

#### Issues with setting up Supplier Communications Agent

For help with problems that might occur when setting up the Supplier Communications Agent, go to [FAQ and solving typical issues when setting up and configure the Supplier Communications Agent](supplier-com-agent-setup-faq.md).

#### Issues with server-side synchronization

Learn how to fix common issues that are related to server-side synchronization in [Troubleshooting and monitoring](/power-platform/admin/troubleshooting-monitoring-server-side-synchronization).

## Refresh data (optional)

After you enable the Supplier Communications Agent in a sandbox environment, we recommend that you do a data refresh. In this way, when you do testing in the sandbox environment, you can use the same data that you have in the production environment. Learn how to do a database refresh in [Refresh database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh).

## <a name="own-email"></a>Set your email address as a vendor contact for testing

When you use the [review and apply purchase order changes received in vendor emails](supplier-com-agent-apply-email-changes.md) feature, the agent only reads emails from vendor domains. This limitation means that when you're testing the system and want to send or forward vendor emails from your own email account, you must add your email address as a vendor contact. To add your email address, follow these steps:

1. Go to **Procurement and sourcing** \> **Vendors** \> **All vendors**.
1. Create or select a vendor.
1. On the **Contact information** FastTab, add a row with your own email address (the one you'll send or forward test messages from).

<!-- Bogdana's note: Use this in the last step of the Wizard -->

- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Select **Check for updates** if the features aren't shown on your system.

    - [*(Production ready Preview) Immersive Home*](../../fin-ops-core/fin-ops/copilot/immersive-home.md)
    - [*(Production ready preview) Agent management*](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md)
    - *(Production ready preview) Supplier Communications Agent*
    - Optional: If you want the agent to send emails automatically, turn on the feature *(Preview) Send follow-up emails to vendors with Supplier Communications Agent - automatically sending emails*. We recommend that you turn off this feature for sandbox environments. The reason is that data (such as purchase orders) might not be up to date, or vendor email addresses might be missing.

    > [!TIP]
    > If you can't enable the *Agent management* features, make sure that all of the [prerequisites](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md) are fulfilled, such as version requirements and Copilot Studio billing enablement.

- In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), make sure you're running the following versions of the following Dynamics 365 Apps in your Supply Chain Management environment. It's important that you install or update them in the following order:
    - First, install *Copilot for finance and operations apps* version 1.0.3048.2 or later. If it's already installed, update it to the latest version.
    - Then, install *Copilot in Microsoft Dynamics 365 Supply Chain Management* version 1.1.03071.1 or later. If it's already installed, update it to the latest version.
- Normally, the Microsoft Copilot Studio agents needed for the Supplier Communications Agent to run are published automatically. But there might be data loss prevention (DLP) policies on your environment that prevent the publishing of these agents. To check if the agents were successfully published, go to [Copilot Studio](https://copilotstudio.microsoft.com/) and find your environment. Make sure that the following Microsoft Copilot Studio agents are published in that environment:
    - *Supplier Communications Agent - inbound*
    - *Supplier Communications Agent - outbound*.

    If the two agents aren't published, you can find help in [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting).
