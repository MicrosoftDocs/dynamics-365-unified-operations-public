---
title: Sales tax summary report
description: This article explains how to generate a Sales tax summary report for legal entities in Italy.
author: liza-golub
ms.date: 07/12/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: 
ms.search.region: Italy
ms.author: egolub
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 
ms.assetid: af07d122-5694-4de6-96bf-7bf5478b0175
ms.search.form: TaxAuthority, TaxPeriod
---

# Sales tax summary report

The article describes how to generate a Sales tax summary report for legal entities in Italy.

As of 10.0.39 version of Dynamics 365 Finance, the **Italian sales tax books** functionality supports reporting of Italian sales tax book in [Electronic reporting (ER) tool](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting) and accomodates reporting for [multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md).

## Prerequisites

Before you begin, you must [Configure Italian sales tax books](emea-ita-sales-tax-books.md).

## Generate Sales tax summary report

Sales tax summary report is generated as part of Italian sales tax books electronic reporting. If **Separate summary register** checkbox parameter is selected for related [Sales tax authority](emea-ita-vat-statements-details.md#sales-tax-authority), a separate sales tax book must be set up as summary sections in **Sales tax books** and **Saels tax book sections**. If **Separate summary register** checkbox parameter is not selected for related [Sales tax authority](emea-ita-vat-statements-details.md#sales-tax-authority), for one of the **Italian sales tax book** of **Sales** type the **Print summary and payment** checkbox parameter must be selected on **Italian sales tax books** page.

To generate Sales tax summary report, follow these steps.

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period**. The **Report sales tax for settlement period** dialog is shown.
2. In the **Settlement period** field, select the sales tax settlement period to generate the report for.
3. In the **From date** field, specify a date in the interval of the settlement period that you want to generate the report for.
4. In the **Sales tax payment version** field, select **Original** and click **OK** button. For **Sales tax settlement periods** associated with **Sales tax authority** connected to a **Vendor account** with address in Italy, only **Original** **Sales tax payment version** can be selected.
5. The **Sales tax (Italy)** dialog is shown. In the **Settlement period** field of **Sales tax (Italy)** dialog the previously selected **Settlement period** is displayed for information.
6. When **Variative period** checkbox of the **Sales tax (Italy)** dialog is not selected, in the **From date** and **To date** fields of **Sales tax (Italy)** dialog you can see the begining and end dates of period interval where **From date** that was selected on previouse dialog belongs to. Use **Variative period** checkbox of the **Sales tax (Italy)** dialog to generate Italian sales tax books electronic report for a period different from the interval of **Sales tax settlement period**. When **Variative period** checkbox is selected, the **Last page number** value in related **Sales tax book status** cannot be updated.
7. In the **Sales tax book type** field, select the type of sales tax book to generate the report for. If this field is blank, the report is generated for all types.
8. In the **From sales tax book** and **To sales tax book** fields, specify the sales tax books to generate the report for. If these fields are blank, the report is generated for all sales tax books.
9. In the **Printout** group of parameters, select the **Sales tax books** checkbox to generate a report that includes the details of the taxable documents in the sales tax books.
10. In the **Printout** group of parameters, select the **Sales tax summary** checkbox.
11. In the **Printout** group of parameters, select the **Sales tax payment** checkbox to generate a report that includes the **Sales tax payment** page of the report.
12. In the **Printout** group of parameters, select **Plafond** checkbox to generate a report that includes the **Tax plafond** section of the Sales tax payment report. For more information, see [Tax plafond](emea-ita-exil-tax-plafond.md).
13. In the **Printout** group of parameters, select the language that you want to generate report on in **Language** field.
14. In the **Update** group of parameters, select **Update number of pages** checkbox to update  **Last page number** value in related **Sales tax book status** record for the sales tax settlement period.

> [!IMPORTANT]
> It is important to generate **Italian sales tax books electronic report** with selected **Update number of pages** checkbox at least onece per each interval of sales tax settlement period to support correct numbering of pages. When **Update number of pages** checkbox is selected and **Attach report to Sales tax book status** checkbox is selected in parameters of the **Sales tax settlement period**, you can find the generated **Italian sales tax books electronic report** attached to the **Sales tax book status** records.

15. When **Sales tax payment** checkbox is selected, the **Sales tax payment** FastTab of the **Sales tax (Italy)** dialog is available and represents following fields necessary for sales ta payment report:
   - **Sales tax balance in period**. This field displays the sales tax balance in period.
   - **Previous sales tax credit (-)**. Enter manually previous sales tax credit amount.
   - **Sales tax credit for compensation (-)**. Enter manually sales tax credit for compensation amount.
   - **Previous sales tax debit (+)**. Enter manually previous sales tax debit amount.
   - **Sales tax paid in advance (-)**. Enter manually sales tax paid in advance.
   - **Sales tax balance**. This field displays calculated sales tax balance for selected period.
   - **Amount of payment**. Enter manually amount of payment.
   - **Date of payment**. Enter manually the date of payment.
   - **Bank account**. Enter manually the bank account.
   - **Bank reference ABI**. Enter manually the bank reference ABI.
   - **Bank reference CAB**. Enter manually the bank reference CAB.
16. On the **Run in the background** FastTab, set up batch parameters if you want to generate the report in batch mode. When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).
17. Select **OK** to generate the report. When **Update number of pages** checkbox is selected and **Attach report to Sales tax book status** checkbox is selected in parameters of the **Sales tax settlement period**, you can find the generated **Italian sales tax books electronic report** attached to the **Sales tax book status** records and the **Last page number** value in related **Sales tax book status** record for the sales tax settlement period is updated. 

