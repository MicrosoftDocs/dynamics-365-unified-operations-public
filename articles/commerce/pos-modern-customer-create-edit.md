---
title: Modernized customer create and edit workflows in Store Commerce
description: Learn about the modernized customer create and edit workflows in Store Commerce POS, including the combined address save, address validation, extensibility model, and how to enable them.
author: anush6121
ms.author: anvenkat
ms.topic: article
ms.date: 04/13/2026
ms.reviewer: v-griffinc
ms.custom:
  - bap-template
---

# Modernized customer create and edit workflows in Store Commerce (preview)

[!include [banner](../includes/banner.md)]

**Applies to:** Dynamics 365 Commerce version 10.0.48 and later

The modernized customer create and edit workflows rebuild the legacy customer add/edit view on React and Fluent UI, consistent with the broader Store Commerce modernization effort. The redesigned workflows simplify the associate experience, optionally enforce address completeness at the time of customer creation, and introduce a richer extensibility model for custom field definitions and validation.

This article describes how to enable the modernized workflows and what's available in version 10.0.48.

## Prerequisites

- Store Commerce app version 10.0.48 or later
- The following feature flag must be enabled in Commerce headquarters:
  - `StoreCommerce.EnableModernCustomerAddEditView`

## Enable the modernized customer create and edit workflows

1. In Commerce headquarters, go to the **Feature management** workspace (**System administration \> Workspaces \> Feature management**).
2. Search for **Modern customer create and edit workflows** and select **Enable now**.
3. Run the **1110 (Global configuration)** distribution schedule job to push the changes to channel databases.
4. Restart the Store Commerce app.

> [!NOTE]
> When this feature flag is enabled, the legacy customer add/edit view is automatically replaced. The two views cannot be active simultaneously.

---

## React-based form layout

The customer create and edit view has been rebuilt on React and Fluent UI with a responsive, section-based layout. The form is organized into named sections — including **Customer information**, **Contact information**, and **Address** — with Fluent UI styling and skeleton loading for a faster perceived experience.

The layout adapts to device form factor automatically:

- **Desktop:** Full-width form with section tiles and a horizontal command bar.
- **Phone/mobile:** Compact single-column layout optimized for touch input.

---

## Combined customer and address save

The address section is now part of the customer create and edit form. Associates complete customer information and address entry in a single view and save both with one action.

This replaces the legacy two-step flow where customer record creation and address creation were separate saves. When address validation is enabled, the combined save ensures every customer record has an associated address at the time of creation, preventing downstream issues at checkout and in fiscal compliance scenarios.

---

## Address validation

Mandatory address validation requires a customer record to have an associated address before it can be saved. Associates are prompted to complete the address section if they attempt to save without one.

Address validation is controlled by a CSU flight and is not enabled by default. To enable it for your environment, contact Microsoft support.

---

## Name pattern validation

The modernized workflow supports configurable name pattern validation via regex. Administrators can define name format requirements in headquarters, and associates are prompted inline when the entered name does not match the required pattern.

---

## Save and add to transaction

When creating a customer from the transaction page, associates can use the **Save and add to transaction** action to save the new customer record and immediately attach them to the current cart — without navigating to the customer details page first.

---

## Extend the customer create and edit view

Version 10.0.48 introduces extensibility support for the modernized customer add/edit view. Extensions can:

- Add custom **app bar commands** by extending `CustomerAddEditExtensionCommandBase` from `PosApi/Extend/Views/CustomerAddEditView`
- Define **custom field definitions** using `CustomerFieldDefinitions` to add, reorder, or modify fields displayed in the form sections
- Implement **custom name pattern validation** by providing a regex pattern through the extension configuration

Extensions are registered in the POS extension manifest under `components.extend.views.CustomerAddEditView`.

---

## Version history

| Version | Enhancements |
|---|---|
| 10.0.48 | React-based form layout, combined customer and address save, optional address validation (CSU flight), name pattern validation, Save and add to transaction action, extensibility support |

---

## Additional resources

- [Modern workflows in Store Commerce POS](POS-UX-modernization.md)
- [Modernized customer details page in Store Commerce](pos-modern-customer-details.md)
- [Store Commerce extensibility overview](dev-itpro/pos-extension/pos-extension-overview.md)
- [Customer management in Store Commerce](customer-mgmt-stores.md)
