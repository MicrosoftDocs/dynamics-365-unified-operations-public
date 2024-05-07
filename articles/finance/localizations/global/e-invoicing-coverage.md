---
title: Supported electronic invoicing countries and regions
description: This article describes for which countries and regions electronic invoicing is supported or planned in Microsoft Dynamics 365 Finance.
author: ilikond
ms.date: 09/05/2023
ms.topic: article
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: All
ms.author: ikondratenko
ms.search.validFrom: 2022-11-03
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Electronic invoicing coverage for supported and planned countries and regions

This article describes current Electronic invoicing geographical coverage in Microsoft Dynamics 365 Finance and known plans for upcoming electronic invoicing implementations. 

## Introduction

Electronic invoicing, or e-invoicing, is the process of sending and receiving invoices in a digital format. E-invoicing is rapidly becoming an important part of business processes and an essential part of compliance with the global and country-specific regulatory requirements for both, buyers and suppliers.

Besides that, e-invoicing has several advantages over traditional paper-based invoicing, such as:
 - Reducing errors and disputes by eliminating manual data entry and validation
 - Increasing cash flow and visibility by speeding up the invoice approval and payment cycle
 - Lowering operational costs by saving time, paper, postage, and storage space
 - Improving customer satisfaction and retention by offering convenience and flexibility
 - Supporting environmental sustainability by reducing paper waste and carbon footprint

Microsoft permanently monitors legislative requirements changes in e-invoicing area for all supported countries and regions and delivers regulatory updates in timely manner. During extending geographical coverages, Microsoft prioritize e-invoicing as one of the most important requirements.

The next chapter contains the detailed information about e-invoicing "out-of-the-box" functionality for already supported countries, including upcomig regulatory changes, as well as plans for new countries implementations.

## Electronic invoicing coverage

> [!NOTE]
> Delivery timelines for the mentioned below planned implementations may change, and projected functionality may not be released at all due to various reasons. For more information, go to [Microsoft policy](https://go.microsoft.com/fwlink/p/?linkid=2007332).

 **Country**  |                                 **Description**                                |**Availability**|
|----------------------|-----------------------------------------------------------------------|------------|
| Argentina            | Generation of electronic documents in the predefined XML formats and submission through WebServices to AFIP.  |Planned for 2025 release wave 1|
| Australia            | Generation of electronic invoices for Sales and Project invoices and credit notes in the Australian extension of **PEPPOL** format.<li>Learn more here: [Electronic invoicing for Australia](../apac/gs-apac-aus-nzl-electronic-invoices.md)</li>    |Available|
| Austria            | Generation of electronic invoices for Sales and Project invoices and credit notes in the **PEPPOL** format|Available|
| Belgium            | Generation of electronic invoices for Sales and Project invoices and credit notes in the **PEPPOL** format|<li>Available</li><li>Regulatory changes expected by January 2026</li>|
| Bolivia | Generation of electronic invoices with the right to fiscal credit, invoices without the right to fiscal credit, and adjustment documents in XML format. |Planned for 2024 release wave 1|
| Brazil            | Generation and direct submission to the authorities of fiscal documents in the **NF-e** and **NFS-e** formats. Import of incoming documents into Microsoft Dynamics 365 Finance from the authorities.<li>Learn more here: [NF-e process overview](../brazil/latam-bra-nf-e-process.md)</li>|Available|
| Chile             | Generation of electronic tax documents (DTE) in country-specific format for Invoices, Debit notes, Credit notes, Export invoices, Export debit notes, Export credit note​, and Packing Slips. <li>Learn more here: [Chilean electronic invoicing](../iberoamerica/ltm-chile-elec-invo-conncection.md)</li> |<li>Available</li><li>Submission planned for 2024 release wave 1</li>|
| China            | Invoice reporting (fapiao) support. File upload integration with **Golden Tax System** via **BaiWang** and **Asino** software. <li>Learn more here: [Golden tax system integration](../china/apac-chn-tax-integration.md)</li> |Available|
| Columbia | Generation of electronic invoices in the standard XML format based on UBL V2.1 and adopted by DIAN. |Planned for 2024 release wave 1|
| Costa Rica       | Generation of e-documents for Invoices, Credit notes and Debit notes in the country-specific format. <li>Learn more here: [Electronic invoicing in Costa Rica](../iberoamerica/ltm-costa-rica-ei-connec-configuration.md)</li> |<li>Available</li><li>Submission planned for 2024 release wave 1</li>|
| Denmark | Generation and submission to the **NemHandel** or to the **Peppol network** of electronic invoices for Sales and Project invoices and credit notes in the **OIOUBL** or **PEPPOL** formats. Import of vendor electronic invoices. <li>Learn more here: [Get started with Electronic invoicing for Denmark](../denmark/e-invoicing-dk-get-started.md)</li>|Available|
| Dominican Republic | Generation of electronic fiscal vouchers (e-CF) in the XML format based on the UBL standard.  |Planned for 2024 release wave 1|
| Ecuador | Generation of electronic receipts in XML format that comply with the legal and regulatory requirements of the SRI. |Planned for 2024 release wave 1|
| Egypt   | Generation and direct submission to the Egyptian Tax Authority of electronic invoices for Sales and Project invoices, credit notes and debit notes in the country-specific format. <li>Learn more here: [Electronic invoicing for Egypt ](../mea/e-invoicing-eg-get-started.md)</li> |Available|
| Estonia | Generation of electronic invoices for Sales and Project invoices and credit notes in the country-specific format.  <li>Learn more here: [Export of customers electronic invoices in Estonia](https://support.microsoft.com/en-us/topic/a-country-specific-update-for-estonia-to-support-export-of-customers-electronic-invoices-in-microsoft-dynamics-365-finance-3f3295b4-62f8-ff24-169a-794379d1fce4)</li> |Available|
| Finland  | Generation of electronic invoices for Sales and Project invoices and credit notes in the **Finvoice** format. <li>Learn more here: [Export of customers electronic invoices in Finland](https://support.microsoft.com/en-us/topic/a-country-specific-update-for-finland-to-support-export-of-customers-electronic-invoices-in-microsoft-dynamics-365-finance-72a33347-e68c-5b39-dbbb-ee9a59d3671f)</li> |Available|
| France  | Generation and submission to the **Chorus Pro** of electronic invoices for Sales and Project invoices and credit notes in the **PEPPOL** format. Import of vendor electronic invoices. <li>Learn more here: [Get started with Electronic invoicing for France](../france/e-invoicing-fr-get-started.md)</li> |Available|
| Germany  | Generation of electronic invoices for Sales and Project invoices and credit notes in the **xRechnung** format <li>Learn more here: [Customer electronic invoices in Germany](../germany/emea-deu-cust-e-invoices.md)</li> |Available|
| Guatemala | Generation of electronic invoices in a file structured in the country-specific XML format. |Planned for 2024 release wave 1|
| Hungary | Generation and submission to the governmental Real-time invoice reporting (RTIR) platform of required data in the country-specific format. <li>Learn more here: [Online invoicing system](../hungary/emea-hun-online-invoicing.md)</li> |Available|
| India   | Generation and submission to the governmental Invoice Registration Portal (IRP) of electronic invoices for Sales and Project invoices and credit notes in the country-specific format. <li>Learn more here: [Electronic invoices in India](../india/apac-ind-e-invoices.md)</li> |Available|
| Indonesia | Generation and files upload integration with the tax authorities software electronic invoices for Sales and Project invoices, credit notes and debit notes in the country-specific format. Import of vendor electronic invoices. <li>Learn more here: [Get started with electronic invoicing for Indonesia](../indonesia/e-invoicing-id-get-started.md)</li> |Available|
| Italy |Generation and direct submission to SDI system of electronic invoices for Sales and Project invoices and credit notes in the **FatturaPA** format. Import of vendor electronic invoices. <p>Learn more here:</p><li>[Customer electronic invoices](../italy/emea-ita-e-invoices.md)</li> <li>[Vendor electronic invoices](../italy/emea-ita-vend-e-invoices.md)</li> <li>[Import of vendors electronic invoices](https://support.microsoft.com/en-us/topic/a-country-specific-update-for-italy-to-support-import-of-vendors-electronic-invoices-in-microsoft-dynamics-ax-and-microsoft-dynamics-365-331ea49f-4d49-f968-6ed8-f369759a689b)</li>  <li>[Direct integration of Italian electronic invoices with SDI](../italy/e-invoicing-ita-fatturapa-get-started.md)</li>|Available|
| Malaysia | Generation and direct submission to IRBM of electronic invoices for Sales, Project and Self invoices and credit notes in the Australian extension of **PEPPOL PINT** format. |Planned for 2024 release wave 1|
| Mexico | Generation and submission of the **CFDI** electronic documents to PAC **Interfactura**. Import of vendor electronic invoices. <li>[Electronic invoices (CFDI)](../iberoamerica/latam-mex-CFDI-electronic-invoices.md)</li> |Available|
| Netherlands | Generation of electronic invoices for Sales and Project invoices and credit notes in the **UBL-OHNL** format. |Available|
| New Zealand | Generation of electronic invoices for Sales and Project invoices and credit notes in the New Zealand extension of PEPPOL format. <li>[Electronic invoicing for New Zealand](../apac/gs-apac-aus-nzl-electronic-invoices.md)</li>|Available|
| Norway  | Generation of electronic invoices for Sales and Project invoices and credit notes in the EHF format. <li>[Customer electronic invoices in Norway](../norway/emea-nor-e-invoices.md)</li> |Available|
| Panama | Generation of e-documents for invoices in the country-specific format. <li>[Electronic invoicing for Panama](../iberoamerica/ltm-panama-ei-connec-configuration.md)</li> |<li>Available</li><li>Submission planned for 2024 release wave 1</li>|
| Paraguay | Generation of electronic documents and electronic tax documents in the standardized country-specific XML format. |Planned for 2024 release wave 1|
| Peru | Generation of electronic invoicing documents in the standard XML format based on UBL V2.1 and adopted by SUNAT, also known as CPE (Electronic Payment Vouchers). |Planned for 2024 release wave 1|
| Poland |Generation and direct submission to the governmental KSEF system of electronic invoices for Sales, Project and Advance invoices and credit notes in a country-specific format. Import of vendor electronic invoices. <li>[Get started with Electronic invoicing for Poland](../poland/e-invoicing-pol-get-started.md)</li> |Available in Public preview|
| Saudi Arabia | Generation and direct submission to **ZATCA** electronic invoices for Customer prepayments, Sales and Project invoices, credit notes and debit notes in the country-specific format. <li>[Customer electronic invoices in Saudi Arabia](../mea/gs-e-invoicing-sa-get-started.md)</li> |Available|
| Spain | Generation of electronic invoices for Sales and Project invoices and credit notes in the **FacturaE** format.  |<li>Available</li><li>Regulatory changes expected by July 2025</li>|
| Spain | Generation and submission to the governmental **SII** system of required data in the country-specific format. <li>[Immediate Supply of Information on VAT (SII)](../spain/emea-esp-sii.md)</li> |Available|
| Uruguay | Generation of Electronic Fiscal Receipt (CFE) based on the XML standard with a syntax defined and maintained by the DGI.  |Planned for 2024 release wave 1|
| PEPPOL| Generation of electronic invoices for Sales and Project invoices and credit notes in the **PEPPOL** format. This country-independent functionality can be used “as is” if no country-specific amendments are supposed or can be used as the base for further modifications. <li>[Export of customers electronic invoices in PEPPOL BIS 3 format](https://support.microsoft.com/en-us/topic/an-update-for-european-union-to-support-export-of-customers-electronic-invoices-in-peppol-bis-3-format-for-microsoft-dynamics-365-814d09db-dae7-6c5e-034c-797687078bac)</li> <li>[Import vendor electronic invoices in PEPPOL format](../europe/emea-peppol-import.md)</li>  |Available|


## Additional resources

- [Electronic invoicing overview](gs-e-invoicing-service-overview.md)
- [Globalization Studio overview](globalization-studio-overview.md)
