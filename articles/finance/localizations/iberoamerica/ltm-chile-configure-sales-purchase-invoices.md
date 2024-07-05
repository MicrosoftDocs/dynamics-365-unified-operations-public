---
title: Configure sales and purchase invoices
description: Learn how to configure sales and purchase invoices for a Chilean company, including an outline and step-by-step process of sales invoice configurations.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 09/21/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure sales and purchase invoices

[!include[banner](../../includes/banner.md)]

This article explains how to use the Latin American (LATAM) features to work with Chilean fiscal documents that are related to sales and purchase transactions. An invoice is represented by a **document class**, not by the invoice transaction. The document class has the same information as a fiscal invoice document, such as the typification, sales point, branch, invoice number structure, and any additional required fields.

## Sales invoice configuration

Configure the following pages for use in future sales transactions:

- Document class type
- Document class letter
- Sales point
- Document class
- Document class sales point
- Number sequence
- Journal names

Follow these steps to complete the configuration for sales invoices.

1. Create the document class types that represent the fiscal documents. Documents include invoices, credit notes, debit notes, and packing slips. These document class types will be used in future transactions. For more information, see [Document class type for Latin America](../ltm-core-document-class-type.md).
2. Create at least one sales point to use in the document class numeration. The sales point should match the document mask of the document class that it's assigned to. For more information, see [Sales point prefixes for Latin America](ltm-core-sales-point-prefixes.md).
3. Create the following document classes that are required for the commercial activity of the company according to the Chilean fiscal requirements:

    - Factura afecta electrónica
    - Factura no afecta electrónica
    - Liquidación Factura Electrónica
    - Factura de compra electrónica
    - Guía de despacho electrónica
    - Nota de débito electrónica
    - Nota de crédito electrónica
    - Factura de exportación
    - Nota de débito de exportación
    - Nota de crédito de exportación

4. Set the document mask to four characters for the sales point prefix and eight characters for the document number.
5. Set the entry to automatic assignment before posting, and make the prefix and document number required. For more information, see [Document classes for Latin America](../ltm-core-document-class.md).
6. Create a document class sales point in every document class that belongs to the company. Select a sales point that has been created and a sequence number. The length of the sales point prefix length must match the length of the document mask prefix, and the number sequence must match the document number mask. For more information, see [Document class sales point for Latin America](../ltm-core-document-class-sales-point.md).
7. Create a customer set, and add the document classes that you created in the previous steps. The customer set contains the document classes that can be used in a customer transaction when it's assigned to its LATAM configuration. For more information, see [Customer sets for Latin America](../ltm-core-customers-set.md).

## Vendor invoice configuration

Vendor invoices have the same requirements as sales invoices, but they don't require automatically generated numeration.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and create a document class for each fiscal document that the company receives from vendors, such as purchase invoices, purchase credit notes, and purchase debit notes.
2. Add a document class type and a document class letter.
3. On the page for each document class, in the **Journal names** section, add the journal names where the document classes can be used.
4. Configure the document mask according to the Chilean requirements: four characters for the prefix and eight characters for the document number.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
