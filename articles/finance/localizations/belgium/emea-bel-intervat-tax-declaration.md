---
title: INTERVAT tax declaration
description: Learn about how to set up and create the INTERVAT tax declaration for legal entities in Belgium only, including prerequisites and settings.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/02/2026
ms.reviewer: johnmichalak
ms.search.region: Belgium
ms.search.validFrom: 2016-05-31
ms.search.form: TaxIntervat
ms.dyn365.ops.version: AX 7.0.1
---

# INTERVAT tax declaration

[!include [banner](../../includes/banner.md)]
> [!NOTE]
> This feature is replaced by the VAT declaration functionality. For more information, see [VAT declaration (Belgium)](emea-bel-vat-declaration-belgium.md).

## Overview

This article provides country/region-specific information about how to set up and create the INTERVAT tax declaration for legal entities in Belgium.

You can create the INTERVAT tax declaration as an XML file. You can also preview the amounts of the value-added tax (VAT) declaration in a printable format.

The INTERVAT declaration that you create includes tax transactions from the current period. It can also include corrections from the previous period, if a transaction was posted in the previous period after that period was closed.

You can enter additional information for the declaration and manually correct data on the **Additional sales tax report boxes** page. You might need to make manual corrections if, for example, you can't print the amount of the reporting code in the INTERVAT declaration because the amount is negative. You must deduct negative amounts from the next VAT declaration, and you must complete this task manually by using corrections. Before you can indicate the corrected amount, you must indicate which sales tax reporting codes allow for corrections.

## Prerequisites

Set up the following prerequisites before you begin to work with the INTERVAT tax declaration:

- Legal entity
- Registration number
- Contact information
- Number sequences
- Posting journal
- Sales tax authorities
- Sales tax reporting codes
- Sales tax codes
- Tax exempt number

### Legal entity

1. Go to **Organization administration** > **Organizations** > **Legal entities**, and select your legal entity.
1. On the **Addresses** FastTab, create an address.
1. In the **Country/region** field, select **Belgium**.
1. Fill in other address components, and mark the address as **Primary**.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, specify the tax registration number for your company.

### Registration number

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
1. Select **Registration IDs**, and then, on the **Registration ID** tab, select **Add**.
1. In the **Registration type** field, select a value.
1. In the **Registration number** field, enter a value.
1. On the **General** tab, enter an effective date. For more information, see [Registration number](../europe/emea-registration-ids.md).

### Contact information

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
1. On the **Contact information** tab, add lines for the phone number and email address, and set them to **Primary**.

### Number sequences

1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
1. On the **Number sequences** tab, set up number sequences for the **Annual sales list ID** and **INTERVAT ID** references.

### Posting journal

1. Go to **General ledger** \> **Journal setup** \> **Posting journals**.
1. On **Journal setup**, select **Create**. The system automatically creates the voucher series.

### Sales tax authorities

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax authorities**.
1. Verify that the **Report layout** field is set to **Belgium report layout**.

### Sales tax reporting codes

- Go to **Tax** \> **Setup** \> **Sales tax** \> **Sales tax reporting codes**, and create new sales tax reporting codes.

If you select the **Sales tax correction** check box for a sales tax reporting code, you can select that code on the **Additional sales tax report boxes** page.

Examples of sales tax reporting code are provided in the [Set up sales tax reporting codes](#set-up-sales-tax-reporting-codes) section later in this article.

### Sales tax codes

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax codes**.
1. Add or select information in the fields on the **Report** and **Report – credit note** tabs.
1. Select the required values in the **Sales tax reporting codes** grid.

### Tax exempt number

1. Go to **Tax** > **Setup** > **Sales tax** > **Tax exempt numbers**.
1. For each tax-exempt number, create a record that includes the following information:

    - In the **Country/region** field, select the tax registration of the counterparty.
    - In the **Tax exempt number** field, enter the tax-exempt number of the counterparty.
    - In the **Company name** field, enter the name of the counterparty.

For more information about how to set up the VAT statement, see [VAT reporting for Europe](../europe/emea-vat-reporting.md).

## Settings

### Set up INTERVAT

Create lines on the **INTERVAT setup** page (**Tax** > **Setup** > **Sales tax** > **INTERVAT setup**). The information that you enter on this page is used when you select **Open Web site** on the **INTERVAT tax declaration** page. Create an element for each language. Set the following fields: **Language**, **Description**, and **URL**.

:::image type="content" source="../media/1_Intervat_setup.png" alt-text="Screenshot of the Intervat setup page.":::

### Set up sales tax reporting codes

For information about how to set up sales tax reporting codes, see [Set up sales tax reporting codes](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md).

If you want users to manually correct a reporting code, select the **Tax corrections** check box. The following table provides an example of sales tax reporting codes for Belgium.

| **Code and corresponding box in the VAT declaration** | **Description** | **Base/tax** |
|---|---|---|
| **Section II. Outputs** | | |
| 100 (Box 00) | Sales that are subject to a special regulation. | Base |
| 01 | Taxable supplies and services at a sales tax rate of 6 percent. The delivery of a product or service transactions at a sales tax rate of 6 percent. | Base |
| 02 | Taxable supplies and services at a sales tax rate of 12 percent. The delivery of a product or service transactions at a sales tax rate of 12 percent. | Base |
| 03 | Taxable supplies and services at a sales tax rate of 21 percent. The delivery of a product or service transactions at a sales tax rate of 21 percent. | Base |
| 44 | Services that the contractual partner owes foreign VAT for. | Base |
| 45 | Turnover that the contractual partner owes VAT for. | Base |
| 46 | Intra-community supply of goods and similar transactions (shipments). | Base |
| 47 | Other tax-free sales and other sales that are generated abroad. | Base |
| 48 | Amount of the issued credit notes, and negative corrections that are related to sales from boxes 44 and 46. | Base |
| 49 | Amount of issued credits, and negative adjustments that are related to other boxes from section II, "Outputs." | Base |
| **Section III. Inputs** | | |
| 81 | Amount of all purchases of goods, raw materials, and consumables, and related acquisition costs, excluding VAT deductible. | Base |
| 82 | Amount of miscellaneous goods and services, regardless of whether they are subject to VAT, excluding VAT deductible. | Base |
| 83 | Amount of purchases of capital goods, regardless of whether they're subject to VAT, excluding VAT deductible. | Base |
| 84 | Amount of credits received, and negative adjustments that are related to sales from boxes 86 and 88. | Base |
| 8684 | Technical reporting code for showing credit note amounts in boxes 86 and 84. | Base |
| 8884 | Technical reporting code for showing credit note amounts in boxes 88 and 84. | Base |
| 85 | Amount of credits received, and negative adjustments that are related to other boxes from section III, "Inputs.", excluding VAT amount (deductible and not deductible) | Base |
| 8185 | Technical reporting code for showing credit note amounts in boxes 81 and 85. | Base |
| 8285 | Technical reporting code for showing credit note amounts in boxes 82 and 85. | Base |
| 8385 | Technical reporting code for showing credit note amounts in boxes 83 and 85. | Base |
| 8785 | Technical reporting code for showing credit note amounts in boxes 87 and 85. | Base |
| 86 | Intra-community acquisitions and similar transactions. | Base |
| 87 | Other receipts that the person who is liable to register owes VAT for. | Base |
| 88 | Intra-community services with transfer of the survey. | Base |
| **Section IV. Taxes payable** | | |
| 54 | VAT that is payable on the turnover that is included in codes **01**, **02**, and **03**. | Tax |
| 55 | VAT that is payable on the turnover that is included in codes **86** and **88**. | Tax |
| 56 | VAT on sales that are declared in box 87, excluding imports that involve relocation of the survey. | Tax |
| 57 | VAT on imports that involve transfer of the survey. | Tax |
| 61 | Various VAT adjustments in favor of the state. | Tax |
| 63 | VAT that must be returned, as shown on the credits that are received. | Tax |
| **Section V. Taxes deductible** | | |
| 59 | Amount of deductible VAT. | Tax |
| 62 | Various VAT corrections in favor of the declarant. | Tax |
| 64 | VAT that must be recovered because of credits that are granted. | Tax |
| **Section VI. Balance** | | |
| 71 | Tax that must be paid. On the INTERVAT report, the value in this box is automatically calculated as the sum of reporting codes **54**, **55**, **56**, **57**, **61**, and **63**, minus reporting codes **59**, **62**, and **64**. | Tax |
| 72 | Tax that must be recovered. On the INTERVAT report, the value in this box is automatically calculated as the sum of reporting codes **59**, **62**, and **64**, minus reporting codes **54**, **55**, **56**, **57**, **61**, and **63**. | Tax |
| **Section VII. Deposit** | | |
| 91 | VAT that is actually owed for the period from December 1 through December 20. This code applies to the monthly declaration for December. | Tax |

> [!NOTE]
> You don't have to enter codes **71**, **72**, and **91**, because the system generates them automatically.

To set up an assignment of sales tax reporting codes to sales tax codes, go to **Sales tax codes \> Report setup/Report setup - Credit note**. Consider the following relations between sales tax reporting codes:

- If there's an amount in code **01**, **02**, or **03**, there should also be an amount in code **54**.
- If there's an amount in code **54**, there should also be an amount in code **01**, **02**, or **03**.
- If there's an amount in code **86**, there should also be an amount in code **55**.
- If there's an amount in code **87**, there should also be an amount in code **56** or **57**.
- The difference between the amount in code **54** and the sum of codes **01**, **02**, and **03** multiplied by the corresponding VAT rates can't be more than €61.97.
- The difference between the amount in code **55** and the sum of codes **84** and **86** multiplied by the corresponding VAT rates can't be more than €610.97.
- The difference between the sum of the amounts in codes **56** and **57** and the sum of codes **85** and **87** multiplied by the corresponding VAT rates can't be more than €61.97.
- The amount in code **59** should be more than the sum of codes **81**, **82**, **83**, **84**, and **85**.
- The amount in code **63** and code **85** multiplied by the corresponding VAT rates can't be more than €61.97.
- The amount in code **64** and code **49** multiplied by the corresponding VAT rates can't be more than €61.97.

### Download the format for the report

In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download the latest versions of the Electronic reporting (ER) configurations for the following VAT declaration format:

- INTERVAT format (BE)

For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Additional sales tax report boxes

1. Go to **Tax** > **Declarations** > **Sales tax** > **Additional sales tax report boxes**.
1. Select **New** to create lines that include extra information about reporting codes, such as manual corrections for the INTERVAT tax declaration. Before you close a settlement period, create the line for that period. You can create the line by posting the sales tax payment or by creating an INTERVAT declaration marked as **Update**. The following table describes the fields that you must set for a new line.

| **Field**         | **Description**                                                                                                                                                                           |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Settlement period | Select the applicable reporting period.                                                                                                                                                   |
| From date         | Enter the first day of the sales tax settlement period to calculate sales tax for. This value corresponds to the date in the **From** field on the **Sales tax settlement periods** page. |
| To date           | Enter the last date of the sales tax settlement period.                                                                                                                                   |

1. On the **General** tab, set the following fields:

- **Orders** section

| **Field**                                 | **Description**                                                                                                                                                                                                                                              |
|-------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Requests repayment of sales tax reclaimed | Select this option to request the repayment of any reclaimed sales tax.                                                                                                                                                                                      |
| Disbursement                              | Enter the amount of disbursement. A disbursement can be paid only for the month of December (monthly declaration). The disbursement corresponds to box 91 in the Belgian VAT declaration. You can set this field only if the month equals December (**12**). |
| Order deposit form                        | Select this option to order deposit pages for tax reporting purposes.                                                                                                                                                                                        |
| Nil annual listing                        | Select this option to indicate that there are no transactions to report, and that the company has no obligation to the Belgian government to declare the annual sales from the previous year.                                                                |

- **Pro-rata percentages** section

| **Field**           | **Description**                                                                                                                                                                                                                 |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Pro-rata percentage | Enter the value of the pro-rata percentage that the system exports in the **\<AdjustedValue\>** tag in the XML file.                                                                                                              |
| B1, B2, B3, B4, B5  | Enter amounts for the values of B1, B2, B3, B4, and B5, which the system exports in the **\<SpecialProRataPercentage\>** tag in the XML file, where **\<SpecialProRataGridNumber\>**=**"1"**, **"2"**, **"3"**, **"4"**, **"5"**. |

### Tax corrections

Follow these steps to enter manual correction amounts.

1. Go to **Tax** > **Declarations** > **Sales tax** > **Additional sales tax report boxes**.
1. Select **Tax corrections** \> **Adjustments** and set the following fields.

| **Field**         | **Description**                                                                                                                                                                           |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Settlement period | Select the applicable reporting period.                                                                                                                                                   |
| From date         | Enter the first day of the sales tax settlement period to calculate sales tax for. This value corresponds to the date in the **From** field on the **Sales tax settlement periods** page. |
| To date           | Enter the last day of the sales tax settlement period.                                                                                                                                    |
| Reporting code    | Select the reporting code. Only the reporting codes that you select the **Tax corrections** check box for are available during tax correction entry.                                      |
| Amount            | Enter the correction amount.                                                                                                                                                              |

> [!NOTE]
> Composed reporting codes that you use for credit notes, such as code **8185**, aren't available for selection. Nor are codes **71**, **72**, and **91**. Codes **71** and **72** are calculated automatically when Belgian sales tax reporting is run. Code **91** is entered in another way (see description of **Disbursement** field above).
>
> If you update a tax period, a voucher number and a date appear. For more information, see the description of the **Update** check box in the [Generate an INTERVAT tax declaration](#generate-an-intervat-tax-declaration) section later in this article. The period that has a voucher number and a date is a closed VAT period for Belgium. Therefore, all values on the **General** tab of the **Tax corrections** page are read-only. When you enter new transactions that have taxes for the closed VAT period, the taxes go to the next available open tax period.

## Generate an INTERVAT tax declaration

1. Go to **Tax** > **Declarations** > **Sales tax** > **INTERVAT tax declaration**.
1. Select **New declaration** to generate an INTERVAT tax declaration.
1. In the **INTERVAT: Belgian sales tax reporting** dialog box, set the following fields.

| **Field**                | **Description**                                                                                                                                                                                                                                                                                                                                                                                                            |
|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Settlement period        | Select the applicable reporting period.                                                                                                                                                                                                                                                                                                                                                                                    |
| From date                | Enter the first day of the sales tax settlement period to calculate sales tax for. This value corresponds to the date in the **From** field on the **Sales tax settlement periods** page.                                                                                                                                                                                                                                  |
| Transaction date         | Enter the date when the sales tax report is calculated. The default value is the current date. The sales tax payment is calculated for all transactions that were posted during the settlement period.                                                                                                                                                                                                                     |
| Update                   | A selected check box closes the period and creates a sales tax payment, if it wasn't already created. Therefore, all VAT transactions that are entered in this period after the update are forwarded to the next available open period. A selected check box also creates the line on the **Additional sales tax report boxes** page, if it wasn't already created. None of the values on this new line can be edited. |
| Replaced VAT declaration | Enter the identification number of the declaration to replace.                                                                                                                                                                                                                                                                                                                                                             |
| File                     | Enter the file name that the INTERVAT tax declaration exports to.                                                                                                                                                                                                                                                                                                                                                 |
| Format mapping           | Select the **INTERVAT format (BE)** ER format that you downloaded earlier.                                                                                                                                                                                                                                                                                                                                                 |

You can also close the tax period by generating a sales tax payment (**Tax** > **Declarations** > **Sales tax** > **Settle and post sales tax**).

1. Select **OK**. The system generates the INTERVAT tax declaration line and an INTERVAT XML file.
1. Review the information in the declaration.

:::image type="content" source="../media/2_Intervat_tax%20declaration.png" alt-text="Screenshot of the INTERVAT tax declaration page.":::

1. On the **General** tab, review the following fields: **INTERVAT ID**, **Date**, **Period**, **Start date**, **End date**, **Period frequency**, **Status**, and **File name**.
1. On the **Frame I: General information** tab, review the following fields. You can edit these fields, even if the period is closed. The exceptions are the fields in the **Pro-rata percentages** section. Those fields are read-only.

| **Field**                        | **Description**                                                                                                                                                                                                                                                                           |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Company name                     | The company name.                                                                                                                                                                                                                                                                         |
| Sales tax number                 | The tax registration number that the system transfers from the setting that you defined in the [Prerequisites](#prerequisites) section earlier in this article.                                                                                                                                   |
| Enterprise number                | The enterprise number that the system transfers from the setting that you defined in the [Prerequisites](#prerequisites) section.                                                                                                                                                               |
| Telephone, Email                 | Contact information that the system transfers from the setting that you defined in the [Prerequisites](#prerequisites) section.                                                                                                                                                                 |
| Request for reimbursement        | Select this check box to request a reimbursement of tax.                                                                                                                                                                                                                                  |
| Request for payment forms        | Select this check box to request payment pages for the INTERVAT tax declarations.                                                                                                                                                                                                         |
| Nil annual listing               | A selected check box indicates that this declaration is an empty declaration. The value is transferred from the **Additional sales tax report boxes** page that is described in the [Additional sales tax report boxes](#additional-sales-tax-report-boxes) section earlier in this article |
| Replaced VAT declaration         | The identification number of the declaration, to replace what you defined in the **INTERVAT: Belgian sales tax reporting** dialog box that is described earlier in this section.                                                                                                          |
| **Pro-rata percentages** section | Review the amounts in the **Pro-rata percentage**, **B1**, **B2**, **B3**, **B4**, and **B5** fields that you defined on the **Additional sales tax report boxes** page that is described in the [Additional sales tax report boxes](#additional-sales-tax-report-boxes) section.         |

On the **INTERVAT tax declaration** page, you can perform the following actions by using the buttons on the Action Pane.

| **Button**     | **Description**                                                                                                                                                                                                                                                   |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Setup          | Open the **Additional sales tax report boxes** page that is described in the [Additional sales tax report boxes](#additional-sales-tax-report-boxes) section.                                                                                                     |
| Re-create file | Recreate the INTERVAT file if the period wasn't closed.                                                                                                                                                                                                           |
| Open file      | Open the generated XML file.                                                                                                                                                                                                                                      |
| Open Web site  | Open the website (URL) that you defined on the **INTERVAT setup** page.                                                                                                                                                                                           |
| Change status  | Change the status to **Sent**. When a declaration is created, it has a status of **Created**. After you manually import the generated file that contains the INTERVAT declaration on the INTERVAT site, you can use this button to change the status to **Sent**. |
| Details        | Open the **INTERVAT details** page, where you can review the amounts in the corresponding reporting codes.                                                                                                                                                        |

## Generate an INTERVAT summary tax declaration

To print an INTERVAT tax declaration for several tax periods, follow these steps:

1. Go to **Tax** > **Inquiries and reports** > **Sales tax reports** > **INTERVAT summary tax declaration**.
1. Use the filters to specify criteria for selecting data, and then review the information on the report.

:::image type="content" source="../media/3_Intervat_summary_tax_declarations.png" alt-text="Screenshot of the generated INTERVAT summary tax declarations report.":::

## Example

The following example shows how you can set up sales tax codes and sales tax reporting codes, post transactions, and generate the INTERVAT tax declaration.

1. Go to **Organization administration \> Organizations \> Legal entities**.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter **0466.158.640**.
1. Select **Registration IDs**, add a line, and set the following values:

- **Registration type:** ENTNUM
- **Registration number:** BTW BE 0466.158.640

1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**, and set up the following sales tax codes.

| **Sales tax code** | **Percentage** | **Description**                                                                      |
|--------------------|----------------|--------------------------------------------------------------------------------------|
| BE21               | 21             | Domestic sales and purchases at a rate of 21 percent.                                |
| BE12               | 12             | Domestic sales and purchases at a rate of 12 percent.                                |
| BE6                | 6              | Domestic sales and purchases at a rate of 6 percent.                                 |
| BEEU21             | 21             | EU purchases at a rate of 21 percent where the **Use tax** option is set to **Yes**. |
| BEEU12             | 12             | EU purchases at a rate of 12 percent where the **Use tax** option is set to **Yes**. |
| BEEU6              | 6              | EU purchases at a rate of 6 percent where the **Use tax** option is set to **Yes**.  |
| BEEUS              | 21             | EU sales where the **Exempt** option is set to **Yes**.                              |

1. On the **Sales tax codes** page, on the **Report setup** FastTab, assign reporting codes to sales tax codes.

The following table shows how to assign the sales tax reporting codes to sales tax codes.

| **Sales tax code** | **Taxable sales** | **Tax-free sale** | **Sales tax payable** | **Taxable purchases** | **Sales tax receivable** | **Taxable import** | **Use tax** | **Offset use tax** |
|--------------------|-------------------|-------------------|-----------------------|-----------------------|--------------------------|--------------------|-------------|--------------------|
| BE21               | 03                |                   | 54                    |                       |                          |                    |             |                    |
| BE12               | 02                |                   | 54                    |                       |                          |                    |             |                    |
| BE6                | 01                |                   | 54                    |                       |                          |                    |             |                    |
| BEEU21             |                   |                   |                       |                       | 81                       | 86                 | 59          | 55                 |
| BEEU12             |                   |                   |                       |                       | 81                       | 86                 | 59          | 55                 |
| BEEU6              |                   |                   |                       |                       | 81                       | 86                 | 59          | 55                 |
| BEEUS              |                   | 46                |                       |                       |                          |                    |             |                    |

1. On the **Sales tax codes** page, on the **Report setup – credit note** FastTab, assign reporting codes to sales tax codes.

The following table shows how to assign the sales tax reporting codes to sales tax codes.

| **Sales tax code** | **Taxable sales CN** | **Tax-free sale CN** | **Sales tax payable CN** | **Taxable purchases CN** | **Sales tax receivable CN** | **Taxable import CN** | **Use tax CN** | **Offset use tax CN** |
|--------------------|----------------------|----------------------|--------------------------|--------------------------|-----------------------------|-----------------------|----------------|-----------------------|
| BEEU21             |                      |                      |                          |                          | 8184                        | 86                    | 59             | 55                    |
| BEEU12             |                      |                      |                          |                          | 8184                        | 86                    | 59             | 55                    |
| BEEU6              |                      |                      |                          |                          | 8184                        | 86                    | 59             | 55                    |

Instead of codes **55** and **59**, you can use corrective codes **63** and **64**.

> [!NOTE]
> The preceding configuration is just an example and depends on the structure of the sales tax codes that you use. If you want values to be calculated and transferred to the sales tax report, for each tax code that you use in the sales tax payment process, set a relevant sales tax reporting code in one or more fields on the **Report setup** tab.

1. Post the following transactions. For example, for customer invoices, go to **Accounts receivable** \> **Invoices** \> **All free text invoices**. For vendor invoices, go to **Accounts payable** \> **Invoices** \> **Invoice journal**.

| **Date**         | **Transaction type**  | **Amount net** | **VAT amount** | **Sales tax code** | **Expected tax base – reporting code**                 | **Expected tax amount – reporting code** |
|------------------|-----------------------|----------------|----------------|--------------------|--------------------------------------------------------|------------------------------------------|
| February 1, 2020 | Customer invoice      | 1,100          | 132            | BE12               | 02                                                     | 54                                       |
| February 1, 2020 | Vendor invoice (EU)   | 1,000          | 210            | BEEU21             | 86 – Base payable 81 – Base deduction                  | 55 – Tax payable 59 – Tax deduction      |
| February 2, 2020 | Vendor invoice (EU)   | \-200          | \-42           | BEEU21             | 86 – Base payable 81 – Base deduction 84 – Credit base | 55 – Tax payable 59 – Tax deduction      |
| February 1, 2020 | Customer invoice (EU) | 100            | 0              | BEEUS              | 46                                                     | Not applicable                           |

1. Go to **Tax \> Declarations \> Sales tax \> Report sales tax for settlement period**.
1. In the **Report sales tax for settlement period** dialog box, in the **Sales tax payment version** field, select **Original**.
1. Select **OK**, and review the data.

:::image type="content" source="../media/4_Intervat_tax_declaration.png" alt-text="Screenshot of the generated INTERVAT tax declaration page.":::

Notice that the amount of the credit note appears in code **84**.

1. Go to **Tax \> Declarations \> Sales tax \> Additional sales tax report boxes**.
1. Select **New** to create a line for February 2020.
1. Select **Tax corrections \> Adjustments**, and create a line.

:::image type="content" source="../media/5_Adjustments.png" alt-text="Screenshot of the Adjustments page.":::

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Settle and post sales tax**.
1. In the **Settle and post sales tax** dialog box, in the **Sales tax payment version** field, select **Original**.
1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **INTERVAT tax declaration**.
1. Select **New declaration**, and set the following values:

- **Settlement period:** MEN
- **From date:** 2/1/2020 (February 1, 2020)
- **Transaction date:** 2/29/2020 (February 29, 2020)
- **Update:** No
- **Format mapping:** INTERVAT format (BE)

:::image type="content" source="../media/6_Intervat.png" alt-text="Screenshot of the New INTERVAT tax declaration page.":::

1. Select **OK**, open the file, and review the report.

:::image type="content" source="../media/7_Intervat_XML.png" alt-text="Screenshot of the xml INTERVAT tax declaration report.":::

1. Select **Details**, and review the data.

:::image type="content" source="../media/8_Intervat_details.png" alt-text="Screenshot of the INTERVAT details page.":::

Notice that the amount in **62** code equals **200**.

## Reconciliation reports for Belgium

For information about reconciliation reports for Belgium, see [Reconciliation reports for Belgium](emea-bel-reconciliation-reports.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
