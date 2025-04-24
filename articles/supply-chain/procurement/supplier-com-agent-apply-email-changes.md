---
title: Review and apply purchase order changes received in vendor emails (production ready preview)
description: Discover how Copilot automates vendor email analysis, identifies purchase order changes, and helps you apply updates.
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
