---
title: Follow up on purchase orders using the Supplier Communications Agent (production ready preview)
description: Learn how to use the Supplier Communications Agent to identify unconfirmed or delayed purchase orders and automate follow-up emails tailored to your business needs.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 11/05/2025
ms.custom:
  - bap-template
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:04/24/2025
---

# Follow up on purchase orders using the Supplier Communications Agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Supplier Communications Agent helps you identify and follow up on purchase orders that vendors didn't yet confirm or that delivery is late for. For each order that it finds, the agent automatically generates a draft email that is addressed to the relevant vendor.

The Supplier Communications Agent helps you perform the following actions:

- Create queries to find purchase orders that require follow-up. Queries are unique for each user. Therefore, you can create and adjust them to meet your specific business needs. Two default queries are provided. One is used to follow up on unconfirmed purchase orders, and the other is used to follow up on late deliveries. You can modify or delete the default queries as required to meet your business needs.
- Configure how emails are generated for each query.
- Review the draft emails that the agent generates. After you review each message, you can modify it, copy it to your email client, and send it. To generate the emails, the agent uses data from the purchase order lines and related tables.

By default, the system provides two premade queries that you can use to find purchase orders that require action:

- *Unconfirmed purchase orders* – This query finds purchase orders that are assigned to you, have a delivery date within the next 60 days, and aren't yet confirmed by the vendor (that is, the confirmed delivery date is blank). The query uses the following specific criteria:

    - The **Confirmed delivery date** field is blank.
    - The **Owner** field is set to your user account (the current user).
    - The **Deliver remainder** field is set to a value other than *0* (zero).

- *Delayed purchase orders* – This query finds purchase orders that are assigned to you and that are delayed (that is, the confirmed delivery date was one or more days ago). The query uses the following specific criteria:

    - The **Confirmed delivery date** field is set to a date that is earlier than the current date.
    - The **Owner** field is set to your user account (the current user).
    - The **Deliver remainder** field is set to a value other than *0* (zero).

## Configure query criteria and email settings

The following procedure explains how to set up queries to find purchase orders that require follow-up. It also explains how to configure the way that Copilot generates vendor email content for each query.

1. Open the **(Preview) Follow-up emails** page by following one of these steps:

    - Go to **Procurement and Sourcing** \> **(Preview) Supplier Communications Agent** \> **(Preview) Follow-up emails**.
    - Open the **Purchase order receipt and follow-up** workspace. A tile named **(Preview) Follow-up emails** indicates the number of emails that require review. Select the tile.

1. Follow one of these steps:

    - To edit an existing query, select it in the list, then select **Edit**.
    - To delete an existing query, select it in the list, then select **Delete**.
    - To create a new query, select **Configure agents**. Then, under **Library**, select **Send follow-up emails with Supplier Communications Agent**.

1. Edit the name of the query as required. (The default name is *Send follow-up emails for purchase orders*.)
1. Select whether you want the query to find unconfirmed purchase orders or delayed purchase orders.
1. Modify the criteria to define which purchase orders require follow-up. For example, you might want the query to find unconfirmed orders for the next two months, orders that were created more than three days ago, or orders that were sent but not confirmed.

        - If you set the query to find delayed purchase orders, the following default criteria are used:

        - The **Deliver remainder** field on the line is set to a value other than *0* (zero).
        - The **Confirmed receipt date** field on the line is set to a date that is between 60 days and 1 day before the current date.
        - The **Orderer** field on the header is set to your user account (the current user).

        - If you set the query to find unconfirmed purchase orders, the following default criteria are used:

        - The **Deliver remainder** field on the line is set to a value other than *0* (zero).
        - The **Confirmed receipt date** field on the line is blank.
        - The **Orderer** field on the header is set to your user account (the current user).
        - The **Document status** field on the header is set to a value other than *None*.

1. Select the fields that should be included in the email, such as the delivery dates or the address.
1. To add a signature, select **Signature**, and enter the desired text. You can also add an email footer that has text such as "This email was written with the help of AI."

    > [!IMPORTANT]
    > If your system is set up to send emails automatically, the email footer is mandatory.

1. Select the tone of the emails (*Casual* or *Formal*, or *Urgent* or *Non-urgent*).

### Examples

Here are some examples of other queries that you might set up:

- To generate emails for orders that were created less than three days ago, and that aren't yet confirmed, specify the following criteria:

    - The **Deliver remainder** field on the line is set to a value other than *0* (zero).
    - The **Confirmed receipt date** field on the line is blank.
    - The **Created date** field is set to a date that's between three days before the current date and current date.
    - The **Orderer** field on the header is set to your user account (the current user).

- To generate emails for orders for vendor group A that were created less than three days ago, and that aren't yet confirmed, specify the following criteria:

    - The **Deliver remainder** field on the line is set to a value other than *0* (zero).
    - The **Confirmed receipt date** field on the line is blank.
    - The **Created date** field is set to a date that's between three days before the current date and current date.
    - The **Orderer** field on the header is set to your user account (the current user).
    - The **Vendor (group)** field is set to *A*.

## Configure the addresses that emails are sent from

Emails that are sent automatically, without user review, are sent from the [agent identity user](supplier-com-agent-setup.md#set-up-agent-identity) email address.

Emails that are drafted by the agent and then reviewed by a user are sent from the email address of the user that presses **Send**.

To learn how to view and edit the email address of the agent identity user or any other user, go to [Configure and send email](../../fin-ops-core/dev-itpro/organization-administration/configure-email.md).

## Review and send drafted emails

To review the emails that were previously created for the various configurations, go to **Procurement and Sourcing** \> **(Preview) Supplier Communications Agent** \> **(Preview) Follow-up emails**. The configurations appear on the left, and the emails for each configuration appear on the right.

Edit each message as required, and then select **Send** to send it to the vendor.

## Automatically send follow-up emails

If emails should be sent automatically, without user review, an administrator must use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to turn on the *(Preview) Send follow-up emails to vendors with Supplier Communications Agent - automatically sending emails* feature. This feature is optional and is turned off by default. Learn more in [Set up and configure the Supplier Communications Agent](supplier-com-agent-setup.md).

When you turn on the feature, the system uses the email address of the administrator who set up the agent as the sender for each email that the system automatically sends.

Learn more in [Configure and send email](../../fin-ops-core/dev-itpro/organization-administration/configure-email.md).

## Set up the agent run schedule and batch job options

The Supplier Communications Agent includes a batch job that runs the agent automatically. To change the default configuration of the job, follow these steps:

1. Go to **System Administration** \> **Inquiries** \> **Batch jobs**.
1. Find and select the job that has a **Job description** that matches the name of the agent configuration, which is described in [Configure query criteria and email settings](#configure-query-criteria-and-email-settings). For example, if the agent name is *Send follow-up emails to vendors with Supplier Communications Agent*, you can locate its batch job quickly by using this text in the **Job description** column header filter. The agent name might be different on your system, so you should check the name before proceeding.

    :::image type="content" source="media/supplier-com-agent-follow-up/supplier-agent-batch-job.png" alt-text="Screenshot showing the column filter for finding a batch job by its description." lightbox="media/supplier-com-agent-follow-up/supplier-agent-batch-job.png":::

1. With the job selected, choose **Recurrence** from the Action Pane.
1. In the **Define recurrence** dialog, set up the run schedule as desired, then select **OK**.

    :::image type="content" source="media/supplier-com-agent-follow-up/supplier-agent-batch-job-schedule.png" alt-text="Screenshot showing the settings provided for scheduling a batch job." lightbox="media/supplier-com-agent-follow-up/supplier-agent-batch-job-schedule.png":::

1. To get more information about the batch job and adjust other settings, return to the **Batch jobs** page and select the link in the **Job ID** column.
