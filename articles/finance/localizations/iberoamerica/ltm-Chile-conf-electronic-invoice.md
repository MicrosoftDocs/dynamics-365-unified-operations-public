---
title: Configure electronic invoice parameters for Chile
description: This article explains how to configure the information required to generate the electronic invoice XML for Chile. 
author: Fhernandez0088
ms.date: 10/20/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Configure electronic invoice parameters for Chile

[!include [banner](../../includes/banner.md)]

This article explains how to configure the information that's required to generate the electronic invoice XML for Chile.

## Prerequisites
Before you complete the procedure in this article, the following prerequisites must be met.

- The country/region-specific Latin American (LATAM) feature for Chile and the general LATAM feature must be enabled.
- The company address must be set to Chile.

## Configuration required for Chilean electronic invoices

The following steps go through the information that the XML tags requires in that specific order.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Tax application**, and select **New** to create a tax application records that has the code **CHFE** (Chilean electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as needed.
2. Go to **Organization administration** > **Organizations** > **Legal entities** and follow these steps:
 
   1. In the **LATAM** section, in the **Country identification number** field, enter the complete RUT number.
   2. In the **Concept 1** field, enter the business activity **Giro emisor**. The title of this field can be changed from **Concept and notes** configuration in **LATAM parameters**.
   3. In the **Contact information** section, add a telephone number and an email and set them as Primary.
   4. In the **Statutory reporting** section, in the **Branch/Subsidiary** field, enter the code for the business activity according to the Chilean normative.

3. Go to **Organization administration** > **Setup** > **LATAM** > **Document class**, and follow these steps.

   1. On the Action Pane, select **Tax application**. 
   2. Assign a tax code to each document class that will be used according to the updated Chilean normative.
   3. Add the letter **R** to the credit note and debit note to require the reference documents when posting those type of transactions.

4. Go to **Accounts receivable** > **Payments setup** > **Terms of payment**.

   1. Create the terms of payments for cash payments, credits. and donations.
   2. Assign a tax code to the terms of payment according the Chilean normative.
     
5. Go to **Organization administration** > **Setup** > **LATAM** > **Document class sales point** and assign a document number sequence to the document class sales point configuration. This is used as the document number for the fiscal document.
6. Go to **Organization administration** > **Setup** > **LATAM** > **Sales point prefix**  and set the tax application code to the sales points that are used with the codification that the fiscal authority assigned to it.
7. Go to **Accounts receivable** > **Customers** > **All customers**.

    1. Select and open a customer record.
    2. In the **LATAM** section, in the **Country identification number** field, select the customer's **RUT**.

8. Go to **Accounts receivable** > **Customers** > **All customers**.

   1. Add a business classification to the customers in use with the business activity.
   2. On the Action Pane, in the **General** group, select the business activity to add this code to each customer.
      
9. Go to **Organization administration** > **Setup** > **LATAM** > **Document class**.

   1. Configure the additional data section fields to match the information requirements for electronic invoicing:
      Remission document classes should have the **Free text 1** and **Free text 3** required and for the driver’s RUT and driver’s name respectively. 

10. Go to **Sales and marketing > Setup > Distribution > Reasons for delivery** and set the options for selling modes according to the Chilean normative stablished by the customs office. It is used only for export documents.
11. Go to **Sales and marketing > Setup > Distribution > Terms of delivery** and set the options for selling clauses according to the Chilean normative (FOB, CIF, etc.).
12. Go to **Sales and marketing > Setup > Distribution > Modes of delivery** and set the options for transportation routes according to the Chilean normative (aerial, terrestrial, maritime, etc.).
13. Go to **General ledger > Currencies > Currencies** and set on each currency used in transactions the **Tax application** code with currency indicator according to the electronic invoice schema (PESO CL, DOLAR USA, EURO, etc.).	
14. Go to **Organization administration** > **Setup** > **LATAM** > **Electronic documents references**. set the **Tax application id** created for electronic invoicing for Chile (CHFE) and set the limit to trigger the global indicator according to the Chilean normative (20). This will trigger the limit for references in one document and make a summary of the references.
15. Go to **Organization administration** > **Setup** > **Units** > **Units** and configure the tax application code for the units that will be used according to the Chilean customs office normative.
16. Go to **Organization administration** > **Setup** > **LATAM** > **Field master list** and create the following field lists:

    - **Field list 3**: add elements with the ports of shipment and their codes according to the Chilean normative.
    - **Field list 4**: add elements with the landing ports and their codes according to the Chilean normative.
    - **Field list 5**: add elements with the options for transport type indicators and their codes according to the Chilean normative.
    - **Field list 7**: add the elements with the options for remission type and their codes according to the Chilean normative.
    - **Field list 8**: add elements with the options for products transfer type and their codes according to the Chilean normative.

After you complete these steps, you will be able to issue electronic invoices from free text invoices, sales orders, and projects.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
