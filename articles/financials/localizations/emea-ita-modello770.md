---
# required metadata

title: Modello 770 report
description: This topic provides information about the Modello 770 report for Italy.
author: ilkond
manager: AnnBe
ms.date: 11/07/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
# ms.search.validFrom: 
# ms.dyn365.ops.version: 

---

# Modello 770

[!include[banner](../includes/banner.md)]

This topic explains how to set up, create and export the Model 770 report used for Withholding tax reporting. 

The Model 770 report is an annual report that provides information about the taxes that are withheld by a company when the company pays contractors and self-employed vendors. Companies remit the withheld taxes directly to the government throughout the year. At the end of the year, the company generates and transmits the Model 770 report, which itemizes the payments that were made and the taxes that were withheld, to each vendor. The Model 770 report contains only information about contractors and self-employed vendors for whom taxes were withheld from payments. 

## General settings required for Model 770 reporting 
Complete the following tasks before you generate a Model 770 report :

-   Set up withholding tax codes, withholding tax groups, withholding tax limits, and withholding tax values. For more information, see  [Set up withholding tax](../general-ledger/tasks/set-up-withholding-tax.md) and [Withholding tax for Italy](emea-ita-withholding-tax.md).
-   Pay vendor invoices and withhold taxes from the payments.
-   Set up Italian sales tax books. For more information, see [Italian sales tax books](emea-ita-fiscal-books.md).

## Set up address information
Use the Address setup form to set up the country code, state and region code, and county and municipality codes for a self-employed vendor or contractor to include in a Model 770 report. You must set up address information for all self-employed vendors and contractors for whom you withhold taxes from payments. For information about the address codes, see the Italian government’s instructions for the Model 770 report published on the [Italian Revenue Agency](www.agenziaentrate.gov.it) website. 

 1. Click **Organization administration** > **Addresses** > **Address setup.**
 2. Click **Country/region**.  
 3. In the **Country/region** field, enter the two-letter International Organization for Standardization (ISO) country code for Italy.
 4. Click **State/province** and then enter the identification code of the state and two-digit IT region code for the self- employed vendors or contractors.
  > [!NOTE] 
  > Use the numeric state code, not the state acronym.
    
 5. Click **County** and enter the two-letter ISO county code for vendors or contractors in the **IT county code** field. 
 6. Click **City** and then enter the four-character Italian municipality code for vendors or contractors in the **IT municipality code** field. The code consists of a letter and three numbers.
 7. Click the **ZIP/postal codes** link, and then in the **ZIP/postal code**
    field, enter the Italian postal code

## Set up a fiscal code for the legal entity
The fiscal code is included in the Model 770 report to allow the Italian government to identify your legal entity.

 1. Click **Organization administration** > **Organizations** > **Legal entities**
 2. Click the **Registration numbers** FastTab, and then in the **Fiscal code** field fo Italy, enter the fiscal code of the legal entity.
 
## Set up a number sequence for the Model 770 report
Use the **General ledger parameters** to set up a number sequence for the Model 770 report.

 1. Click **General ledger ** > **Ledger setup** > **General ledger parameters** 
 2. Click the **Number sequences** link, and then in the **Number sequence code** field, select a number sequence for the **Model ID** reference.

## Set up related information for vendors
 1. Click **Accounts payable ** > **Vendors** > **All vendors** and select a required vendor.
 2. Click the **Invoice and delivery** FastTab, and then in the **Fiscal code** field, enter the fiscal code of the vendor.
  > [!NOTE]
  > For self-employed vendors who are not required to pay VAT, enter the personal fiscal code of the individual. If the vendor is required to pay VAT, enter the VAT registration number (partita IVA) provided by the Italian tax authority as the fiscal code of the vendor. 
 3. On the **Invoice and delivery** FastTab, select the **Calculate withholding tax** check box. Select a withholding tax group to activate the calculation when a payment is entered.
 4. Click the **Purchasing demographics** FastTab and then select the county where the vendor was born. 
 5. Select the **Heir** check box if the vendor is an heir to the company.
 
## Set up Electronic reporting parameters
Download the *actual versions* of the following Electronic reporting configurations:
  - Data model: **Italian tax reports model**
  - Format: **Modello770 report (IT)**
 
See the instruction on how to download the Electronic reporting configurations:  [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs?toc=dynamics365/unified-operations/fin-and-ops/toc.json)

## Create and export the Model 770 report
The Model 770 report exports the information to an ASCII file which will be submitted to the tax authorities. The name of the ASCII file must be [*company fiscal code*] 77S[*YY*].77s, where YY is the last two digits of the filing year. For more information about completing and filing the Model 770 report, see the [Italian Revenue Agency](www.agenziaentrate.gov.it) website.

 1. Click **Tax** > **Inquiries and reports** > **Withholding tax reports** > **Withholding tax - Model 770**.
 2. Create a new report. The report is numbered according to the number sequence that you set up for the **Model ID** reference on the Number sequences link in the **General ledger parameters**.
 3. In the **Filing year** field, enter the year for the tax filing. For example, enter 2017 as the filing year for the tax year 2016. The default value is the current calendar year. 
 4. In the **Report format mapping** field, select the related format configuration which was preliminary downloaded in **Electronic reporting**.
 5. Click the **Report information** FastTab, and then in the **ATECOFIN Code** field, enter the company’s ATECOFIN code. This code is defined in the **Italian sales tax books** form.
 6. In the **Declaration type** field, select the declaration type of the Model 770 report from the following options:  
  - **Integrative** – Indicates that you can compile and submit a new report if you have already submitted a report that requires corrections.
  - **Corrective** – Indicates that the report to be generated is a correction to a previous report.
  - **Original** – Indicates that the Model 770 report is an original report.

 7. In the **Exceptional event** field, select any preliminary defined exceptional event that your company was subject to during the tax year.
 8. In the **Status** field, select the operational status of the company from the following options:
   - **Normal operation** – The company is operating as usual. This option is displayed by default.
   - **In liquidation** – The company is in liquidation.
   - **In bankruptcy** – The company is in bankruptcy. The **Bankruptcy date** field is available if this status is selected.
   - **Business closed** – The company’s operations are closed.
  
 9. In the **Situation** field, select the tax period type from the following options:
   - **Normal tax period** – The report covers the usual tax period. This option is displayed by default.
   - **Liquidation tax period** – The report covers the tax period when the company was in liquidation.
   - **Tax period after bankruptcy** – The report covers the tax period after the company filed bankruptcy.
   - **Tax period when liquidation ended** – The report covers the tax period when the company’s liquidation ended.
   - **IRES transformation tax period** – The report covers the tax period specified by the Imposta sul Reddito delle Società (IRES), or corporate income tax, when the company underwent a transformation.

 10. In the **Editorial comments** field, select the section for which the company must file the withheld tax.
> [!NOTE] 
> The default value is Section II. You can select the section based on the Italian government’s instructions for the Model 770 report published on the [Italian Revenue Agency](www.agenziaentrate.gov.it) website.

 11. In the **Type of declarer** field, specify the type of declarer who sends the tax declaration to the tax authority from the following options: 
  - **Filing for same legal entity** – Indicates that you are sending the Model 770 report for the same legal entity for which the withholding transaction is transferred. 
  - **Filing for other legal entity** – Indicates that the Model 770 report is sent on behalf of another legal entity. 
  - **Filing through fiscal assistance center (CAF)** – Indicates that the Model 770 report is filed through the fiscal assistance center (CAF). 

 12. Depending on the selected **Type of declarer** fill in the following related fields: **Fiscal code**, **CAF inscription number**, **CAF obligation**, **CAF fiscal code** and **CAF transmission date**.
 13. In the **Signatory** field, select the employee who signed the report on behalf of the company. 
 14. In the **Role** field, select the employee’s role from the list of available options.
 15. In the **First date in role**, select the date when the employee was assigned to the role specified in the **Role** field.
 16. Fill in **Signatory** details in the following fields: **Signatory fiscal code**, **Birth county** and **Birth city or foreign country**.
 17. In the field **Foreign resident**, select this check box if the employee is a foreign national.
 18. Fill in the following details of foreign residence: **Country/region**, **Foreign state, province, and county**, **Place of residence**, **Foreign address** and **Foreign fiscal code**.
 > [!NOTE] 
 > These fields are available only if you select the **Foreign resident** check box.
 19. Click the **Addresses** FastTab, and fill in Postal address details and Fiscal address details.
 20. Click the **Withholding tax transactions** FastTab, and then click **Transfer** button to transfer the vendor payment and withholding transactions to the Model 770 report. Verify the transactions with your records and with the **Withholding tax - yearly report**.
 21. Click **Validate** button to validate the data that you set up for vendors and the company.
 22. You can use **Reset** button to reset the values on all of the tabs.
 23. Click **Export** button to open the **Export** form, and then in the **File name** field, specify the name of the compressed file for downloading which will contain the Model 770 report as an ASCII file.
 24. Select the **Final export** check box to initiate the import process by bypassing the validation logic in the government import tool. You can also select this check box if you are working with a previously submitted report that was rejected but that you consider correct and complete in terms of available information published on the [Italian Revenue Agency](www.agenziaentrate.gov.it) website. 
 25. Click **OK** to export the Model 770 report. 


