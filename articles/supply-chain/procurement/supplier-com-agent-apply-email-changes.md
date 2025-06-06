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

When Copilot analyzes a vendor email, it can determine what the message is about (for example, whether it's a purchase order confirmation or a purchase order change request) and which purchase order it applies to. Copilot then matches the information that it extracts from the email to fields in the system and indicates whether there are any changes. Therefore, you just have to review the information that Copilot provides, review the proposed changes, and decide whether to accept those changes. In this way, Copilot saves you time, because you don't have to manually find, open, and edit the purchase order in the system.

Copilot classifies each vendor email that it reads into one of the following categories, based on the intent that it detects in the message:

- *Purchase order confirmation* – Copilot detected that the intent of the message is to confirm one or more purchase orders (all the purchase orders that are mentioned in the email).
- *Purchase order change request* – Copilot detected that the message contains at least one requested change to a purchase order. For example, the vendor wrote to tell you that they can't deliver the full quantity that was requested for one or more lines, to tell you that they can't deliver on time, or to reject the entire order.
- *Rejected* – Copilot detected that the vendor can't supply the requested purchase order.
- *Other* – Copilot couldn't identify any of the previous intents.

For the first two categories, Copilot identifies which purchase orders the email is related to and matches the information in the email to information in the system.

> [!IMPORTANT]
> The agent is able to read incoming PDF attachments but not Microsoft Word or Excel documents.

When you review incoming changes that are based on an email, the system shows the original email, the current information in the system, and the specific changes that are being proposed. Therefore, you can more easily understand each change. After you finish reviewing the proposal and making any corrections that are required, you can apply the changes directly to the relevant purchase order.

## Configure the agent to track your email

The Supplier Communications Agent must be configured to monitor a specific email address for incoming messages from vendors. Follow these steps to complete the configuration.

> [!IMPORTANT]
> Before you begin, complete the steps in [Set up and configure the Supplier Communications Agent](./supplier-com-agent-setup.md). If you want to send/forward email communications from your own email address for testing, then you must also [set up your email address as a vendor contact](supplier-com-agent-setup.md#own-email).

1. Sign in to the Microsoft Dynamics 365 Supply Chain Management environment as a user who has [permissions to manage the agent configuration](./supplier-com-agent-setup.md#permissions-for-users-who-manage-the-agent-configuration).
1. Go to **Agents** \> **Agents (Preview)**.
1. On the **Library** tab, for **Speed up updates in purchase orders with Supplier communications agent**, select **Select**.
1. On the **Agent configuration** page, use the dropdown menu to specify which vendors the agent should analyze emails for. Select **Any vendor** to track all vendors or **Specific vendors** to track a list of specific vendors that you provide.
1. Select the mailbox that the agent should monitor. The dropdown menu should show all mailboxes that the sign-in user has access to. If the mailbox that you're looking for isn't in the list, follow the steps in [Synchronize mailboxes with Dataverse](./supplier-com-agent-setup.md#synchronize-mailboxes-with-dataverse).
1. Select **Activate**.

    > [!TIP]
    > The "Enable email access" warning message that you receive is informational and doesn't prevent you from activating the agent.

## Review and accept changes suggested by the agent

The agent detects changes in the following fields:

- Quantity
- Unit of measure
- Price
- Confirmation
- Delivery date
- Cancellation

To review and accept changes that the agent suggests based on the emails that it has read, follow these steps.

> [!IMPORTANT]
> Before you begin, confirm that the signed-in user has access to the mailboxes. Learn more in [Synchronize mailboxes with Dataverse](./supplier-com-agent-setup.md#synchronize-mailboxes-with-dataverse).

1. Open the **Purchase order receipt and follow-up** workspace.
1. A **(Preview) Purchase order updates** tile indicates the number of emails that require review. Select the tile.

    The left side of the **(Preview) Purchase order updates** page lists all the emails that the agent read. The right side shows summaries that Copilot generated.

1. Follow one of these steps:

    - To apply all the changes that the agent suggested, select **Apply all suggestions**. This action affects all purchase orders that are mentioned in the message.
    - To apply all suggestions to a single selected purchase header and all its lines, select **Apply suggestions** in the **Purchase order header** section.
    - To apply suggestions to specific purchase order lines, select the relevant lines, and then select **Apply suggestions** in the **Purchaser order lines** section.

## Teach the agent to better interpret incoming email content

If a vendor uses acronyms or other language that isn't saved in the system, the Supplier Communications Agent can't interpret it. However, you can teach the agent to better interpret incoming email content. In this way, you help improve its accuracy.

### Teach the agent about column mappings

A **Review column mappings** button might appear at the top of the Copilot summary for several reasons:

- The vendor attached a PDF document to the message, and several columns in that PDF can be mapped to a single field in the system.
- The message or attachment uses an acronym that the agent can't interpret.

To fix the issue, select **Review column mappings**, and clarify the mapping. You can then save the mapping for all vendors, for the current vendor, or not at all.

If you save a mapping for all vendors or the current vendor, you can always go to **Taught items** to view everything that the agent has been taught. You can also learn where to go to delete entries as required.

### Teach the agent about value equivalences

A vendor might use synonyms or industry equivalences that aren't saved in your system. You can train the agent to recognize these equivalences.

For example, you use a unit of measure that is named *cartons*, but one of your vendors always uses the name *cassettes* for the same unit. When the agent detects the different name as a change, you can clarify the equivalence for the appropriate line. In this case, the teaching pane appears. You can then save the equivalence for all vendors, for the current vendor, or not at all.
