---
title: Purchase invoice posting for Latin America
description: This article provides information about the purchase invoice posting process for Latin America. 
author: Fhernandez0088
ms.date: 05/24/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Purchase invoice posting for Latin America

You can add the necessary information for Latin American countries when you post an invoice in an extended LATAM section. Invoice types include:
- Purchase orders
- Invoice journals
- Project invoices
- Invoice register

## Prerequisites

Before you post an invoice, configure the following:

- The LATAM globalization feature must be enabled
- A Country/region that's supported in the LATAM globalization expansion
- The entities involved in transactions including legal entities and vendors
- The LATAM tax and legal information in thoe entities required for purchase invoice transactions
- Document classes as purchase invoices
- The sales point for the document classes
- Document class types as purchase invoices
- The items to be added in the transaction
- A project with a contract

## Post an invoice from a purchase order with LATAM information

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders** and create a new purchase order.
2. Select a vendor and then select **OK**.
3. Enter the item lines, save your changes and then generate a new invoice.
4. Select **Post**.
5. In the **LATAM** section, select a document class ID and then complete the rest of the required fields according to the document class configuration.
6. Select a sales point prefix or enter a value manually.
7. Complete the document number and then select **Post**.

## Post an invoice journal with LATAM information

1. Go to **Accounts payable** > **Invoices** > **Invoice journal**
2. Create a new line with a journal name configured as a vendor invoice recording and then select **Lines**.
3. Select a vendor and enter a value on the vendor line.
4. Select an offset account.
5. On the LATAM tab, in the **LATAM** section, enter a value in the **Document class Id.** field.
6. Select a sales point prefix.
7. Complete the document number if it's required by the document class configuration.
8. Select the document date and due date.
9. Complete the **Additional data** fields when required by the document class configuration.
10. Post the invoice.	

## Post an invoice from a project purchase order with LATAM information

1. Go to **Project management and accounting** > **Projects** > **All projects** and select a project.
2. Select **Item tasks** > **Purchase orders**, and create a new purchase order.
3. Select a vendor and then select **OK**.
4. Enter the item lines and confirm the order.
5. Save and generate a new invoice and then select **Post**.
6. In the **LATAM** section, select a document class ID and complete the rest of the required fields according to the document class configuration.
7. Select a sales point prefix or enter a value manually.
8. Complete the document number and then select **Post**.

## Post a vendor invoice from the invoice register

1. Go to **Accounts payable** > **Invoices** > **Invoice register**
2. Create a new line with a journal name configured as an **Invoice register**, and the select **Lines**.
3. Select a vendor and enter a value for the vendor line.
4. On the **LATAM** tab, in the **LATAM** section, enter a value in the **Document class Id.** field.
5. Select a sales point prefix.
6. Complete the document number if it;s required by the document class configuration.
7. Select the document date and due date.
8. Complete the **Additional data** fields when required by the document class configuration.
9. Post the invoice.
	
