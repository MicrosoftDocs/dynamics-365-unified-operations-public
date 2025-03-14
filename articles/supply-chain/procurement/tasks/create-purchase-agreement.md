---
title: Create a purchase agreement
description: Learn how to create a purchase agreement, which is typically done by purchasing managers, including a step-by-step process.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchAgreement, PurchAgreementCreate, InventItemIdLookupSimple, AgreementConfirmRunForm, PurchAgreementHistory 
ms.topic: how-to
ms.date: 11/18/2024
ms.custom: 
  - bap-template
---

# Create a purchase agreement

[!include [banner](../../includes/banner.md)]

This article guides you through the creation of a purchase agreement. This procedure would typically be done by a purchasing manager. You need to have set up purchase agreement classifications before you start. Once you've created an agreement you can use it when you create a purchase order, and this will copy the purchase agreement conditions to the header and to any lines in the order that are affected by the agreement.

## Create a new purchase agreement

1. Go to **Procurement and sourcing** \> **Purchase agreements** \> **Purchase agreements**.
2. Select **New**.
3. In the **Vendor account** field, select the drop-down menu and select the row of the desired record.
4. In the **Purchase agreement classification** field, select the drop-down menu and select the row of the desired record.
5. Expand the **General** FastTab.
6. In the **Expiration date** field, enter a date. This expiration date will be the default for all commitment lines and will determine how long each specific commitment is valid.  

7. In the **Document title** field, type a name for your purchase agreement.

    - Leave the **Default commitment** field set to **Product quantity commitment** (or change it if it's not set to this).  
    - The default commitment value determines your options on the agreement lines. If you need a new commitment type when you're creating the agreement lines, you need to change the default commitment on the header. There are four types of commitments:
        - *Product quantity commitment* – for a specific quantity of a product.
        - *Product value commitment* – for a specific currency amount of a product
        - *Product category value commitment* – for a specific currency amount in a procurement category where the amount can be for a catalog item or a non-catalog item
        - *Value commitment* – for a specific currency amount which can be fulfilled by any product or by any procurement category.  

8. Select **OK**.

## Add a commitment

1. Select **Add line**.
2. In the **Item number** field, select the desired record from the drop-down menu.
3. In the **Quantity** field, enter a number. This is the total quantity that you have agreed to buy from your vendor.  
4. In the **Unit price** field, enter a number.
5. Expand the **Line details** section.
6. Set the **Max is enforced** option to *Yes*. The **Max is enforced** option limits the use of the commitment. You can only purchase up to the quantity that's specified in the **Quantity** field for the line.  

## Add header conditions

1. On the Action Pane, select **Options**.
2. Select **Change view**.
3. Select **Header view**.
4. Expand the **Terms** section.
5. In the **Method of payment** field, select the desired record in the drop-down menu. The payment terms from the vendor account are shown here by default.  
6. In the **Mode of delivery** field, select the desired record in the drop-down menu.
7. In the **Delivery terms** field, select the drop-down button to open the lookup.

## Confirm and activate the agreement

1. On the Action Pane, select **Purchase agreement**.
2. Select **Confirmation**. Set the **Mark agreement as effective** option to **Yes**.  
3. Select **OK**.
4. On the Action Pane, select **Purchase agreement**.
5. Select **Purchase agreement confirmations**. The **Preview/Print** option allows you to generate a document for the purchase agreement which you can then print or send to the vendor. If you update the agreement later on and reconfirm it, both versions will be shown here.  
6. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
