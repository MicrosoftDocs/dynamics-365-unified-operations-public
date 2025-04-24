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