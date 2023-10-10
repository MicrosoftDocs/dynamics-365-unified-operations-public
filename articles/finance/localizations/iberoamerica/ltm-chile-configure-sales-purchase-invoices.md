---
title: Configure sales and purchase invoices
description: This article provides information about how to configure sales and purchase invoices for a Chilean company. 
author: Fhernandez0088
ms.date: 09/21/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Configure sales and purchase invoices

[!include[banner](../../includes/banner.md)]

This article explains how to use the LATAM features to work with Chilean fiscal documents related to purchase and sales transactions. An invoice is represented by a **Document class**, not the invoice transaction. The document class has the same information as a fiscal invoice document, like the typification, sales point, branch, invoice number structure and any additional required fields.

## Sales invoices

Configure the following forms to use in future sales transactions:

- Document class type
- Document class letter
- Sales point
- Document class
- Dcoument class sales point
- Number sequence
- Journal names


1. Create the document class types that represents the fiscal documents. Documents include invoices, credit notes, debit notes, and packing slips. These class types will be used in future transactions. To learn more, see [Document class type for Latin America](../ltm-core-document-class-type.md).
2. Create at least one sales point to use in the document classes numeration. The sales point should match the document mask of the document class that it's assigned to. To learn more, see [Sales point for Latin America](ltm-core-sales-point-prefixes.md).
3. Create the following document classes required for the commercial activity of the company according to the Chilean fiscal requirements: 

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
5. Set the entry to automatic assignment before posting and make the prefix and document number required. For more information, see [Document classes for Latin America](../ltm-core-document-class.md). 
6. Create a **Document class sales point** in every document class that belongs to the company. Select a sales point created and a sequence number. The sales point prefix length must match the document mask prefix length and the number sequence must match the document number mask. To learn more, see [Document class sales point for Latin America](../ltm-core-document-class-sales-point.md).
7. Create a customer set and add the document classes created in the previous steps. This set contains the document classes that can be used in a customer transactions when it's assigned to its LATAM configuration. To learn more, see [Customer set](../ltm-core-customers-set.md).

## Vendor invoices configuration

The requirements for vendor invoices are the same as sales invoices, however they don't require anautomatically generated numeration. 

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class** and create a document class for each fiscal document that the company receive from vendors, such as purchase invoices, purchase credit notes, and purchase debit notes. 
2. Add a **Document class type** and a **Document class letter**.
4. In each **Document class** form, in the **Journal names** section, add the journal names where the document classes can be used. 
5. Configure the document mask following the Chilean requirements, four characters for the prefix and eight characters for the document number.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
