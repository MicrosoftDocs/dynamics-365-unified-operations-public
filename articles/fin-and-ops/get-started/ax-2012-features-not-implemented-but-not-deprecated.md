---
# required metadata

title: Dynamics AX 2012 features that were postponed
description: This topic lists features of Microsoft Dynamics AX 2012 that were postponed. These features weren't implemented in Microsoft Dynamics AX 7.0. 
author: sericks007
manager: AnnBe
ms.date: 11/07/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21881
ms.assetid: 26793616-9b3f-41f5-8500-6983769c51d8
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---

# Dynamics AX 2012 features that were postponed

[!include[banner](../includes/banner.md)]

This topic lists features of Microsoft Dynamics AX 2012 that were postponed. These features weren't implemented in Microsoft Dynamics AX 7.0. In the following table, the **Current status** column indicates whether the feature has been implemented since the AX 7.0 release.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>AX 2012 feature that was postponed</th>
<th>Description</th>
<th>Current status (as of November 2017)
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Intelligent Data Management Framework (IDMF)</td>
<td>IDMF is an add-on tool that lets system administrators optimize performance. IDMF assesses the health of the application, analyzes current usage patterns, and helps reduce database size.</td>
<td>Not implemented</td>
</tr><tr class="odd">
<td>Alerts</td>
<td>Alerts help users keep track of data changes in the system.</td>
<td>Not implemented</td>
</tr>
<tr class="even">
<td><strong>Graphics</strong> tab in the <strong>Fixed asset value model</strong> and <strong>Depreciation book profile</strong> forms</td>
<td>The chart shows the depreciation, accumulated depreciation, and net book value over time. Users can click the <strong>Data</strong> tab to view more detailed information than the chart shows. This chart will be redesigned in a future update.</td>
<td>Not implemented</td>
</tr>
<tr class="even">
<td>Employee self-service (ESS)</td>
<td><p>ESS shows employees several tiles that show task-related and career-related information on a single page. Employees can view pending work items and click links that open pages where they can take action on their tasks. ESS pages also show employees the status of their certifications, when their next performance reviews are scheduled, skills, goals, and compensation information, and other information, such as balances for vacation and sick time. Employees can also access a company directory from their ESS page.</p><p>In previous versions, ESS let you enter requisitions for employees through a procurement site, view the status of an order (created, received, or receipt confirmed), and request onboarding of a new vendor. ESS also let you configure security and punch-out to external catalogs. In the current version, procurement catalog capabilities are reduced and are used only to limit the products that can be ordered for an organization on a requisition. Additionally, the ability to approve a vendor invoice and the functionality for confirming receipts that are associated with requisitions that lead to purchases aren't currently available.</p></td>
<td>Implemented in Microsoft Dynamics 365 for Operations version 1611</td>
</tr>
<tr class="odd">
<td>Customer self-service (CSS)</td>
<td>CSS lets you create approved customer records. It also lets users can view selected product catalogs, order items, and view the status of invoices. Additionally, CSS provides the ability to create and follow return orders.</td>
<td>Not implemented</td>
</tr>
<tr class="even">
<td>Cost accounting</td>
<td>The <strong>Cost accounting</strong> module is designed to meet the requirements of internal costs and profitability reports at multiple organizational levels. To define the cost object level, the module depends on a correct mapping of financial dimensions. The module lets you perform advanced allocations of cost origin from expenditures that are registered in the general ledger or budget. It also lets you compare realized costs and budgeted costs.</td>
<td>Implemented in Dynamics 365 for Operations version 1611</td>
</tr>
<tr class="even">
<td>Absence management in Human resources</td>
<td>Functionality for entering absence transactions isn't included in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. Additionally, functionality for approving those absence transactions as a manager isn't included. Setup capabilities that are required for integration with other modules are available through the <strong>Human Resources 2</strong> configuration key.</td>
<td>Implemented in Microsoft Dynamics 365 for Talent</td>
</tr>
<tr class="odd">
<td>US Payroll</td>
<td>US Payroll provides gross-to-net processing for employees in the United States. In Payroll, you can set up, enter, and maintain all payroll records and transactions. </td>
<td>Implemented in Dynamics 365 for Operations version 1611</td></tr>
<tr class="even">
<td>External questionnaire and recruiting functionality</td>
<td>Functionality for externally posting questionnaires and open jobs will be added to Talent in a future update.</td>
<td><p>External questionnaire functionality hasn't been implemented.</p><p>Recruiting functionality is available in the Attract app for Talent.</p></td></tr>

<td>Client right-to-left (RTL) layout</td>
<td>RTL layout is now supported.</td>
<td>Implemented in Microsoft Dynamics AX platform update 2</td></tr>
<tr class="odd">
<td>Client drag-and-drop</td>
<td>The web client controls have application programming interfaces (APIs) for drag-and-drop operations, but these APIs are based on the deprecated desktop client technology and must be redesigned so that they work on the new web client platform. APIs that support drag-and-drop operations will be reviewed for inclusion in a future update.</td>
<td>Not implemented</td></tr>
<tr class="odd">
<td>General budget reservations</td>
<td>This document is sometimes referred to as a commitment. Public sector entities often use this document to set aside or earmark budgeted funds so that they aren't available for other purposes. This functionality will be added in a future update.</td>
<td>Not implemented</td></tr>
<td>Microsoft Project client integration</td>
<td>The Microsoft Project client is integrated with projects.</td>
<td>Implemented in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.2 (July 2017)</td></tr>
<tr class="odd">
<td>Specifications for Electronic reporting (ER) payment formats</td>
<td><p>Currently, payment format specifications must be entered manually. In a future update, you will be able to select payment format specifications in a list. Currently, the following payment specifications are supported per payment format.</p>
<blockquote>[!NOTE]<br>
Values for these supported payment specifications are used as payment specification parameters in the <strong>Payment specification</strong> form for a selected method of payment.</blockquote>
<p><strong>BTL91 for the Netherlands</strong></p>
<table>
<thead>
<tr class="header">
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ChqBen</td>
<td>Cheque, Begunstigde</td>
</tr>
<tr class="even">
<td>ChqOff</td>
<td>Cheque, Kantoor opdrachtgever</td>
</tr>
<tr class="odd">
<td>ChqPri</td>
<td>Cheque, Opdrachtgever</td>
</tr>
<tr class="even">
<td>TrfBenBen</td>
<td>Overboeking Begunstigde/Begunstigde</td>
</tr>
<tr class="odd">
<td>TrfBenBenUrg</td>
<td>Overboeking Begunstigde/Begunstigde Spoed</td>
</tr>
<tr class="even">
<td>TrfEurBen</td>
<td>Overboeking Euro/Begunstigde</td>
</tr>
<tr class="odd">
<td>TrfEurBenUrg</td>
<td>Overboeking Euro/Begunstigde Spoed</td>
</tr>
<tr class="even">
<td>TrfEurEur</td>
<td>Overboeking Euro/Euro</td>
</tr>
<tr class="odd">
<td>TrfEurEurUrg</td>
<td>Overboeking Euro/Euro Spoed</td>
</tr>
<tr class="even">
<td>TrfForBen</td>
<td>Overboeking VV-rekening/Begunstigde</td>
</tr>
<tr class="odd">
<td>TrfForBenUrg</td>
<td>Overboeking VV-rekening/Begunstigde Spoed</td>
</tr>
<tr class="even">
<td>TrfForFor</td>
<td>Overboeking VV-rekening/VV-rekening</td>
</tr>
<tr class="odd">
<td>TrfForForUrg</td>
<td>Overboeking VV-rekening/VV-rekening Spoed</td>
</tr>
</tbody>
</table>
<p><strong>Betalingsservice for Denmark</strong></p>
<table>
<thead>
<tr class="header">
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>B0112</td>
<td>BS-B 0112: Lang tekst &amp; adresse</td>
</tr>
<tr class="even">
<td>B0113</td>
<td>BS-B 0113: Erstat. bet. lang tekst</td>
</tr>
<tr class="odd">
<td>T0112</td>
<td>BS-T 0112: Lang tekst &amp; adresse</td>
</tr>
<tr class="even">
<td>T0117</td>
<td>BS-T 0117:FIK;kort frist;lang tekst&amp;adr.</td>
</tr>
</tbody>
</table>
<p><strong>Nordea vendor for Denmark</strong></p>
<table>
<thead>
<tr class="header">
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>56</td>
<td>Currency account transfer between Nordea accounts in Denmark</td>
</tr>
<tr class="even">
<td>47</td>
<td>Domestic check</td>
</tr>
<tr class="odd">
<td>45</td>
<td>Domestic transfer</td>
</tr>
<tr class="even">
<td>50</td>
<td>Express transfer</td>
</tr>
<tr class="odd">
<td>55</td>
<td>Intercompany transfer (domestic)</td>
</tr>
<tr class="even">
<td>51</td>
<td>Intercompany transfer to a foreign bank</td>
</tr>
<tr class="odd">
<td>54</td>
<td>International check</td>
</tr>
<tr class="even">
<td>52</td>
<td>Nordea intercompany payment</td>
</tr>
<tr class="odd">
<td>43</td>
<td>Request for transfer</td>
</tr>
<tr class="even">
<td>46</td>
<td>Transfer form/giro payment</td>
</tr>
</tbody>
</table>
<p><strong>ISO20022 Credit transfer (CH)</strong></p>
<table>
<thead>
<tr class="header">
<th>Payment specification (used in ER)</th>
<th>Export format description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Tp1.ESROPS</td>
<td>Type 1 - ESR orange payment slip</td>
</tr>
<tr class="even">
<td>Tp21.ISR1SPS</td>
<td>Type 2.1 - IS red 1 stage payment slip</td>
</tr>
<tr class="odd">
<td>Tp22.ISR2SPS</td>
<td>Type 2.2 - IS red 2 stage payment slip</td>
</tr>
<tr class="even">
<td>Tp7.Dmstc</td>
<td>Type 7 - Domestic postal order</td>
</tr>
<tr class="odd">
<td>TpE1.PSWR</td>
<td>Type E1 - Payment slip with reference</td>
</tr>
<tr class="even">
<td>TpE2.PSWN</td>
<td>Type E2 - Payment slip with notifications</td>
</tr>
</tbody>
</table></td>
<td>Not implemented</td></tr>
<tr class="even">
<td>Fiscal printers for Poland</td>
<td>Integration with Polish fiscal printers enables the required information to be sent to the fiscal printer in the correct format during invoice posting. Examples of Polish fiscal printers include the Posnet Thermal and Elzab Omega printer types. This feature will be available in a future update.</td>
<td>Not implemented</td></tr>
<tr class="odd">
<td>Bank payment order for Latvia and Lithuania</td>
<td>You can print a payment order for Latvia and Lithuania. This feature will be available in a future update.</td>
<td>Not implemented</td></tr>
<tr class="even">
<td>Bankgirot AP return format for Sweden</td>
<td>The Bankgirot return format is used to import bank return messages. This feature will be available in a future update.</td>
<td>Not implemented</td></tr>
<tr class="odd">
<td>Secure global address book</td>
<td>The ability to help secure the global address book by legal entity and address book hasn't yet been implemented. This feature will be available in a future update.</td>
<td>Not implemented</td></tr>
<tr class="even">
<td>Customizable help topics</td>
<td>The ability to create customized help topics has not yet been implemented. Custom task guides and custom field help are available. This feature will be available in a future update. </td>
<td>Not implemented</td></tr>
</tbody>
</table>
