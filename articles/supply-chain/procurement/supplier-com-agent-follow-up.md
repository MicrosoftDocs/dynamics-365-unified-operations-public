---
title: Follow up on purchase orders using the Supplier Communications Agent (production ready preview)
description: Use the Supplier Communications Agent to identify unconfirmed or delayed purchase orders and automate follow-up emails tailored to your business needs.
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

# Follow up on purchase orders using the Supplier Communications Agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Supplier Communications Agent helps you identify and follow up on purchase orders that vendors haven't confirmed yet or for which delivery is late. For each order it finds, the agent automatically generates a draft email addressed the relevant vendor.

The Supplier Communications Agent lets you do the following actions.

- Create queries to find purchase orders to follow up on. Queries are unique for each user, so you create and adjust them to best match your own business needs. Two queries are provided by default (one for following up on unconfirmed purchase orders and one for following up on late deliveries). You can create, delete, or modify these queries as needed to fit your business needs.
- Configure how emails are authored for each of your queries.
- Review the draft emails created by the agent. After reviewing each message, you can choose to modify it, copy it to your email client, and/or send it. Data used to compose the email comes from the purchase order lines and/or related tables.

By default, the system provides the following two pre-made queries for finding purchase orders that require action.

- *Unconfirmed purchase orders* – Finds purchase orders assigned to you that have a delivery date in the next 60 days that haven't yet been confirmed by the vendor (confirmed delivery date is blank). The specific criteria are:
    - Confirmed delivery date is blank
    - Owner = (your user account)
    - Delivery reminder is not 0

- *Delayed purchase orders* – Finds purchase orders assigned to you that are delayed (where the confirmed delivery date has passed by one or more days). The specific criteria are:
    - Confirmed delivery date is prior to today
    - Owner = (your user account)
    - Delivery remainder is not 0

## Configure query criteria and email settings

The following procedure shows how to set up queries to find purchase orders that require follow-up. It also describes how to configure the way Copilot generates vendor email content for each query.

1. Go to the **(Preview) Follow-up emails** page by doing one of the following steps.
    - Go to **Procurement and Sourcing** \> **(Preview) Supplier Communications Agent** \> **(Preview) Follow-up emails**
    - Go to the **Purchase order receipt and follow-up** workspace. A tile called **(Preview) Follow-up emails** indicates the number of emails that require review. Select the tile to open the **(Preview) Follow-up emails** page.

1. Do one of the following steps.
    - To edit an existing query, select it in the list and then select **Edit**.
    - To delete an existing query, select it in the list and then select **Delete**.
    - To create a new query, select **Configure agents**. Under **Library**, select **Send follow-up emails with Supplier Communications Agent**

1. Edit the name of the query, if desired (the default name is *Draft follow-up emails for purchase orders*).
1. Select whether to find *Unconfirmed purchase orders* or *Delayed purchase orders*.
1. Modify the criteria to set which purchase orders need follow-up. Examples could be orders for the next two months that haven't been confirmed, orders that were created more than three days ago, orders sent but not confirmed, and so on.

    - If you chose to find *Delayed purchase orders*, the criteria are:
        - Deliver remainder (line) is not 0
        - Confirmed receipt (line) is between 60 days before today and 1 day before today
        - Orderer (header) is you (current user)

    - If you chose to find *Unconfirmed purchase orders*, the criteria are:
        - Deliver remainder (line) is not 0
        - Confirmed receipt date (line) is blank ("")
        - Orderer (header) is you (current user)
        - Document status (header) is not None

1. Select the fields that should be included in the email, such as the delivery dates or the address.
1. Add a signature if desired by selecting **Signature** and entering the desired text. You can optionally add an email footer with the text *This email was written with the help of AI*. If your system is set to send emails automatically, this email footer becomes mandatory.
1. Select the tone of the emails (*Casual* or *Formal*, *Urgent* or *Non-urgent*).

Here are some examples of other queries that you might set up:

- To generate emails for orders that were created less than three days ago and aren't confirmed, the criteria could be:
    - Deliver remainder (line) is not 0
    - Confirmed receipt (line) is blank
    - Created date is between today-3 and today
    - Orderer (header) is you (current user)

- To generate emails for orders that were created less than three days ago and aren't confirmed, but only for vendor group A, the criteria could be:
    - Deliver remainder (line) is not 0
    - Confirmed receipt (line) is blank
    - Created date is between today-3 and today
    - Orderer (header) is you (current user)
    - Vendor (group) is A

## Configure the address that emails are sent from

To learn how to view and set the address from which the emails are sent, go to [Configure and send email](../../fin-ops-core/dev-itpro/organization-administration/configure-email.md).

You can always change the sending email address for any or all individual email messages before you send them.

## Review and send drafted emails

Go to **Procurement and Sourcing** \> **(Preview) Supplier Communications Agent** \> **(Preview) Follow-up emails** to see the emails that were already created for the various configurations. Configurations are shown on the left and emails for each configuration are shown on the right.

Edit each message needed and select **Send** to send it to the vendor.

## Automatically send follow-up emails

To automatically send emails without user review, an administrator must use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to turn on the *(Preview) Send follow-up emails to vendors with Supplier Communications Agent - automatically sending emails* feature. This feature is optional and is turned off by default. Learn more in [Set up and configure the Supplier Communications Agent](supplier-com-agent-setup.md).

When this feature is turned on, the system uses the email address of the administrator who set up the agent as the sender for each automatically delivered email.

For more information, see [Configure and send email](../../fin-ops-core/dev-itpro/organization-administration/configure-email.md).
