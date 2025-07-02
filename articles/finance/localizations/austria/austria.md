---
title: Austria overview
description: Access an overview of Dynamics 365 Finance functionality that is specific to Austria, including overviews on depreciation, material fees, and purchase duties.
author: liza-golub
ms.author: egolub
ms.topic: overview
ms.date: 07/02/2025
ms.reviewer: johnmichalak
ms.search.region: Austria
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
---

# Austria overview

[!include [banner](../../includes/banner.md)]

This article includes information and links to resources that can help you set up Dynamics 365 Finance for legal entities with a primary address in Austria.

## Depreciation

For companies in Austria, depreciation for additional acquisitions and acquisition adjustments is calculated according to specific rules. Learn more in [Half-year depreciation on additional acquisitions for Austria](emea-aut-half-year-depreciation.md).

## Packing material fees

In Austria, packing materials are divided into various categories, for example, household and commercial. The government provides tax rates for packing materials in each category. The category that packing material belongs to depends on size and the products that the packaging was used for. Packing material fees are calculated and reported, however the fees aren't considered taxes that must be paid to an authority, which means that ledger transactions are not posted automatically. Learn more in [Packing material fee calculation for Austria](emea-aut-packing-material-fee-calculation.md).

## Purchase duties

A purchase duty is a tax on incoming sales tax that is calculated as a percentage of the paid sales tax. This section includes information about purchase duties for legal entities that have their primary address in Austria. Learn more about the global sales tax functionality in [Sales tax overview](../../general-ledger/indirect-taxes-overview.md).

The calculation of purchase duties is based on sales tax codes. To include a sales tax code in the purchase duty calculation, select the **Purchase duty** check box on the **Saxes tax codes** page. 

You can specify purchase duty settings on the **Tax setup** menu on the **Purchase duty** page. You can set the duty identifier (for example, **KU**), description, tax authority, and accounts that will be used for posting. Duty account is a balance account where the liability for the purchase duty is registered. Cost account is a profit and loss account that the costs are posted to and a settle account where settlement transactions will be generated.

To specify the value of the purchase duty, click **Purchase duty value** to open the **Purchase duty value** page. You can specify the purchase duty percentage (for example **0,30**) for the required period.

Purchase duties are generated when you settle and post sales taxes. You can generate the **Purchase duty** report from the **Purchase duty reporting** menu.

## Reports for Austria

| Report                     | How to get to the report | Additional information                 |
|----------------------------|--------------------------|----------------------------------------|
|Cross-border services report|**General ledger** > **Reports** > **External** > **Cross-border services**|This report prints a summary of the incoming and outgoing cross-border services, countries/regions that are the providers or recipients of the cross-border services, and net amounts paid for the services. This report is typically used by accounting managers, accountants, and sales managers to inquire into the status of sales transactions. Learn more in [Cross-border services report](emea-aut-cross-border-services-report.md).|
|Intrastat report|**Tax** > **Declarations** > **Foreign trade** > **Intrastat**|You can use the Intrastat page to generate and report information about trade among European Union (EU) countries/regions. The Austrian Intrastat declaration contains information about the trade of goods for reporting. Learn more in [Austrian Intrastat](emea-aut-intrastat.md).|
|EU sales list for Austria|**Tax** > **Declarations** > **Foreign trade** > **EU sales list**|This article provides information about the European Union (EU) sales list report that is based on form U13. The Austrian EU sales list report contains information about the sale of goods and services. Learn more in [EU sales list for Austria](emea-aut-eu-sales-list.md).|
| VAT declaration U30 |**Tax** > **Declarations** > **Report sales tax for settlement period**|This article describes how to set up and generate an advance value-added tax (VAT) declaration U30 for Austria in the official XML format. It also describes how to preview the VAT declaration in Microsoft Excel. Learn more in [VAT declaration (Austria)](emea-aut-vat-declaration-austria.md).|
| Annual sales tax report U1 |**Tax** > **Inquires and reports** > **Sales tax reports**|This article describes how to generate an Annual sales tax report U1 for Austria in PDF format. Learn more in [Annual sales tax report U1](emea-aut-annual-sales-tax-report.md).|


## Additional resources

<!-- - [Microsoft Dynamics Localization Portal: Austria report](https://mbs.microsoft.com/files/customer/AX/Support/supportnews/Austria.html) -->
- [Electronic reporting overview](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md)
- [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
