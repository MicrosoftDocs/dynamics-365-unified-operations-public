---
title: Generate an Annual sales tax report U1
description: Learn how to generate an annual sales tax report U1 for Austria in PDF format.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/01/2025
ms.reviewer: johnmichalak
ms.search.region: Global

---

# Generate an Annual sales tax report U1

[!include[banner](../../includes/banner.md)]

This article describes how to generate an Annual sales tax report U1 for Austria in PDF format. 

The Austrian annual sales tax report, Form U1 (Umsatzsteuererklärung), is mandated under the Austrian Value Added Tax Act 1994 (UStG 1994) and serves as a legally required summary of a business’s VAT-relevant transactions for the fiscal year.

The Austrian annual sales tax report is used to print the sales tax information. 
This information is printed on the Umsatzsteuererklärung (U1) .pdf form that is provided by the Austrian Ministry of Finance. 

## Set up sales tax reporting codes

Use the sales tax reporting codes to generate an Annual sales tax report U1 for Austria. 
The four-digit sales tax reporting code syntax is based on the structure of the VAT statement. 
In the VAT statement, amounts are displayed in the Tax base amounts and Tax amounts columns. 
Sales tax reporting codes that begin with 10 are included in the tax boxes in the Tax base amounts column. 
Codes that begin with 11 are contained in the tax boxes in the Tax amounts column. 
The last two digits of the sales tax reporting code refer to the tax box number.

Example: The tax base amount corresponding to sales tax reporting code 1022 and the tax corresponding to the sales tax reporting code 1122 
are reported in tax box 022.
For each tax box in the VAT statement, you can create a sales tax reporting code and assign it to a sales tax code. 
These sales tax reporting codes are entered in the **Taxable sales** and **Sales tax payable** fields on the **Report setup** tab of the **Sales tax codes** form. Learn more in [Set up sales tax reporting codes](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md).

To set up sales tax reporting codes, follow these steps.

1. Select **Tax** > **Setup** > **Sales tax** > **Sales tax reporting codes**.
1. Create a new sales tax reporting code. Learn more in [Set up sales tax reporting codes](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md).
1. In the **Report layout** field, select **Default** report layout.
1. In the **Reporting code** field, enter the sales tax reporting code.
1. In the **Report text** field, enter the text to print on the report for the selected sales tax reporting code.
1. In the **Brief description** field, enter a brief description for the sales tax reporting code.
1. Close the form to save your changes.

## Set up tax number of the reporting organization

The tax number of the reporting organization, shown in the \<Steuernummer\> field of the Austrian annual sales tax report, is derived from the **Tax registration number** field of your legal entity.

The format follows the standard Austrian Steuernummer pattern: 12-345/6789.

## Generate the annual sales tax report U1

To generate the annual sales tax report U1, follow these steps.

1. Go to **Tax** > **Inquires and reports** > **Sales tax reports** > **Annual sales tax (Austria)**.
1. In the **Austrian annual sales tax report** dialog box, on the **Parameters** FastTab, set the following fields.

   |Field|Description|
   |------------|-----------|
   |From date|Select the starting date of the reporting period to include in the report.|
   |To date|Select the ending date of the reporting period to include in the report.|
   |Settlement period|Select the settlement period to include in the report.|
   |PDF file|Select or enter the file path and file name of the U1 form on which the sales tax information is printed.|

1. Select the **OK** button to generate the .xfdf file.
1. Open the generated .xfdf file using the PDF form from Austrian government website for the Form U1 (Umsatzsteuererklärung) U1.

