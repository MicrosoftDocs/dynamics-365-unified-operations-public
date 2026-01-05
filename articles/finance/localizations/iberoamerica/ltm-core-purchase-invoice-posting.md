---
title: Purchase invoice posting for Latin America
description: Learn about the purchase invoice posting process for Latin America, including prerequisites and an outline on posting an invoice from a purchase order.
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Purchase invoice posting for Latin America

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](../includes/does-not-apply-to.md)]

You can add the necessary information for Latin American countries/regions when you post invoices of the following types in an extended LATAM section:

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
1. Select a vendor, and then select **OK**.
1. Enter the item lines, save your changes, and then generate a new invoice.
1. Select **Post**.
1. In the **LATAM** section, select a document class ID, and then complete the remaining required fields according to the document class configuration.
1. Select a sales point prefix, or manually enter a value.
1. Complete the document number, and then select **Post**.

## Post an invoice journal with LATAM information

1. Go to **Accounts payable** \> **Invoices** \> **Invoice journal**.
1. Create a line that uses a journal name that's configured as a vendor invoice recording. Then select **Lines**.
1. Select a vendor, and enter a value on the vendor line.
1. Select an offset account.
1. On the **LATAM** tab, in the **LATAM** section, in the **Document class Id.** field, enter a value.
1. Select a sales point prefix.
1. Complete the document number if it's required by the document class configuration.
1. Select the document date and due date.
1. Complete the **Additional data** fields as required by the document class configuration.
1. Post the invoice.	

## Post an invoice from a project purchase order with LATAM information

1. Go to **Project management and accounting** \> **Projects** \> **All projects**, and select a project.
1. Select **Item tasks** \> **Purchase orders**, and create a purchase order.
1. Select a vendor, and then select **OK**.
1. Enter the item lines, and confirm the order.
1. Save and generate a new invoice, and then select **Post**.
1. In the **LATAM** section, select a document class ID, and complete the remaining required fields according to the document class configuration.
1. Select a sales point prefix, or manually enter a value.
1. Complete the document number, and then select **Post**.

## Post a vendor invoice from the invoice register

1. Go to **Accounts payable** \> **Invoices** \> **Invoice register**.
1. Create a line that uses a journal name that's configured as an invoice register. Then select **Lines**.
1. Select a vendor, and enter a value for the vendor line.
1. On the **LATAM** tab, in the **LATAM** section, in the **Document class Id.** field, enter a value.
1. Select a sales point prefix.
1. Complete the document number if it's required by the document class configuration.
1. Select the document date and due date.
1. Complete the **Additional data** fields as required by the document class configuration.
1. Post the invoice.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
