---
title: Purchase a taxable item from an unregistered vendor (India)
description: Learn about creating a purchase order that includes a taxable item for an unregistered vendor, including a step-by-step process.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/01/2026
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3
---

# Purchase a taxable item from an unregistered vendor (India)

[!include[banner](../../includes/banner.md)]

This article shows you how to create a purchase order that includes a taxable item for an unregistered vendor in India.

1. Create a purchase order that includes a taxable item.
1. On the purchase order lines, select **Tax information**, and make sure that the tax information for the vendor tax is empty.
1. Validate the tax details of a purchase order.
1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document** to review the calculated taxes.
  
   **Example:**
   - **Taxable value:** 10,000.00
   - **CGST:** 10 percent; **Reverse charge percentage:** 100 percent
   - **SGST:** 10 percent; **Reverse charge percentage:** 100 percent

   > [!NOTE]
   > The **Party GST Registration Number** field is blank on the **Purchase order** FastTab. This value means that the dealer isn't registered as a dealer.

1. Close the page.
1. Select **Confirm**.
1. Post the purchase invoice.

   1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
   1. In the **Default quantity for lines** field, select **Ordered quantity**.
   1. Enter the invoice number.
   1. Select **Post**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**.
1. On the **Overview** tab, select **Tax document**.
1. Select the **Purchase invoice** FastTab.
1. Select the **Setup** tab.

   > [!NOTE]
   > The system generates the **Transaction ID** from the number sequence that you defined for the reference **GST invoice** in the **Tax information** for the **Reference number sequence group**.

1. Close the page.
1. Select **Voucher** to validate the financial entries.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
