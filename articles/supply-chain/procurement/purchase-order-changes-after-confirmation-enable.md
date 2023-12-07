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

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Turn on Copilot support for the Confirmed purchase orders with changes workspace

The **Confirmed purchase orders with changes** workspace is enabled by default starting in Supply Chain Management version 10.0.36. <!-- KFM: Confirm version --> The workspace can be used either with or without its AI-powered and Copilot functionality. If you'd like to enable its AI features, then make sure you have also enabled Copilot capabilities in finance and operations apps, as described in [Enable Copilot capabilities in finance and operations apps (preview)](../../fin-ops-core/dev-itpro/copilot/enable-copilot.md).

## Troubleshoot the Copilot configuration

The Copilot experience for the **Confirmed purchase orders with changes** workspace provides a troubleshooting feature that helps you identify missing configuration steps. If one or more of the configuration steps are missing, the Copilot summarization tiles will offer a troubleshooting link.

[<img src="media/po-change-review-trouble-shooting.png" alt="Screenshot of the Confirmed purchase orders with changes workspace." title="Screenshot of the trouble shooter for Copilot configuration." width="720" />](media/po-change-review-trouble-shooting.png#lightbox)

Select the link to open a troubleshooting feature that checks all installation and configuration requirements needed for Copilot to function. It marks the steps that need attention.

You can complete the outstanding configuration steps in a separate browser tab. When you're done, select **Recheck** to reevaluate your configuration.  

## See also

- [Review and accept changes to confirmed purchase orders](purchase-order-changes-after-confirmation.md)
- [Responsible AI FAQ for the Confirmed purchase orders with changes workspace](../faq-confirmed-po-changes.md)
