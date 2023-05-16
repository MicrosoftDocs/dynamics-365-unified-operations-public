---
title: Purchase invoice posting for Latin America
description: This topic provides information about the purchase invoice posting process for Latin America. 
author: Fhernandez0088
ms.date: 05/15/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---
# Purchase invoice posting for Latin America
You can add the information needed for Latin American countries when posting an invoice in an extended LATAM section:
Purchase orders
Invoice journals
Project invoices
Invoice register
# Prerequisites
Before posting an invoice, you must configure the following:
- The LATAM globalization feature must be enabled.
- Country/Region: a country supported in the LATAM globalization expansion.
- Configure the entities involved in transactions: legal entities and vendors.
- Configure the LATAM tax and legal information in those entities required for purchase invoice transactions.
- Configure document classes as purchase invoices.
- Configure the sales point for the document classes.
- Configure a document class type as purchase invoice.
- Configure the items to be added in the transaction.
- Create and configure a project with a contract.
## Post an invoice from a purchase order with LATAM information
1. Go to **Accounts payable > Purchase orders > All purchase orders**.
2. Create a new purchase order.
3. Select a vendor and then ok.
4. Enter the item lines.
5. Save and generate a new invoice and select post.
6. Select a document class id. in the LATAM section and complete the rest of the required fields according to the document class configuration.
7. Select a sales point prefix or enter a value manually.
8. Complete the document number.
9. Select post in the action menu.
## Post an invoice journal with LATAM information
1. Go to **Accounts payable > Invoices > Invoice journal**
2. Create a new line with a journal name configured as a vendor invoice recording and select Lines from the action menu.
3. Select a vendor.
4. Enter a value for the vendor line.
5. Select an offset account.
6. Go to the LATAM tab.
7. Complete the **Document class Id.** field in the **LATAM** section.
8. Select a sales point prefix.
9. Complete the document number if it is required by the document class configuration.
10. Select the document date and due date.
11. Complete the **Additional data** fields when required by the document class configuration.
12. Post the invoice.	
## Post an invoice from a project purchase order with LATAM information
1. Go to **Project management and accounting > Projects > All projects**.
2. Select a project.
3. Select **Purchase orders** from the **Item tasks** menu.
4. Create a new purchase order.
3. Select a vendor and then ok.
4. Enter the item lines and confirm the order.
5. Save and generate a new invoice and select post.
6. Select a document class id. in the LATAM section and complete the rest of the required fields according to the document class configuration.
7. Select a sales point prefix or enter a value manually.
8. Complete the document number.
9. Select post in the action menu.
## Post a vendor invoice from invoice register
1. Go to **Accounts payable > Invoices > Invoice register**
2. Create a new line with a journal name configured as an **Invoice register** and select **Lines** from the action menu.
3. Select a vendor.
4. Enter a value for the vendor line.
5. Go to the LATAM tab.
6. Complete the **Document class Id.** field in the **LATAM** section.
7. Select a sales point prefix.
8. Complete the document number if it is required by the document class configuration.
9. Select the document date and due date.
10. Complete the **Additional data** fields when required by the document class configuration.
11. Post the invoice.
	
