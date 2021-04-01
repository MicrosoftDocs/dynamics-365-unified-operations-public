---
# required metadata

title: Purchase a taxable item from an unregistered vendor (India)
description: This topic walks you through creating a purchase order that includes a taxable item for an unregistered vendor.
author: ShylaThompson
ms.date: 03/20/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# keywords: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.suite: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: ralin
ms.dyn365.ops.version: 7.3
ms.search.validFrom: 2017-12-31

---

# Purchase a taxable item from an unregistered vendor (India)

[!include[banner](../includes/banner.md)]

This topic walks you through creating a purchase order that includes a taxable item for an unregistered vendor in India. 

1. Create a purchase order that includes a taxable item.
2. On the purchase order lines, click **Tax information**, make sure that the tax information for the vendor tax is empty.
3. Validate the tax details of a purchase order.
  1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, click **Tax document** to review the calculated taxes.
  
        **Example:**
        -   **Taxable value:** 10,000.00
        -   **CGST:** 10 percent; **Reverse charge percentage:** 100 percent
        -   **SGST:** 10 percent; **Reverse charge percentage:** 100 percent
    
        > [!NOTE]
        > The **Party GST Registration Number** field is blank on the **Purchase order** FastTab. This means that the dealer is not registered as a dealer.

7.  Close the page.
8.  Click **Confirm**.
9. Post the purchase invoice.
    1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
    2. In the **Default quantity for lines** field, select **Ordered quantity**.
    3. Enter the invoice number.
    4. Click **Post**.
10. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**.
11. On the **Overview** tab, click **Tax document**.
12. Click the **Purchase invoice** FastTab.
13. Click the **Setup** tab.
    > [!NOTE]
    > The **Transaction ID** will be generated from the number sequence that was defined for the reference **GST invoice** in the **Tax information** for the **Reference number sequence group**.

14. Close the page.
15. Click **Voucher** to validate the financial entries.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]