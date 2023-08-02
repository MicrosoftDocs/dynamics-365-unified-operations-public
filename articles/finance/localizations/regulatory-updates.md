---
# required metadata

title: Regulatory updates
description: This article provides a list of planned and released regulatory updates for Microsoft Dynamics 365 Finance.
author: VStamberg
ms.date: 01/03/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Global
# ms.search.industry: 
ms.author: vastrup
ms.search.validFrom: 2019-3-31
ms.dyn365.ops.version: 10.0

---

# Regulatory updates

[!include [banner](../includes/banner.md)]

This article lists the regulatory updates that are planned and released in Dynamics 365 Finance supported localizations. Delivery timelines might change, and projected functionality might be different or might not be released. For more information, see [Microsoft policy](https://go.microsoft.com/fwlink/p/?linkid=2007332). 

Regulatory updates are features that are implemented to support new or changed country/region-specific legislation. For more information about planned and released country/region-specific features, see [Dynamics 365 and Power Platform release plans](/business-applications-release-notes/index).

Microsoft strives to implement new regulatory requirements as early as possible. The actual delivery date depends on the law announcement date, availability of the requirement details from the local authorities, the availability of the validation tools, and on the size and complexity of the change.

We plan to deliver regulatory updates in One Version service updates that are released in time for customers to update and be ready for the enforcement date (for transactional regulatory updates), or for the first mandatory reporting deadline (for regulatory updates related to reporting). Customers and partners can preview the new regulatory updates in the preview package provided for each service update.

In case of late announcement dates, late availability of requirement details or validation tools, or exceptionally large and complex changes, it might not be possible to make a regulatory update available by the General Availability date of a monthly update. In these cases, the regulatory update will be shipped as hot fixes for relevant available monthly updates.

Regulatory updates that are released as part of the monthly updated are indicated by release version only. Regulatory updates that are delivered either as hot fixes or as part of a release preview can be identified through the abbreviations HF and Preview, respectively. 

For the latest regulatory update plans, refer to the following table.   

|Country/region|Release date|Release version|Regulatory update|
|--------------------|---------------|-------|-------| 
| Austria, Bahrain, Belgium, Czechia, Denmark, Egypt, Finland, France, Germany, Hungary, Indonesia, Malaysia, Netherlands, New Zealand, Norway, Poland, Spain, Sweden, Switzerland, United Kingdom | July 2023 | 10.0.33HF, 10.0.34HF, 10.0.35HF, 10.0.36 | [Tax declaration model mapping update](https://fix.lcs.dynamics.com/Issue/Details?kb=0&bugId=819950&dbType=3&qc=8f64cac76f77df0328c110150b0ba0875154bb6f6bda44a38c5af33202fb172f) |
| Switzerland | July 2023 | 10.0.36 | [VAT declaration](emea-che-vat-declaration-switzerland.md) - 2024 |
| Poland | July 2023 | 10.0.36 | [SAF VAT Invoices - JPK-FA](emea-pol-standard-audit-file-saf.md#jpk-fa) project advance invoice handling |
| Poland | July 2023 | 10.0.36 | [VAT declaration - JPK-V7](emea-pol-vdek.md) - supplementary package based on ideas |
| United Arab Emirates | June 2023 | 10.0.36 | [FTA VAT Audit File (AE)](uae-faf.md) redesign to "SAF-T General model mapping" and [SAF-T feature](standard-audit-file.md) |
| France | June 2023 | 10.0.36 | [VAT declaration](emea-fra-vat-declaration-preview-france.md) - 2023 |
| Italy | June 2023 | 10.0.35HF, 10.0.36 | [Modello 770](emea-ita-modello770.md) - 2023 |
| Denmark | May 2023 | 10.0.35 | [Standard Audit File for Tax (SAF-T) for Denmark](emea-dnk-saf-t.md) |
| Germany | March 2023 | 10.0.31HF, 10.0.32HF, 10.0.33HF, 10.0.34HF, 10.0.35 | [VAT declaration](emea-deu-vat-declaration-germany.md) - 2023 |
| Italy | March 2023 | 10.0.31HF, 10.0.32HF, 10.0.33HF, 10.0.34 | [Yearly VAT communication - Dichiarazione Iva annuale](emea-ita-yearly-tax-communication.md) - 2023 |
| Italy | February 2023  | 10.0.30HF, 10.0.31HF, 10.0.32HF, 10.0.33 | [Unique certification](emea-ita-exil-unique-certification.md) - 2023 |
|      Brazil         |   February 2023         | 10.0.33HF         |    Record E115 of EFD ICMS IPI for SC becoming mandatory as of May 1, 2023  |
|      Brazil         |   March 2023         | 10.0.32HF, 10.0.33HF, 10.0.34HF         |    Exclusion of ICMS from the PIS/COFINS CREDITS calculation base (MP 1.159/23, IN 2121/22)-sales tax  |
|      Brazil         |   March 2023         | 10.0.32HF, 10.0.33HF, 10.0.34HF         |    Exclusion of ICMS from the PIS/COFINS CREDITS calculation base (MP 1.159/23, IN 2121/22)-withholding tax  |
|      Denmark         |   November 2022         | 10.0.32   |    VAT declaration preview report update for 2022  |
|      Italy      |   October 2022| 10.0.32 | The new type of TD28 document to communicate the purchase of goods from San Marino |
|      Italy      |   February 2023| 10.0.34 | Changes in the SEPA Payment tracings - Urgent Wire Transfers and Foreign Payments - Address and BIC fields |
|      Japan      |   March 2023| 10.0.34 | New Qualified Invoice System requirements in Japan from October 1, 2023 |
|      Poland      |   April 2023| 10.0.34 | Updates Payment terms in commercial transactions report (PL-00053) in accordance to D20222414L |
|      Saudi Arabia      |   November 2022| 10.0.32 | Retail - Electronic invoicing in Saudi Arabia - Phase 2 |


## Additional resources
- For more information about all planned and released country/region-specific regulatory updates, see [Search for country/region-specific regulatory updates](search-for-regulatory-updates.md). (Sign-in is required.)
- For a list of the localizations that are supported, see the [International availability guide](https://aka.ms/dynamics_365_international_availability_deck).



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
