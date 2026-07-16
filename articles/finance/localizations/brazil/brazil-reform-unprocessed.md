---
title: Set up and create fiscal notes for unprocessed invoices in Brazil tax reform
description: Learn about how to set up and create fiscal notes for unprocessed invoices in Brazil tax reform.
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 07/13/2026
ms.custom: bap-template
---

# Set up and create fiscal notes for unprocessed invoices in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes how to configure Brazilian parameters and create a fiscal document for an unprocessed invoice in Brazil tax reform in Dynamics 365 Finance.

> [!IMPORTANT]
> Unprocessed invoice fiscal notes are available for **Accounts receivable only**. This functionality doesn't apply to Accounts payable.

## Configure Brazilian parameters

Before you create an unprocessed invoice fiscal document, configure the default complementary item and enable the required fiscal document options in Brazilian parameters.

To configure Brazilian parameters, follow these steps:

1. Go to **Organization administration** > **Setup** > **Brazilian parameters**.
1. Select the **Fiscal document** tab.
1. Under the group **Fiscal note for unprocessed invoice**, find the **Default item** field.
1. In the **Default item** field, confirm the selected value is correct.
1. Close the page.

## Workflow for creating fiscal notes for an unprocessed invoice

The follow sections explain the workflow for creating fiscal notes for unprocessed invoices in Brazil tas reform.

### Create an unprocessed invoice fiscal document

Create an unprocessed invoice fiscal document from a regular approved fiscal document in **Accounts receivable**. The system generates a single line based on the original document, regardless of the number of lines on the original invoice.

> [!NOTE]
> Each unprocessed invoice has only one fiscal document line, which represents the total amount of the original reference document.

To create an unprocessed invoice fiscal document, follow these steps:

1. Go to **Accounts receivable** > **Fiscal notes** > **All fiscal notes**.
1. In the list, find and select an approved fiscal document to use as the basis.
1. Under the group **Tax reform fiscal note**, select **Business Type**.
1. Select **Unprocessed invoice**.
1. In the **Issuer** field, enter or select a value.
1. In the **Direction** field, enter or select a value.
1. In the **Fiscal document type** field, enter or select a value.
1. Check the **Debit/Credit** field value.
1. Check the **Currency** field value.
1. In the **Prices includes sales tax** field, select a value.
1. In the list, select the desired row.
1. In the list, select the link in the selected row.
1. Select **OK**.

### Configure the fiscal document line

To set up the CFOP code and tax groups on the fiscal document line, follow these steps:

1. Select **Add line**. The **default item** specified under **Brazilian parameter** appears.
1. Expand the **Line details** section.
1. Select the **Setup** tab.
1. In the **Item sales tax group** field, type a value.
1. In the **Sales tax group** field, type a value.
1. Select the **General** tab.
1. In the **CFOP** field, enter or select a value.
1. In the list, select the link in the selected row.
1. Close the page.

    > [!NOTE]
    > The CFOP code must be compatible with the original invoice operation type. If the CFOP lookup doesn't show the expected values, verify the CFOP matrix setup under **Tax** > **Setup** > **Sales tax** > **CFOP matrix**.
    > The tax value is 0 at this stage. Each line links to one invoice. After you specify the line reference, the total tax amount defaults from the original invoice.

### Add a fiscal reference to the original invoice

After you create the fiscal document, link it to the original invoice as a fiscal reference so the system can track the relationship between the two documents.

To add a fiscal reference, follow these steps:

1. Select **Add fiscal reference**.
1. Select **Fiscal document**.
1. Open the **Document date** column filter.
1. Sort newest to oldest.
1. In the list, find and select the original invoice record.
1. Select **OK**.
1. Close the page.

### Post the unprocessed invoice fiscal document

To post the unprocessed invoice fiscal document, follow these steps:

1. Select **Post**.
1. Close the page.
1. Refresh the page.

> [!NOTE]
> After posting, you can view the fiscal document from **Accounts receivable** > **Fiscal notes** > **All customer fiscal notes** with the business type **Unprocessed**. The original invoice appears as a fiscal reference on the posted document.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
