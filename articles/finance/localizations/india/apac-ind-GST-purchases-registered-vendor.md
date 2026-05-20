---
title: Purchases from registered vendors
description: Learn how to work with purchases that are made by registered vendors, including processes for requesting quotation and quotation replies.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.date: 04/30/2026
ms.custom:
ms.reviewer: johnmichalak  
audience: Application User
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Purchases from registered vendors

[!include [banner](../../includes/banner.md)]

## Request for quotation

1. Go to **Procurement and sourcing** \> **Requests for quotations** \> **All requests for quotations**.
1. Create a record for a taxable item.
1. On the Action Pane, on the **Quotation** tab, in the **Process** group, select **Send**, and publish the request for quotation (RFQ) to the vendor collaboration module.
1. Select **OK**.
1. Close the message that you receive.
1. Close the **Request for quotation details** page.

:::image type="content" source="../media/Annotation-2019-05-15-171525.png" alt-text="Screenshot of the Request for quotation case page.":::

## Request for quotation replies

1. Go to **Procurement and sourcing** \> **Requests for quotations** \> **Request for quotation replies**.
1. Select the record.
1. On the Action Pane, on the **Reply** tab, in the **Maintain** group, select **Edit**.
1. On the Action Pane, on the **Reply** tab, in the **Process** group, select **Copy data to reply**.
1. On the **Purchase quotation lines** FastTab, select **Tax information**.

    :::image type="content" source="../media/Annotation-2019-05-15-171959.png" alt-text="Screenshot of the Tax information dialog box.":::

1. Select the **GST** FastTab.

    :::image type="content" source="../media/Annotation-2019-05-15-172049.png" alt-text="Screenshot of the GST FastTab.":::

1. Select the **Vendor tax information** FastTab.

    :::image type="content" source="../media/Annotation-2019-05-15-172136.png" alt-text="Screenshot of the Vendor tax information FastTab.":::

1. Select **OK**.

## Review and accept the tax details

1. On the Action Pane, on the **Reply** tab, in the **Financials** group, select **Tax document**.
1. Select the **GST** node.
1. Review the tax applicability, tax attributes, and tax calculation.

    What you see might resemble the following example:

    - **Taxable value:** 10,000.00
    - **CGST:** 10 percent
    - **SGST:** 10 percent

1. Select **Close**.
1. On the Action Pane, on the **Reply** tab, in the **Process** group, select **Accept**.
1. Select **OK**, and close the message that you receive.
1. Close the **Request for quotation reply** page.

## Purchase order page

1. Select **Accounts payable** \> **Purchase orders \> **All purchase orders**.
1. Select the purchase order that was created through the RFQ.
1. On the Action Pane, on the **Purchase order** tab, in the **Maintain** group, select **Edit**.
1. On the **Purchase order lines** FastTab, select **Tax information**.

    :::image type="content" source="../media/Annotation-2019-05-15-171959.png" alt-text="Screenshot of the Tax information dialog box.":::

1. Select the **GST** FastTab.

    :::image type="content" source="../media/Annotation-2019-05-15-172049.png" alt-text="Screenshot of the GST FastTab.":::

1. Select the **Vendor tax information** FastTab.

    :::image type="content" source="../media/Annotation-2019-05-15-172136.png" alt-text="Screenshot of the Vendor tax information FastTab.":::

1. Select **OK**.

## Review and confirm the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.
1. Review the tax applicability, tax attributes, and tax calculation.

    What you see might resemble the following example:

    - **Taxable value:** 10,000.00
    - **CGST:** 10 percent
    - **SGST:** 10 percent

1. Select **Close**, and then select **Confirm**.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Default quantity for lines** field, select **Ordered quantity**.
1. Enter the invoice number.
1. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** \> **Post**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. On the **Overview** tab, select **Voucher**.

The following illustration shows the financial entry for the purchase of goods.

:::image type="content" source="../media/Annotation-2019-05-15-173233.png" alt-text="Screenshot of the financial entry for the purchase of goods.":::

The following illustration shows the financial entry for the purchase of services.

:::image type="content" source="../media/Annotation-2019-05-15-173325.png" alt-text="Screenshot of the financial entry for the purchase of services.":::

The following illustration shows the financial entry for the purchase of goods where the ITC category is set to **Others**.

:::image type="content" source="../media/Annotation-2019-05-15-173406.png" alt-text="Screenshot of the financial entry for the purchase of goods where the ITC category is set to Others.":::

The following illustration shows the financial entry for the purchase of services where the service category is set to **Others**.

:::image type="content" source="../media/Annotation-2019-05-15-173457.png" alt-text="Screenshot of the financial entry for the purchase of services where the service category is set to Others.":::

The following illustration shows the financial entry for the purchase of goods where the load on inventory is set to 100 percent.

:::image type="content" source="../media/Annotation-2019-05-15-173548.png" alt-text="Screenshot of the financial entry for the purchase of goods where the load on inventory is set to 100 percent.":::

The following illustration shows the financial entry for the purchase of goods where the reverse charge is set to 100 percent.

:::image type="content" source="../media/Annotation-2019-05-15-173632.png" alt-text="Screenshot of the financial entry for the purchase of goods where the reverse charge is set to 100 percent.":::

The following illustration shows the financial entry for the purchase of goods where the reverse charge is set to 70 percent and the ITC category is set to **Others**.

:::image type="content" source="../media/Annotation-2019-05-15-173734.png" alt-text="Screenshot of the financial entry for the purchase of goods where the reverse charge is set to 70 percent and the ITC category is set to Others.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
