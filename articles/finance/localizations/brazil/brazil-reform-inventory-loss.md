---
title: Fiscal notes for inventory loss in Brazil tax reform
description: Learn about how to create Fiscal notes for inventory loss in Brazil tax reform.
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 06/22/2026
ms.custom: bap-template
---

# Fiscal notes for inventory loss in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article explains how to set up an operation type for inventory loss and create a sales order fiscal document to register that loss in Brazil tax reform.

> [!NOTE]
> You create inventory loss fiscal notes from a sales order, not directly from the **Fiscal notes** form.

## Prerequisites

Before you create a sales order for inventory loss, ensure the following setup is complete:

- An operation type with **Inventory loss** and **Create inventory movements** enabled exists.
- A CFOP code is linked to the operation type in the CFOP matrix (**Tax** > **Setup** > **Sales tax** > **CFOP matrix**).
- The ledger posting group for the relevant sales tax code has the **Sales tax expense** field configured. Without this configuration, posting fails with an error related to the ledger posting group.

## Set up an operation type for inventory loss

To create or verify an operation type that supports inventory loss, follow these steps:

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value.

   > [!NOTE]
   > For inventory loss scenarios, the customer is typically a tax authority.

1. In the list, select the desired row.
1. In the list, select the link in the selected row.
1. Select **OK**.
1. On the Action Pane, select **Invoice**.
1. Select the **Header** tab.
1. Collapse the **General** section.
1. Select the **Operation type** link.
1. Select **Show or hide control**.
1. Close the page.
1. In the **Operation type** field, enter or select a value.
1. In the list, select the desired row.
1. In the list, select the link in the selected row.
1. Select the **Operation type** link.
1. Select **New**.
1. In the **Operation type** field, type a value.
1. Set **Inventory loss** to **Yes**.
1. Set **Create inventory movements** to **Yes**.
1. Select **Save**.
1. Close the page.
1. In the **Operation type** field, enter or select a value.
1. Close the page.
1. In the **Operation type** field, enter or select a value.
1. In the list, select the desired row.
1. In the list, select the link in the selected row.

## Add items and set the CFOP code

To add order lines and configure the CFOP code for the inventory loss transaction, follow these steps:

1. Select the **Lines** tab.
1. In the list, select the row.
1. In the **Item number** field, enter or select a value.
1. Close the page.
1. In the **CFOP** field, enter or select a value.

   > [!NOTE]
   > The CFOP codes available depend on the CFOP matrix setup. For inventory loss, CFOP codes typically start with **5** (intrastate) or **6** (interstate).

1. In the list, select the link in the selected row.
1. Select the **CFOP** link.
1. Select **Show or hide control**.
1. Use the Escape key to close the form.
1. In the **CFOP** field, enter or select a value.
1. Close the page.
1. In the **CFOP** field, enter or select a value.
1. Close the page.
1. Use the Escape key to close the form.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the list, select the row.
1. Use the Escape key to close the form.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Close the page.
1. Close the page.

## Configure taxes on the sales order

To configure the sales tax group and item sales tax group on the order lines, follow these steps:

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. In the list, select the link in the selected row.
1. Select **Add line**.
1. In the list, select the row.
1. In the **Item number** field, enter or select a value.
1. In the list, select the desired row.
1. In the list, select the link in the selected row.
1. In the **CFOP** field, enter or select a value.
1. In the list, select the desired row.
1. In the list, select the link in the selected row.
1. Select the **Setup** tab.
1. In the list, find and select the desired record.
1. In the list, select the desired row.
1. In the list, select the link in the selected row.
1. In the **Sales tax group** field, enter or select a value.
1. Close the page.
1. In the **Sales tax group** field, enter or select a value.
1. In the list, select the desired row.
1. In the list, select the link in the selected row.
1. On the Action Pane, select **Sales order**.
1. On the Action Pane, select **Sell**.
1. Select **Sales tax**.
1. In the **Total actual sales tax amount** field, enter a number.
1. Close the page.
1. In the **Item sales tax group** field, type a value.
1. In the **Sales tax group** field, enter or select a value.
1. In the list, select the link in the selected row.
1. Select **Sales tax**.
1. Select **OK**.

## Post the invoice

> [!IMPORTANT]
> Before posting, make sure the ledger posting group for each sales tax code has the **Sales tax expense** account configured. If this account is missing, posting fails with a ledger posting group error.

To post the sales invoice for the inventory loss, follow these steps:

1. On the Action Pane, select **Invoice**.
1. Select the **Header** tab.
1. Select **Invoice**.
1. Select **OK**.
1. Select the **Lines** tab.
1. Select the link in the **Item sales tax group** field.
1. Select the link in the **Sales tax code** field.
1. In the list, select the row.
1. Use the Escape key to close the form.
1. Select the link in the **Sales tax code** field.
1. Use the Escape key to close the form.
1. Select the **Header** tab.
1. Select the **Operation type** link.
1. Use the Escape key to close the form.
1. Select the **Lines** tab.
1. Select the link in the **Item tax group** field.
1. Select the link in the **Sales tax code** field.
1. In the list, select the row.
1. Select the link in the **Settlement period** field.
1. Use the Escape key to close the form.
1. Select the link in the **Ledger posting group** field.
1. Use the Escape key to close the form.
1. In the list, find and select the desired record.
1. Select the link in the **Sales tax code** field.
1. Select the link in the **Ledger posting group** field.
1. Use the Escape key to close the form.
1. In the list, find and select the desired record.
1. Select the link in the **Sales tax code** field.
1. Select the link in the **Ledger posting group** field.
1. Use the Escape key to close the form.
1. In the list, find and select the desired record.
1. Select the link in the **Sales tax code** field.
1. Select the link in the **Ledger posting group** field.
1. In the **Sales tax expense** field, enter the values.
1. Select **Save**.
1. Close the page.
1. In the list, find and select the desired record.
1. Select the link in the **Sales tax code** field.
1. Select the link in the **Ledger posting group** field.
1. Use the Escape key to close the form.
1. Select **Invoice**.
1. Select **OK**.
1. Select **OK**.
1. Close the page.

## Verify the posted fiscal document

To verify that the inventory loss fiscal document was posted correctly, follow these steps:

1. Go to **Accounts receivable** > **Fiscal notes** > **All Fiscal notes**.
1. In the list, find and select the desired record.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
