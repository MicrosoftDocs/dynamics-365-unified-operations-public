---
title: Enable Copilot support for managing changes to confirmed purchase orders (preview)
description: This article describes how to enable Copilot support for the Confirmed purchase orders with changes workspace, where you can review and accept changes to confirmed purchase orders, based on their downstream impact.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchOrderInReview, PurchOrderApproved, PurchOrderInDraft, PurchOrderAssignedToMe, VendPurchOrderJournalListPage, PurchTableWorkflowDropDialog, VendPurchOrderJournal
ms.topic: how-to
ms.date: 07/06/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Enable Copilot support for managing changes to confirmed purchase orders (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

This article describes how to enable Copilot support for the **Confirmed purchase orders with changes** workspace and its optional support for Copilot features. For more information about how to use this workspace, see [Review and accept changes to confirmed purchase orders](purchase-order-changes-after-confirmation.md).

> [!IMPORTANT]
> The AI-powered and Copilot functionality that's described in this article is available as part of a preview release. All other functionality is generally available. The content and the functionality that's related to AI-powered and Copilot functionality are subject to change. For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).
>
> **During this preview phase, the summaries of changes and downstream impacts are available only in environments that are hosted in the United States (US)**, and they are shown only in English. All other functionality is globally available.
>
> To learn about the capabilities and limitations of AI-powered and Copilot features in Microsoft Dynamics 365 Supply Chain Management, see [Responsible AI FAQs for Dynamics 365 Supply Chain Management](../responsible-ai-overview.md).
>
> - Preview features are subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274).
> - Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release, so that customers can get early access and provide feedback.
> - For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).

## Turn on Copilot support for the Confirmed purchase orders with changes workspace

The **Confirmed purchase orders with changes** workspace is enabled by default. The workspace can be used either with or without its AI-powered and Copilot functionality. If you want to enable its AI features, make sure that you've also enabled Copilot capabilities in finance and operations apps, as described in [Enable Copilot capabilities in finance and operations apps (preview)](../../fin-ops-core/dev-itpro/copilot/enable-copilot.md).

## Troubleshoot the Copilot configuration

The Copilot experience for the **Confirmed purchase orders with changes** workspace provides a troubleshooting feature that helps you identify missing configuration steps. If one or more of the configuration steps are missing, the Copilot summarization tiles offer a troubleshooting link.

[<img src="media/po-change-review-trouble-shooting.png" alt="Screenshot of the Confirmed purchase orders with changes workspace." title="Screenshot of the trouble shooter for Copilot configuration." width="720" />](media/po-change-review-trouble-shooting.png#lightbox)

Select the link to open a troubleshooting feature that checks all installation and configuration requirements that Copilot needs to work. The feature marks the steps that require attention.

You can complete the outstanding configuration steps on a separate browser tab. When you've finished, select **Recheck** to reevaluate your configuration.

## See also

- [Review and accept changes to confirmed purchase orders](purchase-order-changes-after-confirmation.md)
- [Responsible AI FAQ for the Confirmed purchase orders with changes workspace](../faq-confirmed-po-changes.md)
