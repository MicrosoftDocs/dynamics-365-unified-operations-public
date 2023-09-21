---
title: Configure sales and purchase invoices
description: This topic provides information about how to configure sales and purchase invoices for a Chilean company. 
author: Fhernandez0088
ms.date: 09/21/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Configure sales and purchase invoices


## Sales invoices

It is important to configure the following forms that will allow you to use them in sales transactions later. The sales invoices are primarily represented through the **Document class** feature.
1. Create the document class types that represents the fiscal documents that will be used in future transactions (invoices, credit notes, debit notes, packing slips). (See [Document class type for Latin America](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/ltm-core-document-class-type) article)
2. Create at least one sales point to be used in the document classes numeration.
3. Create the document classes required for the commercial activity according to the normative that represent the document emitted by the company: 
    * Factura afecta electrónica
    * Factura no afecta electrónica
    * Liquidación Factura Electrónica
    * Factura de compra electrónica
    * Guía de despacho electrónica
    * Nota de débito electrónica
    * Nota de crédito electrónica
    * Factura de exportación
    * Nota de débito de exportación
    * Nota de crédito de exportación

The document classes should have a document number mask according to the fiscal documents normative, eight characters for the document number, and 4 characters for the prefix. The emission should be automatic, and the prefix and number fields should be required when posting transactions. (See [Document classes for Latin America](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/ltm-core-document-class) article)
12. Create a “Document class sales point” in every document class that belongs to the company Select a sales point created and a sequence number. The sales point prefix length must match the document mask prefix length and the same to the number sequence and the document number mask. (See [Document class sales point for Latin America](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/ltm-core-document-class-sales-point) article)
13. Create a customer set and add the document classes created in the previous steps. This will contain the document classes that can be used in a customer transactions  when it is assigned to its LATAM configuration. (See [Customer set](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/ltm-core-customers-set) article)

## Vendor invoices configuration

The vendor inovices will be represented through the **Document class** feature.
1. Create the document classes that represent the fiscal documents that the company receive from vendors, such as purchase invoices. The requirements are the same as the sales invoices, but they don’t need to have an automatic generated numeration. 
2. Add the journal names where these documents can be used in. 
3. Configure the document mask as required by the Chilean normative.
