---
title: Split invoice functionality
description: Learn about the setup and functionality for splitting invoices by delivery address and tax account number (TAN), including an example.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/01/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
---

# Split invoice functionality

[!include [banner](../../includes/banner.md)]

This article describes the setup and functionality for splitting invoices by delivery address and tax account number (TAN).

On the **Accounts payable parameters** page, on the **General** tab, select the **Product receipt** or **Invoice** checkbox to post and split a product receipt or invoice that has different delivery addresses and TANs on the **Purchase order** page. The posted invoice is then split by delivery address and TAN.

On the **Summary update** tab, on the **Split based on** FastTab, in the **Delivery information** row, set the **Confirmation**, **Picking list**, **Packing slip**, or **Invoice** option to **Yes** to post and split a confirmation, picking list, packing slip, or invoice where different delivery addresses and TANs are defined for different invoice lines on the **Sales order** page. The invoice is split first by delivery address and then by TAN.

> [!IMPORTANT]
> - If you don't set any options for **Delivery information** to **Yes**, the invoice is posted as a single invoice. No invoice splitting occurs.
> - To split and post a packing slip where the invoice lines have different delivery addresses and TANs, set the **Packing slip** option for **Delivery information** to **Yes**.
> - To split and post an invoice where the invoice lines have different delivery addresses and TANs, set the **Invoice** option for **Delivery information** to **Yes**.
> - To post an invoice where the invoice lines have different delivery addresses but the same TAN, set the **Invoice** option for **Delivery information** to **No**. The invoice is split by delivery address.

## Example

In this example, set the **Invoice** option for **Delivery information** to **Yes** on the **Summary update** tab of the **Accounts payable parameters** page. Post a purchase invoice that has the following setup for delivery addresses and TANs on the lines:

- **Item line 1:** Delivery address 1, TAN-ABCD12345A
- **Item line 2:** Delivery address 1, TAN-ABCD12345A
- **Item line 3:** Delivery address 2, TAN-ABCE12345B
- **Item line 4:** Delivery address 3, TAN-ABCD12345A

In this case, the original invoice splits into two invoices and posts in the following way:

- Post invoice 1 for item line 1 and item line 2, because both lines have the same delivery address and TAN.
- Post invoice 2 for item line 3.
- Post invoice 3 for item line 4.
