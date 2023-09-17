---
title: Belgium overview
description: This article provides an overview of functionality specific to Belgium.
author: AdamTrukawka
ms.date: 05/27/2022
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: belgium
ms.author: atrukawk
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
---

# Belgium overview

[!include[banner](../includes/banner.md)]

This article includes information and links to resources that should be considered for legal entities with a primary address in Belgium.

## Coda bank statement
CODA is a report format that is used in the Belgian electronic banking system. For more information, see [CODA bank statement](emea-bel-coda-bank-statement-import.md).

## Export ledger transactions
You can export ledger transactions for a specific interval, such as a fiscal year as an ASCII file in the CED format. You can use batch processing to export transactions. To set up batch processing, go to **General ledger** > **Periodic** > **Export ledger transactions**. For more information, see [Export ledger transactions](emea-bel-export-ledger-transactions.md).

## VAT declaration
For information about how to set up and work with new VAT declaration in Belgium, review [VAT declaration (Belgium)](emea-bel-vat-declaration-belgium.md).

## INTERVAT tax declaration

> [!NOTE]
> This feature has been replaced with the VAT declaration functionality. For more information, see [VAT declaration (Belgium)](emea-bel-vat-declaration-belgium.md).

For information about how to set up and create the INTERVAT tax declaration for legal entities in Belgium only, see [INTERVAT tax declaration](emea-bel-intervat-tax-declaration.md). 
For information about standard reports that can help you with the INTERVAT tax declaration and reconciliation analysis, see [Reconciliation reports for Belgium](emea-bel-reconciliation-reports.md).

## Reports for Belgium

| Report                     | How to get to the report | Additional information                 |
|----------------------------|--------------------------|----------------------------------------|
|Belgisch Luxemburgs Wissel Instituut (BLWI) report|**Tax** > **Declarations** > **Foreign trade** > **BLWI** | To set up BLWI information, see [Set up payment balance reporting (Belgium)](tasks/be-00011-set-up-payment-balance-reporting.md). To generate the BLWI report, see [Create and transfer transactions to the BLWI (Belgium)](tasks/be-00011-create-transfer-blwi.md).| 
|PRODCOM report|**Tax** > **Declarations** > **Foreign trade** > **PRODCOM**|Manufacturers of industrial products send the PRODCOM report to the Nationaal Instituut voor de Statistiek (NIS) in response to the routine PRODCOM survey. The PRODCOM report displays production statistics for industrial products that are manufactured by production companies operating in Belgium. This report is typically used by accounting managers and accountants. For more information, see [Set up and maintain PRODCOM](emea-bel-prodcom-report.md). |
|Journal reports|**General ledger** > **Inquiries and reports** > **Journal reports**|Periodically, Belgian companies must print a report for each journal. The report provides a chronological list of all the postings to the general ledger accounts for each journal. These reports prove the integrity of the accountancy and are used during financial audits to reconcile VAT settlement with the postings on the corresponding general ledger accounts. For more information, see [Journal reports (Posting journals)](emea-bel-journal-reports.md). |
|Annual VAT listing of domestic sales| **Tax** > **Inquiries and reports** > **Sales tax reports** > **Invoice turnover report – Belgium** | The Invoice turnover report is sent to the authorities once a year. It's used to report the turnover for Belgian VAT-obliged customers, if that turnover exceeds a specific amount. The report includes invoices from customer transactions where the customers have an enterprise number that is formatted according to the guidelines of the Belgian authorities. For more information, see [Annual VAT listing of domestic sales](emea-bel-annual-vat-listing-of-domestic-sales.md). |
|Belgium Intrastat|  **Tax** > **Declarations** > **Foreign trade** > **Intrastat** | You can use the **Intrastat** page to generate and report information about trade among European Union (EU) countries/regions. The Belgium Intrastat declaration contains information about the trade of goods for reporting. For more information, see [Belgium Intrastat](emea-bel-intrastat.md). |
|EU sales list for Belgium|  **Tax** > **Declarations** > **Foreign trade** > **EU sales list** | You can use the **EU sales list** page to generate and report information about the sale of goods and services for reporting in XML format. For more information, see [EU sales list for Belgium](emea-bel-eu-sales-list.md). |

## Additional resources

- [Microsoft Dynamics Localization Portal: Belgium report](https://mbs.microsoft.com/files/customer/AX/Support/supportnews/Belgium.html) (requires CustomerSource account)
- [Electronic reporting overview](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md)
- [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)
- [Localization and regulatory features](../../fin-ops-core/dev-itpro/lcs-solutions/country-region.md?toc=%2ffin-and-ops%2ftoc.json)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
