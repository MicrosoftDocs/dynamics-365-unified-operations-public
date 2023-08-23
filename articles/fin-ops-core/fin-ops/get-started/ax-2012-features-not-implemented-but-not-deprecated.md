---
# required metadata

title: AX 2012 features that were postponed
description: This article lists features of Microsoft Dynamics AX 2012 that were postponed, and indicates whether the features have been implemented since the AX 7.0 release.
author: sericks007
ms.date: 09/20/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 26793616-9b3f-41f5-8500-6983769c51d8
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---

# AX 2012 features that were postponed

[!include [banner](../includes/banner.md)]

This article lists features of Microsoft Dynamics AX 2012 that were postponed. These features weren't implemented in Microsoft Dynamics AX 7.0. In the following table, the **Current status** column indicates whether the feature has been implemented since the AX 7.0 release.

For a detailed list of the release date for each version, see [Software lifecycle policy and cloud releases](../../dev-itpro/migration-upgrade/versions-update-policy.md).

<table>
<thead>
<tr>
<th>AX 2012 feature that was postponed</th>
<th>Description</th>
<th>Current status (as of February 2019)</th>
</tr>
</thead>
<tbody>
<tr>
<td>Absence management in Human resources</td>
<td>Functionality for entering absence transactions isn't included. Additionally, functionality for approving absence transactions as a manager isn't included. Setup capabilities that are required for integration with other modules are available through the <strong>Human Resources 2</strong> configuration key.</td>
<td>Implemented in Dynamics 365 Human Resources</td>
</tr>
<tr>
<td>Alerts</td>
<td>Alerts help users keep track of data changes in the system.</td>
<td>Implemented in Platform update 15</td>
</tr>
<tr>
<td>Bank payment order for Latvia and Lithuania</td>
<td>You can print a payment order for Latvia and Lithuania. This feature will be available in a future update.</td>
<td>Not implemented</td>
</tr>
<tr>
<td>Bankgirot AP return format for Sweden</td>
<td>The Bankgirot return format is used to import bank return messages. This feature will be available in a future update.</td>
<td>Not implemented</td>
</tr>
<tr>
<td>Client drag-and-drop</td>
<td>The web client controls have application programming interfaces (APIs) for drag-and-drop operations, but these APIs are based on the deprecated desktop client technology and they require a redesign so that they work on the new web client platform. APIs that support drag-and-drop operations will be reviewed for inclusion in a future update.</td>
<td>Not implemented</td>
</tr>
<tr>
<td>Client right-to-left (RTL) layout</td>
<td>RTL layout is now supported.</td>
<td>Implemented in Platform update 2</td>
</tr>
<tr>
<td>Cost accounting</td>
<td>The <strong>Cost accounting</strong> module is designed to meet the requirements of internal costs and profitability reports at multiple organizational levels. To define the cost object level, the module depends on a correct mapping of financial dimensions. The module lets you perform advanced allocations of cost origin from expenditures that are registered in the general ledger or budget. It also lets you compare realized costs and budgeted costs.</td>
<td>Implemented in version 1611</td>
</tr>
<tr>
<td>Customer self-service (CSS)</td>
<td>CSS lets you create approved customer records. It also allows users to view selected product catalogs, order items, and view the status of invoices. Additionally, CSS lets you create and follow return orders.</td>
<td>Not implemented</td>
</tr>
<tr>
<td>Customizable help topics</td>
<td>The ability to create customized help topics has not yet been implemented. Custom task guides and custom field help are available. This feature will be available in a future update.</td>
<td>Not implemented</td>
</tr>
<tr>
<td>Employee self-service (ESS)</td>
<td>ESS shows employees several tiles that have task-related and career-related information on a single page. Employees can view pending work items and click links that open pages where they can take action on their tasks. ESS pages also show employees the status of their certifications, when their next performance reviews are scheduled, skills, goals, and compensation information, and other information, such as balances for vacation and sick time. Employees can also access a company directory from their ESS page.</td>
<td>Implemented in version 1611</td>
</tr>
<tr>
<td>External questionnaire and recruiting functionality</td>
<td>Functionality for externally posting questionnaires and open jobs will be added to Human Resources in a future update.</td>
<td>External questionnaire functionality hasn't been implemented.
<p>Recruiting functionality is available in Microsoft Dynamics 365 Talent: Attract.</p>
</td>
</tr>
<tr>
<td>Fiscal printers for Poland</td>
<td>Integration with Polish fiscal printers enables the required information to be sent to the fiscal printer in the correct format during invoice posting. Examples of Polish fiscal printers include the Posnet Thermal and Elzab Omega printer types. This feature will be available in a future update.</td>
<td>Not implemented</td>
</tr>
<tr>
<td>General budget reservations</td>
<td>The General budget reservations document is sometimes referred to as a commitment. Public sector entities often use this document to set aside or earmark budgeted funds so that they aren't available for other purposes.</td>
<td>Implemented in version 8.1</td>
</tr>
<tr>
<td><strong>Graphics</strong> tab on the <strong>Fixed asset value model</strong> and <strong>Depreciation book profile</strong> pages</td>
<td>The chart shows the depreciation, accumulated depreciation, and net book value over time. Users can click the <strong>Data</strong> tab to view more detailed information than the chart shows. This chart will be redesigned in a future update.</td>
<td>Not implemented</td>
</tr>
<tr>
<td>Intelligent Data Management Framework (IDMF)</td>
<td>IDMF is an add-on tool that lets system administrators optimize performance. IDMF assesses the health of the application, analyzes current usage patterns, and helps reduce database size.</td>
<td>Not implemented</td>
</tr>
<tr>
<td>Microsoft Project client integration</td>
<td>The Microsoft Project client is integrated with projects.</td>
<td>Implemented in version 7.2 (July 2017 update)</td>
</tr>
<tr>
<td>Procurement site</td>
<td>In previous versions, the Employee self-service procurement site lets you enter requisitions for employees, view the status of an order (created, received, or receipt confirmed), and request onboarding of a new vendor. You could configure different procurement catalogs to show on the site depending on policy. You could also design procurement catalogs by adding new nodes. In the current version, procurement catalog capabilities are reduced and are used only to limit the products that can be ordered for an organization. The structure is always based on the Procurement categories hierarchy. Additionally, on the procurement site the employee could approve a vendor invoice and confirm receipts in relation to the requisitions and derived purchase orders.</td>
<td>Not implemented</td>
</tr>
<tr>
<td>Secure global address book</td>
<td>The ability to help secure the global address book by legal entity and address book is not available. This feature will be available in a future update.</td>
<td>Not implemented</td>
</tr>
<tr>
<td>Specifications for Electronic reporting (ER) payment formats</td>
<td>Currently, you must enter the payment format specifications manually. In a future update, you will be able to select payment format specifications in a list. The following payment specifications are currently supported per payment format.
[!NOTE] Values for these supported payment specifications are used as payment specification parameters on the <strong>Payment specification</strong> page for a selected method of payment.
<p><strong>BTL91 for the Netherlands</strong></p>
<table>
<thead>
<tr>
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr>
<td>ChqBen</td>
<td>Cheque, Begunstigde</td>
</tr>
<tr>
<td>ChqOff</td>
<td>Cheque, Kantoor opdrachtgever</td>
</tr>
<tr>
<td>ChqPri</td>
<td>Cheque, Opdrachtgever</td>
</tr>
<tr>
<td>TrfBenBen</td>
<td>Overboeking Begunstigde/Begunstigde</td>
</tr>
<tr>
<td>TrfBenBenUrg</td>
<td>Overboeking Begunstigde/Begunstigde Spoed</td>
</tr>
<tr>
<td>TrfEurBen</td>
<td>Overboeking Euro/Begunstigde</td>
</tr>
<tr>
<td>TrfEurBenUrg</td>
<td>Overboeking Euro/Begunstigde Spoed</td>
</tr>
<tr>
<td>TrfEurEur</td>
<td>Overboeking Euro/Euro</td>
</tr>
<tr>
<td>TrfEurEurUrg</td>
<td>Overboeking Euro/Euro Spoed</td>
</tr>
<tr>
<td>TrfForBen</td>
<td>Overboeking VV-rekening/Begunstigde</td>
</tr>
<tr>
<td>TrfForBenUrg</td>
<td>Overboeking VV-rekening/Begunstigde Spoed</td>
</tr>
<tr>
<td>TrfForFor</td>
<td>Overboeking VV-rekening/VV-rekening</td>
</tr>
<tr>
<td>TrfForForUrg</td>
<td>Overboeking VV-rekening/VV-rekening Spoed</td>
</tr>
</tbody>
</table>
<p><strong>Betalingsservice for Denmark</strong></p>
<table>
<thead>
<tr>
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr>
<td>B0112</td>
<td>BS-B 0112: Lang tekst &amp; adresse</td>
</tr>
<tr>
<td>B0113</td>
<td>BS-B 0113: Erstat. bet. lang tekst</td>
</tr>
<tr>
<td>T0112</td>
<td>BS-T 0112: Lang tekst &amp; adresse</td>
</tr>
<tr>
<td>T0117</td>
<td>BS-T 0117:FIK;kort frist;lang tekst&amp;adr.</td>
</tr>
</tbody>
</table>
<p><strong>Nordea vendor for Denmark</strong></p>
<table>
<thead>
<tr>
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr>
<td>56</td>
<td>Currency account transfer between Nordea accounts in Denmark</td>
</tr>
<tr>
<td>47</td>
<td>Domestic check</td>
</tr>
<tr>
<td>45</td>
<td>Domestic transfer</td>
</tr>
<tr>
<td>50</td>
<td>Express transfer</td>
</tr>
<tr>
<td>55</td>
<td>Intercompany transfer (domestic)</td>
</tr>
<tr>
<td>51</td>
<td>Intercompany transfer to a foreign bank</td>
</tr>
<tr>
<td>54</td>
<td>International check</td>
</tr>
<tr>
<td>52</td>
<td>Nordea intercompany payment</td>
</tr>
<tr>
<td>43</td>
<td>Request for transfer</td>
</tr>
<tr>
<td>46</td>
<td>Transfer form/giro payment</td>
</tr>
</tbody>
</table>
<p><strong>ISO20022 Credit transfer (CH)</strong></p>
<table>
<thead>
<tr>
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Tp1.ESROPS</td>
<td>Type 1 - ESR orange payment slip</td>
</tr>
<tr>
<td>Tp21.ISR1SPS</td>
<td>Type 2.1 - IS red 1 stage payment slip</td>
</tr>
<tr>
<td>Tp22.ISR2SPS</td>
<td>Type 2.2 - IS red 2 stage payment slip</td>
</tr>
<tr>
<td>Tp7.Dmstc</td>
<td>Type 7 - Domestic postal order</td>
</tr>
<tr>
<td>TpE1.PSWR</td>
<td>Type E1 - Payment slip with reference</td>
</tr>
<tr>
<td>TpE2.PSWN</td>
<td>Type E2 - Payment slip with notifications</td>
</tr>
</tbody>
</table>
<p><strong>AvtaleGiro (NO)</strong></p>
<table>
<thead>
<tr>
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Varsling</td>
<td>AvtaleGiro-trans with notification</td>
</tr>
</tbody>
</table>
<p><strong>AutoGiro (NO)</strong></p>
<table>
<thead>
<tr>
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Melding</td>
<td>Autogiro-trans with notification</td>
</tr>
</tbody>
</table>
<p><strong>eFaktura (NO)</strong></p>
<table>
<thead>
<tr>
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Reklame</td>
<td>Include advertising flag</td>
</tr>
</tbody>
</table>
<p><strong>ISO20022 Credit transfer (DK)</strong></p>
<table>
<thead>
<tr>
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr>
<td>EasyAccountTransfer</td>
<td>Easy-account with CVR (NKV)</td>
</tr>
<tr>
<td>Paym_slip</td>
<td>Transfer forms (OCR)</td>
</tr>
</tbody>
</table>
<p><strong>ISPAG-CNAB240 format (BR)</strong></p>
<table>
<thead>
<tr>
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr>
<td>A</td>
<td>OP (payment order), DOC (wire transfer), TED (other type of wire transfer), and direct credit in the account</td>
</tr>
<tr>
<td>J</td>
<td>Bar code payments (invoice with bar code or other type of documents with bar code)</td>
</tr>
<tr>
<td>O</td>
<td>Tax payments or other publics services payments</td>
</tr>
</tbody>
</table>
</td>
<td>Not implemented</td>
</tr>
<tr>
<td>US Payroll</td>
<td>US Payroll provides gross-to-net processing for employees in the United States. In Payroll, you can set up, enter, and maintain all payroll records and transactions.</td>
<td>Implemented in version 1611</td>
</tr>
<tr>
<td>Vendor collaboration (Vendor Portal)</td>
<td>Dynamics AX 2012 provided vendor portal capabilities via Enterprise Portal. Financial and Operations also provides these capabilities. In version 7.1 (also known as Dynamics 365 for Operations 1611), a vendor could view and respond to purchase orders.
<p>In version 7.3, the vendor can view and respond to RFQs. Vendors can also view and edit selected information from the vendor record such as addresses, contact information, and contact persons, and they can upload documents in relation to their certifications.</p>
</td>
<td>Implemented in version 7.3</td>
</tr>
<tr>
<td>Vendor requests - external request to become a new vendor</td>
<td>Dynamics AX 2012 provided the ability for an anonymous user to sign up to be a vendor in the system, which could lead to a vendor request for adding a new vendor to the vendor master. In version 7.3, the anonymous request from a prospective vendor can be imported via an entity (Data Management/OData), which can lead to inviting the vendor - or the vendor's contact person - to register more details about the prospective vendor. The information provided is included in a new vendor request that can be reviewed and approved via a workflow process. An approval of the vendor request leads to creation of a new vendor account.</td>
<td>Implemented in version 7.3</td>
</tr>
<tr>
<td>Vendor requests in general</td>
<td>Dynamics AX 2012 had a concept of vendor requests that served various purposes related to updating vendor-related information, such as requesting new procurement categories for the vendor, internal employees requesting new vendors, or requesting to add a vendor to another company. Only the vendor's request of being added as a vendor has been implemented in version 7.3.</td>
<td>Not implemented</td>
</tr>
<tr>
<td>[Russia] Tax registers</td>
<td>Legal entities can use registers to disclose their revenues and expenses. The registers are used to track revenue and expense data from the time that primary documents, such as sales invoices and delivery notes, are first entered by using the calculation of cost prices for production. The data from the registers is used to confirm the declared profit of the legal entity. This functionality includes the following features:
<ul>
<li>Current period incomes</li>
<li>Tax expenses</li>
<li>Other expenses of current period</li>
<li>Unrealized expenses of current period</li>
<li>Other unrealized expenses</li>
<li>Accounts receivable debt – inventory</li>
<li>Bad debts reserve calculation</li>
<li>Bad debts reserve movement</li>
<li>Accounts receivable movement</li>
<li>Procedure for writing-off AR bad debts</li>
<li>Accounts payable debt - inventory</li>
<li>Accounts payable debt movement</li>
<li>Procedure for writing-off AP bad debts</li>
<li>Goods cost calculation</li>
<li>FA object information</li>
<li>IA object information</li>
<li>FA depreciation</li>
<li>IA depreciation</li>
<li>FA/IA sale</li>
<li>Depreciation bonus recovery</li>
</ul>
</td>
<td>Implemented in version 8.1.3</td>
</tr>
<tr>
<td>[Russia] Electronic export/import format for Client-Bank interface and reconciliation procedure</td>
<td>Electronic formats for export of outgoing payments, and import of incoming payments.</td>
<td>Implemented in version 8.1.3</td>
</tr>
<tr>
<td>[Russia] VAT declaration</td>
<td>Electronic format of VAT declaration.</td>
<td>Implemented in version 10.0.1</td>
</tr>
<tr>
<td>[Russia] Cash Flow Management</td>
<td>The functionality which obtains a cash flow forecast and performs an analysis, manages payments on a daily basis using payment schedule journals, controls the company's cash position, and maintains the company's cash flows with centralized control,</td>
<td>Implemented in version 10.0.1</td>
</tr>
<tr>
<td>[Russia] Accounting reporting format</td>
<td>Electronic format of the following accounting reports: BalanceSheet, IncomeStatement, CashFlow, EquityStatement, TargetUsageMoney</td>
<td>Implemented in version 10.0.1</td>
</tr>
<tr>
<td>[Russia] Assessed tax reporting</td>
<td>Assessed tax declaration.</td>
<td>Implemented in version 10.0.1</td>
</tr>
<tr>
<td>[Russia] Land tax reporting</td>
<td>Land tax declaration. Creation of Land tax declaration by separate divisions.</td>
<td>Implemented in version 10.0.1</td>
</tr>
<tr>
<td>[Russia] Transport tax reporting</td>
<td>Transport tax declaration.</td>
<td>Implemented in version 10.0.1</td>
</tr>
<tr>
<td>[Russia] Indirect tax return (VAT and Excise) on import of goods</td>
<td>Indirect (withholding) tax return (VAT and Excise) on import of goods from state members of Customs union.</td>
<td>Implemented in version 10.0.1</td>
</tr>
<tr>
<td>[Russia] Journal of Alcohol sales in Retail</td>
<td>Daily Alcohol journal.</td>
<td>Implemented in version 10.0.1</td>
</tr>
<tr>
<td>[Russia] Optional posting of transfer orders to General ledger</td>
<td>Option to post/not post transactions to General ledger when posting a transfer order.</td>
<td>Implemented in version 8.1.2</td>
</tr>
<tr>
<td>[Russia] Inventory owner</td>
<td>Inventory dimension used to track owner of inventory (consignment stock, bailment, tolling, etc.).</td>
<td>Implemented in version 10.0.1</td>
</tr>
<tr>
<td>[Russia] AP/AR - Third-party miscellaneous charges</td>
<td>Registration of third-party miscellaneous charges and allocation by the following regimes: Inclusion into cost of purchased goods (allocation to invoices lines from other vendors), and redrawing to other parties re-allocation to other expense accounts.</td>
<td>Implemented in version 8.1.1</td>
</tr>
<tr>
<td>[Russia] Goods in transit from vendor</td>
<td>Registering goods in transit from vendor by special posting profile with Item type "purchased items en route". Creating Act of inventory holdings en route. (INV-6)</td>
<td>Implemented in version 8.1.2</td>
</tr>
<tr>
<td>[Russia] Goods in transit - sales to customer with postponed passing of property</td>
<td>Post sales invoice with postponed property transfer: no customer debts posted, all outgoing taxes are posted, items are transferred to transit warehouse. Register passing of property with posting debts and items sale from transit warehouse.</td>
<td>Implemented in version 8.1.2</td>
</tr>
<tr>
<td>[Russia] Bailment - accounting at bailee side</td>
<td>Accounting of inventory receipt for bailment as required by the Law and generation of primary form MX-1. Accounting of inventory return from bailment and generation of primary form MX-3. Bailment costs calculation from bailee side.</td>
<td>Implemented in version 8.1.2</td>
</tr>
<tr>
<td>[Russia] Bailment - accounting at owner side</td>
<td>Accounting of inventory transfer to bailment and inventory return from bailment on goods owner side under bailment service contract.</td>
<td>Implemented in version 8.1.2</td>
</tr>
<tr>
<td>[Russia] Localization of Process Industries solution</td>
<td>Basic localization in two areas: correspondence of accounts for all new general ledger postings, and functional coexistence of Process Industries features and Russian country/region context (no issues when both Process Industries and Russian country/region context are enabled).</td>
<td>Implemented in version 10.0.1</td>
</tr>
<tr>
<td>[Russia] Alcohol sales declarations: Application 6, 7, 8 for wholesale. Applications 11, 12 for retail</td>
<td>Keeping track of alcoholic beverages types including producers, unit of measures, licenses for retail and wholesale trade. Preparing data for alcoholic beverages activities, including printing declarations and exporting them in XML format through e-reporting.</td>
<td>Implemented in version 10.0.1</td>
</tr>
</tbody>
</table>


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]