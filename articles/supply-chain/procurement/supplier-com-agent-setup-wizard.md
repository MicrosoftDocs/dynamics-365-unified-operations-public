---
title: Set up and configure the Supplier Communications Agent (production ready preview) by using the Microsoft Copilot agent deployment wizard 
description: Learn how to use the Microsoft Copilot agent deployment wizard, to set up and configure the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management to streamline vendor communications.
author: BogdanaBotez
ms.author: andbot
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 01/16/2026
ms.custom:
  - bap-template
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:04/24/2025
---

<!-- Bogdana's note: I haven't linked this anywhere yet - let's review it first, then I will link it to the main setup documentation.-->

# Set up and configure the Supplier Communications Agent (production ready preview) by using the Microsoft Copilot agent deployment wizard

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how system administrators can set up and configure the Supplier Communications Agent, by using the [Agent deployment wizard](../../fin-ops-core/dev-itpro/copilot/agent-deployment.md) from Copilot Hub.

## Setup the agent by using the agent deployment wizard

To access the agent deployment wizard, follow these steps:

1. Open [Copilot Hub in Power Platform admin center and select Dynamics 365](https://aka.ms/InstallD365Agents).
1. Select the target environment.
1. Choose **Supplier Communications Agent**.
1. Select **Add** to launch the agent deployment wizard.

### Check Prerequisites

Before you can use the Supplier Communications Agent, your system must meet the following requirements:

- Validate that the apps listed in the wizard are installed with a version equal or greater than the ones listed.
- Confirm that [Copilot is enabled](/power-apps/maker/canvas-apps/ai-overview?WT.mc_id=ppac_inproduct_settings#enable-or-disable-copilot-features).
- Confirm message consumption settings and billing for Copilot. You can manage these settings [on the **Licenses** page in Power Platform admin center](https://admin.preview.powerplatform.microsoft.com/billing/licenses/copilotStudio/overview).
- Normally, the Microsoft Copilot Studio agents needed for the Supplier Communications Agent to run are published automatically. But there might be data loss prevention (DLP) policies on your environment that prevent the publishing of these agents. To check if the agents were successfully published, go to [Copilot Studio](https://copilotstudio.microsoft.com/) and find your environment. Make sure that the following Microsoft Copilot Studio agents are published in that environment:
    - *Supplier Communications Agent - inbound*
    - *Supplier Communications Agent - outbound*.

If the two agents aren't published, you can find help in [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting). 

When done, choose Next to advance to the following wizard step.

### Set up agent identity

The Supplier Communications Agent interacts with Dataverse and Microsoft Copilot Studio to do its work. 

> [!TIP]
> For security and ease of maintenance, use a dedicated identity for the agent.

Use the user management features for your tenant to create an *agent identity user*.

#### Create your agent's Entra user ID

Activate the selection field to choose an eligible user. If no such user exists, follow the instructions on the screen to create one.

#### Assign product licenses

The Supplier Communications Agent uses premium tier connectors, so the agent identity user must have a license that permits those connectors. Learn more in [Power Platform licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq) or download the [Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130).

Examples of sufficient licenses include *Power Apps Premium*, *Power Automate Premium*, or *Dynamics 365 Supply Chain Management*.

Use the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?referrer=entra#/licenses) to assign the required licenses.

#### Add agent user to environment, assign required security roles

Add the agent identity user to the Dataverse environment. Assign the agent identity user the following security roles:

- Required Dataverse user roles:

    - *Finance and Operation Basic User*
    - *Supplier Communications Agent*
    - *Environment Maker*

#### Add agent user to Finance and Operations, assign required security roles

- Required Supply Chain Management user roles:

    - *(Preview) Supplier Communications Agent*
    - *System user*

### Connect the agent

#### Create the required connections

There are two connection types that the agent will use: *Microsoft Dataverse* and *Microsoft Copilot Studio*. For each type, if a connection already exists, select an existing one from the menu. If no connections are available, use the *+* button to create a new connection.

Select the button **Connect the agent** to use the connections you have just selected, and wait until the agent is connected.

#### Activate data flows and processes

Select the button **Activate data flows**, and wait for all of the flows listed to switch to a state of *Activated*.

### Configure mailbox

To enable the email analysis and delivery features of the Supplier Communications Agent, you must configure one or more mailboxes and synchronize them with Dataverse using server-side synchronization.
Your organization can choose to use shared mailboxes, private mailboxes, or both. At a minimum, at least one mailbox must be configured for the agent to work.

#### Configure Shared mailbox

If you use a shared mailbox, follow these steps:

1. Select **Set up shared mailbox**.
1. Enter the shared mailbox email address. Make sure the shared mailbox already exists in Exchange Server. See [Create a shared mailbox](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-a-shared-mailbox).
1. Select Search, then select Set up.
1. Follow the on-screen instructions to approve and enable the configuration for the shared mailbox.
This process associates the shared mailbox with a team in the Power Platform environment.

    > [!IMPORTANT]
    > Add all users who create agent configurations or review agent results related to this mailbox as members of the associated team.

### Configure private mailbox

To set up a private mailbox, follow these steps:

1. Select **Set up private mailbox**.
2. Search for a user. If the user does not appear, see [Add users to environment](https://learn.microsoft.com/en-us/power-platform/admin/add-users-to-environment)
3. Select the mailbox associated with the selected user.
4. Select **Set up**.
5. Follow the on-screen instructions to approve and enable the configuration. This process enables synchronization between the email server and Dataverse for the selected mailbox.

> [!IMPORTANT]
> Only the owner of a private mailbox can create agent configurations and review agent results related to that mailbox. The owner must have permissions to [manage the agent configuration](./supplier-com-agent-setup.md#permissions-for-users-who-manage-the-agent-configuration) and [review agent results](./supplier-com-agent-setup.md#permissions-for-users-who-review-agent-results).

Get detailed instructions in [Set up server-side synchronization of email](/power-platform/admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks).

### Enable agent

#### Publish Copilot Studio agents

Normally, the Microsoft Copilot Studio agents needed for the Supplier Communications Agent to run are published automatically. But there might be data loss prevention (DLP) policies on your environment that prevent the publishing of these agents. To check if the agents were successfully published, go to [Copilot Studio](https://copilotstudio.microsoft.com/) and find your environment. Make sure that the following Microsoft Copilot Studio agents are published in that environment:
    - *Supplier Communications Agent - inbound*
    - *Supplier Communications Agent - outbound*.

If the two agents aren't published, you can find help in [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting).

#### Enable agent related features

- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Select **Check for updates** if the features aren't shown on your system.

    - [*(Production ready Preview) Immersive Home*](../../fin-ops-core/fin-ops/copilot/immersive-home.md)
    - [*(Production ready preview) Agent management*](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md)
    - *(Production ready preview) Supplier Communications Agent*
    - Optional: If you want the agent to send emails automatically, turn on the feature *(Preview) Send follow-up emails to vendors with Supplier Communications Agent - automatically sending emails*. We recommend that you turn off this feature for sandbox environments. The reason is that data (such as purchase orders) might not be up to date, or vendor email addresses might be missing.

    > [!TIP]
    > If you can't enable the *Agent management* features, make sure that all of the [prerequisites](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md) are fulfilled, such as version requirements and Copilot Studio billing enablement.

<!-- Bogdana: The following is a step not included in the wizard - TODO: contact Christian/Karl to figure it out -->

### Assign user permissions

All Dynamics 365 Supply Chain Management users working with the agent must also be created as Dataverse users (if they aren't already). To learn how, go to [Create users](/power-platform/admin/create-users).

Additionally, assign the roles described in the following subsections.

#### Permissions for users who manage the agent configuration

- Required Dataverse user roles:

    - *Basic User*
    - *Finance and Operations Agent Configuration Manager*
    - *Finance and Operations Basic User*

- Required Supply Chain Management user roles:

    - *System user*
    - *Purchasing manager* and/or *Purchasing agent*

#### Permissions for users who review agent results

- Required Dataverse user roles:
    - *Basic User*
    - *Finance and Operations Basic User*

- Required Supply Chain Management user roles:
    - *System user*
    - *Purchasing agent*

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
