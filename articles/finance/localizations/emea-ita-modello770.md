---
# required metadata

title: Modello 770 report
description: This topic provides information about the Modello 770 report for Italy.
author: ilkond
ms.date: 07/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: Taxreport770Table_IT
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Modello 770 report

[!include [banner](../includes/banner.md)]

This topic explains how to set up, create, and export the Model 770 report that is used to report withholding tax.

The Model 770 report is an annual report that provides information about the taxes that a company withholds when it pays contractors and self-employed vendors. Companies remit the withheld taxes directly to the government throughout the year. At the end of the year, the company creates and transmits the Model 770 report. This report itemizes the payments that were made to each contractor and self-employed vendor, and the taxes that were withheld from those payments. The Model 770 report contains information only about contractors and self-employed vendors whose taxes were withheld from payments. 

The following types of records are supported:
- Record A: Declaration header
- Record B: Company information and other additional information of declaration
- Record D: Operations ST, SV, SX , DI 
- Record Z: Quantity of reported records by type


## General settings that are required for the Model 770 report
Complete the following tasks before you create a Model 770 report:

- Set up withholding tax codes, withholding tax groups, withholding tax limits, and withholding tax values. For more information, see [Set up withholding tax](../general-ledger/tasks/set-up-withholding-tax.md) and [Withholding tax for Italy](emea-ita-withholding-tax.md).
- Pay vendor invoices, and withhold taxes from the payments.
- Set up Italian sales tax books. For more information, see [Italian sales tax books](emea-ita-fiscal-books.md).

## Set up address information
Use the **Address setup** page to set up the country/region code, state and region codes, and county and municipality codes for a contractor or self-employed vendor who should be included on a Model 770 report. You must set up address information for all contractors and self-employed vendors for whom you withhold taxes from payments. For information about the address codes, see the instructions that the Italian government has published for the Model 770 report on the [Italian Revenue Agency](https://www.agenziaentrate.gov.it) website.

1. Select **Organization administration** > **Addresses** > **Address setup**.
2. Select **Country/region**, and then, in the **Country/region** field, enter the two-letter International Organization for Standardization (ISO) country/region code for Italy.
3. Select **State/province**, and then enter the identification code of the state and the two-digit IT region code for the contractors or self-employed vendors.

    > [!NOTE]
    > Use the numeric state code, not the state abbreviation.

4. Select **County**, and then, in the **IT county code** field, enter the two-letter ISO county code for the contractors or self-employed vendors.
5. Select **City**, and then, in the **IT municipality code** field, enter the four-character Italian municipality code for the contractors or self-employed vendors. The municipality code consists of a letter and three numbers.
6. Select the **ZIP/postal codes** link, and then, in the **ZIP/postal code** field, enter the Italian postal code.

## Set up a fiscal code for the legal entity
The fiscal code is included on the Model 770 report so that the Italian government can identify your legal entity.

1. Select **Organization administration** > **Organizations** > **Legal entities**.
2. On the **Registration numbers** FastTab, in the **Fiscal code** field for Italy, enter the fiscal code of the legal entity.

## Set up a number sequence for the Model 770 report
Use the **General ledger parameters** page to set up a number sequence for the Model 770 report.

1. Select **General ledger** > **Ledger setup** > **General ledger parameters**.
2. Select the **Number sequences** link, and then, in the **Number sequence code** field, select a number sequence for the **Model ID** reference.

## Set up related information for vendors
1. Select **Accounts payable** > **Vendors** > **All vendors**, and then select a required vendor.
2. On the **Invoice and delivery** FastTab, in the **Fiscal code** field, enter the fiscal code of the vendor.

    > [!NOTE]
    > For self-employed vendors who aren't required to pay value-added tax (VAT), enter the personal fiscal code of the individual. If a vendor is required to pay VAT, enter the VAT registration number (partita IVA) that the Italian tax authority provides as the fiscal code of the vendor.

3. On the **Invoice and delivery** FastTab, select the **Calculate withholding tax** check box. Select a withholding tax group to activate the calculation when a payment is entered.
4. On the **Purchasing demographics** FastTab, select the county where the vendor was born.
5. If the vendor is an heir to the company, select the **Heir** check box.

## Set up Electronic reporting parameters
Download the *actual versions* of the following Electronic reporting (ER) configurations:

- **Data model:** Italian tax reports model
- **Format:** Modello770 report (IT)
 
For instruction about how to download ER configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Create and export the Model 770 report
The Model 770 report exports the information to an ASCII file that will be submitted to the tax authorities. The name of the ASCII file must be \[company fiscal code\] 77S\[*YY*\].77s, where **YY** is the last two digits of the filing year. For more information about how to complete and file the Model 770 report, see the [Italian Revenue Agency](https://www.agenziaentrate.gov.it) website.

1. Select **Tax** > **Inquiries and reports** > **Withholding tax reports** > **Withholding tax - Model 770**.
2. Create a new report. The report is numbered according to the number sequence that you set up for the **Model ID** reference on the **General ledger parameters** page.
3. In the **Filing year** field, enter the year for the tax filing. For example, enter **2017** as the filing year for the tax year 2016. The default value is the current calendar year.
4. In the **Report format mapping** field, select the preliminary related format configuration that you downloaded in **Electronic reporting**.
5. On the **Report information** FastTab, in the **ATECOFIN Code** field, enter the company's ATECOFIN code. This code is defined on the **Italian sales tax books** page.
6. In the **Declaration type** field, select the declaration type of the Model 770 report:

    - **Integrative** – You can compile and submit a new report if you've already submitted a report that requires corrections.
    - **Corrective** – The report that you're creating is a correction of a previous report.
    - **Original** – The Model 770 report is an original report.

7. In the **Exceptional event** field, select any preliminary defined exceptional event that your company was subject to during the tax year.
8. In the **Status** field, select the operational status of the company:

    - **Normal operation** – The company is operating as usual. This option is selected by default.
    - **In liquidation** – The company is in liquidation.
    - **In bankruptcy** – The company is in bankruptcy. If you select this option, the **Bankruptcy date** field becomes available.
    - **Business closed** – The company's operations are closed.

9. In the **Situation** field, select the type of tax period:

    - **Normal tax period** – The report covers the usual tax period. This option is selected by default.
    - **Liquidation tax period** – The report covers the tax period when the company was in liquidation.
    - **Tax period after bankruptcy** – The report covers the tax period after the company filed for bankruptcy.
    - **Tax period when liquidation ended** – The report covers the tax period when the company's liquidation ended.
    - **IRES transformation tax period** – The report covers the tax period that is specified by the Imposta sul Reddito delle Società (IRES), or corporate income tax, when the company underwent a transformation.

10. In the **Editorial comments** field, select the section that the company must file the withheld tax for.

    > [!NOTE] 
    > The default section is Section II. Select a section according to the instructions that the Italian government has published for the Model 770 report on the [Italian Revenue Agency](https://www.agenziaentrate.gov.it) website.

11. In the **Type of declarer** field, specify the type of declarer who sends the tax declaration to the tax authority:

    - **Filing for same legal entity** – You're sending the Model 770 report for the same legal entity that the withholding transaction is transferred for.
    - **Filing for other legal entity** – You're sending the Model 770 report on behalf of another legal entity.
    - **Filing through fiscal assistance center (CAF)** – The Model 770 report is filed through the fiscal assistance center (CAF).

12. Depending on the value that you selected in the **Type of declarer** field, fill in the following related fields: **Fiscal code**, **CAF inscription number**, **CAF obligation**, **CAF fiscal code**, and **CAF transmission date**.
13. In the **Signatory** field, select the employee who signed the report on behalf of the company.
14. In the **Role** field, select the employee's role.
15. In the **First date in role** field, select the date when the employee was assigned to the role that you selected in the **Role** field.
16. Fill in the following fields to specify the details of the signatory: **Signatory fiscal code**, **Birth county**, and **Birth city or foreign country**.
17. If the employee is a foreign national, select the **Foreign resident** check box.
18. If you selected the **Foreign resident** check box, fill in the following fields to specify the details of the employee who is a foreign national: **Country/region**, **Foreign state, province, and county**, **Place of residence**, **Foreign address**, and **Foreign fiscal code**.
 
    > [!NOTE] 
    > These fields are available only if you selected the **Foreign resident** check box.

19. On the **Addresses** FastTab, fill in the details of the postal address and fiscal address.
20. On the **Withholding tax transactions** FastTab, select **Transfer** to transfer the vendor payment and withholding transactions to the Model 770 report. Verify the transactions against your records and the **Withholding tax - yearly report** report.
21. Select **Validate** to validate the data that you set up for vendors and the company.
22. You can use the **Reset** button to reset the values on all the tabs.
23. Select **Export**, and then, on the **Export** page, in the **File name** field, specify the name of the compressed file to download. This compressed file contains the Model 770 report as an ASCII file.
24. Select the **Final export** check box to start the import process by bypassing the validation logic in the government import tool. You can also select this check box if you're working with a report that was previously submitted and rejected, but that you consider correct and complete per the available information that is published on the [Italian Revenue Agency](https://www.agenziaentrate.gov.it) website.
25. Select **OK** to export the Model 770 report.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
