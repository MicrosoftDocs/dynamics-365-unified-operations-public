---
title: Charges allocation on Bill of entry page for import orders
description: Learn about about charge allocation for import orders, including outlines on key changes introduced, enabling features, and creating purchase orders.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.date: 04/30/2026
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User 
ms.search.region: India
ms.search.validFrom: 2022-03-01
ms.search.form:
ms.dyn365.ops.version:
---

# Charges allocation on Bill of entry page for import orders

[!include [banner](../../includes/banner.md)]

For transactions that involve importing goods, customs duty and taxes are calculated based on a custom cost, insurance, and freight (CIF) value. You determine this value by adding freight and insurance charges to the value of the imported goods. Customs authorities also refer to the custom CIF value as the assessable value. They determine this value when you submit a bill of entry (BOE).

Generally, actual freight and insurance charges are added to the value of goods to determine the assessable value. Sometimes, the quantity of goods that are received against an import order or a purchase order differs from the actual quantity that was ordered. This difference affects the actual amount of charges that are incurred for freight and insurance, and the assessable value that is used to determine the customs duty and goods and services tax (GST). Therefore, this feature lets you edit the charge amount at the BOE stage and allocate charges to all BOE line items on a net amount or quantity basis. This capability will help you match the BOE assessable value with the value that customs authorities determine, for taxation purposes.

Currently, the system applies freight and insurance charges to the full value or quantity of all the line items on an import order or purchase order to determine the assessable value. However, importers often receive only a partial quantity of goods. In these cases, and the freight and insurance charges can't be edited on the **Bill of entry** page. Additionally, these partial receipts also cause the assessable value that is used to determine duties and taxes to be incorrect. Therefore, the new feature lets you edit charges on the **Bill of entry** page and allocate the edited charges to selected BOE lines. This capability will help you allocate actual charges to the line items and determine the correct assessable value as it's determined by customs authorities.

> [!NOTE]
> The government determines the assessable value when you submit a BOE. Therefore, allocate charges on the **Bill of entry** page instead of the **Import order** or **Purchase order** page.

## Key changes introduced

The new experience introduces the following key changes:

- The system automatically copies charges that you define on the import order header to the **Bill of entry** page.
- You can define or edit charges on the **Bill of entry** page.
- You must allocate charges on the **Bill of entry** page instead of at the import order level.
- You receive a warning if you try to allocate header charges on import order lines.
- The charge allocation option on the **Bill of entry** page is available only for the **Fixed charge** calculation category, because customs authorities consider charges only on an actual or notional percentage basis.
- You can edit charges that you allocate on BOE lines.
- The system automatically calculates the assessable value for every BOE line after you add charges.
- When determining the assessable value, the system considers either the actual charge amount or charge percentage of the assessable value, whichever is lower.
- The system copies charges that you post on the **Bill of entry** page to the **Posting invoice** page.
- Although you can edit the charges on the **Posting invoice** page, your changes don't affect the assessable value of items on the import order.
- You can post-import an invoice on the following bases:

  - One BOE > One invoice
  - One BOE > One product receipt > One invoice
  - One BOE > Multiple receipts > One invoice
  - One BOE > Multiple receipts > Multiple invoices

- You can apply charges to the BOE in the company currency and a foreign currency.

## Create a purchase (import) order

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
1. Create a purchase order that has a foreign vendor account and a port ID.
1. Add multiple line items.
1. On the purchase order header, enter the charges for freight and insurance.

   > [!NOTE]
   > If you allocate charges on the purchase order lines, you receive a warning when you select **Allocation**.
   >
   > :::image type="content" source="../media/allocate-charges-to-order-lines.png" alt-text="Screenshot of the warning on the Allocate charges to order lines pane.":::  

1. Save the record.
1. Select **Tax information**.
1. Select the Harmonized System of Nomenclature (HSN) code and the customs tariff code, and then select **OK**.
  
## Validate the tax details

1. On the **Purchase order** page, on the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.
1. On the **Tax details** FastTab, review the tax calculation.
1. Select **Close**.
1. Select **Confirm**.

## Update the invoice registration

1. On the **Import order** page, on the Action Pane, on the **Customs** tab, in the **Maintain** group, select **Invoice registration**.
1. Select **Import invoice number**.
1. Edit the quantity that you received, and then select **Update**.

## Post the BOE

1. On **Import order**, on the Action Pane, on the **Customs** tab, in the **Generate** group, select **Bill of entry**.
1. Select **Import invoice number**.
1. Select **Bill of entry number**.
1. In the **Settings** group, select **Maintain charges**.

   :::image type="content" source="../media/bill-of-entry-page.png" alt-text="Screenshot of the Bill of entry page with Maintain charges.":::

   The system automatically enters charges that you define on the purchase order header under **Maintain charges** on the **Bill of entry** page.

1. Edit the charges as needed.

   :::image type="content" source="../media/maintain-charges-page.png" alt-text="Screenshot of the Maintain charges page to edit.":::

1. On the **Bill of entry** page, on the Action Pane, select **Allocate charges**.

   The system allocates charges to BOE lines. You can allocate charges based on the following options:

     - Net amount
     - Quantity
  
   :::image type="content" source="../media/charges-allocation-field.png" alt-text="Screenshot of the Charge allocation field on the Allocate charges to order lines pane.":::

1. Review the assessable value for each BOE line.

   :::image type="content" source="../media/assessable-value.png" alt-text="Screenshot of BOE lines with the Assessable value field.":::

   > [!NOTE]
   > You can still edit charges on the BOE lines.

1. Save your changes, and then post the BOE.

## Post the purchase invoice

1. On **Bill of entry**, on the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**. By default, the value of the **Quantity for lines** field equals the value of the **Bill of entry quantity** field. You can select the product receipt quantity as required. You can continue to edit charges on lines on the **Posting invoice** page without affecting the posted assessable value.
1. Enter the invoice number.
1. On the Action Pane, on the **Vendor invoice** tab, in the **Actions** group, select **Post** > **Post**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice** > **Overview** > **Voucher**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
