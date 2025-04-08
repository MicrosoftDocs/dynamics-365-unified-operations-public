---
title: Configure electronic invoice parameters for Chile
description: Learn how to configure the information required to generate the electronic invoice XML for Chile, including prerequisites and a process of electronic invoices.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 10/20/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure electronic invoice parameters for Chile

[!include [banner](../../includes/banner.md)]

This article explains how to configure the information that's required to generate the electronic invoice XML for Chile.

## Prerequisites

Before you complete the procedure in this article, the following prerequisites must be met:

- The country/region-specific Latin American (LATAM) feature for Chile and the general LATAM feature must be enabled.
- The company address must be set to Chile.

## Configuration required for Chilean electronic invoices

The following steps go through the information that the XML tags require, in the specific order that they require it in.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application records that has the code **CHFE** (Chilean electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.
2. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and follow these steps:
 
    1. In the **LATAM** section, in the **Country identification number** field, enter the complete Rol Único Tributario (RUT) number.
    2. In the **Concept 1** field, enter **Giro emisor** as the business activity. The title of this field can be changed in the **Concept and notes** configuration on the **LATAM parameters** page.
    3. In the **Contact information** section, add a telephone number and an email address, and set them as **Primary**.
    4. In the **Statutory reporting** section, in the **Branch/Subsidiary** field, enter the code for the business activity according to the Chilean normative.

3. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and follow these steps:

    1. On the Action Pane, select **Tax application**.
    2. Assign a tax code to each document class that will be used, according to the updated Chilean normative.
    3. Add the letter **R** to the credit note and debit note to require the reference documents when those types of transactions are posted.

4. Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**, and follow these steps:

    1. Create the terms of payments for cash payments, credits, and donations.
    2. Assign a tax code to the terms of payment according the Chilean normative.

5. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class sales point**, and assign a document number sequence to the document class sales point configuration. This number sequence is used for the document number for the fiscal document.
6. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**, and set the tax application code to the sales points that are used with the codification that the fiscal authority assigned to it.
7. Go to **Accounts receivable** \> **Customers** \> **All customers**, and follow these steps:

    1. Select and open a customer record.
    2. In the **LATAM** section, in the **Country identification number** field, select the customer's RUT number.

8. Go to **Accounts receivable** \> **Customers** \> **All customers**, and follow these steps:

    1. On the Action Pane, in the **General** group, select **Business classification**.
    2. Create a record to add the business classification that's declared in the fiscal records to each customer record.

9. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and configure the required information for fiscal documents.

    1. For remission document classes, select each one that has been created. Then, in the **General** section, set **Concept Label 1** field to **RUT Chofer** and the **Concept Label 3** field to **Nombre Chofer**.
    2. In the **Additional data** section, configure the fields for each remission document class to match the information requirements for electronic invoicing. For remission document classes, the **Free text 1** field should be required and should be for the driver's RUT number. The **Free text 3** field should be required and should be for the driver's name.
    3. In the **Additional data** section, enable lists 3, 4, 5, 7, and 8.
    4. For each credit/debit note document class that has been created, in the **Additional data** section, enable lists 9 and 10.

    For more information, see [Document classes for Latin America](ltm-core-document-class.md).

10. Go to **Sales and marketing \> Setup \> Distribution \> Reasons for delivery**, and set the options for selling modes according to the Chilean normative that's established by the customs office. This information is used only for export documents.
11. Go to **Sales and marketing \> Setup \> Distribution \> Terms of delivery**, and set the options for selling clauses according to the Chilean normative (FOB, CIF, and so on).
12. Go to **Sales and marketing \> Setup \> Distribution \> Modes of delivery**, and set the options for transportation routes according to the Chilean normative (aerial, terrestrial, maritime, and so on).
13. Go to **General ledger \> Currencies \> Currencies**. For each currency that's used in transactions set the **Tax application** code with the currency indicator according to the electronic invoice schema (PESO CL, DOLAR USA, EURO, and so on).	
14. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Electronic documents references**. Set the **Tax application id** value that has been created for electronic invoicing for Chile (**CHFE**), and set the limit to trigger the global indicator according to the Chilean normative (**20**). These settings will trigger the limit for references in one document and make a summary of the references.
15. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**, and configure the tax application code for the units that will be used, according to the Chilean customs office normative.
16. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Field master list**, and create the following field lists:

    - **Field list 3:** Add elements that have the ports of shipment and their codes according to the Chilean normative.
    - **Field list 4:** Add elements that have the landing ports and their codes according to the Chilean normative.
    - **Field list 5:** Add elements that have the options for transport type indicators and their codes according to the Chilean normative.
    - **Field list 7:** Add elements that have the options for remission types and their codes according to the Chilean normative.
    - **Field list 8:** Add elements that have the options for products transfer types and their codes according to the Chilean normative.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
