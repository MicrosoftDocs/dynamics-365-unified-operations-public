---
title: Supplier portal home page (preview)
description: Learn about the supplier portal home page, including workspaces, essentials, notifications, and how the page adapts based on vendor status.
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

# Supplier portal home page (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The supplier portal home page is the main entry point for vendor collaboration within the Supplier Engagement solution. It provides vendors with quick access to key business areas such as purchase order confirmations, vendor bidding, consignment inventory, and invoicing. The home page layout is designed for ease of navigation and can be customized to reflect your organization's branding and communication style.

The content displayed on the home page is dynamically personalized based on the vendor's profile and access permissions.

The following screenshot shows an example of the supplier portal home page.

:::image type="content" source="media/supplier-portal-home-page.png" alt-text="Screenshot of the supplier portal home page showing workspaces, essentials, and navigation options." lightbox="media/supplier-portal-home-page.png":::

## Workspaces section

The **Workspaces** area provides a consolidated view of vendor-related activities. Each workspace panel displays key metrics and links directly to detailed pages.

| Panel | Description | Example metrics |
|---|---|---|
| Vendor bidding | View and respond to requests for quotation (RFQs). | New invitations, Returned, In progress, Awarded |
| Purchase order confirmation | Manage and confirm purchase orders. | For review, Awaiting customer action, Open confirmed PO |
| Consignment inventory | Track consignment stock and consumption status. | On hand CI, PO consuming CI |
| Invoicing | View and manage invoice submissions and approvals. | Submitted, Approved, Paid |

> [!NOTE]
> Record counts are calculated based on the signed-in user's access rights. The workspaces section is hidden for prospective vendors who aren't yet fully approved.

## Essentials section

The **Essentials** section provides quick links to the most frequently used pages and management functions.

### Vendor details

The **Vendor details** panel provides quick links to the pages where you maintain your organization's profile, legal entity information, and portal user accounts. The following table describes each link.

| Link | Description |
|---|---|
| Global vendor setup | View, edit, and manage information related to the global vendor profile. |
| Local vendor details | View, edit, and manage information related to local vendor entities. |
| Users | View and manage user accounts related to the vendor organization. |

### Notifications

The **Notifications** panel provides updates and alerts about vendor data management activities, such as certificate expiration. Here you can:

- View recent notifications directly on the home page.
- **Dismiss** notifications you already reviewed.
- Select **View all notifications** to open the full list.

### Help

The **Help** section offers guidance and support links for portal users. By default, the portal includes example links on the home page:

- **Terms & Conditions** – Legal information for using the supplier portal.
- **How to respond to a Purchase Order** – Step-by-step instructions for confirming or updating POs.
- **How to Add or Remove a User** – Guidance for managing user access.
- **Contact Support** – Direct link to customer support for technical or functional help.

These links are placeholders. Customize them to include your organization's actual help materials.

## Home page versions based on global vendor status

The home page layout adapts depending on the global vendor's qualification status:

- **Qualified or Approved global vendor** – Displays the full home page, including **Workspaces**, **Essentials**, **Notifications**, and **Help** sections.
- **Prospective global vendor** – Shows a simplified version with introductory content and limited access. Workspace tiles and transactional data are hidden.

## Related information

- [Supplier portal overview](supplier-engagement-portal-overview.md)
- [Personalize the supplier portal](personalize-portal-overview.md)
- [Supplier portal landing page and vendor onboarding](supplier-engagement-portal-landing.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
