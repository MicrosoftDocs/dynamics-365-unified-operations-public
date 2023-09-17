---
title: Sales invoice posting for Latin America
description: This article provides information about the process of posting sales invoices for Latin America.
author: Fhernandez0088
ms.date: 03/28/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Sales invoice posting for Latin America

[!include [banner](../includes/banner.md)]

You can add the information that's required for Latin American countries/regions when you post an invoice in an extended **LATAM** section to the following documents:

- Sales orders
- Project invoices
- Free text invoices

## Prerequisites

Before you post an invoice, the following prerequisites must be met:

- The **LATAM globalization** feature must be enabled.
- The primary address must be in a country/region that's supported in the LATAM globalization expansion.
- Configure the entities that are involved in transactions, including legal entities and customers.
- Configure the LATAM tax and legal information in the entities that are required for invoice transactions.
- Configure document classes as sales invoices.
- Configure the sales point for the document classes.
- Configure a document class type as a sales invoice.
- Configure the items that will be added to a transaction.
- Create and configure a project that has a contract.

## Post a sales invoice from a sales order with LATAM information

Follow these steps to post a sales invoice from a sales order that includes LATAM information.

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**.
2. Create a sales order.
3. Select a customer, and enter the appropriate line items.
4. Save the new sales order, and generate an invoice.
5. In the **LATAM** section of the invoice, select a document class ID, and complete the remaining required fields according to the document class configuration.
6. Select or enter a sales point prefix.
7. Complete the document number.
8. Select **OK** to post the transaction.

## Post a free text invoice

Follow these steps to post a free text invoice that includes LATAM information.

1. Go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
2. Create a free text invoice.
3. Select a customer, and add invoice lines that have the corresponding tax codes and prices.
4. On the **Header** tab, in the **LATAM** section, in the **Document class Id.** field, select a value.
5. Select a sales point prefix.
6. Complete the document number if it's required by the document class configuration.
7. Select the document date and due date.
8. Complete the **Additional data** fields as required by the document class configuration.
9. Post the invoice.

## Post a project invoice

Follow these steps to post a project invoice that includes LATAM information.

1. Go to **Project management and accounting** \> **Projects** \> **All projects**.
2. Select a project, and then select **Project invoice proposals**.
3. Create an invoice proposal.
4. Select a project and a transaction to post, and then select **OK**.
5. On the Action Pane, select **Post**.
6. On the **Posting** page, on the **LATAM** tab, in the **Document class Id.** field, select a value.
7. Select a sales point prefix.
8. Enter the document number if it's required by the document class configuration.
9. Select the document date and due date.
10. Complete the **Additional data** fields as required by the document class configuration.
11. Select **OK** to post the invoice.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
