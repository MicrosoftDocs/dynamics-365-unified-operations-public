---
title: Configure inline actions in the modern transaction grid
description: Learn how to use Screen Layout Designer in Dynamics 365 Commerce headquarters to configure which inline actions appear on transaction line items in the Store Commerce modern transaction grid.
author: anush6121
ms.author: anvenkat
ms.topic: article
ms.date: 04/13/2026
ms.reviewer: v-griffinc
ms.custom:
  - bap-template
---

# Configure inline actions in the modern transaction grid

[!include [banner](../includes/banner.md)]

**Applies to:** Dynamics 365 Commerce version 10.0.48 and later

Inline actions extensibility lets retailers and implementation partners control which operations appear as inline actions on transaction line items in the modern transaction grid. Configuration is done in Screen Layout Designer in Dynamics 365 Commerce headquarters — no code changes are required for standard operations.

## Prerequisites

- Store Commerce app version 10.0.48 or later
- The following feature flag must be enabled in Commerce headquarters:
  - **Enable Modern Transaction Grid in POS Transaction View** (`RetailModernTransactionGridFeature`)

The legacy transaction grid does not support inline actions extensibility. Inline actions configuration is ignored if the modern transaction grid is not enabled.

---

## Default behavior

No configuration is required to preserve the current experience. If no inline actions are configured for a screen layout, Store Commerce continues to display the existing default set of inline operations for that layout.

Once inline actions are configured for a specific layout, the configured list replaces the defaults for that layout only. Other layouts remain unaffected.

---

## What you can configure

### Which actions appear

You can add any eligible out-of-the-box POS operation or custom operation registered in headquarters as an inline action on transaction line items. Both standard and custom operations are available from the same configuration surface in Screen Layout Designer.

### Display order

You control the sequence in which inline actions appear on a line item. Ordering the most relevant operations first helps associates access common actions without scrolling or expanding a list.

### Custom operations

Operations built through the POS extension framework can be added as inline actions alongside out-of-the-box operations. This gives retailers a unified configuration experience for both standard and customized workflows.

---

## Configure inline actions in Screen Layout Designer

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Screen layouts**.
2. Open the screen layout you want to configure and launch **Screen layout designer**.
3. Select the transaction grid component and open the inline actions configuration.
4. Add operations from the available list, remove any operations that aren't needed, and set the display order.
5. Save the layout and run the **Channel configuration (1090)** distribution schedule job to push the changes to stores.

Changes take effect in Store Commerce after the updated layout is downloaded at the register.

---

## Localization

**Out-of-the-box operations**: Display names are automatically localized using existing POS resource strings. No additional localization work is required.

**Custom operations**: Display names fall back to the operation name configured in headquarters. To provide localized display names for custom operations, use resource files and operation mappings in your extension code via the POS extension framework.

---

## Security and permissions

Inline actions respect the same POS security roles and permission model as button grid operations. Use role-based access controls to restrict sensitive operations — such as price override or void line — to managers, while presenting a simplified action set to cashiers.

---

## Version history

| Version | Enhancements |
|---|---|
| 10.0.48 | Inline actions extensibility via Screen Layout Designer — configure operations, display order, and custom operations per screen layout |

---

## Additional resources

- [Modernized transaction grid in Store Commerce](pos-modern-transaction-grid.md)
- [Modern workflows in Store Commerce POS](POS-UX-modernization.md)
- [Store Commerce extensibility overview](dev-itpro/pos-extension/pos-extension-overview.md)
