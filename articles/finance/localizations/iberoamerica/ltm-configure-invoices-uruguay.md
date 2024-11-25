---
title: Configure sales and purchase invoices for Uruguay
description: Learn how to configure sales and purchase invoices for a company in Uruguay, including an outline and process for sales invoice configuration.
author: Cpicon85
ms.author: v-cpicon
ms.topic: article
ms.date: 12/08/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure sales and purchase invoices for Uruguay

This article explains how to use fiscal documents that are specific to Uruguay through the Latin American (LATAM) features in purchase and sales transactions. An invoice is represented by a **document class** instead of an invoice transaction, and by all the information that a fiscal invoice document contains and can be related to. This information includes the typification, sales point, branch, invoice number structure, and additional fields that should be completed during posting.

## Sales invoice configuration

Configure the following pages for use in future sales transactions:

- Document class type
- Document class letter
- Sales point
- Document class
- Document class sales point
- Number sequence
- Journal names

Follow these steps to complete the configuration.

1. Create the **document class types** that represent the fiscal documents that will be used in future transactions. Examples include invoices, credit notes, debit notes, and packing slips. For more information, see [Document class type for Latin America](ltm-core-document-class-type.md).
2. Create at least one **sales point** to use in the document classes numeration. This sales point should match the document mask of the document class that it will be assigned to. For more information, see [Sales point prefixes for Latin America](ltm-core-sales-point-prefixes.md).
3. Create the **document classes** that are required for the commercial activity of the company according to the requirements of the Uruguayan fiscal authorities.
4. Set the **document mask** with the required number of characters for the sales point and the document number. Set the entry to automatic, set it for assignment before posting, and set it as mandatory for both the prefix and the document number. For more information, see [Document classes for Latin America](ltm-core-document-class.md).
5. Create a **document class sales point** in every document class that belongs to the company. On the **Document class point** page, select a sales point and a number sequence. The length of the sales point prefix must match the length of the document mask prefix, and the length of the number sequence must match the length of the document mask. For more information, see [Document class sales point for Latin America](ltm-core-document-class-sales-point.md).
6. Create a **customer set**, and add the document classes that you created in the previous steps. The customer set contains the document classes that can be used in a customer transaction when it's assigned to its LATAM configuration. For more information, see [Customer sets for Latin America](ltm-core-customers-set.md).

## Vendor invoice configuration

Vendor invoices have the same configuration requirements as sales invoices, except automatically generated numeration isn't required.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and create one document class for each fiscal document that the company receives from vendors. Examples include purchase invoices, purchase credit notes, and purchase debit notes.
2. Add a document class type.
3. Add a document class letter.
4. On each **Document class** page, in the **Journal names** section, add the journal names that the document classes can be used in.
5. Configure the document mask as required by the Uruguayan normative. Use the required number of characters for the sales point and the document number.
