---
title: Configure sales and purchase invoices for Peru
description: Learn how to configure sales and purchase invoices for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/17/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.author: v-federicohe
ms.custom: bap-template
---

# Configure sales and purchase invoices for Peru

[!include [banner](../../includes/banner.md)]

This article explains how to configure sales and purchase invoices for Peru in Microsoft Dynamics 365 Finance.

The following procedures show how to start to use fiscal documents that are specific to Peru through the Latin American (LATAM) features in sales and purchase transactions. The LATAM localization uses the concept of *document classes* to refer to fiscal documents such as invoices, credit notes, and debit notes. These documents might have to be completed with specific information, such as the typification, sales point, branch, and invoice number structure.

## Configure a sales invoice

You must configure the following pages to use them in future sales transactions:

- Document class type
- Document class letter
- Sales point
- Document class
- Document class sales point
- Number sequence
- Journal names

To configure a sales invoice, follow these steps.

1. Create the *document class type* that represents the fiscal documents to use in future transactions. Examples of these documents include invoices and credit notes.
1. Create at least one *sales point prefix* to use in the document class numeration. The sales point should match the document mask of the document class that it's assigned to. Learn more in [Sales point prefixes for Latin America](ltm-core-sales-point-prefixes.md).
1. Create the *document classes* that are required for the commercial activity of the company according to the requirements of the Peruvian fiscal authorities.
1. Set the *document mask* with the required number of characters for the sales point and the document number. Set the entry to automatic, and then set it to mandatory for both the prefix and the document number. Learn more in [Document classes for Latin America](ltm-core-document-class.md).
1. Create a *document class sales point* in every document class that belongs to the company. On the **Document class sales point** page, select a sale point and a number sequence. The length of the sales point prefix must match the length of the document mask prefix, and the length of the number sequence must match the length of the document mask. Learn more in [Document class sales point for Latin America](ltm-core-document-class-sales-point.md).
1. Create a *customer set*, and add the document classes that you created in the previous steps. The customer set contains the document classes that can be used in a customer transaction when it's assigned to its LATAM configuration. Learn more in [Customer sets for Latin America](ltm-core-customers-set.md).

## Configure a vendor invoice

Vendor invoices have the same configuration requirements as sales invoices, except automatically generated numeration isn't required.

To configure a vendor invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and create one document class for each fiscal document that the company receives from vendors. Examples include purchase invoices, purchase credit notes, and purchase debit notes.
1. Add a document class type.
1. Add a document class letter.
1. On each **Document class** page, in the **Journal names** section, add the journal names that the document class can be used in.
1. Configure the document mask as required by the Peruvian normative. Use the required number of characters for the sales point and the document number.
