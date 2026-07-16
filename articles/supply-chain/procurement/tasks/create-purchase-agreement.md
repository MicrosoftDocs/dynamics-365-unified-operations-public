---
title: Create a purchase agreement
description: Learn how to create a purchase agreement, which is typically done by purchasing managers, including a step-by-step process.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchAgreement, PurchAgreementCreate, InventItemIdLookupSimple, AgreementConfirmRunForm, PurchAgreementHistory 
ms.topic: how-to
ms.date: 05/21/2026
ms.custom: 
  - bap-template
---

# Create a purchase agreement

[!include [banner](../../includes/banner.md)]

This article shows you how to create a purchase agreement. Typically, a purchasing manager completes this procedure. Set up purchase agreement classifications before you start. After you create an agreement, use it when you create a purchase order. This action copies the purchase agreement conditions to the header and to any lines in the order that the agreement affects.

## Create a new purchase agreement

1. Go to **Procurement and sourcing** > **Purchase agreements** > **Purchase agreements**.
1. Select **New**.
1. In the **Vendor account** field, select the drop-down menu and select the row of the desired record.
1. In the **Purchase agreement classification** field, select the drop-down menu and select the row of the desired record.
1. Expand the **General** FastTab.
1. In the **Expiration date** field, enter a date. This expiration date is the default for all commitment lines and determines how long each specific commitment is valid.  

1. In the **Document title** field, type a name for your purchase agreement.

    - Leave the **Default commitment** field set to **Product quantity commitment** (or change it if it's not set to this).  
    - The default commitment value determines your options on the agreement lines. If you need a new commitment type when you're creating the agreement lines, change the default commitment on the header. There are four types of commitments:
        - *Product quantity commitment* – for a specific quantity of a product.
        - *Product value commitment* – for a specific currency amount of a product.
        - *Product category value commitment* – for a specific currency amount in a procurement category where the amount can be for a catalog item or a non-catalog item.
        - *Value commitment* – for a specific currency amount which any product or any procurement category can fulfill.  

1. Select **OK**.

## Add a commitment

1. Select **Add line**.
1. In the **Item number** field, select the desired record from the drop-down menu.
1. In the **Quantity** field, enter a number. This number is the total quantity that you agree to buy from your vendor.  
1. In the **Unit price** field, enter a number.
1. Expand the **Line details** section.
1. Set the **Max is enforced** option to *Yes*. The **Max is enforced** option limits the use of the commitment. You can only purchase up to the quantity specified in the **Quantity** field for the line.

## Add header conditions

1. On the Action Pane, select **Options**.
1. Select **Change view**.
1. Select **Header view**.
1. Expand the **Terms** section.
1. In the **Method of payment** field, select the desired record in the drop-down menu. The payment terms from the vendor account appear here by default.  
1. In the **Mode of delivery** field, select the desired record in the drop-down menu.
1. In the **Delivery terms** field, select the drop-down button to open the lookup.

## Confirm and activate the agreement

1. On the Action Pane, select **Purchase agreement**.
1. Select **Confirmation**. Set the **Mark agreement as effective** option to **Yes**.  
1. Select **OK**.
1. On the Action Pane, select **Purchase agreement**.
1. Select **Purchase agreement confirmations**. The **Preview/Print** option generates a document for the purchase agreement that you can print or send to the vendor. If you update the agreement later and reconfirm it, both versions appear here.  
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
