---
title: Derived dimensions
description: Learn how to configure derived dimensions so that entering a value for one financial dimension automatically fills in values for other dimensions.
author: ethanrimes
ms.author: ethanrimes
ms.topic: article
ms.date: 04/05/2026
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: DimensionDetails
ms.dyn365.ops.version: July 2017 update
---

# Derived dimensions

[!include [banner](../includes/banner.md)]

You can configure a dimension so that information for other dimensions is automatically entered when you enter that dimension in a document. For example, if you enter cost center 10, a value of **20** can be automatically entered in the department dimension.

> [!NOTE]
> The dimension whose value triggers the derivation is called the *driving dimension*. In the previous example, cost center is the driving dimension because entering a cost center value drives the automatic entry of the department value.

Set up derived values on the dimensions page.

1. Select a dimension and then select **Derived dimensions**.

    The **Derived dimensions** page includes a grid. The selected dimension segment is the first column in this grid.

1. Add the segments that you want to derive. Each segment appears as a column.

Enter the dimension combinations that you want to derive from the dimension in the first column. For example, to use the cost center as the dimension that the department and location derive from, enter cost center 10, department 20, and location 30. Then, when you enter cost center 10 in a master record or on a transaction page, department 20 and location 30 are entered by default.

## Shared dimensions only

You can only configure derived dimensions for shared dimensions, not company-specific dimensions.

**Examples of shared dimensions (allowed):** Departments, Cost Center

**Examples of company-specific dimensions (not allowed):** Project, Bank Accounts, Customers, Vendors

To check if a dimension is shared or company-specific, go to **General ledger > Chart of accounts > Dimensions > Financial dimensions** and select **Dimension values** from the action pane. Company-specific dimensions show the company name at the bottom of the tile.

If you need to use a company-specific dimension, you can create a shared custom table that includes the company-specific values. For more information, see [Make backing tables consumable as financial dimensions](../../fin-ops-core/dev-itpro/financial/dimensionable-entities.md).

> [!IMPORTANT]
> When you rename an entity that is used as the basis for a driving dimension in derived dimensions, the dimension values in the derived dimension configurations are automatically updated to reflect the new entity name.

## Overriding existing values with derived dimensions

By default, derived dimensions don't override existing values. This means you can establish default dimensions on master records, and those dimensions aren't changed by derived dimensions.

To change this behavior, select the **Replace existing dimension values with derived values** checkbox on the **Derived dimensions** page. Using the previous example, if department was already set to 50 and location to 60, entering cost center 10 would change them to department 20 and location 30.

The **Replace existing dimension values with derived values** setting only applies when a user manually enters a driving dimension value on a page. If the system fills in dimension values automatically through defaulting (for example, when default dimensions from a customer record are applied to a new sales order), derived dimensions don't override those defaulted values, even with this setting enabled.

![](media/derived-dimensions-replace-values.png)

When **Replace existing dimension values with derived values** is disabled, the derived dimensions will still automatically overwrite blank fields.

## Preventing changes with derived dimensions

When you use **Add segment** on the **Derived dimensions** page to add a segment as a derived dimension, an option at the bottom of the **Add segment** page lets you prevent changes to that dimension when it's derived. The default setting is off. Change it to **Yes** to prevent the dimension from being changed after it is derived.

Prevent changes only applies when the entered dimension value has derived values set up for it. If there are no derived values defined for a particular value, users can still change the related dimensions freely. Using the previous example, entering cost center 10 would lock department to 20. But entering cost center 20, if it has no derived rules, would leave department editable.

In all cases, the account value and all dimensions values are still validated against the account structures after the derived dimensions values are applied. If you use derived dimensions and they fail validation when used on a page, you must change the derived dimensions values on the **Derived dimensions** page before you can use them in transactions.

## Derived dimensions and entities

You can set up the derived dimensions segments and values by using entities.

- The **Derived dimensions** entity sets up the driving dimensions and the segments that are used for those dimensions.
- The **Derived dimensions value** entity lets you import the values that should be derived for each driving dimension.

When you use an entity to import data, if that entity imports dimensions, the derived dimension rules are applied during the import unless the entity specifically overrides those dimensions.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
