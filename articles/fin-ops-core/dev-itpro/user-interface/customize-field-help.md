---
title: Customize field descriptions
description: Learn about how you can customize existing field descriptions and add your own descriptions, with overviews on adding new descriptions and labeling file names.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/12/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: 94d555d7-28f3-4d94-91b4-6038e2be5047
---

# Customize field descriptions

[!include [banner](../includes/banner.md)]

This article describes how you can customize existing field descriptions and add your own descriptions.

Some of the more complex fields have descriptions that appear when you hover over a field. You can customize these descriptions if you want to add company-specific information. You can also add descriptions for additional fields. Use the **HelpText** property for field controls to create field descriptions. In previous versions, you specified the **HelpText** property for table fields and data types. Additionally, the inheritance of the **HelpText** property from data types and table fields to form controls is obsolete. Field descriptions should be specific to an individual field, in the context of the other controls and information that are available on the page. To add and customize field descriptions, you must have access to the development environment. Like other metadata changes, add new descriptions in a new model to prevent them from being overwritten when a new version of Operations is released. For more information, see [Customize through extension and overlayering](../extensibility/customization-overlayering-extensions.md).

## Customize a field description or add a new description

Use the same procedure to customize existing field descriptions and to add new field descriptions. However, when you customize an existing description, replace the existing label reference.

1. In Application Explorer, find the relevant page (form), and add it to your project.
1. In the node for the page, find the relevant field control. Make a note of the name, so that you can use it as part of the label ID.
1. Add a new label for your description. You can follow the conventions that Microsoft uses to name the label files for field descriptions and to create the label file IDs. For more information, see the next section.
1. In the **HelpText** property of the field control, add a reference to the label.

## Label file names and label IDs

Microsoft stores field descriptions in separate label files. Each module in each model has one label file. The pattern for the label file names is `FieldDescriptions_*ModuleName*_*ModelName*.*CountryCode*.label.txt`. Here are some examples:

- `FieldDescriptions_AccountsPayable_ApplicationFoundation.en-US.label.txt`
- `FieldDescriptions_SystemAdministration_ApplicationFoundation_en-US.txt`

The pattern for label IDs is `@FieldDescriptions_*ModuleName*:PageName*_*ControlName*`. Here are some examples:

- `@FieldDescriptions_AccountsPayable:CustSettlement_CustSettlement_OffsetCompany` is the ID for the label for the **Company accounts** field (`CustSettlement_OffsetCompany`) on the **Customer settlement** page (`CustSettlement`).
- `@FieldDescriptions_ProcurementAndSourcing:PurchLineBackOrder_LinkViewCheckBox` is the ID for the label for the **Link on change view** option (`LinkViewCheckBox`) on the **Backorder purchase lines** page (`PurchLineBackOrder`).

## Additional resources

[Create localizable labels](create-localizable-labels-client.md)

[View and export field descriptions](../../fin-ops/get-started/view-export-field-descriptions.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
