---
# required metadata

title: Dynamics AX 2012 features that haven't been implemented but aren't deprecated
description: This topic lists Microsoft Dynamics AX 2012 features that haven't yet been implemented in Dynamics 365 for Finance and Operations, Enterprise Edition July 2017 update. Although these features haven't yet been implemented, they aren't deprecated. 
author: sericks007
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: sericks007
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 21881
ms.assetid: 26793616-9b3f-41f5-8500-6983769c51d8
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---

# Dynamics AX 2012 features that haven't been implemented but aren't deprecated

[!include[banner](../includes/banner.md)]


This topic lists Microsoft Dynamics AX 2012 features that haven't yet been implemented in Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update. Although these features haven't yet been implemented, they aren't deprecated. 

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Alerts</td>
<td>Implementation of the alerts functionality is planned for a future update. Alerts help users keep track of data changes in the system.</td>
</tr>
<tr class="even">
<td><strong>Graphics</strong> tab in the Fixed asset value model and Depreciation book profile forms</td>
<td>The chart shows the deprecation, accumulated depreciation, and net book value over time. Users can click the <strong>Data</strong> tab to view more detailed information than the chart shows. This chart will be redesigned in a future update.</td>
</tr>
<tr class="odd">
<td>Generate an electronic file to communicate payment advice information. The file can be sent to a vendor.</td>
<td>From the vendor payment journal, you can generate payment advice as a report or as a file. The payment advice is used to inform the vendor about the list of invoices that are being paid. The payment advice report is still available in the current version, but you can no longer generate this information in an electronic file format. That functionality depended on Application Integration Framework (AIF), which has been deprecated.</td>
</tr>
<tr class="even">
<td>Cash flow forecasting</td>
<td>The functionality for creating a cash flow forecast will be enhanced and will be included in a future update.</td>
</tr>
<tr class="odd">
<td>Vendor portal</td>
<td>Vendor portal lets you certify and validate suppliers as claims users through identity providers such as Microsoft account or Yahoo. It also supports unsolicited vendor sign-up. Vendor portal lets vendors review purchase orders, update their own (supplier) data, review product receipts to generate invoices, and upload and maintain a product catalog. Vendor portal lets you collaborate with or notify a supplier, and also lets you upload requests for quotation (RFQs) and allow vendors to respond to them. A vendor portal interface will be available in the web client, for Microsoft Azure Active Directory (Azure AD) users who have a dedicated security role. These users can review, confirm, and reject purchase orders, and can view confirmed orders.</td>
</tr>
<tr class="even">
<td>Employee self-service (ESS)</td>
<td>ESS lets you enter requisitions for employees through a procurement site, view the status of an order (created, received, or receipt confirmed), and request onboarding of a new vendor. ESS also lets you configure security and punch-out to external catalogs. In the current version, procurement catalog capabilities are reduced and are used only to limit the products that can be ordered on a requisition for an organization. Additionally, the functionality for confirming receipts that are associated with requisitions that lead to purchases and the ability to approve a vendor invoice isn't currently available.</td>
</tr>
<tr class="odd">
<td>Customer self-service (CSS)</td>
<td>CSS lets you create approved customer records, and lets users view selected product catalogs, order items, and view the status of invoices. It also provides the ability to create and follow return orders.</td>
</tr>
<tr class="even">
<td>Cost accounting</td>
<td>The Cost accounting module is designed to meet the requirements of internal costs and profitable reports at multiple organizational levels. To define the cost object level, the module depends on a correct mapping of financial dimensions. The module lets you perform advanced allocations of cost origin from expenditures that are registered in the general ledger or budget, and also lets you compare realized costs and budgeted costs.</td>
</tr>
<tr class="even">
<td>Absence management in Human Resources</td>
<td>Functionality for entering absence transactions through both ESS and the client are not included. It also doesn't include functionality for approving those transactions as a manager. In a future update, the current functionality will be enhanced to support a wider range of scenarios. Setup capabilities that are required for integration with other modules are available through the <strong>Human Resources 2</strong> configuration key.</td>
</tr>
<tr class="odd">
<td>US Payroll</td>
<td>US Payroll is not included. Limited initial setup capabilities will be available through the <strong>Human Resources 1</strong> &gt; <strong>Payroll</strong> configuration key.</td>
</tr>
<tr class="even">
<td>External questionnaire and recruiting functionality</td>
<td>Functionality for externally posting questionnaires and open jobs will be added in a future update.</td>
</tr>
<tr class="odd">
<td>Main account allocations for accounting distributions</td>
<td>Allocation rules that are defined for a main account won't be applied on accounting distributions. In a future update, main allocation rules will be applied during journalization.</td>
</tr>
<tr class="even">
<td>Client right-to-left (RTL) layout</td>
<td>The web client uses only left-to-right (LTR) layout for controls and labels. The ability to use RTL layout for Arabic and Hebrew languages will be added in a future update.</td>
</tr>
<tr class="odd">
<td>Client drag-and-drop</td>
<td>The web client controls have application programming interfaces (APIs) for drag-and-drop operations, but these APIs are based on the deprecated desktop client technology and must be redesigned to work on the new web client platform. APIs to support drag-and-drop operations will be reviewed for inclusion in a future update of Dynamics 365 for Operations.</td>
</tr>
<tr class="even">
<td>Vendor catalog import</td>
<td>Vendor catalog import is available and uses the new data management capabilities for import. However, this feature doesn't support the import of product images and attributes. It also doesn't let you generate schema files per vendor catalog. This functionality will be added in a future update.</td>
</tr>
<tr class="odd">
<td>General budget reservations</td>
<td>This document is sometimes referred to as a commitment. Public sector entities often use this document to set aside or earmark budgeted funds so that they aren't available for other purposes. This functionality will be added in a future update.</td>
</tr>
<tr class="even">
<td>Electronic data exchange</td>
<td>The electronic exchange of documents, such as order confirmations and similar supply chain management (SCM) documents that were previously enabled as AIF documents is not supported. This functionality will be added in a future update.</td>
</tr>
<tr class="odd">
<td>Windows 8 and mobile apps</td>
<td>Mobile and tablet functionality enables expense capture and approval, and timesheet entry and approval.</td>
</tr>
<tr class="even">
<td>Microsoft Project client integration</td>
<td>The Microsoft Project client is integrated with Dynamics 365 for Operations projects.</td>
</tr>
<tr class="odd">
<td>Specifications for Electronic reporting (ER) payment formats</td>
<td>Currently, payment format specifications must be entered manually. In a future update of Dynamics 365 for Operations, you will be able to select payment format specifications in a list. Currently, the following specifications are supported per payment format. <strong>Note</strong>: Values of supported payment specifications listed below are used as Payment specification parameters in Payment specification form for a selected method of payment. 
<strong>BTL91 for the Netherlands</strong>
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
<strong>Betalingsservice for Denmark</strong>
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
<strong>Nordea vendor for Denmark</strong>
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
<strong>ISO20022 Credit transfer (CH)</strong>
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
</tr>
<tr class="even">
<td>Fiscal printers for Poland</td>
<td>Polish fiscal printers are integrated with Dynamics 365 for Operations. The following types of printers in the local Polish market are supported: Posnet Thermal and Elzab Omega. During invoice posting, the required information is sent to the fiscal printer in the correct format. This feature will be available in a future update.</td>
</tr>
<tr class="odd">
<td>Bank payment order for Latvia and Lithuania</td>
<td>Print a payment order for Latvia and Lithuania. This feature will be available in a future update.</td>
</tr>
<tr class="even">
<td>Bankgirot AP return format for Sweden</td>
<td>The Bangirot return format is used to import bank return messages. This feature will be available in a future update.</td>
</tr>
</tbody>
</table>





