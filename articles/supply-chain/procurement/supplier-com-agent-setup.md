---
title: Set up and configure the Supplier Communications Agent (production ready preview)
description: Learn how to set up and configure the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management to streamline vendor communications.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 05/28/2025
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

This article explains how system administrators can set up and configure the Supplier Communications Agent.

## Video instructions

For video instructions on how to set up the Supplier Communications Agent, go to [Supplier Communications Agent: Set up and Configure | Dynamics 365 Bites (video)](https://aka.ms/SupplierCommunicationsAgentSetup).

The remaining sections in this article provide the same instructions in a text-based format.

## Prerequisites

Before you can use the Supplier Communications Agent, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later, with all available quality updates.  
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Select **Check for updates** if the features aren't shown on your system.

    - [*(Production ready Preview) Immersive Home*](../../fin-ops-core/fin-ops/copilot/immersive-home.md)
    - [*(Production ready preview) Agent management*](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md)
    - *(Production ready preview) Supplier Communications Agent*

> [!TIP]
> If you can't enable the *Agent management* features, then make sure that all of the [prerequisites](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md) are fulfilled, such as version requirements and Copilot Studio billing enablement.

- In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), make sure you're running the following versions of the following Dynamics 365 Apps in your Supply Chain Management environment. It's important that you install or update them in the following order:
    - First, install (or update to) *Copilot for finance and operations apps* version 1.0.3048.2 or later.
    - Then, install (or update to) *Copilot in Microsoft Dynamics 365 Supply Chain Management* version 1.1.3046.2 or later.

- Optional: If you want the agent to send emails automatically, turn on the *(Preview) Send follow-up emails to vendors with Supplier Communications Agent - automatically sending emails* feature in Feature management. We recommend that you turn off this feature for sandbox environments, where data such as purchase orders might not be up to date, or vendor email addresses might be missing.

## <a name="set-up-agent-identity"></a>Set up an agent identity

The Supplier Communications Agent interacts with Dataverse and Microsoft Copilot Studio to do its work. You must select the identity that is used for these interactions and create the required connections.

> [!TIP]
> For security and ease of maintenance, we recommend that you use a dedicated identity for the agent.

### Set up agent identity users and assign security roles

Use the user management features for your tenant to create an *agent identity user*. Then assign the licenses and security roles described in the following subsections to that user.

#### License requirements

The Suppler Communications Agent utilizes premium tier connectors, so the agent identify user must have a license that permits those. Find more information in the [Power Platform licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq) or download the [Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130).

Examples of sufficient licenses include *Power Apps Premium*, *Power Automate Premium* or *Dynamics 365 Supply Chain Management*.

Use the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?referrer=entra#/licenses) to assign the required licenses.

#### Required security roles

Add the agent identity user both to the Dataverse environment and to Supply Chain Management. Assign the agent identify user the security roles shown in the following lists.

- Required Dataverse user roles:

    - *Finance and Operation Basic User*
    - *Supplier Communications Agent*
    - *Environment Maker*

- Required Supply Chain Management user roles:

    - *(Preview) Supplier Communications Agent*
    - *System user*

### Create the required connections

To create the required connections, follow these steps.

1. Open the [Power Apps Maker portal](https://make.powerapps.com) and sign in as an environment administrator user.
1. Use the **Environment** drop-down list in the page header to select the environment associated with your finance and operations apps.
1. In the left navigator, select **Connections**.
1. At the top of the page, select **New connection**.
1. Use the **Search** field at the right side of the page to find the connection with a **Name** of *Microsoft Dataverse* (if you see two, use the one with the green icon). Select **Create** for that row and follow the instructions on your screen. Sign in with the intended *agent identity user* when prompted.
1. You return to the **Connections** list. Your new connector is now shown at the bottom of the list and is named after the agent identity you signed in with when creating it.
1. At the top of the page, select **New connection**.
1. Find the connection with a **Name** of *Microsoft Copilot Studio (preview)*. Select **Create** for that row and follow the instructions on your screen. Sign in as the intended agent identity when prompted.
1. You return to the **Connections** list. Your new connector is now shown at the bottom of the list and is named after the agent identity you signed in with when creating it.

    :::image type="content" source="media/sca-connections-setup.png" alt-text="Example connections setup" lightbox="media/sca-connections-setup.png":::

### Activate the flows

To finish setting up the agent identity, you must activate the triggering Power Automate flows. A Canvas app is provided to help you do this. To use the app, follow these steps.

1. Sign in to [Power Apps](https://make.powerapps.com) as an environment administrator user.
1. In the left pane, select **Apps**.
1. Select the app with a **Name** of *(Production ready preview) Setup Supplier Communications Agent*.
1. On the command bar, select **Play**.
1. Under **Connections**, select the connections you created in the previous section for both *Microsoft Dataverse* and *Microsoft Copilot Studio*.
1. Select **Apply** at the bottom-right of the page and wait for all of the flows listed under **Agent trigger flows status** to switch to a state of *Activated*.

## Assign permissions to users working with the agent

All Dynamics 365 Supply Chain Management users working with the agent must also be created as Dataverse users (if they aren't already). To learn how, go to [Create users](/power-platform/admin/create-users).

Additionally, they be assigned the roles described in the following subsections.

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
> Only the owner of a private mailbox can create an agent configuration and review agent results that are related to it. The owner must have permissions to [manage the agent configuration](./supplier-com-agent-setup.md#permissions-for-users-who-manage-the-agent-configuration) and [review agent results](./supplier-com-agent-setup.md#permissions-for-users-who-review-agent-results).

To set up a private mailbox, follow these steps.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as a user who has a system administrator security role. (Although users who don't have an administrator role can enable synchronization for their own mailboxes, administrator approval might be required.)
1. Select the environment that you want to set up.
1. On the command bar, select **Settings**.
1. On the **Settings** page, under **Email**, select **Mailboxes**.
1. On the **Select a view** dropdown menu at the top of the page, select **Active Mailboxes**.
1. Select the checkbox for each mailbox that you want to use with the Supplier Communications Agent.
1. On the command bar, select **Test & enable mailbox** to enable synchronization for the selected mailboxes.

After a private mailbox is set up, the user who owns it must update the personalization settings to specify that all emails should be tracked.

To enable tracking of all emails for a private mailbox that you own, follow these steps.

1. Go to the URL of your environment.
1. Select the **Settings** button (gear symbol) in the upper right, and then select **Personalization Settings**.
1. In the **Set Personal Options** dialog, on the **Email** tab, in the **Track** field, select *All email messages*.
1. Select **OK**.

### Shared mailbox

If you're using a shared mailbox, create a queue so that all users who work on the shared mailbox can access email contents.

1. Sign in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as user who has a system administrator security role.
1. Select the environment that you want to set up.
1. On the command bar, select **Settings**.
1. On the **Settings** page, under **Users + permissions**, select **Teams**.
1. Select **Create team**.
1. In the **New team** dialog, specify a name, business unit, and administrator as required. Set the **Team type** field to *Owner*.
1. Select **Next**.
1. In the **Add team members** dialog, add all the users who should have access to the shared mailbox.

    > [!IMPORTANT]
    > All users who create an agent configuration and review agent results that are related to this mailbox must be added as team members.

1. Select **Next**.
1. In the **Manage security roles** dialog, select **Finance and Operations Basic User** and **Basic User**, and then select **Save**.
1. Return to the **Settings** page for your environment, and then, under **Business** section, select **Queues**.
1. Select **New** to create a **Queue** entity record.
1. Enter a name, set the **Incoming email** field to the email address of the shared mailbox, and set the **Owner** field to the team that you created earlier.
1. Select **Save**.
1. A mailbox should now be created in the **Email settings** section. Select the mailbox name.
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

To solve issues that might occur when setting up the Supplier Communications Agent, go to [FAQ and solving typical issues when setting up and configure the Supplier Communications Agent](supplier-com-agent-setup-faq.md)

#### Issues with server-side synchronization

Learn how to fix common issues that are related to server-side synchronization in [Troubleshooting and monitoring](/power-platform/admin/troubleshooting-monitoring-server-side-synchronization).

## Refresh data (optional)

After you enable the Supplier Communications Agent in a sandbox environment, we recommend that you do a data refresh. In this way, when you do testing in the sandbox environment, you can use the same data that you have in the production environment. Learn how to do a database refresh in [Refresh database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh).

## <a name="own-email"></a>Set your email address as a vendor contact for testing

When you use the [review and apply purchase order changes received in vendor emails](supplier-com-agent-apply-email-changes.md) feature, the agent only reads emails from vendor domains. This means that when you're testing the system (and want to send/forward vendor emails from your own email account), you must add your email address as a vendor contact. To do so, follow these steps.

1. Go to **Procurement and sourcing** \> **Vendors** \> **All vendors**.
1. Create or select a vendor.
1. On the **Contact information** FastTab, add a row with your own email address (the one you'll send/forward test messages from).
