---
title: Configure electronic invoice parameters for Ecuador
description: Learn how to configure electronic invoice parameters for Ecuador.
author: Fhernandez0088
ms.date: 01/22/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure electronic invoice parameters for Ecuador

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure the information that's required to generate the electronic invoice XML for Ecuador.

## Prerequisites

Before you complete the procedure in this article, the following prerequisites must be met:

* The country/region-specific Latin American (LATAM) feature for Ecuador and the general LATAM feature must be enabled.
* The company address must be set to Ecuador.

## Configuration required for Ecuadorian electronic invoices

The following steps go through the information that the XML tags requires in the specific order that it's required in.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application records that has the code **ECUFE** (Ecuadorian electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and follow these steps:
    
   1. In the LATAM section, in the **Country identification** number field, enter the complete **Registro Único de Contribuyentes** (RUC) number.
   1. In the Note 1 field, enter the special taxpayer code if applicable. The title of this field can be changed in the Concept and notes configuration on the LATAM parameters page.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and follow these steps:
    
   1. On the **Action** pane, select **Tax application**.
   1. Assign a tax code to each document class that will be used, according to the updated Ecuadorian normative.
   1. Add the letter **R** to the credit note and debit note to require the reference documents when those types of transactions are posted.
   1. Document classes for credit and debit notes must have the **reference document** check set to **Yes**.

1. Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**, and create the terms of payments for cash payments, credits, and debits.

1. Go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**, and follow these steps:
    
   1. Create the methods of payment according the Ecuadorian normative.
   1. Assign a tax application code to the methods of payment as specified by the regulation.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class sales point**:
    
   1. Assign a document number sequence the first three numbers of the sequence will be the sales point code. 
   1. Complete the fields **Printing concepts 1, 2 and 3** with the headquarter's street and street number, headquarter's city and headquarter's department respectively.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**, complete the **Prefix** field with the establishment code.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and follow these steps:

   1. Select and open a customer record.
   1. In the LATAM section complete the **Country identification number** field with the customer's RUC number.
   1. Configure email and phone number into the **Contact information** tab.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type** and complete the **Tax application** code with the identification type as specified by the regulation.

1. For shipping guide documents, a **Shipping carrier** must be created. Go to **Inventory and management** \> **Setup** \> **Shipping carriers** and create a new record. Into the LATAM Tab, follow these steps:

   1. Complete the **Tax payer type**, **Country document type** and **Country identification number** of the carrier.
   1. Create a transportation method. Its name will be used for the vehicles plate.

1. When creating a shipping guide, both confirmed ship and receipt date from the Sales Order lines, must be configured.

1.	When creating a shipping guide, delivery reasons from the Sales Order header, in the delivery tab, must be configured.

1.	Go to **TAX** \> **Sales tax** \> **Sales tax codes** and configure the required taxes that will be used in the transactions.

   1. For each tax configured, select **LATAM** \> **Tax application** on the action pane and in the **Income tax code** field configure the corresponding tax code from table 16 as specified by the regulation.
   1. In the **Code regime** field configure the corresponding code from table 17 as specified by the regulation.

1.	**Go to General ledger** \> **Currencies** \> **Currencies**. For each currency that's used in transactions set the **Tax application** code with the currency indicator according to the electronic invoice regulation.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
