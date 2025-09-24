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

This article explains how to configure the information that is required to generate the electronic invoice XML for Ecuador.

## Prerequisites

Before you complete the procedure in this article, the following prerequisites must be met:

* Both the country/region-specific Latin American (LATAM) feature for Ecuador and the general LATAM feature must be enabled.
* The company address must be set to Ecuador.

## Required configuration for Ecuadorian electronic invoices

Follow these steps to configure the information that the XML tags require, in the order that they require it.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application record that has the code **ECUFE** (Ecuadorian electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.
1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and follow these steps:

    1. In the **LATAM** section, in the **Country identification** field, enter the complete Unique Taxpayer Registry (Registro Único de Contribuyentes \[RUC\]) number.
    1. In the **Note 1** field, enter the special taxpayer code, if it's applicable. You can change the name of this field in the **Concept and notes** configuration on the **LATAM parameters** page.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and follow these steps:

    1. On the Action Pane, select **Tax application**.
    1. Assign a tax code to each document class that will be used, according to the updated Ecuadorian normative.
    1. Add the letter **R** to the credit note and debit note to require the reference documents when those types of transactions are posted.
    1. For document classes for credit and debit notes, you must set the option for the **reference document** check to **Yes**.

1. Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**, and create the terms of payments for cash payments, credits, and debits.
1. Go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**, and follow these steps:

    1. Create the methods of payment according the Ecuadorian normative.
    1. Assign a tax application code to the methods of payment as specified by the electronic invoice regulation.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class sales point**, and follow these steps:

    1. Assign a document number sequence. The first three numbers of the sequence will be the sales point code.
    1. In the **Printing concepts 1** field, enter the street and street number of the headquarters.
    1. In the **Printing concepts 2** field, enter the city of the headquarters.
    1. In the **Printing concepts 3** field, enter the department of the headquarters.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**, and set the **Prefix** field to the establishment code.
1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and follow these steps:

    1. Select and open a customer record.
    1. In the **LATAM** section, set the **Country identification number** field to the customer's RUC number.
    1. On the **Contact information** tab, configure the customer's email address and phone number.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and complete the **Tax application** code with the identification type as specified by the regulation.
1. For shipping guide documents, you must create a shipping carrier. Go to **Inventory and management** \> **Setup** \> **Shipping carriers**, and follow these steps:

    1. Create a record.
    1. On the **LATAM** tab, set the **Tax payer type**, **Country document type**, and **Country identification number** fields to appropriate values for the carrier.
    1. Create a transportation method. Its name will be used for the vehicle plate.

1. When you create a shipping guide, you must configure confirmed ship and receipt dates from the sales order lines.
1.	When you create a shipping guide, on the **Delivery** tab, you must configure delivery reasons from the sales order header.
1.	Go to **Tax** \> **Sales tax** \> **Sales tax codes**, and configure the required taxes for transactions.

    1. For each tax that you configure, select **LATAM** \> **Tax application** on the Action Pane. Then, in the **Income tax code** field, configure the corresponding tax code from table 16, as specified by the regulation.
    1. In the **Code regime** field, configure the corresponding code from table 17, as specified by the regulation.

1.	Go to **General ledger** \> **Currencies** \> **Currencies**. For each currency that is used in transactions, complete the **Tax application** code with the currency indicator as specified by the regulation.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
