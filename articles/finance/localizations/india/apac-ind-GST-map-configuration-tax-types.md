---
title: Map configuration tax types - Customs
description: Learn how to map configuration tax types for customs, including outlines on customs tax types, the GST tax types, and defining tax periods.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak 
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Map configuration tax types - Customs

[!include [banner](../../includes/banner.md)]

## Customs tax type 

### Define the tax type mapping

1. Go to **Tax** > **Setup** > **Tax Configuration** > **Tax Setup**.
1. Select a company, and then select **Setup**.
1. Select the **Customs** node.
1. On the **Tax type mapping** tab, in the **Tax type** field, select **Customs**.

    :::image type="content" source="../media/custom-duty.png" alt-text="Screenshot of the Customs tax type mapping.":::

### Define the tax period

For each node for the tax component, on the **Reporting** tab, in the **Period** field, select a value.

:::image type="content" source="../media/reporting-period.png" alt-text="Screenshot of the reporting period field.":::

### Define main accounts

1. On the **Accounting** tab, on the **Conditions** FastTab, select **Add**.
1. In the **Import Order** field, select a value.
1. In the **Export order** field, select a value.
1. Save the record.
1. On the **Values** FastTab, in the **Main account** field, select a value.

    > [!NOTE]
    > The list of accounts is dynamically generated, based on the posting profile from the configuration. The selected main account should have the **Customs** posting type.

    :::image type="content" source="../media/main-accounts.png" alt-text="Screenshot of the main accounts settings.":::

1. Select the **IGST CUS** node.
1. On the **Values** FastTab, in the **Main account** field, select a value.

    > [!NOTE]
    > The main account that you select for **Customs duty accrual** should be the same account that is selected for the **Customs duty accrual** account for the **GST** \> **IGST** node.

    :::image type="content" source="../media/IGST-CUS.png" alt-text="Screenshot of the main account for the IGST CUS node.":::

## GST tax type

### Define the tax type mapping

1. Go to **Tax** > **Setup** > **Tax Configuration** > **Tax Setup**.
1. Select a company, and then select **Setup**.
1. Select the **GST** node.
1. On the **Tax type mapping** tab, in the **Tax type** field, select **GST**.

    :::image type="content" source="../media/gst-tax-type-mapping.png" alt-text="Screenshot of the GST tax type mapping.":::

### Define the tax period

For each node for the tax component, on the **Reporting** tab, in the **Period** field, select a value.

:::image type="content" source="../media/gst-reporting-period.png" alt-text="Screenshot of the GST reporting period field.":::

### Define main accounts

1. On the **Accounting** tab, on the **Conditions** FastTab, select **Add**.
1. In the **GST Registration Number** field, select a value.
1. Save the record.
1. On the **Values** FastTab, in the **Main account** field, select a value.

    > [!NOTE]
    > The list of accounts is dynamically generated, based on the posting profile from the configuration.

    :::image type="content" source="../media/gst-main-accounts.png" alt-text="Screenshot of the GST main accounts settings.":::

> [!NOTE]
> You can define tax main accounts at the level of the tax type or at the level of the tax component. The value at the tax component level overrides the value at the tax type level. If you leave the field blank for a posting type at the tax component level, the corresponding value from the tax type level is used for posting. Set up the tax accounts at the tax component level per registration.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
