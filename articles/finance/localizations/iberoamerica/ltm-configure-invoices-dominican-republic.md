---
title: Configure sales and purchase invoices for the Dominican Republic
description: Learn how to configure sales and purchase invoices for the Dominican Republic.
author: cpicon85
ms.date: 04/03/2025
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon

---

# Configure sales and purchase invoices for the Dominican Republic

[!INCLUDE[banner](../../../includes/banner.md)]

This article explains how to start to use fiscal documents that are specific to the Dominican Republic through the Latin American (LATAM) features in purchase and sales transactions. The LATAM localization uses the concept of *document classes* to refer to fiscal documents such as invoices, credit notes, and debit notes. These documents might have to be completed with specific information, such as the typification, sales point, branch, invoice number structure, and additional fields that should be completed.

## Sales invoice configuration

Configure the following pages to use them in future sales transactions:

- Document class type
- Document class letter
- Sales point
- Document class
- Document class sales point
- Number sequence
- Journal names

To configure a sales invoice, follow these steps:

1. Create the **document class type** that represents the fiscal documents that will be used in future transactions. Examples include invoices, credit notes, debit notes, and packing slips. Learn more in [Document class type for Latin America](ltm-core-document-class-type.md).
1. Create **document class letters** according to the requirements of the Dominican fiscal authorities.
1. Create at least one **sales point prefix** to use in the document classes numeration. This sales point should match the document mask of the document class that it will be assigned to. Learn more in [Sales point prefixes for Latin America](ltm-core-sales-point-prefixes.md).
1. Create the **document classes** that are required for the commercial activity of the company according to the requirements of the Dominican fiscal authorities.
1. Set the **document mask** with the required number of characters for the sales point and the document number. Set the entry to automatic, and set it to mandatory for both the prefix and the document number. Learn more in [Document classes for Latin America](ltm-core-document-class.md).
1. Create a **document class sales point** in every document class that belongs to the company. On the **Document class point** page, select a sale point and a number sequence. The length of the sales point prefix must match the length of the document mask prefix, and the length of the number sequence must match the length of the document mask. Learn more in [Document class sales point for Latin America](ltm-core-document-class-sales-point.md).
1. Create a **customer set**, and add the document classes that you created in the previous steps. The customer set contains the document classes that can be used in a customer transaction when it's assigned to its LATAM configuration. Learn more in [Customer sets for Latin America](ltm-core-customers-set.md).

## Vendor invoice configuration

Vendor invoices have the same configuration requirements as sales invoices, except automatically generated numeration isn't required.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and create one document class for each fiscal document that the company receives from vendors. Examples include purchase invoices, purchase credit notes, and purchase debit notes.
1. Add a document class type.
1. Add a document class letter.
1. On each **Document class** page, in the **Journal names** section, add the journal names that the document classes can be used in.
1. Configure the document mask as required by the Dominican normative. Use the required number of characters for the sales point and the document number.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
