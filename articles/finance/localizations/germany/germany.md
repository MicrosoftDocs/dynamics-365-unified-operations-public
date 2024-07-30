---
title: Germany overview
description: Access an overview of Dynamics 365 Finance functionality that is specific to Germany with links to resources about audit files, depreciation, and VAT declarations.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Germany
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
---

# Germany overview

[!include[banner](../../includes/banner.md)]

This article includes information and links to resources that should be considered for legal entities with a primary address in Germany.

## Audit file
- [German audit file (GDPdU/GoBD) overview](emea-deu-gdpdu-audit-data-export.md)
- [Customize German audit file configuration](customize-german-audit-file-configuration.md)
- [Generate German audit file](german-audit-file.md)
- [Import German audit file configuration](import-german-audit-file-configuration.md)

## Depreciation
-   [Additional acquisition depreciation](emea-deu-additional-acquisition-depreciation.md)
-   [Depreciation adjustments for additional acquisitions in the second year](de-00002-depreciation.md)

## VAT declaration 
-   [VAT declaration for Germany](emea-deu-vat-declaration-germany.md)

## Electronic transmission of VAT declaration (ELSTER)
This feature is deprecated. For more information, see [Removed and deprecated features](../../get-started/removed-deprecated-features-finance.md#elster-declaration-for-germany-design-based-on-reporting-codes-electronic-tax-declaration-log-menu-item-and-page-electronic-tax-declaration-setup-menu-item-and-page-german-report-layout-taxreport_de-ssrs-format). For more information about VAT declaration, see [VAT declaration (Germany)](emea-deu-vat-declaration-germany.md)
- [Electronic transmission of VAT declaration (ELSTER)](../tasks/de-00003-electronic-transmission-elster.md)
- [ELSTER VAT statement for Germany](../emea-de-vat-declaration.md)

## Electronic invoices in Germany
- [Customer electronic invoices export](emea-deu-e-invoices.md)

## Credit memos originating from sales
You can specify the label that appears on credit memos that originate from sales.

On the **Legal entities** page, you can use the **Print corrective invoice on a sales memo** option on the **Foreign trade and logistics** tab to specify the label that appears on credit memos that originate from sales (sales orders, non-item sales, and project sales).

-   If the **Print corrective invoice on a sales memo** option is set to **No**, the label "Gutschrift" will be printed on all credit memos.
-   If the **Print corrective invoice on a sales memo** option is set to **Yes**, the label "Rechnungskorrektur” will be printed on credit memos for sales orders, free text invoices, and project invoices.


## Reports for Germany
[German journal list report](emea-deu-journal-list-report.md).

## Intra-community reporting
-   [EU sales list for Germany](emea-deu-eu-sales-list.md)
-   [Intrastat](emea-deu-intrastat.md)

## Additional resources
<!-- - [Microsoft Dynamics Localization Portal: Germany report](https://mbs.microsoft.com/files/customer/AX/Support/supportnews/Germany.html) -->
- [Electronic reporting overview](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md)
- [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)
- [Localization and regulatory features](../../../fin-ops-core/fin-ops/lcs/country-region.md?toc=%2ffin-and-ops%2ftoc.json)
- [Create a VAT declaration in the XML format without transferring it to ELSTER (White paper)](https://www.microsoft.com/download/details.aspx?id=101929)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
