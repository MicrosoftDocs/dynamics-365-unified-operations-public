---
title: Import services that have GST
description: Learn how to import services that have Goods and Services Tax (GST), including a step-by-step process for validating tax details.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/01/2026
ms.reviewer: johnmichalak 
audience: Application User 
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Import services that have GST

[!include [banner](../../includes/banner.md)]

Complete the procedures in this article to import services that have Goods and Services Tax (GST).

1. Go to **Accounts payable** \> **Invoices** \> **Invoice journal**.
1. Create a journal.
1. Select **Lines**.
1. Create a purchase of services for a foreign vendor, and save the record.
1. Select **Tax information**.
1. On the **GST** FastTab, in the **SAC** field, select a value.
1. Select the **Vendor tax information** FastTab.
1. Select **OK**.

### Validate the tax details

1. Select **Tax document**.

    **Example**

    - **Taxable value:** 20,000.00
    - **IGST:** 20 percent
    - **Normal exchange rate:** 1 USD = 60 INR

1. Select **Close**.
1. Select **Post** \> **Post**.
1. Close the message that you receive.
1. Select **Inquiries** \> **Voucher**.

:::image type="content" source="../media/Annotation-2019-05-21-104142.png" alt-text="Screenshot of the voucher transaction results for the imported service with GST.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
