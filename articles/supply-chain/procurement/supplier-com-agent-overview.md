---
title: Supplier Communications Agent overview (production ready preview)
description: The Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management helps purchasers be more productive by using AI to automate many of these communications so they can focus on more value-adding tasks
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: overview
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Supplier Communications Agent overview (production ready preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Purchasing personnel spend a large part of their day on manual tasks related to communicating with vendors, following up with vendors, and maintaining changes related to purchase orders. Often, these tasks are manual, repetitive, and low-complexity, which procurement personnel would be eager to automate so they could save time for more complex and meaningful tasks. Automating these tasks can also help companies save on procurement costs in general.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

Communication between procurement departments and vendors is commonly unstructured and via email, even for companies using Electronic Data Interchange (EDI) implementations and even when working with recurrent vendors.

The Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management helps purchasers be more productive by automating many of these communications so they can focus on more value-adding tasks.

## Follow up on purchase orders

The agent can automatically compose emails that remind vendors to confirm a purchase order or ask why a delivery is late. This saves the time otherwise needed to find the orders that require attention and then author specific emails for them. The agent can either send the emails automatically, right away, or generate draft for human review before sending.

## Speed up purchase order communications

The agent helps purchasers speed up communications with vendors by allowing Copilot to read emails from some or all vendors.

The Supplier Communications Agent understands what the email is about (purchase order confirmation, purchase order changes requested from the vendor or other intent), which purchase order numbers it is about, and then matches the information extracted from the email to the fields in the system, indicating if there are any changes. This way, the purchaser only must review this information and update the fields in the system if needed, instead of manually opening the purchase order in the system and doing all the work, saving time that can be used on other more value-adding tasks.

## Cost

Using the agent will incur charges utilizing Microsoft Copilot Studio messages.

Please see the billing rates and management for Microsoft Copilot Studio here: [Billing rates and management - Microsoft Copilot Studio \| Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-messages-management)

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

# Follow up on purchase orders using the Supplier Communications Agent (production ready preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Supplier Communications Agent helps you identify and follow up on purchase orders that vendors have not confirmed yet or for which delivery is late. For each order it finds, it automatically generates a draft email addressed the relevant vendor.

To supplier communications agent lets you do the following actions.

- Create queries to find the purchase orders to follow up on. Queries are unique for each user, so you create and adjust them to best your own business needs. By default, you'll have two queries (one for following up on unconfirmed purchase orders and one for following up on late deliveries). These queries can be deleted, modified or new ones can be created fitting business needs.
- Configure how emails are authored for each of your queries.
- Review the draft emails created by the agent. After reviewing each message, you can choose to modify it, copy it to email client, and/or send. Data used to compose the email comes from the purchase order lines and/or related tables.

By default, the system provides the following two premade queries for finding purchase orders that require action.

- **Unconfirmed purchase orders** – Finds purchase orders assigned to you that have a delivery date in the next 60 days that haven't yet been confirmed by the vendor (confirmed delivery date is blank). The specific criteria are:
    - Confirmed delivery date is blank
    - Owner = (your user account)
    - Delivery reminder is not 0

- **Delayed purchase orders** – Finds purchase orders assigned to you that are delayed (where the confirmed delivery date has passed by 1 or more days). The specific criteria are:
    - Confirmed delivery date is prior to today
    - Owner = (your user account)
    - Delivery remainder is not 0

## Configure query criteria and email settings

This section describes how to set up queries to find purchase orders that require follow-up. It also describes how to configure the way Copilot generates vendor email content for each query.

1. Go to the **(Preview) Follow-up emails** page by doing one of the following steps.

    - Looking for it on the menu item, under Procurement and **Sourcing &gt; (Preview) Supplier Communications Agent &gt; (Preview) Follow-up emails**

    - Go to the **Purchase order receipt and follow-up** workspace, where you will find a tile that it **(Preview) Follow-up emails** indicating the number of emails

2. Do one of the following steps.

    - To edit an existing query, select it in the list and then select **Edit**.

    - To delete an existing query, select it in the list and then select **Delete.**

    - To create a new query, select **Configure agents**. Under **Library**, select **Send follow-up emails with Supplier Communications Agent**

3. Change the name of the query if desired by editing the default **Draft follow-up emails for purchase orders**

4. Select whether to find **Unconfirmed purchase orders** or **Delayed purchase orders.**

5. Modify the criteria to set which purchase orders need follow up. Examples could be orders that have not been confirmed for the next 2 months; or that have been created 3 days ago, sent and not confirmed etc.

    - When **delayed purchase order** is chosen the criteria is:
        - Deliver remainder (line) is not 0
        - Confirmed receipt (line) is between 60 days before today and 1 day before today
        - Orderer (header) is you (current user)

    - When **unconfirmed purchase order** is chosen, the criteria is:
        - Deliver remainder (line) is not 0
        - Confirmed receipt date (line) is blank ("")
        - Orderer (header) is you (current user)
        - Document status (header) is not None

6. Select the fields that should be included in the email, such as the delivery dates, or the address.

7. Add a signature if desired by just selecting signature and entering the desired text. Note that *This email was written with the help of AI* email footer can be optionally added. If emails are automatically sent, this email footer becomes mandatory.

8. Select the tone of the emails: Casual or Formal, Urgent or Non-urgent.

![A screenshot of a email AI generated content may be incorrect ](media/image8.png)

Examples of other queries may be:

For creating emails where the order was created less than 3 days ago and is not confirmed:

- Deliver remainder (line) is not 0
- Confirmed receipt (line) is blank
- Created date is between today-3 and today
- Orderer (header) is you (current user)

Or the same case also only for a certain vendor group A when they are unconfirmed:

- Deliver remainder (line) is not 0
- Confirmed receipt (line) is blank
- Created date is between today-3 and today
- Orderer (header) is you (current user)
- Vendor (group) is A

Configure the email address the emails will be sent from

Check the email address that the emails will be sent from on the settings indicated on [Configure and send email - Finance & Operations \| Dynamics 365 \| Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/organization-administration/configure-email)

You can always change the email address it is being sent from on the specific email.

## Review and send drafted emails

Go to the page **(Preview) Follow-up emails** to see the emails already created for the different configurations. On the left you will find the configurations and on the right the different emails for the selected configuration.

Edit as needed, and select **Send** to be able to send it to the vendor.

## Automatically send emails

Note that for automatically sending emails, the optional feature below must be turned on.

(Preview) Supplier Communications Agent – automatically sending emails

If that has been the case, the emails will be automatically sent from the email address of the administrator that setup the agent.

Look into the following for details: [Configure and send email - Finance & Operations \| Dynamics 365 \| Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/organization-administration/configure-email)

# Review and apply purchase order changes received in vendor emails (production ready preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The supplier communications agent helps speed up communications with vendors about purchase orders by allowing Copilot to read emails from some or all vendors.

When Copilot analyzes a vendor email, it's able to understand what the message is about (confirmation, change request, or other) and which purchase order it refers to. Copilot then matches the information extracted from the email to the fields in the system and indicates any changes. Then, you just need to review the information provided by Copilot, review the proposed changes, and decide whether to accept them. Copilot saves you the time otherwise needed to manually find, open, and edit the purchase order in the system.

When Copilot reads a vendor email, it classifies the intent of the message into one of the following categories:

- **Purchase order confirmation** – Copilot detected that the purpose of the messages was to confirm one or more purchase orders (including all the purchase orders mentioned in the email).
- **Purchase order change request** – Copilot detected that the message contains at least one requested change to a purchase order. For example, the vendor is writing to tell you that they can't deliver the full quantity requested for one or more lines, can't deliver on time, or to reject the entire order.
- **Rejected** – Copilot detected that the vendor cannot supply the requested purchase order.
- **Other** – Copilot couldn't identify each of the previous intents.

For both the first cases of intent, Copilot identifies which purchase orders the email relates to and matches the information in the email to information in the system.

When you're reviewing incoming changes based on email, the system shows the original email, the current information in the system, plus the specific changes being proposed, which makes it easy to understand each change. After you've reviewed the proposal and made any corrections, the system lets you apply the changes directly to the relevant purchase order.

## Prerequisites

To use this feature, your system admin must enable and configure it for your system, as described in [Set up and configure the supplier communications agent (preview)](#set-up-and-configure-the-supplier-communications-agent-preview).

## Enable Copilot to track your email

To use this feature, you must configure your personal options to allow tracking of all email messages. Follow these steps to view or change this setting.

1. Sign in to the Dynamics 365 Power platform environment as a user that requires access to this feature.
2. Open the **Setting** menu (the gear icon in upper-right corner) and then select **Personalization options**.
3. Open the **Email** tab.
4. Under the **Select the email messages to track in Microsoft Dynamics 365** section, set **Track** to *All email messages*.
5. Select **OK** to save your settings.

## Set up vendors whose email you want to analyze

The feature must be set up to allow access to your email and indicate whether it should analyze emails from all vendors or only from certain vendor email addresses. A vendor email address must be setup in the system, in the vendor page as a contact for it to be recognized as a vendor email address.

Select the vendors by selecting the **any vendor** drop-down in the agent configuration. When a vendor is selected, all mails from that vendor domain will be read.

![A screenshot of a email AI generated content may be incorrect ](media/image9.png)

## Review and accept changes suggested by the agent

1. Go to the **(Preview)** **Purchase order updates** page by
    - looking for it on the menu item, or
    - from the Purchase order receipt and follow-up workspace, where you will find a tile that it (Preview) Purchase order updates indicating the number of emails

2. In this page you will find on the left side all the emails read by the agent and in the right side, the summary by copilot.

3. Now, you are able to:
    - **Apply all suggestions** if you would like to apply in the system all the changes the vendor is suggesting in the email. This will apply for all purchase orders.
    - **Apply suggestions** for a single purchase order by selecting on Apply suggestions under the **Purchase order header** section. It will apply all suggestions both for the header and all lines for the selected purchaser orders.
    - **Apply suggestions** for a single or set of lines by selecting the needed lines and then select on the Apply suggestions under the **Purchaser order lines** section.

## Teach the agent to better interpret incoming email content

There may be cases where the vendor uses acronyms or other language that is not saved in the system, so the agent may be confused in how to interpret it. There are two possible cases.

### Teach about column mappings

You may see in the top of the summary by copilot, that the agent writes **Review column mappings**. This may be because the vendor attached a pdf that contains several columns that may be mapped to a single field in the system or it may be an acronym that the agent does not know how to interpret.

Whenever you select **Review column mappings**, you may save the mapping:

- For all vendors
- For this vendor
- Or not save it, do it as one time change

If you decide to save it for all vendors or for this vendor, you can always go to **Taught items** and see what items have been taught. You can as well delete from here if necessary.

### Teach about value equivalences

In case that there may be synonyms or industry equivalences not saved on your system, you can also save them when you apply the change.

For example, you may have that the unit for a certain item is *cartons*, but a given vendor always uses *cassettes*,which is essentially the same for this specific vendor. So, whenever the agent detects this as a change, you will be able to change it in the given line, and then it will pop-up the teaching panel where you will be able again to choose if you want to save it for all vendor or for this vendor.
