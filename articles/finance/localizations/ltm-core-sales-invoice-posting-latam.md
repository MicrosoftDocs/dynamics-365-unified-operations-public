---
title: Sales invoice posting for Latin America
description: This article provides information about the the process of posting sales invoices for Latin America. 
author: Fhernandez0088
ms.date: 03/28/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Sales invoice posting for Latin America

[!include [banner](../includes/banner.md)]

You can add necessary information needed for Latin American countries when you post an invoice in an extended LATAM section to the following documents:

- Sales orders
- Project invoices
- Free text invoices

## Prerequisites

Before you post an invoice, the following prerequisites must be met:

- The **LATAM globalization** feature must be enabled.
- The primary address of the country/region must be located in a country supported in the LATAM globalization expansion.
- Configure the entities involved in transactions, including legal entities and customers.
- Configure the LATAM tax and legal information in those entities that are required for invoice transactions.
- Configure document classes as sales invoices.
- Configure the sales point for the document classes.
- Configure a document class type as a sales invoice.
- Configure the items to be added to a transaction.
- Create and configure a project with a contract.

## Post a sales invoice from a sales order with LATAM information
Complete the following steps to post a sales invoice from a sales order wtih LATAM information included.

1. Go to **Accounts receivable** > **Orders** > **All sales orders** and create a new sales order.
2. Select a customer and enter the appropriate line items.
3. Save the new sales order and generate an invoice.
4. In the **LATAM** section of the invoice, select a document class ID and complete the rest of the required fields according to the document class configuration.
5. Select or enter a sales point prefix.
6. Complete the document number.
7. Select ok to post the transaction.

## Post a free text invoice

Complete the following steps to post a free text invoice with LATAM information included. 

1. Go to **Accounts receivable** > **Invoices** > **All free text invoices**.
2. Create a new free text invoice and select a customer.
3. Add invoice lines with the corresponding tax codes and prices.
5. On the **Header** tab, in the **LATAM** section, in the **Document class Id.** field select a value.
7. Select a sales point prefix.
8. Complete the document number if it's required by the document class configuration.
9. Select the document date and due date.
10. Complete the **Additional data** fields as required by the document class configuration.
11. Post the invoice.

## Post a project invoice

Complete the following steps to post a project invoice with LATAM information included.

1. Go to **Project management and accounting** > **Projects** > **All projects**.
2. Select a project and then select **Project invoice proposals**.
3. Create a new invoice proposal.
4. Select a project and a transaction to be posted, and then select **OK**.
5. On the Action Pane, select **Post**.
6. On the **Posting** page, on the **LATAM** tab, in the **Document class Id.** field, select a value.
7. Select a sales point prefix.
8. Enter the document number if it's required by the document class configuration.
9. Select the document date and due date.
12. Complete the **Additional data** fields as required by the document class configuration.
13. Select **OK** to post the invoice.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]


