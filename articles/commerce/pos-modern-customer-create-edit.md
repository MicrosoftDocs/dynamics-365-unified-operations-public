---
title: Modernized customer creation and editing workflows in Store Commerce (preview)
description: Learn about the modernized customer creation and editing workflows in Store Commerce POS, including the combined address save, address completeness, extensibility model, and how to enable them.
author: anush6121
ms.author: anvenkat
ms.topic: article
ms.date: 05/13/2026
ms.reviewer: mirao
ms.custom:
  - bap-template
---

# Modernized customer creation and editing workflows in Store Commerce (preview)

[!include [banner](../includes/banner.md)]

**Applies to:** Dynamics 365 Commerce version 10.0.48 and later

The modernized customer creation and editing workflows rebuild the legacy customer add and edit view on React and Fluent UI, consistent with the broader Store Commerce modernization effort. The redesigned workflows simplify the associate experience, optionally enforce address completeness at the time of customer creation, and introduce a richer extensibility model for custom field definitions and validation.

This article describes how to enable the modernized workflows and what's available in version 10.0.48.

## Prerequisites

- Store Commerce app version 10.0.48 or later

## Enable the modernized customer creation and editing workflows

1. In Commerce headquarters, go to the **Feature management** workspace (**System administration** > **Workspaces** > **Feature management**).
1. Search for **Enable modernized customer details page** and select **Enable now**.
1. Run the **1110 (Global configuration)** distribution schedule job to push the changes to channel databases.
1. Restart the Store Commerce app.

> [!NOTE]
> When you enable this feature flag, it automatically replaces the legacy customer add/edit view. You can't activate both views at the same time. This flag also controls the modernized customer details page, so enabling it activates both experiences simultaneously.

## React-based form layout

The customer creation and editing view is rebuilt on React and Fluent UI with a responsive, section-based layout. The form is organized into named sections, including **Customer information**, **Contact information**, and **Address**, with Fluent UI styling and skeleton loading for a faster perceived experience.

The layout adapts to device form factor automatically:

- **Desktop**: Full-width form with section tiles and a horizontal command bar.
- **Phone/mobile**: Compact single-column layout optimized for touch input.

## Combined customer and address save

The address section is a part of the customer creation form. Associates complete customer information and address entry in a single view and save both information with one action.

This behavior replaces the legacy two-step flow where customer record creation and address creation were separate saves. When you enable address completeness, the combined save ensures every customer record has an associated address at the time of creation, preventing downstream issues at checkout and in fiscal compliance scenarios.

To edit a customer's address after the record is created, associates can use the **Manage addresses** button in the **Shipping addresses** section of the customer details page.

## Address completeness

Mandatory address completeness requires a customer record to have an associated address before it can be saved. Associates are prompted to complete the address section if they attempt to save without one.

A CSU flight controls the address completeness and it isn't enabled by default. To enable it for your environment, contact Microsoft support.

## Name pattern validation

The modernized workflow supports configurable name pattern validation via regular expressions (regex). Administrators can define name format requirements through extensions, and associates are prompted inline when the entered name doesn't match the required pattern.

## Save and add to transaction

When creating a customer from the transaction page, associates can use the **Save and add to transaction** action to save the new customer record and immediately attach it to the current cart. They don't need to go to the customer details page first.

## Extend the customer creation and editing view

The modernized customer add/edit view supports the same extensibility model as the legacy version. Existing extensions built for the legacy view work with the modernized page without any changes. Extensions can:

- Add custom **app bar commands** by extending `CustomerAddEditExtensionCommandBase` from `PosApi/Extend/Views/CustomerAddEditView`.
- Define **custom field definitions** using `CustomerFieldDefinitions` to add, reorder, or modify fields displayed in the form sections.
- Implement **custom name pattern validation** by providing a regex pattern through the extension configuration.
- Add **custom controls** that appear in the form view, consistent with legacy customer add/edit view behavior.

Extensions are registered in the POS extension manifest under `components.extend.views.CustomerAddEditView`.

## Version history

| Version | Enhancements |
| ------- | ------------ |
| 10.0.48 | React-based form layout, combined customer and address save, optional address completeness (CSU flight), name pattern validation, save and add to transaction action, and extensibility support. |

## More resources

- [Modern workflows in Store Commerce POS](POS-UX-modernization.md)
- [Modernized customer details page in Store Commerce](pos-modern-customer-details.md)
- [Store Commerce extensibility overview](dev-itpro/pos-extension/pos-extension-overview.md)
- [Customer management in Store Commerce](customer-mgmt-stores.md)
