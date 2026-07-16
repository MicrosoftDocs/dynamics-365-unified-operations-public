---
title: Set up fiscal notes for credit cancellation in Brazil tax reform
description: Learn about how to set up and create fiscal notes for credit cancellation in Brazil tax reform.
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 07/13/2026
ms.custom: bap-template
---

# Set up fiscal notes for credit cancellation in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes how to configure tax groups in Globalization Studio and create a fiscal document for credit cancellation in Brazil tax reform in Dynamics 365 Finance.

## Setup

### Configure tax codes in Globalization Studio

Before you create a credit cancellation fiscal document, configure the tax codes (CBS and IBS) in the tax calculation feature in Globalization Studio and publish the updated version.

To configure tax codes for credit cancellation, follow these steps:

1. Go to **All workspaces** > **Globalization Studio**.
1. Select **Tax calculation**.
1. In the list, find and select the desired tax calculation feature.
1. Select **New** to create a new version, and then select **Edit**.
1. Expand the **Tax codes and groups** section.
1. Select **Add** to add a CBS tax code.
1. In the **Tax code** field, enter a value for CBS.
1. In the **Calculation origin** field, enter or select a value.
1. In the list, select the link in the selected row.
1. Select **Add** to add an IBS tax code.
1. In the **Tax code** field, enter a value for IBS.
1. In the **Calculation origin** field, enter or select a value.
1. In the list, select the link in the selected row.
1. For each tax code, configure the following fields:
    - In the **Tax type** field, enter or select a value.
    - In the **Fiscal indicator** field, enter or select a value.
    - In the **cClassTrib code** field, enter or select a value.
1. Select **Save**.
1. Select **Change status** > **Complete**.
1. Select **Yes** to confirm.
1. Close the page.

    > [!NOTE]
    > The tax codes must include all applicable Brazil Tax Reform taxes: CBS, IBS-State, and IBS-City. Ensure the fiscal indicator and tax type are correctly configured for each code to avoid posting errors.
    >
    > The **Rate** for the tax codes for **credit cancellation** should be blank.

### Assign the tax calculation version to parameters

After you create the new version, assign it to the tax calculation parameters so the system uses it for credit cancellation transactions.

To assign the tax calculation version, follow these steps:

1. Go to **Tax** > **Setup** > **Tax configuration** > **Tax calculation parameters**.
1. In the **Name** field, enter or select the applicable tax calculation feature.
1. In the list, select the link in the selected row.
1. Select **Save**.
1. Close the page.

### Configure tax groups

To create or update the tax group and item tax group to include the credit cancellation tax codes, follow these steps:

1. Go to **All workspaces** > **Globalization Studio**.
1. Select **Tax calculation**.
1. In the list, find and select the desired feature.
1. Select **New**, and then select **Edit**.
1. Select the **Tax group** tab.
1. Select **Add**.
1. In the **Lines.Tax Group** field, enter or select a value.
1. In the **Tax codes** field, select all applicable tax codes (CBS, IBS-State, IBS-City).
1. Select **Select**.
1. Select the **Item tax group** tab.
1. Select **Add**.
1. In the **Lines.Item Tax Group** field, enter or select a value.
1. In the **Tax codes** field, select all applicable tax codes.
1. Select **Select**.
1. Select **Save**.
1. Select **Change status** > **Complete** > **Yes**.
1. Close the page.
1. Go to **Tax** > **Setup** > **Tax configuration** > **Tax calculation parameters**.
1. Update the **Name** field to point to the newly completed version.
1. Select **Save**.
1. Close the page.

## Workflow

### Create a credit cancellation fiscal document

Create a credit cancellation fiscal document from an existing posted fiscal document in **Accounts payable**.

To create a credit cancellation fiscal document, follow these steps:

1. Go to **Accounts payable** > **Fiscal documents** > **All fiscal documents**.
1. In the list, find and select the fiscal document to cancel.
1. Select **Business Type**.
1. Select **Credit cancellation**.
1. In the **Fiscal document type** field, enter or select a value.
1. In the list, select the link in the selected row.
1. Select **OK**.

### Enter CBS and IBS tax amounts

After you create the credit cancellation document, manually enter the CBS and IBS tax amounts on each line.

To enter tax amounts, follow these steps:

1. In the list, find and select the desired line.
1. In the **CBS amount** field, enter a number.
1. In the **IBS-City amount** field, enter a number.
1. In the **IBS-State amount** field, enter a number.

    > [!NOTE]
    > Repeat this step for each line in the fiscal document that requires tax amounts.

### Configure taxes on the fiscal document lines

To set up the sales tax group and item sales tax group on the fiscal document lines, follow these steps:

1. Expand the **Line details** section.
1. Select the **Setup** tab.
1. In the **Sales tax group** field, enter or select a value.
1. In the list, select the link in the selected row.
1. In the **Item sales tax group** field, enter or select a value.
1. In the list, select the link in the selected row.
1. Select **Sales tax** to verify the calculated tax amounts.
1. Select **OK**.
1. Close the page.

### Post the credit cancellation fiscal document

To post the credit cancellation fiscal document, follow these steps:

1. Select **Post**.
1. Close the page.
1. Refresh the page.
1. In the list, find and select the posted record to verify.
1. Select **Posted sales tax** to confirm the tax amounts were recorded correctly.
1. Close the page.

> [!NOTE]
> After posting, the credit cancellation fiscal document links to the original fiscal document with business type **Credit cancellation**. You can verify the posted sales tax from the fiscal document header.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
