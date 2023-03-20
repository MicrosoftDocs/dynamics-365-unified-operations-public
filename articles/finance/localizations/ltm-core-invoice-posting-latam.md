---
title: Sales invoice posting for Latin America
description: This topic provides information about the Sales invoice posting process for Latin America. 
author: Fhernandez0088
ms.date: 03/20/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---
# Sales invoice posting for Latin America
You can add the information needed for Latin American countries when posting an invoice in an extended LATAM section:
Sales orders
Project invoices
Free text invoices
## Prerequisites
Before posting an invoice, you must configure some elements:
- The LATAM globalization feature must be enabled.
- Country/Region: a country supported in the LATAM globalization expansion.
- Configure the entities involved in transactions: legal entities and customers.
- Configure the LATAM tax and legal information in those entities required for invoice transactions.
- Configure document classes as sales invoices.
- Configure the sales point for the document classes.
- Configure a document class type as sales invoice.
- Configure the items to be added in the transaction.
- Create and configure a project with a contract.
## Post a sales invoice from a sales order with LATAM information
1. Go to **Accounts receivable > Orders > All sales orders**.
2. Create a new sales order.
3. Select a customer.
4. Enter the item lines.
5. Save and generate a new invoice.
6. Select a document class id. in the LATAM section and complete the rest of the required fields according to the document class configuration.
7. Select a sales point prefix or enter a value manually.
8. Complete the document number.
9. Select ok to post the transaction.
## Post a free text invoice
1. Go to **Accounts receivable > Invoices > All free text invoices**
2. Create a new free text invoice.
3. Select a customer.
4. Create the invoice lines with the corresponding tax codes and prices.
5. Go to the header tab.
6. Complete the **Document class Id.** field in the **LATAM** section.
7. Select a sales point prefix.
8. Complete the document number if it is required by the document class configuration.
9. Select the document date and due date.
10. Complete the **Additional data** fields when required by the document class configuration.
11. Post the invoice.
## Post a project invoice
1. Go to **Project management and accounting > Projects > All projects**.
2. Select a project.
3. Select **Project invoice proposals**.
4. Create a new invoice proposal.
5. Select a project and a transaction to be posted, and then select ok.
6. Select **Post** from the action pane.
7. In the posting form go to the LATAM tab.
8. Complete the **Document class Id.** field.
9. Select a sales point prefix.
10. Complete the document number if it is required by the document class configuration.
11. Select the document date and due date.
12. Complete the **Additional data** fields when required by the document class configuration.
13. Select ok to post the invoice.





