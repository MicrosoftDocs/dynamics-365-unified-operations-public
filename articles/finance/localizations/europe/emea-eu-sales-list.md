---
title: EU Sales list reporting
description: Learn about European Union (EU) Sales list reporting, including overviews on EU Sales list reporting, the reporting process, and prerequisites.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.search.validFrom: 2016-02-28
ms.search.form: EUSalesList
ms.custom: 
  - bap-template
---

# EU sales list reporting

[!include [banner](../../includes/banner.md)]

This article provides information about European Union (EU) sales list reporting.

## EU sales list reporting

A supplier that performs intra-community supplies of goods or services to businesses that are established within the European Union (EU) must submit a Declaration of Intra-Community Supplies (EU Sales list, or ESL). In general, you must submit the ESL to tax authorities no later than the last day of the month after the calendar period that the ESL covers. The supplier must state its value-added tax (VAT) identification number on the ESL and must also state, by customer, the following information:

- VAT identification number of the EU customer
- Total value of the intra-community supplies of goods and services that are made to the EU customer in that period. The supplier must also separate general supplies of goods from triangular trade supplies. A triangular trade transaction involves direct delivery of goods from the supplier's supplier to its customer when both parties are registered in other member states of the EU.

By using the ESL, tax authorities of each EU member state can verify whether VAT was paid for each intra-community transaction. The combination of listings and VAT returns lets EU member states exchange information about the flow of goods throughout the EU.

## EU sales list reporting process

You can complete the following tasks for EU sales list reporting:

- Collect information about intra-community trade transactions. An intra-community trade transaction can be a sales invoice, free text invoice, project invoice, or vendor invoice. The system identifies a transaction based on the country/region of the counterparty. The system collects intra-community trade transactions of different types into the EU Sales list table, where it represents them in the common form. Each record of the ESL table represents single transaction and consists of the VAT identifier of a counterparty and the total value of goods and services that were supplied.
- (Optional) Preview the **EU Sales list** report. You can preview and validate the **EU Sales list** report for a given period in the form of a Microsoft Excel workbook.
- Generate the **EU Sales list** report. The system generates the **EU Sales list** report in the form of an electronic file of a particular format that is specific to each member state of the EU. In general, an **EU Sales list** report contains basic information about the reporting party and the values of supplies of goods and services. The system groups the information by the country/region and VAT identifier of a counterparty.
- Close the EU Sales list reporting period. After you generate and submit the **EU Sales list** report to authorities, you can mark the records of the ESL table as **Closed**. These transactions aren't included in additional reports.

## Prerequisites

The following table shows the prerequisites that you must have in place before you start.

| Category | Prerequisite |
|----------|-------------|
| **Setup:** Legal entity | The primary address of the legal entity must be in a EU member state. On the **Legal entities** page (select **Organization administration** > **Organizations** > **Legal entities**), select your legal entity. On the **Addresses** FastTab, create an address, select a country/region and other address components, and mark the address as **Primary**. On the **Tax registration** FastTab, in the **Tax registration number** field, specify the tax registration number for your company. |
| **Setup:** Tax exempt identification parameters | Set up tax exempt identification parameters on the **Country/region parameters** page (select **Tax** > **Setup** > **Sales tax** > **Country/region parameters**). For each country/region where you have counterparties, create a record on the page, and specify the following information: **Country/region** – Select a country/region to associate with a tax exempt identification. **Sales tax** – Enter the tax exempt identification number (that is, the VAT registration number or tax exempt number prefix) for the selected country/region. **Check tax exempt number** – Select this checkbox to validate the tax exempt identification for the selected country/region. |
| **Setup:** VAT registration numbers | Create VAT registration numbers for your counterparties on the **All customers** page (go to **Sales and marketing** > **Customers** > **All customers**, select a customer record, and then select **Customers** > **Registration IDs**) or the **Vendors** page (go to **Procurement and sourcing** > **Vendors** > **Vendors**, select a vendor record, and then select **Vendors** > **Registration IDs**). On the **Registration ID** FastTab, on the **General** tab, create a record, and specify the following information: **Registration type** – Select the registration type assigned to the **VAT ID** registration category for the country/region of the counterparty. **Registration number** – Enter the VAT registration number of the counterparty. **Effective** – Select the start of the VAT registration number usage period. Alternatively, you can create a VAT registration number for your counterparties on the **Tax exempt numbers** page (go to **Tax** > **Setup** > **Sales tax** > **Tax exempt numbers**). For each tax exempt number, create a record on the page, and specify the following information: **Country/region** – Select the country/region of the tax registration of the counterparty. **Tax exempt number** – Enter the tax exempt number of the counterparty. **Company name** – (Optional) Enter the name of the counterparty. |
| **Setup:** Tax registration of counterparties | Set up tax registration information for your counterparties on either the **All customers** page (select **Sales and marketing** > **Customers** > **All customers**, select a customer record, and then select **Options** > **Change view** > **Details view**) or the **Vendors** page (select **Procurement and sourcing** > **Vendors** > **Vendors**, select a vendor record, and then select **Options** > **Change view** > **Details view**). On the **Invoice and delivery** FastTab, in the **Tax exempt number** field, select the VAT registration number. |
| **Setup:** Sales tax | Set up the tax codes to include on the **EU Sales list** report on the **Sales tax codes** page (select **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**). On the **Report setup** FastTab, for each sales tax code that should be included on the report, clear the **Excluded** checkbox. Set up sales tax parameters for items on the **Item sales tax groups** page (select **Tax** > **Indirect taxes** > **Sales tax** > **Item sales tax groups**). For each item sales tax group, select a value in the **Reporting type** field. The value that you select determines the ESL amount column that the line amount will be included in. **Blank** – The line amount is included in the **Not assigned value** column. **Item** – The line amount is included in the **Items value** column. **Service** – The line amount is included in the **Services value** column. **Investment** – The line amount is included in the **Investment value** column. This column is relevant only for Belgium. |
| **Setup:** ESL reporting configurations | Import or create electronic reporting configurations for the ESL. For information about how to create and maintain electronic reporting configurations, see the Electronic reporting documentation. |
| **Setup:** General parameters | Set up ESL reporting parameters on the **Foreign trade parameters** page (select **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**). Specify the following parameters: **EU sales list** tab: **Report cash discount** – Select this checkbox if a cash discount should be included in the value when a transaction is included on the ESL. **Transfer purchases** – Select this checkbox to include purchases on the ESL. **File format mapping** – Select the electronic reporting format to use when an electronic file is generated for the ESL. **Report format mapping** – Select the electronic reporting format to use when a preview report is generated for the ESL. **Rounding rule** – Specify a real number to use for rounding. ESL amounts are rounded to multiples of this number. **Rounding method** – Select the rounding method to use when ESL amounts are rounded (**Normal**, **Downward**, or **Rounding-up**). **Use minimum value** – Select this checkbox if you want amounts that are less than the **Rounding rule** number to be rounded up to the **Rounding rule** number. **Number of decimals** – Specify the number of decimal places to show in ESL amounts (both in electronic files and on the **ESL preview** report). **Country/region parameters** tab: Identify EU member states. For each EU member state, create a record on the page, and specify the following information: **Country/region** – Select a country/region. **Country/region type** – If the **Country/region** value is the country/region that your company is registered in, select **Domestic**. If the **Country/region** value is an EU member state other than the country/region that your company is registered in, Select **EU**. If the **Country/region** value isn't an EU member state, select **Third country/region**. **Number sequences** tab: On the line where the **Reference** value is **EU sales list**, select a number sequence code. |
| **Related transactions** | Register a sale to a customer in another EU member state. Register a free text invoice for a customer in another EU member state. Register a project invoice for a customer in another EU member state. Register an invoice from a vendor in another EU member state. |

## Working with the ESL

### Collecting information about intra-community trade transactions

Transactions of the following types are considered intra-community trade transactions:

- Sales invoices
- Free text invoices
- Project invoices
- Vendor invoices

A transaction is considered an intra-community trade transaction if the delivery address of the transaction is in a member state of the EU. For such countries/regions, a record should exist on the **Country/region parameters** tab of the **Foreign trade parameters** page, and the **Country/region type** value should be set to **EU**. Mark intra-community trade transactions in the **List code** field. By using this field, you can also separate general intra-community trade transactions from triangular trade transactions. You can collect information about intra-community trade transactions on the **EU Sales list** page (select **Tax** &gt; **Declarations** &gt; **Foreign trade** &gt; **EU Sales list**) by using the **Transfer** function. This function lets you include transactions that have amounts of different reporting types (such as items or services), according to the item sales tax groups that you specify on transaction lines. You can also apply other filters to define the transactions that should be included. The **Transfer** function creates a record on the **EU Sales list** page for each intra-community trade transaction that it includes, and specifies a counterparty account number, a country/region, a tax exempt number, an invoice number and date, and the total amounts of lines per reporting type. It also copies the **List code** value from the transaction. You can manually change the list code for a transaction on the **EU Sales list** page. The **Transfer** function creates records where the **Reporting status** value is set to **Included**. You can validate the information that is collected on the **EU Sales list** page by using the **Validate** function. You can get detailed information about the invoice (for sale direction) by using the **Totals** function.

### Generating the EU Sales list report

You can generate an **EU Sales list** report by using the **Reporting** function on the **EU Sales list** page. The function lets you select a reporting period and apply filters to define the ESL records to include. Additionally, you can specify other parameters that are specific to each country/region. You can also choose to generate a preview report, an electronic file, or both. The **Reporting** function uses the report and file format settings that you specify on the **Foreign trade parameters** page. In general, an **EU Sales list** report consists of separate lines that list the total amounts of supplies per counterparty country/region, tax exempt number, and reporting type (triangular trade transactions are included). After you generate an **EU Sales list** report for a specific period, you can mark the ESL records that are included on the report by setting the **Reporting status** value to **Reported**. To set this status, use the **Mark as reported** function on the **EU Sales list** page.

### Closing the EU Sales list reporting period

When you complete the reporting process for a specific period (for example, when tax authorities accept the **EU Sales list** report), you can mark the ESL records that are included on the report for the period by setting the **Reporting status** value to **Closed**. To set this status, use the **Mark as closed** function on the **EU Sales list** page. If you revert the closing of the period, you can mark ESL records by setting the **Reporting status** value to **Included**. These records can then be included on an **EU Sales list** report again. To set this status, use the **Mark as included** function on the **EU Sales list** page.

## List of country/region articles

| Country/region   | Link      |
|------------------|-----------|
| Austria          | [EU Sales list for Austria](../austria/emea-aut-eu-sales-list.md)|
| Belgium          |[EU sales list for Belgium](../belgium/emea-bel-eu-sales-list.md)|
| Czech Republic          |[EU Sales list for Czech Republic](../czech-republic/emea-cze-eu-sales-list.md)|
| Denmark          |[EU Sales list for Denmark](../denmark/emea-dnk-eu-sales-list.md)|
| Estonia          |[EU Sales list for Estonia](../estonia/emea-est-eu-sales-list.md)|
| Finland          |[EU Sales list for Finland](../finland/emea-fin-eu-sales-list.md)|
| France          |[EU Sales list for France](../france/emea-fra-eu-sales-list.md)|
| Germany          |[EU Sales list for Germany](../germany/emea-deu-eu-sales-list.md)|
| Hungary          |[EU Sales list for Hungary](../hungary/emea-hun-eu-sales-list.md)|
| Latvia          |[EU Sales list for Latvia](../latvia/emea-lva-eu-sales-list.md)|
| Lithuania          |[EU Sales list for Lithuania](../lithuania/emea-ltu-eu-sales-list.md)|
| Netherlands          |[EU sales list for Netherlands](../netherlands/emea-nl-eu-sales-list.md)|
| Poland          |[EU Sales list for Poland](../poland/emea-pol-eu-sales-list.md)|
| Spain          |[EU sales list for Spain (Report 349)](../spain/emea-esp-sales-list.md)|
| Sweden          |[EU Sales list for Sweden](../sweden/emea-swe-eu-sales-list.md)|
| UK (Northern Ireland)          |[EU Sales list for UK (Northern Ireland)](../united-kingdom/emea-uk-eu-sales-list.md)|

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
