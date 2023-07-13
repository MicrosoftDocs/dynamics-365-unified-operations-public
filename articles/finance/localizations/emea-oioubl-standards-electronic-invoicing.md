---
# required metadata
title: Supported standards for electronic invoicing in Europe
description: This article explains the level of coverage that exists for electronic invoicing for Europe. 
author: mrolecki
ms.date: 11/19/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.search.region: Austria, Denmark, Italy, Norway, Spain, France, Belgium, Netherlands
ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Supported standards for electronic invoicing in Europe

[!include [banner](../includes/banner.md)]

This article explains the level of coverage that exists for electronic invoicing for Europe. 

Implementation and adoption of European Union-wide electronic invoicing is regulated [Council Directive 2010/45/EU](https://eur-lex.europa.eu/LexUriServ/LexUriServ.do?uri=OJ:L:2010:189:0001:0008:EN:PDF), which affects all EU member states. Companies that want to benefit from electronic invoicing must submit sales order invoices, free text invoices, project invoices, sales order credit notes, and project invoice credit notes as .xml files to the government or other trading parties that mandate use of electronic invoicing. These .xml files must comply with certain standards. The country/region-specific requirements and their implementation may differ across EU member states but commonly they are using Universal Business Language ([UBL](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=ubl)) in different versions with customizations as well as [PEPPOL](https://www.peppol.eu) specifications and access points for validation and transportation. The primary advantage of UBL is that business documents can be standardized for different purposes. Because UBL is a flexible, international standard that supports many business requirements, these business documents can be exchanged across national borders.

## Electronic invoice formats currently available in Dynamics 365 Finance

The following country/region-specific formats of electronic invoices are available:

-   OIOUBL v.2.02 for Denmark
-   EHF v.3.0 for Norway
-   PEPPOL BIS v.2 for Austria, France, and Belgium
-   UBL-OHNL 1.9 for the Netherlands
-   FacturaE v.3.2.1 for Spain
-   FatturaPA v.1.2 for Italy
-   xRechnung v.1.2 for Germany
-   Open PEPPOL BIS Billing v.3.0 for European Union
-   Estonian specific format version 1.2
-   Finvoice 3.0 for Finland

Electronic invoicing is based on [Electronic reporting (ER)](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md). An **Invoice model** data model, invoice model mapping, and several country/region-specific ER format configurations have been created for the following countries/regions: 

- Austria (AT)
- Denmark (DK)
- Italy (IT)
- Norway (NO)
- Spain (ES)
- France (FR)
- Belgium (BE)
- The Netherlands (NL)
- Germany (DE)
- Estonia (EE)
- Finland (FI)
- The European Union (EU)

The **Invoice model** data model, invoice model mapping, and country/region-specific ER format configurations include:

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
-   Sales Invoice DE
-   Project Invoice DE
-   Peppol Sales Invoice - for EU
-   Peppol Sales Credit Note - for EU
-   Peppol Project Invoice - for EU
-   Peppol Project Credit Note - for EU
-   Sales invoice (EE)
-   Project invoice (EE)
-   Sales invoice (FI)
-   Project invoice (FI)

The electronic invoices and credit notes that you generate include required information, such as a European Article Numbering (EAN) number, contact person, dimension account number, and address information for the customer. Validation rules are applied when invoices are generated so you can verify that the correct information has been entered. The set of required information may differ from country/region to country/region. Because the requirements, as well as supported countries/regions and formats, is subject to change, you should always go to the Shared asset library on Microsoft Dynamics Lifecycle Services (LCS) and view the most up-to-date list of available files that have an asset type of **GER configuration**.

## Electronic invoice configuration
The setup and specifics of electronic invoices depend on the country/region that it's implemented for. For more information about how to set up and use customer electronic invoices, see the related country/region-specific topics:

- [Italy](emea-ita-e-invoices.md)
- [Norway](emea-nor-e-invoices.md)
- [Denmark](emea-dnk-e-invoices.md)
- [Germany](emea-deu-e-invoices.md)
- [Finland](https://support.microsoft.com/help/4559937)
- [Estonia](https://support.microsoft.com/help/4552679)
- [PEPPOL](https://support.microsoft.com/help/4490320)

## Additional resources
For more details about how to set up electronic invoices, you can play the following [Task guides](../../fin-ops-core/fin-ops/get-started/help-overview.md#task-guides) in the Help pane:

 - Set up OIOUBL electronic invoicing
 - Import OIOUBL electronic invoicing configurations
 - Set up customer accounts for OIOUBL electronic invoicing

> [!NOTE] 
> Although these Task guides were created for Danish-specific e-invoice format *OIOUBL*, they are applicable for other supported countries/regions with minor deviations.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
