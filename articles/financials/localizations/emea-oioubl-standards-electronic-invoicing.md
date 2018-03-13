---
# required metadata
title: Supported standards for electronic invoicing in Europe
description: This topic explains the level of coverage that exists for electronic invoicing in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition in the European region. 
author: mrolecki
manager: AnnBe
ms.date: 07/11/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 10274
ms.search.region: Austria, Denmark, Italy, Norway, Spain, France, Belgium, Netherlands
ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Supported standards for electronic invoicing in Europe

[!include[banner](../includes/banner.md)]


This topic explains the level of coverage that exists for electronic invoicing for Europe. 

Implementation and adoption of European Union-wide electronic invoicing is regulated [Council Directive 2010/45/EU](http://eur-lex.europa.eu/LexUriServ/LexUriServ.do?uri=OJ:L:2010:189:0001:0008:EN:PDF), which affects all EU member states. Companies that want to benefit from electronic invoicing must submit sales order invoices, free text invoices, project invoices, sales order credit notes, and project invoice credit notes as .xml files to the government or other trading parties that mandate use of electronic invoicing. These .xml files must comply with certain standards. The country-specific requirements and their implementation may differ across EU member states but commonly they are using Universal Business Language ([UBL](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=ubl)) in different versions with customizations as well as [PEPPOL](http://www.peppol.eu) specifications and access points for validation and transportation. The primary advantage of UBL is that business documents can be standardized for different purposes. Because UBL is a flexible, international standard that supports many business requirements, these business documents can be exchanged across national borders.

## What electronic invoice formats are currently available in Finance and Operations?

The following country-specific formats of electronic invoices are available:

-   OIOUBL v.2.02 for Denmark
-   EHF v.2.0.8 for Norway
-   PEPPOL BIS v.2 for Austria, France, and Belgium
-   UBL-OHNL 1.9 for the Netherlands
-   FacturaE v.3.2.1 for Spain
-   FatturaPA v.1.2 for Italy

Electronic invoicing is based on [electronic reporting](../../dev-itpro/analytics/general-electronic-reporting.md). There is a **Customer invoice model** data model and a number of country-specific electronic reporting format configurations created for Austria (AT), Denmark (DK), Italy (IT), Norway (NO), Spain (ES), France (FR), Belgium (BE), and the Netherlands (NL).

-   OIOUBL Sales invoice - for AT, DK, and NO
-   OIOUBL Sales credit note - for AT, DK, and NO
-   OIOUBL Project invoice - for AT, DK, and NO
-   OIOUBL Project credit note - for AT, DK, and NO
-   UBL Sales Invoice FR
-   UBL Sales Credit Note FR
-   UBL Project Invoice FR
-   UBL Project Credit Note FR
-   UBL Sales Invoice BE
-   UBL Sales Credit Note BE
-   UBL Project Invoice BE
-   UBL Project Credit Note BE
-   UBL Sales Invoice NL
-   UBL Sales Credit Note NL
-   UBL Project Invoice NL
-   UBL Project Credit Note NL 
-   Sales invoice (ES)
-   Sales invoice (IT)
-   Project invoice (ES)
-   Project invoice (IT)

The electronic invoices and credit notes that you generate include required information, such as a European Article Numbering (EAN) number, contact person, dimension account number, and address information for the customer. Validation rules are applied when invoices are generated so you can verify that the correct information has been entered. The set of required information may differ from country to country. Because the requirements, as well as supported countries and formats, is subject to change, you should always go to the Shared asset library on Microsoft Dynamics Lifecycle services (LCS) and view the most up-to-date list of available files that have an asset type of **GER configuration**.

## Additional information
For more details about how to set up electronic invoices, you can play the following [Task guides](../../fin-and-ops/get-started/help-overview.md#task-guides) in the Help pane:

 - Set up OIOUBL electronic invoicing
 - Import OIOUBL electronic invoicing configurations
 - Set up customer accounts for OIOUBL electronic invoicing

> [!NOTE] 
> Although these Task guides were created for Danish-specific e-invoice format *OIOUBL*, they are applicable for other supported countries with minor deviations.
