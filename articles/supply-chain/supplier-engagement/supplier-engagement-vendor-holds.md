---
title: Global and local vendor holds (preview)
description: Control vendor transactions by applying or releasing global and local vendor holds in the Supplier Engagement app.
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

# Global and local vendor holds (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Vendor holds help you control supplier activity when compliance, risk, or operational conditions require temporary restrictions. You can apply holds at the global vendor level to affect all released vendors, or at the local vendor level for a single legal entity. Hold updates sync with Supply Chain Management so that transaction controls stay aligned.

## Understand vendor hold types

Depending on the hold type that you apply, the system blocks specific actions such as invoice posting, payment generation, or requisition creation.

| Hold type | Effect |
|---|---|
| *No* | All transactions are allowed. |
| *Invoice* | Invoice creation or posting is blocked. |
| *Payment* | New payments can't be generated, although existing payments can still post. |
| *Requisition* | Requisition creation is blocked. |
| *All* | All transactions are blocked for the vendor. |
| *Never* | The vendor can't be put on hold for inactivity. |

## Place a global or local vendor on hold

To place a global or local vendor on hold, follow these steps:

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record).
1. To do one of these steps:
    - To place the currently selected global vendor on hold, stay on this page. When you place a global vendor on hold, all related local vendors are also placed on hold.
    - To place a local vendor on hold, open the **Lifecycle** tab, and in the **Vendors** section, open the target local vendor record.
1. On the command bar, select **On Hold**.
1. Confirm by selecting **OK**.
1. Enter the hold details:
    - **On hold** – Select the hold type to apply
    - **On hold reason** – Select the business reason for the hold.
    - **On hold release date** – Optionally, select a date when the hold should be automatically released. If you leave this field blank, the hold remains in effect until you manually release it.
1. Select **OK**.

After you apply the hold, the vendor status updates and the changes sync to Supply Chain Management.

## Release a global or local vendor from hold

To release a global or local vendor from hold, follow these steps:

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record).
1. To do one of these steps:
    - To release the currently selected global vendor from hold, stay on this page. When you release a global vendor from hold, all related local vendors are also released.
    - To release a local vendor from hold, open the **Lifecycle** tab, and in the **Vendors** section, open the target local vendor record.
1. On the command bar, select **On Hold Release**.
1. Confirm by selecting **OK**.

After you complete these steps, the system clears the hold status and syncs the updates to Supply Chain Management.

## Related information

- [Work with the Supplier Engagement app](supplier-engagement-app-overview.md)
- [Manage local vendors](supplier-engagement-manage-local-vendors.md)
- [Supplier Engagement overview](supplier-engagement-overview.md)
