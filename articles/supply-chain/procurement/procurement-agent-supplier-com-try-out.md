---
title: Try out the updates from vendors feature without a complete email setup (production ready preview)
description: Learn how to try out the updates from vendors (reading vendor emails) functionality of the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management without having to do a complete email setup first.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/09/2026
ms.custom:
  - bap-template
---

# Try out the *updates from vendors* feature without a complete email setup (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how to try out the *updates from vendors* (reading vendor emails) functionality of the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management without having to do a complete email setup first.

The Supplier Communications Agent has two independent features:

- *Follow-up with vendors* (writing reminders)
- *Updates from vendors* (reading vendor emails)

The *follow-up with vendors* feature is straightforward to set up and try out, but the *updates from vendors* feature requires a more complex email setup. If you want to try the *updates from vendors* feature without doing a complete email setup, use the approach described in this article. This approach lets you try the feature by creating a few test emails so you can see how the agent works and how it handles the kinds of messages that you receive.

To try out this feature, follow these steps:

1. Enable the *(Production Ready Preview) Supplier Communications Agent* feature in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
1. Go to **Procurement and sourcing** \> **(Preview) Procurement Agent - Supplier Communications** \> **(Preview) Emails from vendors**.
1. When the feature is fully configured, the **Emails from vendors** workspace lists the emails that the agent identified as coming from vendors. However, you can manually add messages to try out the feature without needing to set up email integration. To do that, select **Add vendor messages** from the Action Pane.
1. Enter the following information into the dialog:
    - **Title** – Enter a title for your test message.
    - **Message** – Enter or paste the body of the email. This body can be the content of an existing email you want to try or just any fictional message.
    - **Attachment** – If you'd like to add an attachment, select the **Browse** button here and then select an image or PDF file. You can add up to 10 attachments.
  
1. Select **Save**.
1. Wait for a few minutes and refresh the page, which then shows your message. Select the email to see how the agent processed it, what information it extracted, and how it classified the email.
