---
title: Purchases from unregistered vendors
description: Learn how to work with purchase requisitions for unregistered vendors, including processes for creating and approving purchase requisitions.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.date: 04/30/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak 
audience: Application User 
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Purchases from unregistered vendors

[!include [banner](../../includes/banner.md)]

## Create a purchase requisition

1. Go to **Procurement and sourcing** > **Purchase requisitions** > **All purchase requisitions**.
1. Create a purchase requisition for a taxable item, and save the record.

    The **Tax information** button becomes available.

    :::image type="content" source="../media/Annotation-2019-05-15-153813.png" alt-text="Screenshot of the Purchase requisitions page.":::

1. Select **Tax information**.
1. On the **GST** FastTab, validate the default values for the following fields:

    - **GSTIN/GDI/UID**
    - **HSN code**
    - **ITC category:** Input
    - **Service category:** Inward

1. Select the **Vendor tax information** FastTab.

    > [!NOTE]
    > Because the **Tax information** field is blank for the vendor, the dealer is an unregistered dealer.

1. Select **OK**.

1. On the Action Pane, on the **Purchase Requisition** tab, in the **Summary** group, select **Tax document** to review the calculated taxes.

    What you see might resemble the following example:

    - **Taxable value:** 1,000.00
    - **CGST:** 5 percent
    - **SGST:** 10 percent

    :::image type="content" source="../media/Annotation-2019-05-15-161112.png" alt-text="Screenshot of the Tax document page, Tax details FastTab.":::

1. Select **Close**.
1. Select **Submit**.
1. Update the comment, and then select **Submit** to process the purchase requisition through a workflow.

## Approve the purchase requisition

1. Go to **Procurement and sourcing** > **Purchase requisitions** > **Purchase requisitions prepared by me**.
1. Select the purchase requisition, and then select **Actions** > **Approve**.
1. Update the comment, and then select **Approve**.

## Release the approved purchase requisition

1. Go to **Procurement and sourcing** > **Purchase requisitions** > **Release approved purchase requisition**.
1. Select the purchase requisition, and then select **New Purchase order**.
1. Close the message that you receive.

## Purchase order page

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
1. Select the purchase order.
1. On the **Purchase order lines** FastTab, select **Tax information**.
1. Select the **GST** FastTab.
1. Select the **Vendor tax information** FastTab.
1. Select **OK**.

## Validate the tax details

1. On the Action Pane, on the **Purchase** tab, in the **Tax group** group, select **Tax document** to review the calculated taxes.

    What you see might resemble the following example:

    - **Taxable value:** 1,000.00
    - **CGST:** 5 percent
    - **SGST:** 10 percent

    :::image type="content" source="../media/Annotation-2019-05-15-163603.png" alt-text="Screenshot of the Tax document page.":::

1. If you change any tax attributes after you create the order line, select **Recalculate** to recalculate the tax.
1. Select **Close**, and then select **Confirm**.

## Post the purchase invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Default quantity for lines** field, select **Ordered quantity**.
1. Enter the invoice number. Then, on the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** \> **Post**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. On the **Overview** tab, select **Voucher**.

The following illustration shows the financial entry for the purchase of goods.

:::image type="content" source="../media/Annotation-2019-05-15-165701.png" alt-text="Screenshot of the financial entry for the purchase of goods.":::

> [!NOTE]
> After the authority payment, claim the credit.

The following illustration shows the financial entry for the purchase of services.

:::image type="content" source="../media/Annotation-2019-05-15-165743.png" alt-text="Screenshot of the financial entry for the purchase of services.":::

The following illustration shows the financial entry on invoice payment.

:::image type="content" source="../media/Annotation-2019-05-15-165829.png" alt-text="Screenshot of the financial entry on invoice payment.":::

> [!NOTE]
> Select an appropriate Service Accounting Code (SAC).

The following illustration shows the financial entry for the purchase of goods where the ITC category is set to **Others**.

:::image type="content" source="../media/Annotation-2019-05-15-165912.png" alt-text="Screenshot of the financial entry for the purchase of goods where the ITC category is set to Others.":::

The following illustration shows the financial entry for the purchase of services where the service category is set to **Others**.

:::image type="content" source="../media/Annotation-2019-05-15-165958.png" alt-text="Screenshot of the financial entry for the purchase of services where the service category is set to Others.":::

The following illustration shows the financial entry on invoice payment.

:::image type="content" source="../media/Annotation-2019-05-15-170044.png" alt-text="Screenshot of the financial entry invoice payment.":::

The following illustration shows the financial entry for purchases where the load on inventory is set to 100 percent.

:::image type="content" source="../media/Annotation-2019-05-15-170133.png" alt-text="Screenshot of the financial entry for purchases where the load on inventory is set to 100 percent.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
