---
title: Configure sales and purchase invoices for Costa Rica
description: This topic provides information about how to configure sales and purchase invoices for a Costa Rica company. 
author: Cpicon85
ms.date: 10/09/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-cpicon
ms.custom: bap-template
---

# Configure sales and purchase invoices for Costa Rica
This article shows the needed configurations to start using Costa Rca fiscal documents through LATAM features in purchase and sales transactions.
An invoice is represented by a **Document class**, not the invoice transaction, but has all the information that a fiscal invoice document can contain and be related to, such as the typification, sales point, branch, invoice number structure and the additional (and customizable) fields that you must/should complete when posting one.

## Sales invoices

It is important to configure the following forms that will allow you to use them in sales transactions later:
   
   * Document class type
   * Document class letter
   * Sales point
   * Document class
   * Document class sales point
   * Number sequence
   * Journal names

1. Create the **Document class types** that represents the fiscal documents that will be used in future transactions (invoices, credit notes, debit notes, packing slips). (See [Document class type for Latin America](../ltm-core-document-class-type.md) article)
2. Create at least one **Sale point** to be used in the document classes numeration. This sales point should match the document mask of the document class that will be assigned to. (See [Sales point for Latin America]( https://learn.microsoft.com/en-us/dynamics365/finance/localizations/ltm-core-sales-point-prefixes) article)
3. Create the document classes required for the commercial activity of the company according to the Costa Rica fiscal normative
Set the **Document mask** with the required number of characters for the sales point and document number. Set the entry to automatic, assignment before post and mandatory for both prefix and document number.
(See [Document classes for Latin America](../ltm-core-document-class.md) article)
12. Create a “Document class sales point” in every document class that belongs to the company. In this form select a **Sale point** created and a number sequence. The sales point prefix length must match the document mask prefix length and the same between the number sequence and the document number mask. (See [Document class sales point for Latin America](../ltm-core-document-class-sales-point.md) article)
13. Create a customer set and add the document classes created in the previous steps. This will contain the document classes that can be used in a customer transaction when it is assigned to its LATAM configuration. (See [Customer set](../ltm-core-customers-set.md) article)

## Vendor invoices configuration
The requirements are the same as the sales invoices, but they don’t need to have an automatic generated numeration. 
1. Go to **Organization administration > Setup > LATAM > Document class** and create one document class for each fiscal document that the company receive from vendors, such as purchase invoices, purchase credit notes and purchase debit notes. 
2. Add a **Document class type**.
3. Add a **Document class letter**
4. In each **Document class** form in the **Journal names** section add the journal names where these document classes can be used in. 
5. Configure the document mask as required by the Costa Rica normative with the required number of characters for the sales point and document number.
