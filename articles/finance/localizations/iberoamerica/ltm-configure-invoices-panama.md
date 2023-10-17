---
title: Configure sales and purchase invoices for Panama
description: This article explains how to configure sales and purchase invoices for a company located in Panama. 
author: Cpicon85
ms.date: 10/11/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-cpicon
ms.custom: bap-template
---

# Configure sales and purchase invoices for Panama

[!include [banner](../../includes/banner.md)]

This article explains how to start using fiscal documents specific to Panama through the LATAM features in purchase and sales transactions.
An invoice is represented by a **Document class** instead of an nvoice transaction, and all the information that a fiscal invoice document contains and be related to. This includes the typification, sales point, branch, invoice number structure and additional fields that should be complete during posting.

## Sales invoices

Configure the following pages to use them in future sales transactions:
	
- Document class type
- Document class letter
- Sales point
- Document class
- Document class sales point
- Number sequence
- Journal names

1. Create the **Document class types** that represent the fiscal documents that will be used in future transactions. For example, invoices, credit notes, debit notes, and packing slips. To learn more, see [Document class type for Latin America](ltm-core-document-class-type.md).
2. Create at least one sales point to use in the document classes numeration. This sales point should match the document mask of the document class that it will be assigned to. For more details, see [Sales point for Latin America](ltm-core-sales-point-prefixes.md).
3. Create the document classes required for the commercial activity of the company according to the Panama fiscal requirements.
4. Set the **Document mask** with the required number of characters for the sales point and document number. Set the entry to automatic, assignment before post and mandatory for both prefix and document number. For more details, see [Document classes for Latin America](ltm-core-document-class.md).
5. Create a **Document class sales point** in every document class that belongs to the company. On the **Document class point** page, select a sale point and a number sequence. The sales point prefix length must match the document mask prefix length and the number sequence length must match the document mask length. For more information, see [Document class sales point for Latin America](tm-core-document-class-sales-point.md).
6. Create a customer set and add the document classes you created in the previous steps. The customer set will contain the document classes that can be used in a customer transaction when it's assigned to its LATAM configuration. For more details, see [Customer set](ltm-core-customers-set.md).

## Vendor invoices configuration
The requirements to configure vendor invoices are the same as sales invoices, but automatic generated numeration isn't necessary. 

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class** and create one document class for each fiscal document that the company receive from vendors, such as purchase invoices, purchase credit notes and purchase debit notes. 
2. Add a **Document class type**.
3. Add a **Document class letter**
4. In each **Document class** page, in the **Journal names** section, add the journal names where the document classes can be used in. 
5. Configure the document mask as required by the Panama normative with the required number of characters for the sales point and document number.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
