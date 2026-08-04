---
title: Manage users of the Supplier Engagement app and supplier portal (preview)
description: Learn about user management for the Supplier Engagement app and supplier portal, including security roles, web roles, and access control.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage users of the Supplier Engagement app and supplier portal (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Supplier Engagement solution uses a multilayered security framework to control access across the Supplier Engagement app, the supplier portal, and Supply Chain Management. Security roles and web roles define what each user can see and do—from managing global vendor data and processing registrations to inviting portal users and accessing transactional documents.

User management is divided into two areas:

- **Supplier Engagement app users** – Internal users such as procurement staff and supplier managers who work in the Supplier Engagement model-driven app. Access is controlled through Dataverse security roles that map to corresponding roles in Supply Chain Management.
- **Supplier portal users** – External supplier representatives who access the portal to collaborate on purchase orders, RFQs, invoices, and consignment inventory. Access is controlled through Power Pages web roles that are synchronized with Supply Chain Management external user roles.

Both areas share a common principle: user permissions are managed centrally in the Supplier Engagement app and automatically synchronized to Supply Chain Management. This approach eliminates the need for separate user administration in each system.

> [!IMPORTANT]
> Internal users who are part of the procurement team must have the required security roles in both Supply Chain Management and the Supplier Engagement (Dataverse) app. This dual access is required to allow synchronization and related Supplier Engagement processes to work correctly across both systems.

## How user access works

The following table summarizes how access control works at each layer of the solution.

| Layer | User type | Access mechanism |
|---|---|---|
| Supplier Engagement app (Dataverse) | Internal users | Dataverse security roles |
| Supplier portal (Power Pages) | External supplier contacts | Web roles assigned in the Supplier Engagement app |
| Supply Chain Management | Both internal and external | Roles synchronized from the Supplier Engagement app |

For internal users, Dataverse security roles determine what features are available in the Supplier Engagement app. These roles map to Supply Chain Management roles, such as *Purchasing Manager* and *Purchasing Agent*, so that internal users also have appropriate access to supply chain data.

For external users, web roles control what portal pages and features are visible. Each portal user automatically maps to an external user in Supply Chain Management. Supply Chain Management roles are assigned based on the web roles, and extensible data security (XDS) policies ensure that each user can only access data belonging to their vendor.

## Related information

- [Manage Supplier Engagement app users](supplier-engagement-app-users.md)
- [Manage supplier portal users](supplier-engagement-portal-users.md)
- [Supplier Engagement overview](supplier-engagement-overview.md)
- [Supplier Engagement deployment overview, prerequisites, and licensing](deploy-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
