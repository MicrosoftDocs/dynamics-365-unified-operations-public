---
title: Configure Supplier Engagement app settings (preview)
description: Configure vendor types, countries or regions, and hold reasons to support consistent supplier classification and reporting.
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

# Configure Supplier Engagement app settings (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Portal management setup defines reference data that's used throughout the Supplier Engagement application. Before you onboard vendors, configure the global settings that support consistent classification, compliance alignment, and reporting. These settings include global vendor types, countries and regions, and hold reasons.

## Global vendor types

Global vendor types classify vendors based on the nature of their business or the goods and services that they provide. This setup helps organize vendors for management and analysis in the Supplier Engagement app.

## Countries/regions

Countries/regions identify a vendor's geographic location in the system. This setup also supports registration requests from anonymous users who don't have direct access to Supply Chain Management.

The list should match the countries/regions that are configured in Supply Chain Management so data stays consistent between systems.

## Hold reasons

Hold reasons specify why a vendor is on hold, such as compliance issues, performance concerns, or regulatory requirements. These reasons help users record and communicate why vendor activity is restricted.

## Create, delete, and edit settings

Use the following procedure to manage global vendor types, countries/regions, and hold reasons.

1. Open the Supplier Engagement app, and at the bottom of the navigation pane, select the **Configuration** area.
1. On the navigation pane, in the **Settings** section, select **Global vendor types**, **Countries/regions**, or **Hold reasons**.
1. Either open an existing record to edit it or, on the command bar, select **New** to create a record. You can also select **Delete** to remove a selected record.
1. Enter the following information for the new or selected record:
    - **Name** – For global vendor types and hold reasons only, enter a descriptive name. Users and vendors see these names as selectable options in Supplier Engagement and the supplier portal, so each name should clearly represent the option.
    - **Description** – For global vendor types and hold reasons only, enter a longer description.
    - **Country/region** – For countries/regions only, enter the three-letter country or region code that's used in Supply Chain Management.
    - **Long name** and **Short name** – For countries/regions only, use **Short name** for a common name such as *United Kingdom* and **Long name** for the full formal name such as *United Kingdom of Great Britain and Northern Ireland*.
1. Select **Save**.

## Related information

- [Configure the Supplier Engagement app overview](configure-app-overview.md)
- [Configure certificate types and organizations](configure-certificate-types.md)
- [Configure capabilities](configure-capabilities.md)
- [Configure risk management elements](configure-risk-management.md)
- [Configure self-assessment questions](configure-self-assessment.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
