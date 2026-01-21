---
title: Review and apply purchase order changes received in vendor emails (production ready preview)
description: Learn how Copilot automates vendor email analysis, identifies purchase order changes, and helps you apply updates.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: null
ms.topic: how-to
ms.date: 04/24/2025
ms.custom:
  - bap-template
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:04/24/2025
---

# Review and apply purchase order changes received in vendor emails (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Supplier Communications Agent helps speed up communications with vendors about purchase orders by enabling Copilot to read emails from some or all vendors.

When Copilot analyzes a vendor email, it determines what the message is about (for example, whether it's a purchase order confirmation or a purchase order change request) and which purchase order it applies to. Copilot then matches the information that it extracts from the email to fields in the system and indicates whether there are any changes. Therefore, you just need to review the information that Copilot provides, review the proposed changes, and decide whether to accept those changes. In this way, Copilot saves you time, because you don't have to manually find, open, and edit the purchase order in the system.

Copilot classifies each vendor email that it reads into one of the following categories, based on the intent that it detects in the message:

- *Purchase order confirmation* – Copilot detected that the intent of the message is to confirm one or more purchase orders (all the purchase orders that the email mentions).
- *Purchase order change request* – Copilot detected that the message contains at least one requested change to a purchase order. For example, the vendor wrote to tell you that they can't deliver the full quantity that was requested for one or more lines, to tell you that they can't deliver on time, or to reject the entire order.
- *Rejected* – Copilot detected that the vendor can't supply the requested purchase order.
- *Other* – Copilot couldn't identify any of the previous intents.

For the first two categories, Copilot identifies which purchase orders the email is related to and matches the information in the email to information in the system.

> [!IMPORTANT]
> The agent can read incoming PDF attachments but not Microsoft Word or Excel documents.

When you review incoming changes that are based on an email, the system shows the original email, the current information in the system, and the specific changes that are being proposed. Therefore, you can more easily understand each change. After you finish reviewing the proposal and making any corrections that are required, you can apply the changes directly to the relevant purchase order.

## Configure the agent to track your email

You need to configure the Supplier Communications Agent to monitor a specific email address for incoming messages from vendors. Follow these steps to complete the configuration.

> [!IMPORTANT]
> Before you begin, complete the steps in [Set up and configure the Supplier Communications Agent](./supplier-com-agent-setup.md). If you want to send or forward email communications from your own email address for testing, you must also [set up your email address as a vendor contact](supplier-com-agent-setup.md#own-email).

1. Sign in to the Microsoft Dynamics 365 Supply Chain Management environment as a user who has [permissions to manage the agent configuration](./supplier-com-agent-setup.md#permissions-for-users-who-manage-the-agent-configuration).
1. Go to **Agents** \> **Agents (Preview)**.
1. On the **Library** tab, for **Speed up updates in purchase orders with Supplier communications agent**, select **Select**.
1. On the **Agent configuration** page, use the dropdown menu to specify which vendors the agent should analyze emails for. Select **Any vendor** to track all vendors or **Specific vendors** to track a list of specific vendors that you provide.
1. Select the mailbox that the agent should monitor. The dropdown menu shows all mailboxes that the sign-in user has access to. If the mailbox that you're looking for isn't in the list, follow the steps in [Synchronize mailboxes with Dataverse](./supplier-com-agent-setup.md#synchronize-mailboxes-with-dataverse).
1. Select **Activate**.

## Review and accept changes suggested by the agent

The agent detects changes in the following fields:

- Quantity
- Unit of measure
- Price
- Confirmation
- Delivery date
- Cancellation

To review and accept changes that the agent suggests based on the emails that it reads, follow these steps:

> [!IMPORTANT]
> Before you begin, confirm that the signed-in user has access to the mailboxes. For more information, see [Synchronize mailboxes with Dataverse](./supplier-com-agent-setup.md#synchronize-mailboxes-with-dataverse).

1. Open the **Purchase order receipt and follow-up** workspace.
1. A **(Preview) Emails from vendors** tile indicates the number of emails that require review. Select the tile.

    The left side of the **(Preview) Emails from vendors** page lists all the emails that the agent reads. The right side shows summaries that Copilot generates.

1. Follow one of these steps:

    - To apply all the changes that the agent suggests, select **Apply all suggestions**. This action affects all purchase orders that the message mentions.
    - To apply all suggestions to a single selected purchase header and all its lines, select **Apply suggestions** in the **Purchase order header** section.
    - To apply suggestions to specific purchase order lines, select the relevant lines, and then select **Apply suggestions** in the **Purchaser order lines** section.

## Teach the agent to better interpret incoming email content

If a vendor uses acronyms or other language that isn't saved in the system, the Supplier Communications Agent can't interpret it. However, you can teach the agent to better interpret incoming email content. By doing this, you help improve its accuracy.

Two types of teaching are available:

1. Column mapping teaching
1. Value teaching

### Teach the agent about column mappings

This type of learning happens when any of the following cases occur:

1. The incoming email from the vendor contains a term or acronym that the agent can't interpret.
1. The email contains multiple possible matches for a given field in Finance & Operations. For example, the field **Confirmed delivery date** appears in incoming vendor emails with a lot of variety when it comes to naming. Examples include:

    - *Estimated delivery date*
    - *Confirmed delivery date*
    - *Transportation load date*
    - *Ship date*
    - *Ship by*
    - *Approx delivery date*, etc.

If the agent detects ambiguity in the possible match for a field, it shows that "Some columns are mapped with low confidence.". In this case, you can use the **Review** button to manually choose which of the fields from the vendor's email you want the agent to use. This action opens a side panel, where the potential mappings of the field are listed. After you choose the correct option, you can decide when to apply this teaching for all vendors, for the current vendor, or only one time.

To map more fields, select **Show more**. This action expands the list of fields that are available for mapping. Agent teaching on field mapping is currently available for the fields: **Confirmed receipt date**, **Unit**, **Quantity**, and **Unit price**.

### Teach the agent about value mappings

For values of fields like **Unit**, a vendor might use synonyms or industry equivalences that aren't saved in your system. You can train the agent to recognize these equivalences. For example, as a value for **Unit**, you use *cartons*, but one of your vendors always uses the name *cassettes* for the same unit. When the agent detects the different value as a change, you can clarify the equivalence. When you edit the field, the teaching pane appears. You can then save the equivalence for all vendors, for the current vendor, or not at all.

### Locate existing teaching items

If any teaching is previously saved for all vendors or a specific vendor, you can always find it later, review it, or delete it:

1. Go to **Procurement and sourcing** \> **(Preview) Supplier Communications Agent** \> **(Preview) Emails from vendors**.
1. On the top menu, select **Taught items** to view everything that the agent has been taught.
