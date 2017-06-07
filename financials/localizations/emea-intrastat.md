---
# required metadata

title: Intrastat
description: This article provides information about Intrastat reporting for the trade of goods and, in some cases, services among countries/regions of the European Union (EU). It provides an overview of the reporting process, and describes the required settings and prerequisites.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: Intrastat
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 28581
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Intrastat

[!include[banner](../includes/banner.md)]


This article provides information about Intrastat reporting for the trade of goods and, in some cases, services among countries/regions of the European Union (EU). It provides an overview of the reporting process, and describes the required settings and prerequisites.

Intrastat is the system for collecting information and generating statistics about the trade of goods among countries/regions of the European Union (EU). Intrastat reporting is required whenever a product crosses the border of another EU country/region. In several countries/regions, Intrastat reporting also applies to services. Mandatory and optional elements can be collected in Intrastat reporting. The following elements are mandatory: the value-added tax (VAT) number of the party that is responsible for providing information, the reference period, the flow (arrival or dispatch), the eight-digit commodity code, the partner member state (member state of consignment on arrivals and member state of destination on dispatches), the value of the goods, the quantity of the goods (net mass and supplementary unit), and the nature of the transaction. Countries/regions can also collect optional elements under various conditions. Some optional elements are the country/region of origin, the delivery terms, the mode of transport, a more detailed commodity code than CN8, the region of origin on dispatches and the region of destination on arrivals, the statistical procedure, the statistical value, a description of the goods, and the port/airport of loading/unloading.

## Overview of the Intrastat reporting process
The following sections describe the overall flow of information that is used for Intrastat reporting.

### 1. Enter a transaction that crosses the border of another EU country/region

A customer invoice, free text invoice, purchase invoice, project invoice, customer packing slip, vendor product receipt, or transfer order is transferred to the Intrastat journal only if the country/region type of the destination (on dispatches) or consignment (on arrivals) is **EU**. This feature was extended for Microsoft Dynamics 365 for Operations version 1611 and allows you to specify lading addresses for an intra-community transaction. If a lading address differs with a vendor business address (or customer business address for return order) the Intrastat reporting will operate with this information. When you create a sales order, free text invoice, purchase order, vendor invoice, project invoice, or transfer order, some fields that are related to foreign trade have default values in the document header or on the line. The default transaction code is taken from the corresponding field on the **Foreign trade parameters** page. The default commodity code, country/region of origin, and state/province of origin are taken from the item. You can change the default values and can also fill in other foreign trade–related information: the statistics procedure, transport method, and port.

### 2. Use the Intrastat journal to generate information about trade among EU countries/regions

For statistical purposes, you generate information about trade among EU countries/regions every month. You can transfer transactions from a free text invoice, customer invoice, customer packing slip, vendor invoice, vendor packing slip, project invoice, or transfer order, according to the transfer criteria that are set up on the **Foreign trade parameters** page. Alternatively, you can enter transactions manually. You can manually update transferred transactions in the Intrastat journal, if any updates are required. Under specific conditions that are set up on the **Compression of Intrastat** page, you can compress the transactions in the Intrastat journal. Some countries/regions let you apply a small transaction threshold. You can then report transactions that are below that threshold under the specified commodity code. You can update the commodity code on the corresponding Intrastat journal lines, based on the **Minimum limit** setting on the **Foreign trade parameters** page. You can also compress those transactions, based on the **Compression of Intrastat** setting. You can validate the completeness of the transactions in the Intrastat journal, based on the **Check setup** setting on the **Foreign trade parameters** page. The data in corresponding fields might be validated for completeness: country/region, state or province, weight, commodity code, transaction code, additional unit, port, origin, terms of delivery, transport method, and tax exempt number. Transactions that aren't completed will be marked as not valid.

### 3. Use the Intrastat journal to report information about trade among EU countries/regions

For statistical purposes, you report information about trade among EU countries/regions every month. You can print the Intrastat report, based on the **Report format mapping** settings on the **Foreign trade parameters** page. You can also generate an electronic file, based on the **File format mapping** settings on the **Foreign trade parameters** page. For more information about Intrastat reporting, including required prerequisites, see the Intrastat reporting task recordings:

-   Generate an EU Intrastat declaration,
-   Transfer transactions to the Intrastat,
-   Specifying lading address for an intra-community transaction.

## Prerequisites
The following table lists the prerequisites for Intrastat reporting.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Prerequisite</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Address setup</td>
<td>Set up International Organization for Standardization (ISO) codes for countries/regions.</td>
</tr>
<tr class="even">
<td>Legal entity</td>
<td>Set up tax exempt numbers for import/export, the branch number extension for import/export, and the Intrastat code that is assigned to the legal entity.</td>
</tr>
<tr class="odd">
<td>Product category hierarchy (sales hierarchy, procurement hierarchy)</td>
<td>Assign the Intrastat commodity codes to the category nodes on the <strong>Commodity codes</strong> tab of the <strong>Category hierarchy</strong> page. When you assign a commodity code to a parent category node, that code is applicable to all child category nodes. The selected commodity codes will be available in the <strong>Selected</strong> view when you select a commodity code in the released product details, and on sales order, purchase order, and transfer order lines.</td>
</tr>
<tr class="even">
<td>Released product details</td>
<td>Set up the following foreign trade data for released products:
<ul>
<li><strong>Commodity code</strong> – Select from either the list of selected commodities that is retrieved from assigned product categories or the full list of Intrastat commodity codes.</li>
<li><strong>Statistical charges percentage</strong></li>
<li><strong>Country/region of origin</strong> – Select the default country/region where the goods were completely obtained or produced.</li>
<li><strong>State/province of origin/destination</strong> – Select the default state/province of destination for arrivals and the state/province of origin for dispatches.</li>
<li><strong>Net weight in kg</strong></li>
</ul></td>
</tr>
<tr class="odd">
<td>Customers</td>
<td>Set up the customer delivery address in the EU country/region.</td>
</tr>
<tr class="even">
<td>Vendors</td>
<td>Set up the vendor address in the EU country/region.</td>
</tr>
<tr class="odd">
<td>Miscellaneous charges</td>
<td>Set up the miscellaneous charges code to include in the invoice amount, the statistical amount, or both. On the <strong>Charges codes</strong> page, on the <strong>Foreign trade</strong> tab, enable <strong>Intrastat invoice value</strong> to include the charges amount in the invoice value, and enable <strong>Intrastat statistical value</strong> to include the charges amount in the statistical value.</td>
</tr>
<tr class="even">
<td>Electronic reporting</td>
<td>Set up electronic reporting configurations to export Intrastat data in an electronic file that has the format that is requested by the relevant authorities, and to preview Intrastat data in a user-friendly, readable format (for example, in Microsoft Excel).</td>
</tr>
</tbody>
</table>

## Setup
The following sections describe the settings that are required for Intrastat reporting.

### Set up all required Intrastat-related lists

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>List</th>
<th>Additional information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Commodity codes</td>
<td>Set up a category hierarchy of type <strong>Commodity code</strong>, and enter all commodity codes according to the combined nomenclature list. For each commodity, you set up the following information:
<ul>
<li>The name of the commodity and the commodity code</li>
<li>The friendly name and/or translated name</li>
<li>Settings for reporting additional (supplementary) units on the <strong>Foreign trade</strong> tab. You can select the additional unit in the unit list. You can also specify whether the weight of commodities must be reported in addition to the selected additional unit.</li>
</ul></td>
</tr>
<tr class="even">
<td>Transaction codes</td>
<td>Set up the nature of the transaction according to your country's/region's requirements. For each transaction code that you set up, you must set up the rules for calculating invoice amounts and statistical amounts for transfer orders and sales/purchase orders.
<ul>
<li>For transfer orders, you set up one of the following rules for calculating invoice amounts and statistical amounts:
<ul>
<li><strong>Empty</strong> – The amount will be 0 (zero).</li>
<li><strong>Financial cost amount</strong> – The amount will be equal to the financial cost.</li>
<li><strong>Total cost</strong> – The amount will be equal to the total cost of the transaction.</li>
<li><strong>Manual</strong> – The amount will be equal to the amount that is manually specified on the transfer order line.</li>
</ul></li>
<li>For sales orders and purchase orders, you set up one of the following rules for calculating invoice amounts and statistical amounts:
<ul>
<li><strong>Empty</strong> – The amount will be 0 (zero).</li>
<li><strong>Invoice amount</strong> – The amount will be equal to the amount that is invoiced for the commodity.</li>
<li><strong>Base amount</strong> – The amount will be equal to the amount that would be invoiced before any discount is applied.</li>
</ul></li>
</ul></td>
</tr>
<tr class="odd">
<td>Transport methods</td>
<td>Set up the transport mode according to your country's/region's requirements. For each delivery mode, you can set up a default transport method on the <strong>Foreign trade</strong> tab.</td>
</tr>
<tr class="even">
<td>Ports</td>
<td>Set up the port/airport of loading/unloading if this information is collected by your country/region.</td>
</tr>
<tr class="odd">
<td>Statistics procedures</td>
<td>Set up the statistical procedure if this information is collected by your country/region.</td>
</tr>
</tbody>
</table>

### Set up rules for compressing Intrastat transactions

On the **Compression of Intrastat** page, you can select the fields to use for compression. All transactions that have the same combination of values for the selected fields in the Intrastat journal will be compressed into a single transaction when you run the Compress function in the Intrastat journal.

### Set up foreign trade parameters

Use the **Foreign trade parameters** page to set up the parameters in the following table.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tab</th>
<th>Parameters</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>General</td>
<td><ul>
<li><strong>General</strong> – Specify the following information:
<ul>
<li>The default transaction codes for sales orders, purchase orders, credit notes, and transfer orders. The transaction code that is set up for credit notes is also used as the code for physical goods return and is used for deviating physical returns versus correction credit notes.</li>
<li>The employee who is responsible for preparing Intrastat reports.</li>
</ul></li>
<li><strong>Minimum limit</strong> – Specify the settings for updating transactions that are below the threshold:
<ul>
<li>The threshold amount and weight</li>
<li>The commodity code to apply to transactions that are under the threshold</li>
</ul></li>
<li><strong>Transfer</strong> – Specify the criteria for transferring transactions to the Intrastat journal. You can specify that transactions are transferred only when the items meet one or all of the following criteria:
<ul>
<li>The items aren't service items.</li>
<li>The items have a commodity code.</li>
<li>The items have a weight.</li>
<li>The items have additional units.</li>
</ul></li>
<li><strong>Check setup</strong> – Specify the rules for validating the completeness of Intrastat data. You can select which data is validated.</li>
<li><strong>Rounding rules</strong> – Specify the following settings for rounding amounts and weights in Intrastat reporting:
<ul>
<li>The rounding rule (precision)</li>
<li>The rounding method: up, down, or normal</li>
<li>The number of decimal places for amounts and weights</li>
<li>Instructions for rounding weights that are less than 1 kilogram (kg): up to 1 kg, normal, or no rounding</li>
</ul></li>
<li><strong>Electronic reporting</strong> – Specify references to electronic reporting configurations, so that you can generate an electronic file and report.</li>
<li><strong>Commodity code hierarchy</strong> – Specify the category hierarchy of the <strong>Commodity code</strong> type that represents Intrastat commodity code CN8.</li>
</ul></td>
</tr>
<tr class="even">
<td>Agent contact information</td>
<td>Specify the agent's name, address, tax exempt number, telephone number, and fax number.</td>
</tr>
<tr class="odd">
<td>Country/region properties</td>
<td>Set the country/region of the current legal entity to <strong>Domestic</strong>. Set the country/region of EU countries/regions that participate in EU trade with the current legal entity to <strong>EU</strong>. For each country/region, you also identify country/region code for foreign trade purposes.</td>
</tr>
<tr class="even">
<td>Number sequence</td>
<td>Specify the number sequence for the Intrastat journal.</td>
</tr>
</tbody>
</table>

 



