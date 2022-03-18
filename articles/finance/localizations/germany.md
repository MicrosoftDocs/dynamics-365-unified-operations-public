---
# required metadata

title: Germany overview
description: This topic provides an overview of Dynamics 365 Finance functionality that is specific to Germany.
author: kfend
ms.date: 03/02/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 

ms.search.region: Germany
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Germany overview

[!include[banner](../includes/banner.md)]

This topic includes information and links to resources that should be considered for legal entities with a primary address in Germany.

## Audit file
- [German audit file (GDPdU/GoBD) overview](emea-deu-gdpdu-audit-data-export.md)
- [Customize German audit file configuration](tasks/customize-german-audit-file-configuration.md)
- [Generate German audit file](tasks/german-audit-file.md)
- [Import German audit file configuration](tasks/import-german-audit-file-configuration.md)

## Depreciation
-   [Additional acquisition depreciation](emea-deu-additional-acquisition-depreciation.md)
-   [Depreciation adjustments for additional acquisitions in the second year](tasks/de-00002-depreciation.md)

## VAT declaration 
-   [VAT declaration for Germany](emea-deu-vat-declaration-germany.md)

## Electronic transmission of VAT declaration (ELSTER)
- [Electronic transmission of VAT declaration (ELSTER)](tasks/de-00003-electronic-transmission-elster.md)
- [Elster Testmerker (PDF download)](https://msdnshared.blob.core.windows.net/media/2018/04/Dyn365_ElsterTestmerker.pdf)
- [VAT declaration for Germany](emea-de-vat-declaration.md)

## Electronic invoices in Germany
- [Customer electronic invoices export](emea-deu-e-invoices.md)

## Credit memos originating from sales
You can specify the label that appears on credit memos that originate from sales.

On the **Legal entities** page, you can use the **Print corrective invoice on a sales memo** option on the **Foreign trade and logistics** tab to specify the label that appears on credit memos that originate from sales (sales orders, non-item sales, and project sales).

-   If the **Print corrective invoice on a sales memo** option is set to **No**, the label "Gutschrift" will be printed on all credit memos.
-   If the **Print corrective invoice on a sales memo** option is set to **Yes**, the label "Rechnungskorrektur” will be printed on credit memos for sales orders, free text invoices, and project invoices.


## Reports for Germany

| Report                     |  Description  |How to get to the report |
|----------------------------|--------------------------|----------------------------------------|
|German journal list report|The **German journal list** report displays a list of transactions, sorted by journal sequence number, that result from running the journalizing function. This report is used to review the status of general ledger processes. This report is typically used by chief executive officers, chief financial officers, compliance managers, accounting managers, accounting supervisors, and financial controllers. For more information, see [German journal list report](emea-deu-journal-list-report.md).|  **General ledger** > **Periodic** > **Journals** > **Ledger journal** > **German journal list**|

## Intra-community reporting
-   [EU sales list for Germany](emea-deu-eu-sales-list.md)
-   [Intrastat](emea-deu-intrastat.md)

## Additional resources
- [Microsoft Dynamics Localization Portal: Germany report](https://mbs.microsoft.com/files/customer/AX/Support/supportnews/Germany.html)
- [Electronic reporting overview](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md)
- [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)
- [Localization and regulatory features](../../fin-ops-core/dev-itpro/lcs-solutions/country-region.md?toc=%2ffin-and-ops%2ftoc.json)
- [Create a VAT declaration in the XML format without transferring it to ELSTER (White paper)](https://www.microsoft.com/download/details.aspx?id=101929)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
