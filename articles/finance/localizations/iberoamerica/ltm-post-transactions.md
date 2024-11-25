---
title: Set up transaction posting for Latin America
description: Learn how to set up transaction posting for Latin America (LATAM), including outlines on activating features and setting a company address to the LATAM region.
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: article
ms.date: 07/29/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Set up transaction posting for Latin America 

[!include [banner](../../includes/banner.md)]

This article provides the information that you need and the steps that you must complete to set up the functionality for posting transactions in Latin America (LATAM) by using LATAM-specific features. Supported transactions include customer and vendor invoices, customer and vendor payments, and remission documents.

## Step 1. Activate LATAM features

1. Open the **Feature management** workspace.
2. In the list, find and select the **LATAM globalization expansion** feature for each country/region that you want to enable the functionality for, and then select **Enable now**. 

## Step 2. Set the company's primary address to a LATAM country/region

You can enable and use the LATAM-specific features only if the company's primary address is in LATAM. Follow these steps to set the primary address so that it's in LATAM.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select the legal entity that you're updating the primary address for.
3. On the **Addresses** FastTab, select **Add**.
4. Enter the address information, and mark the address as **Primary**.
5. Select **OK**.

## Step 3. Create tax ID types according to the country/region legislation

Tax ID types represent the way that the fiscal regulatory entity classifies every taxpayer identification code. For example, fiscal codification works differently for a physical entity and an organization. The document types are used in every LATAM tax and legal information section for any entity. Entities include company, customer, vendor, shipping carrier, bank group, and employee. The document types contain the characteristics that are related to that classification, such as the tax report codes, format, algorithmic validation, and jurisdiction belonging. 

For more information about how to create tax ID types, see [Tax ID types for Latin America](ltm-core-tax-id-type.md).

## Step 4. Create document class letters for the country/region fiscal document structure

This configuration isn't mandatory. It depends on the fiscal document identification structure of the country/region. Document class letters are part of the complete document number when a transaction that has LATAM information is posted. The document class letter is part of a fiscal document identification that's assigned to a document class. For more information, see [Document class letter for Latin America](ltm-core-document-class-letter.md). 

## Step 5. Create the taxpayer type according to the country/region legislation

The concept of a taxpayer type is specific to each country/region and establishes a classification of each taxpayer based on attributes such as the company size, business type, location, and any other quality that the country/region normative determines. Add the **tax ID types** and the **document class letters** to the taxpayer configuration so that they can be used by the entity where the taxpayer type is assigned. For more information about taxpayer types, see [Taxpayer types for Latin America](ltm-core-taxpayer-type.md).

## Step 6. Add the tax ID types to the LATAM country/region address configuration

The tax ID types that you add to an address in a LATAM country/region can be selected in the **Tax and legal attributes** section when the taxpayer is selected. This selection is used to define which tax ID types belong to each country/region according to the legislation. For more information about addresses in LATAM, see [Address setup for Latin America](ltm-core-address-setup.md).

## Step 7. Set the company with the LATAM country/region tax and legal information

To enable the LATAM extension on the **Legal entity** page, set the country/region value of the address to the same LATAM country/region that the feature is enabled for. This section contains information that's related to the fiscal identification, fiscal country/region address, and business activity description, and any other information that's required.

## Step 8. Create the required journal names

Journal names should represent the transactions that are being used, such as vendor invoices, payments, and collectables. For more information, see [Configure journal names for Latin America](ltm-core-journal-name-configuration.md).

## Step 9. Create bank groups

The **LATAM** section on the **Bank groups** page contains fiscal information that's stored when transactions that use the bank group are posted. This information includes the fiscal identification, fiscal address, and other fiscal concepts. This information is used in some country/region-specific reports.

## Step 10. Create bank accounts

Create a new bank account, and assign the bank group that has LATAM information to it.

## Step 11. Select the document class types to assign to the document classes

This configuration represents the nature of the fiscal documents: what they represent in relation to customer and vendor invoices, packing slips, and payment methods. It also defines which journal line account types the document can be used in, and whether the document class can be used with credit or debit lines. For more information, see [Document class type for Latin America](ltm-core-document-class-type.md).

## Step 12. Set document classes for invoice and payment documents

The document class represents any fiscal and commercial document that supports a transaction. To be used when a transaction is posted, the document class must contain the following information:

- Assign a document class type that fits the nature of the document class.
- Assign a document class letter.
- Add the journal names where the document class will be used.
- If the document class represents a payment method, add the bank accounts to it.
- Configure the document mask according to the document identification structure. The document mask is functionality that defines complex document numbering for any document class that's used in a transaction. The mask configuration in a document class sets a format that the document number must follow. The result is another requirement to use a document class in a transaction. For example, in Argentina, the legal format consists of two letters that identify the fiscal document, then one letter for the fiscal type, then a numeric sales point for the business unit, and finally a number sequence. Every part of the complete document number can be configured by using the extended LATAM functionality.
- If an automatically generated document number is used, set up a document class sales point. This configuration must match the document mask that's set, where the sales point prefix and the document number match. Set up a document class sales point for the account type that you want, so that it has a sales point and a number sequence. For more information, see [Document classes for Latin America](ltm-core-document-class.md).

## Step 13. Create the customer/vendor sets that have the required document classes

The customer and vendor set must contain the document classes that a customer and vendor can use. For more information, see [Customer sets for Latin America](ltm-core-customers-set.md) and [Vendor sets for Latin America](ltm-core-vendors-set.md).

## Step 14. Create the customers and vendors that have the required tax and legal information

In the tax and legal information in the **LATAM** section, provide the taxpayer type, country/region, document type, document ID, and any other fiscal or commercial information that's required.

## Step 15. Complete the remission/invoice sales point form with the required combinations

In this configuration, create the combination of remission document sales points and invoice sales points. This combination is required to post an invoice that comes from a packing slip. If it isn't configured, the sales point in the **LATAM** section for the posting invoice page can't be selected. For more information, see [Sales point relation for sales documents and remission](ltm-core-point-relation.md).

## Step 16. Post transactions

Invoices can be posted from free text invoices, invoice journals, sales orders, purchase orders, invoice registers, and projects invoices. Complete the **LATAM** information section from the posting page as configured (document class, sales point, document number, and so on). For more information, see [Sales invoice posting for Latin America](ltm-core-sales-invoice-posting-latam.md) and [Purchase invoice posting for Latin America](ltm-core-purchase-invoice-posting.md).

Payments can be posted from customer or vendor payments.

Remission documents can be posted from sales or purchase orders and inventory transfers. For more information, see [Post packing slips for Latin America](ltm-core-packing-slip-posting.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
