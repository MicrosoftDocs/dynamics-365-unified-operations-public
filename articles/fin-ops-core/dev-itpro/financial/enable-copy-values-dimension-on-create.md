---
title: Enable copy values on create for financial dimensions
description: Learn how to enable the Copy values to this dimension on each new row created feature for custom or unsupported entity-backed financial dimensions.
author: anaborges02
ms.author: aolson
ms.topic: how-to
ms.date: 03/06/2026
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
---

# Enable copy values on create for financial dimensions

[!include [banner](../includes/banner.md)]

This article explains how to enable the **Copy values to this dimension on each new <DimensionName> created** feature for custom entity-backed financial dimensions or for entity-backed dimensions that don't support it out of the box.

## Overview

When a financial dimension is backed by an entity such as Customer or Vendor, the system can automatically copy the dimension value into the default dimensions of a new record. For example, when you create a new customer, the customer ID is automatically added as the customer dimension value in the default dimensions for that customer record.

This behavior is controlled by the **Copy values to this dimension on each new <DimensionName> created** toggle on the **Financial dimensions** details form. However, this toggle is only enabled for entity-backed dimensions whose backing table has been specifically configured to support it.

Out of the box, the following 13 entities support this feature:

- AssetTable
- BankAccountTable
- CustGroup
- CustTable
- HcmPosition
- HcmWorker
- InventTable
- ProjInvoiceTable
- ProjTable
- RetailChannel
- RetailStore
- RetailTerminal
- VendTable

If you have a custom entity-backed dimension or need to enable this feature for another entity, follow the steps in this article.

## Prerequisites

- The entity must already be set up as a financial dimension backing table. For more information, see [Make backing tables consumable as financial dimensions](dimensionable-entities.md).
- You need a development environment with access to the X++ source code.

## Step 1: Add the DimensionCanCopyValuesOnCreateAttribute to the view

The **Copy values to this dimension on each new <DimensionName> created** toggle on the dimension details form is activated by the `DimensionCanCopyValuesOnCreateAttribute` attribute. You must add this attribute to the `DimAttribute` view for your backing table.

Open the view in Visual Studio and add the following attribute to the view class declaration:

```xpp
[DimensionCanCopyValuesOnCreateAttribute]
public class <ViewName> extends common
{
}
```

## Step 2: Add the copy logic to the backing table insert method

You must add code to the `insert` method of the backing table so that when a new record is created, the dimension value is automatically copied into the default dimensions of that record.

### For a custom dimension (you own the table)

Add the following code to the `insert` method on the backing table:

```xpp
public void insert()
{
    super();
    DimensionDefaultFacade::copyDimensionValueToDefaultDimensionField(
        this,
        fieldNum(<TableName>, <KeyField>),
        this,
        fieldNum(<TableName>, <DefaultDimensionForeignKey>));
}
```

Replace `<TableName>` with the name of your backing table, `<KeyField>` with the field that contains the natural key value (for example, `ItemId`), and `<DefaultDimensionForeignKey>` with the field that holds the default dimension reference.

### For a core product dimension (you don't own the table)

If the backing table is part of the standard product and you can't directly modify it, use a post-event handler on the `insert()` method, and then, implement chain of Command on the `DimensionEnabledType::canCopyValuesOnCreate()` method to return `true` for your entity.

## Step 3: Build and validate

1. Build your project and synchronize the database.
2. Navigate to **General ledger** > **Chart of accounts** > **Dimensions** > **Financial dimensions**.
3. Select the dimension that you configured and verify that the **Copy values to this dimension on each new <DimensionName> created** toggle is now enabled and can be turned on.
4. Turn on the toggle, then create a new record of the backing entity type. Verify that the dimension value is automatically added to the default dimensions of the new record.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
