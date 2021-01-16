---
# required metadata

title: Austria overview
description: This topic provides an overview of Dynamics 365 Finance functionality that is specific to Austria.
author: ShylaThompson
manager: AnnBe
ms.date: 07/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Austria
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Austria overview

[!include [banner](../includes/banner.md)]

This topic includes information and links to resources that can help you set up Dynamics 365 Finance for legal entities with a primary address in Austria.

## Depreciation

For companies in Austria, depreciation for additional acquisitions and acquisition adjustments is calculated according to specific rules. For more information, see [Half-year depreciation on additional acquisitions for Austria](emea-aut-half-year-depreciation.md).

## Packing material fees

In Austria, packing materials are divided into various categories, for example, household and commercial. The government provides tax rates for packing materials in each category. The category that packing material belongs to depends on size and the products that the packaging was used for. Packing material fees are calculated and reported, however the fees aren't considered taxes that must be paid to an authority, which means that ledger transactions are not posted automatically. For more information, see [Packing material fee calculation for Austria](emea-aut-packing-material-fee-calculation.md).

## Purchase duties

A purchase duty is a tax on incoming sales tax that is calculated as a percentage of the paid sales tax. This section includes information about purchase duties for legal entities that have their primary address in Austria. For more information about the global sales tax functionality, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md).

The calculation of purchase duties is based on sales tax codes. To include a sales tax code in the purchase duty calculation, select the **Purchase duty** check box on the **Saxes tax codes** page. 

You can specify purchase duty settings on the **Tax setup** menu on the **Purchase duty** page. You can set the duty identifier (for example, **KU**), description, tax authority, and accounts that will be used for posting. Duty account is a balance account where the liability for the purchase duty is registered. Cost account is a profit and loss account that the costs are posted to and a settle account where settlement transactions will be generated.

To specify the value of the purchase duty, click **Purchase duty value** to open the **Purchase duty value** page. You can specify the purchase duty percentage (for example **0,30**) for the required period.

Purchase duties are generated when you settle and post sales taxes. You can generate the **Purchase duty** report from the **Purchase duty reporting** menu.

## VAT
For information about setting up the value-added tax (VAT) statement for legal entities in Austria, see [VAT statement details for Austria](emea-aut-vat-statement-details.md). 

For general information about the setup of VAT statements, see [VAT reporting for Europe](emea-vat-reporting.md).

## Reports for Austria

| Report                     | How to get to the report | Additional information                 |
|----------------------------|--------------------------|----------------------------------------|
|Cross-border services report|**General ledger** > **Reports** > **External** > **Cross-border services**|This report prints a summary of the incoming and outgoing cross-border services, countries that are the providers or recipients of the cross-border services, and net amounts paid for the services. This report is typically used by accounting managers, accountants, and sales managers to inquire into the status of sales transactions. |


## Additional resources

- [Microsoft Dynamics Localization Portal: Austria report](https://mbs.microsoft.com/files/customer/AX/Support/supportnews/Austria.html)
- [Electronic reporting overview](../../dev-itpro/analytics/general-electronic-reporting.md)
- [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)
