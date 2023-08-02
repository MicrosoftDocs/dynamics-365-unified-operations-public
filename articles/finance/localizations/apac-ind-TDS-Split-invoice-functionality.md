---
# required metadata

title: Split invoice functionality
description: This article describes the setup and functionality for splitting invoices by delivery address and tax account number (TAN).
author: kailiang
ms.date: 02/12/2021
ms.topic: article
ms.prod: 

ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# 
# ms.tgt_pltfrm: 
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# Split invoice functionality

[!include [banner](../includes/banner.md)]

This article describes the setup and functionality for splitting invoices by delivery address and tax account number (TAN).

On the **Accounts payable parameters** page, on the **General** tab, select the **Product receipt** or **Invoice** checkbox to post and split a product receipt or invoice that has different delivery addresses and TANs on the **Purchase order** page. The posted invoice will then be split by delivery address and TAN.

On the **Summary update** tab, on the **Split based on** FastTab, in the **Delivery information** row, set the **Confirmation**, **Picking list**, **Packing slip**, or **Invoice** option to **Yes** to post and split a confirmation, picking list, packing slip, or invoice where different delivery addresses and TANs are defined for different invoice lines on the **Sales order** page. The invoice will be split first by delivery address and then by TAN.

> [!IMPORTANT]
> - If no options for **Delivery information** are set to **Yes**, the invoice will be posted as a single invoice. No invoice splitting will occur.
> - To split and post a packing slip where the invoice lines have different delivery addresses and TANs, you must set the **Packing slip** option for **Delivery information** to **Yes**.
> - To split and post an invoice where the invoice lines have different delivery addresses and TANs, you must set the **Invoice** option for **Delivery information** to **Yes**.
> - To post an invoice where the invoice lines have different delivery addresses but the same TAN, set the **Invoice** option for **Delivery information** to **No**. The invoice will be split by delivery address.

## Example

In this example, the **Invoice** option for **Delivery information** is set to **Yes** on the **Summary update** tab of the **Accounts payable parameters** page. A purchase invoice is posted that has the following setup for delivery addresses and TANs on the lines:

- **Item line 1:** Delivery address 1, TAN-ABCD12345A
- **Item line 2:** Delivery address 1, TAN-ABCD12345A
- **Item line 3:** Delivery address 2, TAN-ABCE12345B
- **Item line 4:** Delivery address 3, TAN-ABCD12345A

In this case, the original invoice is split into two invoices and posted in the following way:

- Invoice 1 is posted for item line 1 and item line 2, because both lines have the same delivery address and TAN.
- Invoice 2 is posted for item line 3.
- Invoice 3 is posted for item line 4.
