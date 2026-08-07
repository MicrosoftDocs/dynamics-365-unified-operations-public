---
title: View and create invoices in the supplier portal (preview)
description: Learn how vendors can create, submit, recall, and track invoices using the supplier portal's invoice management workspace.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 08/07/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# View and create invoices in the supplier portal (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The supplier portal enables vendors to create, submit, and track invoices through the **Invoice management** workspace. Vendors can create invoices from purchase orders or as cost invoices, add lines and attachments, and monitor invoice status through to payment.

## Prerequisites

To use the invoice management features in the supplier portal, the purchasing organization must set up the vendor invoice workflow as described in [Configure Supplier Engagement features in Supply Chain Management](deploy-configure-scm.md).

## Open the Invoice management workspace

To open the **Invoice management** workspace, sign in to the supplier portal and complete any of the following steps:

- On the top navigation bar, select **Invoices** and then select any of the views listed.
- On the home page, select any of the links in the **Invoicing** panel.

The workspace displays tiles for the following statuses:

The workspace displays a set of tiles, each of which represents an invoice status. Each tile displays a count of invoices in that status. Select a tile to view a list of invoices in that status. The following tiles are available in the **Invoice management** workspace:

- **Draft** – Invoices that the vendor created but didn't submit yet.
- **Submitted** – Invoices that the vendor submitted for approval but aren't yet approved.
- **Approved** – Invoices that are approved and waiting to be paid.
- **Paid** – Invoices that are fully paid.
- **Rejected** – Invoices rejected in the workflow.

## Create and submit an invoice

To create an invoice from a purchase order, follow these steps:

1. Open the **Invoice management** workspace.
1. Select **New Invoice**.
1. In the **Create invoice** dialog, select one of the following options:
    - Select **Choose a purchase order** to create an invoice from an existing purchase order.
    - Select **Start from Scratch** to create a cost invoice that isn't associated with a purchase order.
1. Fill out the rest of the dialog to identify the vendor and purchase order, and enter details about the invoice. Then select **Submit**.
1. A detailed invoice form opens where you can add terms and conditions, lines, attachments, and other details.
1. Select **Save as draft** on the toolbar to save the invoice without submitting it. You can find and open your draft invoices by selecting the **Draft** tile of the **Invoice management** workspace.
1. To view details about charges and sales tax, select the **Total charges** or **Total sales tax** information icon at the top of the invoice form.
1. When the invoice is ready, select **Submit** on the toolbar to submit the invoice to the purchaser for approval.

> [!NOTE]
> The supplier portal only shows procurement categories that the current vendor has access to. Vendors that need additional procurement categories can request them through [vendor management](supplier-engagement-portal-vendor-details.md).

## Recall an invoice

To recall an invoice and make corrections while it's still under review, follow these steps:

1. Open the **Invoice management** workspace and select the **Submitted** tile.
1. Open the invoice you want to recall.
1. On the toolbar, select **Recall**.
1. Confirm the action.
1. The details of the invoice are now editable. Make the necessary corrections and then select **Save as draft** or **Submit** on the toolbar. If you don't save or submit it, the invoice is deleted.

## Track invoice status

To check the status of your invoices, open the **Invoice management** workspace and view the tiles for **Draft**, **Submitted**, **Approved**, **Paid**, and **Rejected** invoices.

## Related information

- [Supplier portal overview](supplier-engagement-portal-overview.md)
- [View and confirm purchase orders in the supplier portal](supplier-engagement-portal-purchase-orders.md)
- [Supplier portal home page](supplier-engagement-portal-home-page.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
