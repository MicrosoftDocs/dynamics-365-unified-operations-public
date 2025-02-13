---
title: Configure printing for Purchase bank Books for Bolivia
description: Learn about the required configuration for printing a Purchase Bank Book report for Bolivia. 
author: Cpicon85
ms.date: 02/xx/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for Purchase Bank Books for Bolivia

This article explains how to set up and generate reports for purchase Bank books for Bolivia.

Banking in Bolivia consists in the presentation of a specific report for all those purchase transacctions equal to or higher than the amount determined according to the regulations. These operations must be carried out through any of the institutions of the Financial System. Banking reports obliges individuals and companies to carry out their transactions necessarily through banks when they exceed the defined amount. 
Transaction does not refer to the invoice amount or payment amount, it refers to the agreement between parties

## Prerequisites

Before you complete the steps in this article to generate the report, the following prerequisites must be met:

- The legal entity's address must be in Bolivia.
- Both the country/region-specific LATAM feature for Bolivia and the general LATAM feature must be enabled.
- You must download the specific report from the Global repository. For more information, see [Download ER configurations from the Global repository of Configuration service](er-download-configurations-global-repo.md). 
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md).
- You must create a tax application to use on the report for example Tax application id **LB** Tax application description **Libro Bancarizacion**. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- You must create field list 10 as including in bank book report? And in the reference code section add two options  **YES** and **NO**. This list is enable in legal purchase transactions and is required in payments orders.  Learn more in [Field list configuration for Latin America](ltm-core-field-master).
## Common configurations for all transactions type:
-	Create a document class **orden de pago** and enable field list 10 as required.
-	You must configure document class payment media **payment documents** and configure the tax application code according if is check, bank transfer, deposit, etc.

> Document class type for each payment media must have selected **unique per entry**. Learn more in document class type

- Configure Latam extension in Bank group field of the bank account associated with the payment media. That will bring the information related to Bank account number and tax identification.
- 
## Configuration for payment of invoice transactions:


## Configuration for other payments 

|Document class|Tax application|Tax application code|Letter code|user define fiel 2|

## Set up application-specific parameters

To configure application-specific parameters, follow these steps.
1. Open the **Electronic reporting** workspace, and select **Reporting configurations**.
2. Select **Purchase Bank Book BO**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
3. On the **Application specific parameters** page, on the **Lookups** tab, select **ApplicablePaymentDocuments**.
4. In the **Conditions** FastTab, select **Add**.
5. In the **Lookup result** field, select **Yes**
6. In Document classification Id (VoucherClassId) select the document class that represents a payment. 
7. If you have another document class that represents a payment Repeat steps 4, 5 and 6  

To ensure that the report shows the transactions that meet the configured conditions, complete the **Lookup result** fields as **Not Applicable** or **No** with **blank** and **non-blank** conditions

## Run Purchase Bank Book BO report:

To generate the **Purchase bank Book BO** report, follow these steps.
1. Go to **Tax > Inquiries and reports > LATAM > Tax reporting**.
2. In the **Format mapping field**, enter or select a value.
3. Click OK.
4. In the **TAX application Id** field, specify the tax application code created for this report.
5. In the From date field, enter a date.
6. In the To date field, enter a date.
7. Click OK.


