---
title: Create a global vendor (preview)
description: Create global vendors by approval, manual entry, or initial sync so you can centralize supplier data across legal entities.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Create a global vendor (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

You can create global vendors through supplier self-registration, direct entry by an internal user, or synchronization from existing vendor data in Supply Chain Management. The creation method determines the initial **Origin** value, but each method creates the same centralized vendor profile that you can qualify, approve, and release to legal entities.

## Understand the creation methods

The Supplier Engagement solution supports three creation methods for global vendors.

### Manual creation in the Supplier Engagement app

An internal user such as a Supplier Engagement manager can create the global vendor directly in the app. The **Origin** field is set to *Supplier Engagement*. Manual creation works well when your organization identifies a supplier first and wants to create the master profile before inviting the supplier to the portal or qualifying the record. This method is described later in this article.

### Portal registration and approval

When a supplier submits a registration request through the supplier portal and your organization approves it, the system automatically creates a prospect global vendor. The **Origin** field is set to *Supplier portal* so you can identify how the record entered the system. This method is useful when suppliers begin the relationship through self-service registration and then continue onboarding in the portal. Learn more in [Review and approve incoming vendor registrations](supplier-engagement-review-registrations.md).

### Automated creation through initial sync

During the initial synchronization process, the system can create a qualified global vendor from an existing vendor in Supply Chain Management. The **Origin** field is set to *Supply Chain Management*. This method helps you adopt Supplier Engagement without recreating supplier records manually. Learn more in [Create global vendors from existing data](deploy-configure-scm.md#create-global-vendors-from-existing-data).

## Create a global vendor manually

Use this procedure when you want to create a new vendor profile directly in the Supplier Engagement app. After you save the record, the system assigns a unique global vendor number, sets the initial status to *Prospect*, and records *Supplier Engagement* as the origin.

1. Open the Supplier Engagement app, and at the bottom of the navigation pane, select the **Menu** area.
1. On the navigation pane, go to **General** \> **Global vendors**.
1. On the command bar, select **New**.
1. Enter the vendor details in the fields provided. Use tooltips to understand the purpose of each field. Required fields are marked with an asterisk (*).
1. On the command bar, select **Save**. Notice the following values, which are generated on save:
    - **Global vendor number** – The system assigns this number automatically.
    - **Status reason** – The initial status is *Prospect*, which indicates that the vendor is not yet qualified for operational use.
    - **Origin** – Set to *Supplier Engagement* to indicate that you created the vendor manually.

## Next steps

After the global vendor is created, you can continue onboarding by adding addresses, contact methods, certificates, capabilities, and assessment details. You can then qualify the vendor and release it to one or more legal entities when it's ready for operational use. Learn more in [Manage global vendor information](supplier-engagement-global-vendor-info.md).

## Related information

- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Manage global vendor information](supplier-engagement-global-vendor-info.md)
- [Detect and manage duplicate global vendors](supplier-engagement-duplicate-global-vendors.md)
- [Synchronize data between Supplier Engagement and Supply Chain Management](supplier-engagement-data-sync.md)
- [Supplier Engagement overview](supplier-engagement-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
