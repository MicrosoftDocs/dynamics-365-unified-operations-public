---
title: Set up transaction posting for Latin America  
description: This article explains how to set up transaction posting for LATAM. 
author: Fhernandez0088
ms.date: 10/13/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Set up transaction posting for Latin America 

[!include [banner](../../includes/banner.md)]

This article provides the essential information and required steps you must complete to set up the functionality for and post transactions in Latin America (LATAM) using LATAM-specific features. Supported transactions include customer and vendor invoices, customer and vendor payments, and remission documents.

## 1. Activate LATAM features

1. Go to the **Feature management** workspace.
2. In the list, find and select the **LATAM globalization expansion** feature for each country that you want to enable functionality for and select **Enable now**. 

## 2. Set the company primary address to a LATAM country 
To enable and use the LATAM-specific features, the company's primary address must be located in LATAM. Follow the steps to set the primary address in LATAM.

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select the legal entity for which you are updating the primary address.
3. On the **Addresses** FastTab, select **Add**.
4. Enter the address information and mark the address as **Primary**.
5. Select **OK**.

## 3. Create Tax ID types according to country legislation
Tax ID types represent the way the fiscal regulatory entity classifies every taxpayer identification code. For example, the way fiscal codification works for a physical entity differs from an organization's fiscal codification. These document types are used in every LATAM tax and legal information section for any entity. This includes company, customer, vendor, shipping carrier, bank group, and employee. The document types contain the characteristics related to that classification, such as tax report codes, format, algorithmic validation, and jurisdiction belonging. 

To learn more about how to create TAX ID types, see [Tax ID types](ltm-core-tax-id-type.md).

## 4. Create document class letters for the country fiscal documents’ structure
This configuration isn't mandatory, Instead, it's dependent on the fiscal document identification structure of the country. Document class letters are part of the complete document number when posting a transaction with LATAM information. The document class letter is part of a fiscal document identification that is assigned to a document class. For more information, see [Document class letter](ltm-core-document-class-letter.md). 

## 5. Create the taxpayer type according to the country legislation
The taxpayer type is a concept that's established specific to each country as a way to classify each taxpayer based on attributes like company size, business type, location, and any other quality that the country normative determines. Add the **Tax ID types** and the **Document class letters** to the taxpayer configuration so they can be used by the entity where the taxpayer type is assigned. For more information about taxpayer types, see [Taxpayer type](ltm-core-taxpayer-type.md).

## 6.Add the Tax ID types to the LATAM Country address configuration
The tax ID types you add to an address in a LATAM country can be selected in the **Tax and legal attributes** section when the taxpayer is selected. This selection is used to define which tax ID types belong to each country according to the legislation. For more details about addresses in LATAM, see [LATAM country address setup](ltm-core-address-setup.md).

## 7. Set company with the LATAM country tax and legal information
To enable the LATAM extension on the **Legal entity** page, set the country value of the address to the same as the LATAM country for which the feature is enabled. This section contains information related to the fiscal identification, fiscal country address, business activity description, and any other information required.

## 8. Create the journal names required
Journal names should represent the transactions that being used. For example, vendor invoices, payments, and collectables. For more details, see [Journal names for LATAM](ltm-core-journal-name-configuration.md).

## 9. Create bank groups 
The **LATAM** section on the **Bank groups** page contains fiscal information, including fiscal identification, fiscal address, and other fiscal concepts, that are stored when posting transactions that use the bank group. This information is used in some country specific reports.

## 10. Create bank accounts 
Create a new bank account and assign the bank group with LATAM information to it.

## 11. Select the document class types to assign to the document classes
This configuration represents the nature of the fiscal documents, what they represent in relation to customer and vendor invoices, packing slips, and payment methods. This configuration also defines in which journal line account types the document can be used and if the document class can be used with credit or debit lines. To learn more, see [Document class types](ltm-core-document-class-type.md).

## 12. Set document classes for invoice and payment documents
The document class represents any fiscal and commercial document that supports a transaction. The document class must contain the following information to be used when posting a transaction.

- Assign a document class type that fits nature of the document class.
- Assign a document class letter.
- Add the journal names where the document class will be used.
- Add the bank accounts to the document class when it represents a payment method.
- Configure the document mask according to the document identification structure. The document mask is a functionality that's used to define complex document numbering for any document class used in a transaction. The mask configuration in a document class sets a format that the document number must follow, which results another requirement to use a document class in a transaction. For example, in Argentina the legal format consists of two letters to identify the fiscal document, then one letter for the fiscal type, then a numeric a sales point for the business unit, and a number sequence. Every part of the complete document number can be configured using the extended LATAM functionality.
- Set up a document class sales point when using an automatic generated document number. This configuration must match the document mask set where the sales point prefix matches and document number. Set a document class sales point for the account type you want with a sales point and a number sequence. To learn more, see [Document classes](ltm-core-document-class.md).

## 13. Create the customer/vendor sets with required document classes
The customer and vendor set must contain the document classes that a customer and vendor can use. For more details, see [Customer set](ltm-core-customers-set.md) and [Vendor set](ltm-core-vendors-set.md).

## 14. Create the customers and vendors with the required tax and legal information
In the tax and legal information from the **LATAM** sectio, provide the taxpayer type, country/region, document type, document ID, and any other required fiscal or commercial information.

## 15. Complete the remission/invoice sales point form with the required combinations
In this configuration, create the combination between remission documents sales points and invoices sales points.
This combination is required to post an invoice that comes from a packing slip. If it's not configured, the sales point in the **LATAM** section for the posting invoice page can't be selected. For more details, see [Sales point relation](ltm-core-point-relation.md).

## 16. Post transactions
Invoices can be posted from free text invoices, invoice journals, sales orders, purchase orders, invoice register, and projects invoices. Complete the **LATAM** information section from the posting page as configured (document class, sales point, document number, etc.) For more information, see [Sales invoice posting](ltm-core-sales-invoice-posting-latam.md) and [Purchase invoice posting](ltm-core-purchase-invoice-posting.md).

Payments can be posted from customer or vendor payments.

Remission documents can be posted from sales or purchase orders and inventory transfers. To learn more, see [Packing slip posting](ltm-core-packing-slip-posting.md).




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
