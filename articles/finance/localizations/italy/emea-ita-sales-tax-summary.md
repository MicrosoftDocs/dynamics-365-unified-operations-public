---
title: Sales tax summary report
description: Learn how to generate a sales tax summary report for legal entities in Italy, including prerequisites and an outline on generate sales tax reports.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 03/04/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2016-11-30
ms.search.form: TaxAuthority, TaxPeriod
ms.dyn365.ops.version: Version 1611
ms.assetid: af07d122-5694-4de6-96bf-7bf5478b0175
---

# Sales tax summary report

This article explains how to generate a sales tax summary report for legal entities in Italy.

As of Microsoft Dynamics 365 Finance version 10.0.39, the Italian sales tax books functionality supports reporting of Italian sales tax books in the [Electronic reporting (ER) tool](/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting). It also accommodates reporting for [multiple value-added tax (VAT) registrations](../global/emea-multiple-vat-registration-numbers.md).

## Prerequisites

Before you begin, you must [configure Italian sales tax books](emea-ita-sales-tax-books.md).

## Generate a sales tax summary report

A sales tax summary report is generated as part of Italian sales tax books electronic reporting. If the **Separate summary register** checkbox is selected for the related [sales tax authority](emea-ita-vat-statements-details.md#sales-tax-authority), a separate sales tax book must be set up as summary sections in sales tax books and sales tax book sections. If the **Separate summary register** checkbox is cleared for the related [sales tax authority](emea-ita-vat-statements-details.md#sales-tax-authority), the **Print summary and payment** checkbox must be selected for one of the Italian sales tax books of the **Sales** type on the **Italian sales tax books** page.

To generate a sales tax summary report, follow these steps.

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period**. The **Report sales tax for settlement period** dialog box appears.
1. In the **Settlement period** field, select the sales tax settlement period to generate the report for.
1. In the **From date** field, specify a date in the interval of the settlement period that you want to generate the report for.
1. In the **Sales tax payment version** field, select **Original**. If the sales tax settlement period is associated with a sales tax authority that's connected to a vendor account that has an address in Italy, **Original** is the only value that can be selected.
1. Select **OK**. The **Sales tax (Italy)** dialog box appears. The **Settlement period** field shows the previously selected settlement period, for reference.
1. To generate the Italian sales tax books electronic report for a period that differs from the interval of the sales tax settlement period, use the **Variative period** checkbox. If you clear this checkbox, the **From date** and **To date** fields show the start and end dates of the period interval that the **From date** that you specified selected in the previous dialog box belongs to. If you select this checkbox, the **Last page number** value in the related **Sales tax book status** record can't be updated.
1. In the **Sales tax book type** field, select the type of sales tax book to generate the report for. If this field is blank, the report is generated for all types.
1. In the **From sales tax book** and **To sales tax book** fields, specify the sales tax books to generate the report for. If these fields are blank, the report is generated for all sales tax books.
1. In the **Printout** section, select the **Sales tax books** checkbox to generate a report that includes the details of the taxable documents in the sales tax books.
1. Select the **Sales tax summary** checkbox.
1. Select the **Sales tax payment** checkbox to generate a report that includes the **Sales tax payment** page of the report.
1. Select the **Plafond** checkbox to generate a report that includes the **Tax plafond** section of the sales tax payment report. For more information, see [Tax plafond](emea-ita-exil-tax-plafond.md).
1. In the **Language** field, select the language that you want to generate the report in.
1. In the **Update** section, select the **Update number of pages** checkbox to update the **Last page number** value in the related **Sales tax book status** record for the sales tax settlement period.

    > [!IMPORTANT]
    > To ensure correct numbering of pages, be sure to generate the Italian sales tax books electronic report with the **Update number of pages** checkbox selected at least once for each interval of the sales tax settlement period. If the **Update number of pages** checkbox is selected, and the **Attach report to Sales tax book status** checkbox is selected in the parameters of the sales tax settlement period, you can find the generated Italian sales tax books electronic report attached to the **Sales tax book status** records.

1. If you selected the **Sales tax payment** checkbox, the **Sales tax payment** FastTab is available. Set or review the following fields that are required for the sales tax payment report:

    - **Sales tax balance in period** – The sales tax balance in the period.
    - **Previous sales tax credit (-)** – Enter the amount of the previous sales tax credit.
    - **Sales tax credit for compensation (-)** – Enter the amount of the sales tax credit for compensation.
    - **Previous sales tax debit (+)** – Enter the amount of the previous sales tax debit.
    - **Sales tax paid in advance (-)** – Enter the amount of sales tax that was paid in advance.
    - **Sales tax balance** – The calculated sales tax balance for the selected period.
    - **Amount of payment** – Enter the amount of the payment.
    - **Date of payment** – Enter the date of the payment.
    - **Bank account** – Enter the bank account.
    - **Bank reference ABI** – Enter the bank reference Italian Banking Association (ABI) code.
    - **Bank reference CAB** – Enter the bank reference bank branch code (CAB).

1. On the **Run in the background** FastTab, set up batch parameters if you want to generate the report in batch mode. When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).
1. Select **OK** to generate the report. If the **Update number of pages** checkbox is selected, and the **Attach report to Sales tax book status** checkbox is selected in the parameters of the sales tax settlement period, you can find the generated Italian sales tax books electronic report attached to the **Sales tax book status** records. In addition, the **Last page number** value in the related **Sales tax book status** record for the sales tax settlement period is updated.
