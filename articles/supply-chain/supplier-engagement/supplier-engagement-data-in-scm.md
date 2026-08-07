---
title: Work with Supplier Engagement data in Supply Chain Management (preview)
description: Learn how global vendor data, certificates, and risk reports work in Supply Chain Management with the Supplier Engagement solution.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: VRMGlobalVendor, FormTabControl, VendSupplyRiskPowerBI
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Work with Supplier Engagement data in Supply Chain Management (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Supplier Engagement solution introduces several changes to Supply Chain Management that support the new global vendor model. These changes include a dedicated global vendors form, global vendor certificates, and enhancements to the supply risk assessment report. This article describes how to work with Supplier Engagement data directly in Supply Chain Management.

## Supplier Engagement and vendor collaboration

The Supplier Engagement solution is intended to replace the older vendor collaboration feature. Key differences between vendor collaboration and the new solution include:

- **Global vendor concept** – Supplier Engagement introduces the global vendor concept, where a single master profile represents a vendor across legal entities. Only vendors that are associated with a global vendor are accessible through the Supplier Engagement app or the supplier portal. Learn more in [Global vendor management overview](supplier-engagement-global-vendors-overview.md).
- **Supplier Engagement app** – A model-driven Power Apps application is available for internal procurement specialists and buyers to manage vendor relationships. Learn more in [Work with the Supplier Engagement app](supplier-engagement-app-overview.md).
- **Supplier portal** – The supplier portal is a dedicated Power Pages app that vendors use to collaborate with your organization. Previously, vendors interacted through the Vendor Collaboration module in Supply Chain Management. <!-- TODO: Add link to supplier portal article when available -->

Learn more in [How Supplier Engagement compares to the vendor collaboration interface](supplier-engagement-comparison.md).

## Global vendors in Supply Chain Management

In Supply Chain Management, you can access global vendors by going to **Procurement and sourcing** \> **Vendors** \> **Supplier engagement** \> **All global vendors**. The **All global vendors** page shows the following data:

- Global vendor name and ID
- Global vendor status
- Global vendor holds
- Released vendors

The global vendor table in Supply Chain Management is shared, with each global vendor represented by a single party in the global address book. When details such as contacts, addresses, or contact persons for a global vendor party are updated in Supply Chain Management, these changes are synchronized with the Supplier Engagement app.

## Local vendors

Local vendors that are involved in Supplier Engagement continue to be managed as they were previously. You can create new vendors either from the **All vendors** page or by releasing from the party within the global address book.

Learn more in [Create global vendors from existing data](deploy-configure-scm.md#create-global-vendors-from-existing-data).

## Manage certificates

Local vendor certificate management remains unchanged. With Supplier Engagement and the global vendor model, certificates can now be added at the global vendor level and automatically apply to all associated local vendors. These certificates are marked with a **Global vendor certification** checkbox on the **Certifications** page and can only be created in the Supplier Engagement app. To open the **Certifications** page, go to **Procurement and sourcing** \> **Vendors** \> **All vendors**, select a vendor, and then, on the Action Pane, open the **Vendor** tab and select **Certifications**.

Learn more in [Manage certificates](supplier-engagement-manage-certificates.md).

## Create a global vendor based on existing vendor data

You can convert existing vendors to global vendors or merge an existing vendor with a global vendor. Learn more in [Create global vendors from existing data](deploy-configure-scm.md#create-global-vendors-from-existing-data).

Learn more in [Create a global vendor](supplier-engagement-create-global-vendor.md).

## Supply risk assessment report

When the Supplier Engagement feature is turned on in Supply Chain Management, the standard **Supply Risk Assessment** report (**Procurement and Sourcing** \> **Inquiries and Reports** \> **Supply Risk Assessment** \> **Supply Risk Assessment**) is enhanced with the following changes:

- A **Date** filter is added to enable time-based analysis.
- A **Global Vendor** filter is introduced as a hierarchy level above vendors.
- Global vendor data is incorporated into report visuals to provide aggregated insights.

Learn more in [Risk management and corrective actions](supplier-engagement-risk-corrective-actions.md).

## Related information

- [Supplier Engagement overview](supplier-engagement-overview.md)
- [Work with the Supplier Engagement app](supplier-engagement-app-overview.md)
- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Risk management and corrective actions](supplier-engagement-risk-corrective-actions.md)
- [Synchronize data between Supplier Engagement and Supply Chain Management](supplier-engagement-data-sync.md)
