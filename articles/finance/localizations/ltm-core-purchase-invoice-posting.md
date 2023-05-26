---
title: Purchase invoice posting for Latin America
description: This article provides information about the purchase invoice posting process for Latin America.
author: Fhernandez0088
ms.date: 05/26/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Purchase invoice posting for Latin America

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

You can add the necessary information for Latin American countries when you post invoices of the following types in an extended LATAM section:

- Purchase orders
- Invoice journals
- Project invoices
- Invoice register

## Prerequisites

Before you post an invoice, the LATAM globalization feature must be enabled.

In addition, the following items must be configured:

- A country or region that's supported in the LATAM globalization expansion
- The entities that are involved in transactions, including legal entities and vendors
- In those entities, the LATAM tax and legal information that's required for purchase invoice transactions
- Document classes as purchase invoices
- The sales point for the document classes
- Document class types as purchase invoices
- The items that must be added in the transactions
- A project that has a contract

## Post an invoice from a purchase order with LATAM information

1. Go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**, and create a purchase order.
2. Select a vendor, and then select **OK**.
3. Enter the item lines, save your changes, and then generate a new invoice.
4. Select **Post**.
5. In the **LATAM** section, select a document class ID, and then complete the remaining required fields according to the document class configuration.
6. Select a sales point prefix, or manually enter a value.
7. Complete the document number, and then select **Post**.

## Post an invoice journal with LATAM information

1. Go to **Accounts payable** \> **Invoices** \> **Invoice journal**.
2. Create a line that uses a journal name that's configured as a vendor invoice recording. Then select **Lines**.
3. Select a vendor, and enter a value on the vendor line.
4. Select an offset account.
5. On the **LATAM** tab, in the **LATAM** section, in the **Document class Id.** field, enter a value.
6. Select a sales point prefix.
7. Complete the document number if it's required by the document class configuration.
8. Select the document date and due date.
9. Complete the **Additional data** fields as required by the document class configuration.
10. Post the invoice.	

## Post an invoice from a project purchase order with LATAM information

1. Go to **Project management and accounting** \> **Projects** \> **All projects**, and select a project.
2. Select **Item tasks** \> **Purchase orders**, and create a purchase order.
3. Select a vendor, and then select **OK**.
4. Enter the item lines, and confirm the order.
5. Save and generate a new invoice, and then select **Post**.
6. In the **LATAM** section, select a document class ID, and complete the remaining required fields according to the document class configuration.
7. Select a sales point prefix, or manually enter a value.
8. Complete the document number, and then select **Post**.

## Post a vendor invoice from the invoice register

1. Go to **Accounts payable** \> **Invoices** \> **Invoice register**.
2. Create a line that uses a journal name that's configured as an invoice register. Then select **Lines**.
3. Select a vendor, and enter a value for the vendor line.
4. On the **LATAM** tab, in the **LATAM** section, in the **Document class Id.** field, enter a value.
5. Select a sales point prefix.
6. Complete the document number if it's required by the document class configuration.
7. Select the document date and due date.
8. Complete the **Additional data** fields as required by the document class configuration.
9. Post the invoice.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
