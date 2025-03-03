---
title: Printing configuration for Sales Bank Book Bolivia
description: Learn about the required configuration for printing a Sales Bank Book report for Bolivia. 
author: Cpicon85
ms.date: 03/03/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for Sales Bank Books for Bolivia

[!include[banner](../../includes/banner.md)]

This article explains how to set up and generate report sales bank book for Bolivia.

The bank book in Bolivia is a report that allows detailing all those customer payments equal to or greater than the amount established by the regulations of the National Tax Service (Servicio de Impuestos Nacionales). The report will allow downloading the information on a monthly basis about customer payments for sales of goods and/or services with the presentation structure requested by the tax authority.


![Sales bank book report diagram](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/ltm-sales-bank-book-report-Bo-cpicon85/articles/finance/localizations/media/LTM-Sales-bank-book.BO.png)

## Prerequisites

Before you can generate the report, the following prerequisites must be met:

- The legal entity's address must be in Bolivia.
- Both the country/region-specific LATAM feature for Bolivia and the general LATAM feature must be enabled.
- You must download the specific report from the Global repository. For more information, see [Download ER configurations from the Global repository of Configuration service](er-download-configurations-global-repo.md). 
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must create a tax application to use on the report for example Tax application id **LB** and Tax application description **Libro Bancarizacion**. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- Create a field called **List 10**, and in the reference code section add two options  **YES** and **NO**. Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).

## Common configurations for all transaction types

-	Create a document class that represent the receipt **recibo** and enable field list 10 as required. Field list 10 will allow you to set if the transaction should be included or not in the report.
-	You must configure a document class payment media called **payment documents**, and configure the tax application code accordingly if it's a check, a bank transfer, a deposit, etc. Select **unique per entry** for the document class type of each payment media. Learn more in [Document class type configuration](ltm-core-document-class-type.md).
- Configure Latam extension in Bank group field of the bank account associated with the payment media. That will bring the information related to Bank account number and tax identification.
  
### Configure payment of invoice transactions

Before receiving payments from your customer, verify that the Document class settings are configured according to the following steps: 

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class** select a document class that represent invoice **Factura** and check that you have completed the required fields for this type of document. Learn more in [Configure sales invoices for Bolivia](ltm-Configure-invoices-Bolivia.md)
1. On the Action Pane, select **Tax application**.
   1. In the **Tax application ID** field, verify the **LB** value is entered..
   1. In the **Tax application code** field, enter **2** as transaction type.
   1. In the **letter code** field, enter **FC** for invoices.
   1. In the **user define fiel 2** field, enter **2** as type supporting document.

In case of a successive tract contract, you might change **letter code** field to **CS** and enable concept 3 field of the document class to add contract number.

### Configure other payments  

When you have to receive payments for real estate sales, check the following configuration:

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class** Select a document class that represent supporting document for real estate sales **Venta de Bienes Inmuebles**. Check that you have completed the required fields for this type of document. Learn more in [Configure sales invoices for Bolivia](ltm-Configure-invoices-Bolivia.md).
1. On the Action Pane, select **Tax application**.
   1. In the **Tax application ID** field, verify the **LB** value is entered..
   1. In the **Tax application code** field, enter **1** as transaction type.
   1. In the **user define fiel 2** field, enter **430** as type supporting document.    

In case of successive tract contract you might add **letter code** field to **CS** and enable concept 3 field of the document class to add contrat number.

## Set up application-specific parameters

To set up application-specific parameters, follow these steps.

1. Open the **Electronic reporting** workspace, and select **Reporting configurations**.
1. Select **Sales Bank Book BO**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **ApplicablePaymentDocuments**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**
1. In Document classification Id select the document class that represents a receipt. 
1. If you have another document class that represents receipts repeat steps 4, 5, and 6.  

## Run Sales Bank Book BO report:

To run the **Sales bank Book BO** report, follow these steps.

1. Go to **Tax > Inquiries and reports > LATAM > Tax reporting**.
1. In the **Format mapping field**, enter or select a value.
1. Select OK.
1. In the **TAX application Id** field, specify the tax application code created for this report.
1. In the From date field, enter a date.
1. In the To date field, enter a date.
1. Select OK.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
