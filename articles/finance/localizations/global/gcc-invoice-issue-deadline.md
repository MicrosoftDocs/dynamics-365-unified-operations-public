---
title: Invoice issue deadline (GBL)
description: Learn how to calculate the due dates for issuing customer invoices, including prerequisites and a step-by-step process for setup.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.search.region: GBL
ms.search.validFrom: 2020-07-03
---
# Invoice issue deadline (GBL)

[!include [banner](../../includes/banner.md)]

This article explains how to configure Microsoft Dynamics 365 Finance so that it complies with legal requirements for the invoice issue deadline. For example, legislation can require that you issue an invoice no later than the fifteenth day of the month after the month when the sale occurs.

## Prerequisites

In the **Feature management** workspace, turn on the **Invoice issue deadline availability** feature. This feature is available for all countries and regions in version 10.0.15 and later.

For more information about how to turn on features, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

> [!NOTE]
> This feature is the same as the out-of-box feature for European Union (EU) countries and regions. For more information, see [Invoice issue deadline](../europe/emea-invoice-issue-deadline.md).

## Setup

Follow these steps to set up the functionality for the invoice issue deadline.

1. Go to **General ledger** > **Ledger setup** > **Date intervals**.
1. On the **Date intervals** page, create a date interval.
1. On the **General** FastTab, in the **Interval start** and **Interval end** sections, set the fields to appropriate values.

    :::image type="content" source="../media/gcc-invoice-issue-deadline-date-interval.jpg" alt-text="Screenshot of the Date intervals page.":::

    > [!NOTE]
    > The preceding illustration shows an interval of 15 days. If you set up the date interval in this way, the deadline for issuing the invoice is the fifteenth day of the month after the month when the packing slip is issued. If you leave the **To date period type** and **To date Start/End** fields in the **Interval end** section blank, the deadline for issuing the invoice is the fifteenth day after the packing slip is issued.

1. Go to **Tax** > **Setup** > **Foreign trade**.
1. On the **Foreign trade parameters** page, on the **Country/region properties** tab, select **New**.
1. On the line for the new record, in the **Party country/region** field, select a country or region. Then, in the **Country/region type** field, select the type of country or region. For example, select **Domestic**.

    :::image type="content" source="../media/gcc-invoice-issue-deadline-Foreign-trade-parameters.jpg" alt-text="Screenshot of the Foreign trade parameters page.":::

1. Go to **Accounts receivable** > **Setup** > **Set up calculation for invoice issue date** or **Accounts payable** > **Setup** > **Set up calculation for invoice issue date**.
1. On the **Set up calculation for invoice issue due date** page, create a record.
1. Set the **Country/region type** and **Date interval code** fields.

    In the following illustration, the validation for the invoice issue deadline applies to posted packing slips or product receipts that have a domestic address.

    :::image type="content" source="../media/gcc-invoice-issue-deadline-calculation-for-invoice-issue-deadline.jpg" alt-text="Screenshot of the Set up calculation for invoice issue due date page.":::

1. Go to **Accounts receivable** > **Setup** > **Parameters**.
1. On the **Accounts receivable parameters** page, on the **Updates** tab, on the **Invoice date control** FastTab, in the **Invoice date control** field, select one of the following values:

    - **None** – Date control isn't run.
    - **Warning** – The invoice is posted, but a warning message appears afterward.
    - **Error** – The invoice isn't posted, and an error message appears.

    > [!NOTE]
    > If you select **Warning** or **Error**, the validation applies to sales invoices that you posted based on packing slips.

    :::image type="content" source="../media/gcc-invoice-issue-deadline-ar-parameters.jpg" alt-text="Screenshot of the Accounts receivable parameters page.":::

Based on the settings, the system enters a value in the **Invoice issue due date** field in the packing slip journal and the product receipt journal. You can view all the packing slips that aren't yet invoiced by going to **Sales and marketing** > **Sales orders** > **Order shipping** > **Packing slip not invoiced**. You can view all the product receipts that aren't yet invoiced by going to **Procurement and sourcing** > **Purchase orders** > **Receiving products** > **Product receipt not invoiced**.

> [!NOTE]
> If you set the **Invoice date control** field on the **Accounts receivable parameters** page to **None**, the system leaves the **Invoice issue due date** field in the packing slip journal blank.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
