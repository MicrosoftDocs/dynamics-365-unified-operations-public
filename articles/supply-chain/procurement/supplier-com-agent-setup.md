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

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how system administrators can set up and configure the Supplier Communications Agent.

## Prerequisites

To use the Supplier Communications Agent, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.044 or later.

- The following features must be turned on in [feature management](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview). Please select **Check for updates** if the features do not appear.
    - *(Preview) Immersive Home*
    - *(Production ready preview) Agent management*
    - *(Production ready preview) Supplier Communications Agent*

- Optionally, you can also turn the following feature on, if you would like to automatically send emails. We recommend to not turn it on for sandbox environments where data such as the purchase orders may not be up to date or vendor emails may be missing.
    - *(Preview) Send follow-up emails to vendors with Supplier Communications Agent - automatically sending emails*

## Synchronize mailboxes with Dataverse

To enable email analysis and delivery features of the Supplier Communications Agent, you must set up targeted mailboxes to be synchronized with Microsoft Dataverse at the server level.

### Private mailbox

Follow the following steps to set up a private mailbox.

1. Sign in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as user with a system administrator security role. (Users without an administrator role can enable synchronization on their own mailboxes, but this might still require administrator approval.)
2. Select the environment you want to set up.
3. On the command bar, select **Settings.**
4. On the **Settings** page, expand the **Email** heading and select **Mailboxes**.
5. Open the **Select a view** drop-down list in the heading of the page and select **Active Mailboxes**.
6. Select the check box for each of the mailboxes that you want to use with the supplier communication agent .
7. On the command bar, select **Test & Enable Mailbox** to enable synchronization for the selected mailboxes.

After the above has been set up, the user who owns the mailbox needs to update the Personalization Settings to track all the emails. The owner of the mailbox must follow the following steps:

1. Navigate to the **Environment URL.** Select on the gear button on the top right and select **Personalization Settings.**  
    ![](media/image1.png)

2. Select the **Email** tab and select **All email messages** on the **Track** option and select Ok.  
    ![](media/image2.png)

This should set up server-side sync on the mailbox.

### Shared Mailbox

If you are using a shared mailbox, then you should create a queue so that all the users working on the shared mailbox can access email contents.

1. Sign in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as user with a system administrator security role.
2. Select the environment you want to set up.
3. On the command bar, select **Settings.**
4. On the **Settings** page, expand the **Users + Permissions** heading and select **Teams**.
5. Select **Create team** on the top.
6. Fill out a name, business unit, and administrator as needed and select **Owner** as the team type.  
    ![](media/image3.png)

7. In the next page, add all the members that should have access to the shared mailbox. This will allow the users to access email contents from the Supplier Communications Agent incoming email workspace in FnO.
8. Head back to the **Settings** page, expand the **Business** heading and select **Queues**.
9. Select the **New** button on top to create a new **Queue** entity record.
10. Fill out the **Name,** set the **Incoming email** as the email address of the shared mailbox and assign the **Owner** as the team that was created earlier and hit **Save**.  
    ![](media/image4.png)

11. After saving, a mailbox should be created under **Email Settings.** Select the mailbox name.
12. Select Test & Enable Mailboxes on the top command bar.  
    ![](media/image5.png)  

    Note: If this operation fails, check the **Alerts** section in the mailbox. If you see the following error, you need to contact Global/Exchange admin to approve the mailbox. Find more information about the process at <https://aka.ms/D365emailapproval>.  
    ![](media/image6.png)

Note: Make sure that no other mailboxes with the same email address are set up and are active. To check this, navigate to **All Mailboxes** and make sure that there is only one mailbox with the same shared mailbox email address. If there are multiple, deactivate all the other mailboxes that have the same shared mailbox address that we are setting up. For example; in the following example there is only one mailbox with the email address that we are setting up so this is correctly set up.

![](media/image7.png)

For detailed instructions, go to [Set up server-side synchronization of email](https://learn.microsoft.com/en-us/power-platform/admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks).

## Troubleshoot server-side synchronization

For information about how to solve common issues related to server-side synchronization, go to [Troubleshooting and monitoring](https://learn.microsoft.com/en-us/power-platform/admin/troubleshooting-monitoring-server-side-synchronization).

## Refresh data

After you enable the supplier communication agent on a sandbox environment, we recommend that you do a data refresh, which will let you test in the sandbox environment with the same data that you would have on your production environment. See the following page for how to do a database refresh: [Refresh database - Finance & Operations \| Dynamics 365 \| Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/database/database-refresh)

Users for both Dataverse and Dynamics

The existing Dynamics 365 Supply Chain Management users that would be reviewing the agent emails and summaries would also need to be created as Dataverse users (if not already).

Please follow the instructions to create these users: [Create users - Power Platform \| Microsoft Learn](https://learn.microsoft.com/en-us/power-platform/admin/create-users)
