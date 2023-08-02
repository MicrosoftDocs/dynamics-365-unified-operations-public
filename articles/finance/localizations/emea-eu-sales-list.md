---
# required metadata

title: EU Sales list reporting
description: This article provides information about European Union (EU) Sales list reporting.
author: EvgenyPopovMBS
ms.date: 06/14/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EUSalesList
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# EU sales list reporting

[!include [banner](../includes/banner.md)]

This article provides information about European Union (EU) Sales list reporting.

## EU Sales list reporting

A supplier that is performing intra-community supplies of goods or services to businesses that are established within the European Union (EU) must submit a Declaration of Intra-Community Supplies (EU Sales list, or ESL). In general, the ESL must be submitted to tax authorities no later than the last day of the month after the calendar period that the ESL covers. The supplier must state its value-added tax (VAT) identification number on the ESL and must also state, by customer, the following information:

-   VAT identification number of the EU customer
-   Total value of the intra-community supplies of goods and services that are made to the EU customer in that period. The supplier must also separate general supplies of goods from triangular trade supplies. A triangular trade transaction involves direct delivery of goods from the supplier's supplier to its customer when both parties are registered in other member states of the EU.

By using the ESL, tax authorities of each EU member state can verify whether VAT has been paid for each intra-community transaction. The combination of listings and VAT returns let EU member states exchange information about the flow of goods throughout the EU.

## Overview of the EU Sales list reporting process
You can complete the following tasks for EU Sales list reporting:

-   Collect information about intra-community trade transactions. An intra-community trade transaction can be a sales invoice, free text invoice, project invoice, or vendor invoice. A transaction is identified based on the country/region of the counterparty. Intra-community trade transactions of different types are collected into the EU Sales list table, where they are represented in the common form. Each record of the ESL table represents single transaction and consists of the VAT identifier of a counterparty and the total value of goods and services that were supplied.
-   (Optional) Preview the **EU Sales list** report. You can preview and validate the **EU Sales list** report for a given period in the form of a Microsoft Excel workbook.
-   Generate the **EU Sales list** report. The **EU Sales list** report is generated in the form of an electronic file of a particular format that is specific to each member state of the EU. In general, an **EU Sales list** report contains basic information about the reporting party and the values of supplies of goods and services. The information is grouped by the country/region and VAT identifier of a counterparty.
-   Close the EU Sales list reporting period. After the **EU Sales list** report is generated and submitted to authorities, you can mark the records of the ESL table as **Closed**. These transactions won't be included in additional reports.

## Prerequisites
The following table shows the prerequisites that must be in place before you start.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Prerequisite</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Setup:</strong> Legal entity</td>
<td>The primary address of the legal entity must be in a EU member state. On the <strong>Legal entities</strong> page (click <strong>Organization administration</strong> &gt; <strong>Organizations</strong> &gt; <strong>Legal entities</strong>), select your legal entity. On the <strong>Addresses</strong> FastTab, create an address, select a country/region and other address components, and mark the address as <strong>Primary</strong>. On the <strong>Tax registration</strong> FastTab, in the <strong>Tax registration number</strong> field, specify the tax registration number for your company.</td>
</tr>
<tr class="even">
<td><strong>Setup:</strong> Tax exempt identification parameters</td>
<td>Set up tax exempt identification parameters on the <strong>Country/region parameters</strong> page (click <strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Sales tax</strong> &gt; <strong>Country/region parameters</strong>). For each country/region where you have counterparties, create a record on the page, and specify the following information:
<ul>
<li><strong>Country/region</strong> – Select a country/region to associate with a tax exempt identification.</li>
<li><strong>Sales tax</strong> – Enter the tax exempt identification number (that is, the VAT registration number or tax exempt number prefix) for the selected country/region.</li>
<li><strong>Check tax exempt number</strong> – Select this check box to validate the tax exempt identification for the selected country/region.</li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>Setup:</strong> VAT registration numbers</td>
<td>Create VAT registration numbers for your counterparties on the <strong>All customers</strong> page (go to <strong>Sales and marketing</strong> &gt; <strong>Customers</strong> &gt; <strong>All customers</strong>, select a customer record, and then select <strong>Customers</strong> &gt; <strong>Registration IDs</strong>) or the <strong>Vendors</strong> page (go to <strong>Procurement and sourcing</strong> &gt; <strong>Vendors</strong> &gt; <strong>Vendors</strong>, select a vendor record, and then select <strong>Vendors</strong> &gt; <strong>Registration IDs</strong>). On the <strong>Registration ID</strong> FastTab, on the <strong>General</strong> tab, create a record, and specify the following information: 
<ul>
<li><strong>Registration type</strong> – Select the registration type assigned to the <strong>VAT ID</strong> registration category for the country/region of the counterparty.</li>
<li><strong>Registration number</strong> – Enter the VAT registration number of the counterparty.</li>
<li><strong>Effective</strong> – Select the start of the VAT registration number usage period.</li>
</ul>  
Alternatively, you can create a VAT registration number for your counterparties on the <strong>Tax exempt numbers</strong> page (go to <strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Sales tax</strong> &gt; <strong>Tax exempt numbers</strong>). For each tax exempt number, create a record on the page, and specify the following information:
<ul>
<li><strong>Country/region</strong> – Select the country/region of the tax registration of the counterparty.</li>
<li><strong>Tax exempt number</strong> – Enter the tax exempt number of the counterparty.</li>
<li><strong>Company name</strong> – (Optional) Enter the name of the counterparty.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Setup:</strong> Tax registration of counterparties</td>
<td>Set up tax registration information for your counterparties on either the <strong>All customers</strong> page (click <strong>Sales and marketing</strong> &gt; <strong>Customers</strong> &gt; <strong>All customers</strong>, select a customer record, and then click <strong>Options</strong> &gt; <strong>Change view</strong> &gt; <strong>Details view</strong>) or the <strong>Vendors</strong> page (click <strong>Procurement and sourcing</strong> &gt; <strong>Vendors</strong> &gt; <strong>Vendors</strong>, select a vendor record, and then click <strong>Options</strong> &gt; <strong>Change view</strong> &gt; <strong>Details view</strong>). On the <strong>Invoice and delivery</strong> FastTab, in the <strong>Tax exempt number</strong> field, select the VAT registration number.</td>
</tr>
<tr class="odd">
<td><strong>Setup:</strong> Sales tax</td>
<td>Set up the tax codes to include on the <strong>EU Sales list</strong> report on the <strong>Sales tax codes</strong> page (click <strong>Tax</strong> &gt; <strong>Indirect taxes</strong> &gt; <strong>Sales tax</strong> &gt; <strong>Sales tax codes</strong>). On the <strong>Report setup</strong> FastTab, for each sales tax code that should be included on the report, clear the <strong>Excluded</strong> check box. Set up sales tax parameters for items on the <strong>Item sales tax groups</strong> page (click <strong>Tax</strong> &gt; <strong>Indirect taxes</strong> &gt; <strong>Sales tax</strong> &gt; <strong>Item sales tax groups</strong>). For each item sales tax group, select a value in the <strong>Reporting type</strong> field. The value that you select determines the ESL amount column that the line amount will be included in.
<ul>
<li><strong>Blank</strong> – The line amount is included in the <strong>Not assigned value</strong> column.</li>
<li><strong>Item</strong> – The line amount is included in the <strong>Items value</strong> column.</li>
<li><strong>Service</strong> – The line amount is included in the <strong>Services value</strong> column.</li>
<li><strong>Investment</strong> – The line amount is included in the <strong>Investment value</strong> column. This column is relevant only for Belgium.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Setup:</strong> ESL reporting configurations</td>
<td>Import or create electronic reporting configurations for the ESL. For information about how to create and maintain electronic reporting configurations, see the Electronic reporting documentation.</td>
</tr>
<tr class="odd">
<td><strong>Setup:</strong> General parameters</td>
<td>Set up ESL reporting parameters on the <strong>Foreign trade parameters</strong> page (click <strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Foreign trade</strong> &gt; <strong>Foreign trade parameters</strong>). Specify the following parameters:
<ul>
<li><strong>EU sales list</strong> tab:
<ul>
<li><strong>Report cash discount</strong> – Select this check box if a cash discount should be included in the value when a transaction is included on the ESL.</li>
<li><strong>Transfer purchases</strong> – Select this check box to include purchases on the ESL.</li>
<li><strong>File format mapping</strong> – Select the electronic reporting format to use when an electronic file is generated for the ESL.</li>
<li><strong>Report format mapping</strong> – Select the electronic reporting format to use when a preview report is generated for the ESL.</li>
<li><strong>Rounding rule</strong> – Specify a real number to use for rounding. ESL amounts will be rounded to multiples of this number.</li>
<li><strong>Rounding method</strong> – Select the rounding method to use when ESL amounts are rounded (<strong>Normal</strong>, <strong>Downward</strong>, or <strong>Rounding-up</strong>).</li>
<li><strong>Use minimum value</strong> – Select this check box if you want amounts that are less than the <strong>Rounding rule</strong> number to be rounded up to the <strong>Rounding rule</strong> number.</li>
<li><strong>Number of decimals</strong> – Specify the number of decimal places to show in ESL amounts (both in electronic files and on the <strong>ESL preview</strong> report).</li>
</ul></li>
<li><strong>Country/region parameters</strong> tab: Identify EU member states. For each EU member state, create a record on the page, and specify the following information:
<ul>
<li><strong>Country/region</strong> – Select a country/region.</li>
<li><strong>Country/region type</strong> – If the <strong>Country/region</strong> value is the country/region that your company is registered in, select <strong>Domestic</strong>. If the <strong>Country/region</strong> value is an EU member state other than the country/region that your company is registered in, Select <strong>EU</strong>. If the <strong>Country/region</strong> value isn&#39;t an EU member state, select <strong>Third country/region</strong>.</li>
</ul></li>
<li><strong>Number sequences</strong> tab: On the line where the <strong>Reference</strong> value is <strong>EU sales list</strong>, select a number sequence code.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Related transactions</strong></td>
<td><ul>
<li>Register a sale to a customer in another EU member state.</li>
<li>Register a free text invoice for a customer in another EU member state.</li>
<li>Register a project invoice for a customer in another EU member state.</li>
<li>Register an invoice from a vendor in another EU member state.</li>
</ul></td>
</tr>
</tbody>
</table>

## Working with the ESL
### Collecting information about intra-community trade transactions

Transactions of the following types can be considered intra-community trade transactions:

-   Sales invoices
-   Free text invoices
-   Project invoices
-   Vendor invoices

A transaction is considered an intra-community trade transaction if the delivery address of the transaction is in a member state of the EU. For such countries/regions, a record should exist on the **Country/region parameters** tab of the **Foreign trade parameters** page, and the **Country/region type** value should be set to **EU**. Intra-community trade transactions are marked in the **List code** field. Using this field, you can also separate general intra-community trade transactions from triangular trade transactions. You can collect information about intra-community trade transactions on the **EU Sales list** page (click **Tax** &gt; **Declarations** &gt; **Foreign trade** &gt; **EU Sales list**) by using the **Transfer** function. This function lets you include transactions that have amounts of different reporting types (i.e., items or services), according to the item sales tax groups that are specified on transaction lines. You can also apply other filters to define the transactions that should be included. The **Transfer** function creates a record on the **EU Sales list** page for each intra-community trade transaction that is included, and specifies a counterparty account number, a country/region, a tax exempt number, an invoice number and date, and the total amounts of lines per reporting type. It also copies the **List code** value from the transaction. You can manually change the list code for a transaction on the **EU Sales list** page. The **Transfer** function creates records where the **Reporting status** value is set to **Included**. You can validate the information that is collected on the **EU Sales list** page by using the **Validate** function. You can get detailed information about the invoice (for sale direction) by using the **Totals** function.

### Generating the EU Sales list report

You can generate an **EU Sales list** report by using the **Reporting** function on the **EU Sales list** page. The function lets you select a reporting period and apply filters to define the ESL records to include. Additionally, you can specify other parameters that are specific to each country/region. You can also choose to generate a preview report, an electronic file, or both. The **Reporting** function uses the report and file format settings that are specified on the **Foreign trade parameters** page. In general, an **EU Sales list** report consists of separate lines that list the total amounts of supplies per counterparty country/region, tax exempt number, and reporting type (triangular trade transactions are included). After you generate an **EU Sales list** report for a specific period, you can mark the ESL records that are included on the report by setting the **Reporting status** value to **Reported**. To set this status, use the **Mark as reported** function on the **EU Sales list** page.

### Closing the EU Sales list reporting period

When you've completed the reporting process for a specific period (for example, when tax authorities have accepted the **EU Sales list** report), you can mark the ESL records that are included on the report for the period by setting the **Reporting status** value to **Closed**. To set this status, use the **Mark as closed** function on the **EU Sales list** page. If you revert the closing of the period, you can mark ESL records by setting the **Reporting status** value to **Included**. These records can then be included on an **EU Sales list** report again. To set this status, use the **Mark as** **included** function on the **EU Sales list** page.

## List of country/region-specific topics

| Country/region   | Link      |
|------------------|-----------|
| Austria          | [EU Sales list for Austria](emea-aut-eu-sales-list.md)| 
| Belgium          |[EU sales list for Belgium](emea-bel-eu-sales-list.md)|
| Czech Republic          |[EU Sales list for Czech Republic](emea-cze-eu-sales-list.md)|
| Denmark          |[EU Sales list for Denmark](emea-dnk-eu-sales-list.md)|
| Estonia          |[EU Sales list for Estonia](emea-est-eu-sales-list.md)|
| Finland          |[EU Sales list for Finland](emea-fin-eu-sales-list.md)|
| France          |[EU Sales list for France](emea-fra-eu-sales-list.md)|
| Germany          |[EU Sales list for Germany](emea-deu-eu-sales-list.md)|
| Hungary          |[EU Sales list for Hungary](emea-hun-eu-sales-list.md)|
| Latvia          |[EU Sales list for Latvia](emea-lva-eu-sales-list.md)|
| Lithuania          |[EU Sales list for Lithuania](emea-ltu-eu-sales-list.md)|
| Netherlands          |[EU sales list for Netherlands](emea-nl-eu-sales-list.md)|
| Poland          |[EU Sales list for Poland](emea-pol-eu-sales-list.md)|
| Spain          |[EU sales list for Spain (Report 349)](emea-esp-sales-list.md)|
| Sweden          |[EU Sales list for Sweden](emea-swe-eu-sales-list.md)|
| UK (Northern Ireland)          |[EU Sales list for UK (Northern Ireland)](emea-uk-eu-sales-list.md)|


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
