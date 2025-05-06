---
title: Set up and configure the Supplier Communications Agent (production ready preview)
description: Learn how to set up and configure the Supplier Communications Agent in Dynamics 365 Supply Chain Management to streamline vendor communication.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 04/24/2025
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

## Prerequisites

To use the Supplier Communications Agent, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Select **Check for updates** if the features aren't shown on your system.
    - *(Preview) Immersive Home*
    - *(Production ready preview) Agent management*
    - *(Production ready preview) Supplier Communications Agent*

- Optionally, you can also use feature management to turn on the following feature if you'd like to automatically send emails. We recommend that turn it off for sandbox environments where data such as purchase orders might not be up to date or vendor emails could be missing.
    - *(Preview) Send follow-up emails to vendors with Supplier Communications Agent - automatically sending emails*

To learn more about the *Immersive Home* feature, go to [Immersive Home overview](../../fin-ops-core/fin-ops/copilot/immersive-home.md).

## Synchronize mailboxes with Dataverse

To enable email analysis and delivery features of the Supplier Communications Agent, you must set up targeted mailboxes to be synchronized with Microsoft Dataverse at the server level.

### Private mailbox

To set up a private mailbox, follow these steps:

1. Sign in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as a user with a system administrator security role. (Users without an administrator role can enable synchronization on their own mailboxes, but this might still require administrator approval.)
1. Select the environment you want to set up.
1. On the command bar, select **Settings.**
1. On the **Settings** page, expand the **Email** heading and select **Mailboxes**.
1. Open the **Select a view** drop-down list in the heading of the page and select *Active Mailboxes*.
1. Select the check box for each of the mailboxes that you want to use with the supplier communication agent.
1. On the command bar, select **Test & enable mailbox** to enable synchronization for the selected mailboxes.

After the private mailbox is set up, the user who owns the mailbox must update personalization settings to track all the emails. The owner of the mailbox must follow these steps:

1. Go to your environment URL.
1. Select the gear button on the top right and select **Personalization settings**.
1. Open the **Email** tab and set **Track** to *All email messages*.
1. Select **OK**.

### Shared mailbox

If you're using a shared mailbox, then create a queue to allow all users working on the shared mailbox to access email contents.

1. Sign in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as user with a system administrator security role.
1. Select the environment you want to set up.
1. On the command bar, select **Settings**.
1. On the **Settings** page, expand the **Users + permissions** heading and select **Teams**.
1. Select **Create team** at the top.
1. Fill out a name, business unit, and administrator as needed and set the **Team type** to *Owner*. Then select **Next**.
1. On the next page, add all the members that should have access to the shared mailbox. This allows the selected users to access email contents from the Supplier Communications Agent incoming email workspace in Supply Chain Management.
1. On the **Manage security roles** page, select *Finance and Operations Basic User* and then select **Save**.
1. Go back to the **Settings** page, expand the **Business** heading, and select **Queues**.
1. Select the **New** button on top to create a new **Queue** entity record.
1. Enter a **Name**, set **Incoming email** to the email address of the shared mailbox, and assign the **Owner** as the team that was created earlier. Then select **Save**.  
1. A new mailbox should now be created under **Email settings**. Select the mailbox name.
1. On the top command bar, select **Test & enable mailboxes**.  

    > [!TIP]
    > If this operation fails, check the **Alerts** section for the mailbox. If you see an error message that says approval is needed to send outgoing mail, you must ask your global or Exchange admin to approve the mailbox. Learn more in [Approve email](/power-platform/admin/connect-exchange-online#approve-email).  

1. Make sure that no other mailboxes with the same email address are set up and active. To check this, go back to the **Settings** page for your environment in Power Platform Admin Center. Expand the **Email** heading and select **Mailboxes**. Then, select *All Mailboxes* from the drop-down list at the top. Make sure that there's only one mailbox with the same shared mailbox email address. If more than one exists, deactivate all the others.

For detailed instructions, go to [Set up server-side synchronization of email](/power-platform/admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks).

## Troubleshoot server-side synchronization

To learn how to solve common issues related to server-side synchronization, go to [Troubleshooting and monitoring](/power-platform/admin/troubleshooting-monitoring-server-side-synchronization).

## Refresh data

After you enable the supplier communication agent on a sandbox environment, we recommend that you do a data refresh, which will let you test in the sandbox environment with the same data that you would have on your production environment. To learn how to do a database refresh, go to [Refresh database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh)

## Users for both Dataverse and Supply Chain Management

Existing Dynamics 365 Supply Chain Management users that should be able to read the agent emails and summaries must also be created as Dataverse users (if the aren't already). To learn how, go to [Create users](/power-platform/admin/create-users).
