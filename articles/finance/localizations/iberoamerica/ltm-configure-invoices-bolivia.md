---
title: Configure sales and purchase invoices for Bolivia
 
description: This topic provides information about sales and purchase invoices for Bolivia. 
author: Cpicon85
ms.date: 02/10/2025
ms.topic: Article
ms.reviewer: johnmichalak
ms.author: v-cpicon
ms.custom: bap-template
---
# Configure sales and purchase invoices for Bolivia

This article explains how to start to use fiscal documents that are specific to Bolivia through the Latin American (LATAM) features in purchase and sales transactions. The LATAM localization uses the concept of *document classes* to refer to fiscal documents such as Invoice, credit and debit note a so on. These documents may need to be completed with certain information such as the typification, sales point, branch, invoice number structure, and additional fields that should be completed.

# Sales invoice configuration
Configure the following pages to use them in future sales transactions:
- Document class type
- Document class letter
- Sales point 
- Document class
- Document class sales point
- Number sequence
- Journal names
Follow these steps to complete the configuration.
1. Create the **document class type** that represent the fiscal documents that will be used in future transactions. Examples include invoices, credit notes, debit notes, and packing slips. For more information, see [Document class type for Latin America](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class-type).
2. Create at least one **Sales point prefix** to use in the document classes numeration. This sales point should match the document mask of the document class that it will be assigned to. For more information, see [Sales point prefixes for Latin America](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/iberoamerica/ltm-core-sales-point-prefixes).
3. Create the **document classes** that are required for the commercial activity of the company according to the requirements of the Bolivian fiscal authorities.
4. Set the **document mask** with the required number of characters for the sales point and the document number. Set the entry to automatic,  and mandatory for both the prefix and the document number. For more information, see. For more information, see [Document classes for Latin America](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class).
5. Create a **document class sales point** in every document class that belongs to the company. On the **Document class point** page, select a sale point and a number sequence. The length of the sales point prefix must match the length of the document mask prefix, and the length of the number sequence must match the length of the document mask.. For more information, see [Document class sales point for Latin America](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class-sales-point).
6. Create a **Customer set**, and add the document classes that you created in the previous steps. The customer set contains the document classes that can be used in a customer transaction when it's assigned to its LATAM configuration. For more information, see [Customer sets for Latin America](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/iberoamerica/ltm-core-customers-set).
7. If you need it enable authorization code functionality. Learn more in [Sales authorization code](ltm-core-sales-ca.md)

# Vendor invoice configuration
Vendor invoices have the same configuration requirements as sales invoices, except automatically generated numeration isn't required.
1. Go to **Organization administration > Setup > LATAM > Document class**, and create one document class for each fiscal document that the company receives from vendors. Examples include purchase invoices, purchase credit notes, and purchase debit notes.
2. Add a document class type.
3. Add a document class letter.
4. On each **Document class** page, in the **Journal names** section, add the journal names that the document classes can be used in. 
5. Configure the document mask as required by the Bolivia normative. Use the required number of characters for the sales point and the document number.
6. If you need it enable authorization code functionality. Learn more in [Sales authorization code](ltm-core-sales-ca.md)


