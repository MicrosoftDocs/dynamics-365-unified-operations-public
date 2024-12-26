---
title: Removed or deprecated features in Dynamics 365 Finance 
description: Learn about features that are removed, or that are planned for removal from Dynamics 365 Finance, with an outline on features removed.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.custom: 
  - bap-template
  - evergreen
ms.date: 12/05/2024
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2020-03-02
ms.dyn365.ops.version: Platform update 33
---

# Removed or deprecated features in Dynamics 365 Finance

[!include [banner](../includes/banner.md)]

This article describes features that are removed, or that are planned for removal from Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning. 

> [!NOTE]
> Detailed information about objects in finance and operations apps can be found in the [Technical reference reports](/dynamics/s-e/global/axtechrefrep_61). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of finance and operations apps.

## Features removed or deprecated in the Finance 10.0.43 release

### Making Tax Digital – VAT return submission in the United Kingdom for on-premises deployments

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | To meet security requirements, we're implementing modifications to the Dynamics 365 Finance direct system-to-system integration with the HMRC web service for submitting VAT returns for companies registered for VAT in the UK. This enhancement involves the adoption of an [Electronic Invoicing service](/dynamics365/finance/localizations/global/gs-e-invoicing-service-overview?context=%2Fdynamics365%2Fcontext%2Ffinance) as an intermediary that facilitates secure access to the storage of credentials essential for software authorization within the HMRC APIs. *These services aren't accessible from on-premises deployments*. | 
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By June 6, 2025, we plan to no longer support the Making Tax Digital – VAT return submission in the United Kingdom **for on-premises** deployments. It's still possible to generate the report (VAT 100) in Excel and JSON formats. Direct submission for on-premises deployments to MTD VAT APIs is eliminated. For more information, see [Deprecation and removal of VAT return direct submission to UK MTD in Dynamics 365 Finance for on-premises deployments](https://go.microsoft.com/fwlink/?linkid=2292714) |

### Batch submission of VAT returns in the UK via Making Tax Digital for VAT in cloud deployments

[Making Tax Digital – VAT return submission in the United Kingdom](/dynamics365/finance/localizations/united-kingdom/emea-gbr-mtd-vat-integration?branch=main&branchFallbackFrom=liza-no-saf-971248)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | To meet security requirements, we're implementing modifications to the Dynamics 365 Finance direct system-to-system integration with the HMRC web service for submitting VAT returns for companies registered for VAT in the UK. This enhancement involves the adoption of an [Electronic Invoicing service](/dynamics365/finance/localizations/global/gs-e-invoicing-service-overview?context=%2Fdynamics365%2Fcontext%2Ffinance) as an intermediary, that facilitates secure access to the storage of credentials essential for software authorization within the HMRC APIs. VAT return submission in a batch is no longer available. | 
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By June 6, 2025, we plan to no longer support batch mode for submission of VAT return in the Making Tax Digital feature. It's still possible to generate in batch the report (VAT 100) in Excel and JSON formats. |

### SAF Accounting books (JPK_KR) for Poland

[SAF Accounting Books - JPK_KR](../localizations/poland/emea-pol-standard-audit-file-saf-kr.md)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Replaced with the new, regulatory-required [SAF Accounting Books Income Tax - JPK_KR_PD](../localizations/poland/emea-pol-standard-audit-file-saf-pd.md). | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By January 1, 2026, we plan to no longer support the SAF Accounting Books - JPK_KR, including the **Accounting Books (PL)** Electronic reporting (ER) format, the **SAF Accounting books** parameter in General ledger parameters, and the **SAF Accounting books** menu item in the **General ledger** module. |

### SAF VAT sales and purchase register (JPK_VAT) for Poland

[SAF VAT sales and purchase register - JPK_VAT](../localizations/poland/emea-pol-standard-audit-file-saf-vat.md)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Replaced with the new, regulatory-required [VAT declaration with registers (JPK-V7, VDEK)](../localizations/poland/emea-pol-vdek.md). | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By January 1, 2026, we plan to no longer support the [SAF VAT sales and purchase register - JPK_VAT, including the **VAT Register (PL)** Electronic reporting (ER) format, the **SAF VAT sale and purchase registers** parameter in General ledger parameters, and the **SAF VAT sales and purchase register** menu item in the **General ledger** module. |

## Features removed or deprecated in the Finance 10.0.42 release

### Sales tax report for Latvia (design based on reporting codes)

[Sales tax report for Latvia](../localizations/latvia/emea-lva-vat-statement-details.md)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Replaced with a new value-added tax (VAT) declaration design, [VAT declaration for Latvia](../localizations/latvia/emea-lva-vat-declaration-latvia.md). | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By October 1, 2025, we plan to no longer support the Sales tax report for Latvia design based on reporting codes, including the **VAT declaration (LV)**, **VAT declaration 218 (LV)**, **VAT declaration v6 (LV)**, **VAT declaration v7 (LV)** Electronic reporting (ER) formats under the **VAT declaration model** together with the following objects: EDT/TaxAmountOverpaid_LV, Enum/LvBusinessType, Enum/LvDocumentType, Enum/LvDocumentAggregationType, Enum/TaxTransDataOrigin_W, Enum/TaxDeclarationType_W, Class/VATDeclarationService_LV, Table/TaxTable/Field/BusinessType_LV, Table/TmpTaxReportTaxTransData_LV. New **VAT declaration XML (LV)** and **VAT declaration Excel (LV)** ER formats are introduced under the **Tax declaration** model. |

### Sales tax report for Norway (design based on reporting codes)

[VAT statement for Norway](../localizations/norway/emea-nor-sales-tax-payment-report.md)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Replaced with a new value-added tax (VAT) declaration design, [VAT return with direct submission to Altinn](../localizations/norway/emea-nor-vat-return.md). | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By January 1, 2026, we plan to no longer support the Sales tax report for Norway design that's based on reporting codes, including the **VAT declaration (NO)** Electronic reporting (ER) format under the **VAT declaration model** together with following objects: Table/TmpTaxTransInfo_W, Class/VATDeclaraitonContract_W. New **VAT declaration XML (NO)** and **VAT declaration Excel (NO)** ER formats are introduced under the **Tax declaration** model. |

## Features removed or deprecated in the Finance 10.0.41 release

### Sales tax report for Lithuania (design based on reporting codes)

[Sales tax report for Lithuania](../localizations/lithuania/emea-ltu-vat-statement-details.md)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Replaced with a new value-added tax (VAT) declaration design, [VAT declaration for Lithuania](../localizations/lithuania/emea-ltu-vat-declaration-lithuania.md). | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By May 1, 2025, we plan to no longer support the Sales tax report for Lithuania design that's based on reporting codes, including the **VAT declaration (LT)** Electronic reporting (ER) format under the **VAT declaration model**, **Main economic activity code**, and **Deduction percent** fields on the **Sales tax** tab of the **General ledger parameters** page. New **VAT declaration XML (LT)** and **VAT declaration Excel (LT)** ER formats are introduced under the **Tax declaration** model. |

## Features removed or deprecated in the Finance 10.0.39 release

### Sales tax report for Estonia (design based on reporting codes)

[Sales tax report for Estonia](../localizations/estonia/emea-est-vat-statement-details.md)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Replaced with a new value-added tax (VAT) declaration design, [VAT declaration for Estonia](../localizations/estonia/emea-est-vat-declaration.md). | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By February 1, 2025, the Sales tax report for Estonia (Estonian report layout) won't be supported. New **VAT declaration XML (EE)** and **VAT declaration Excel (EE)** Electronic reporting (ER) formats are introduced under the **Tax declaration** model. |

### Sales tax (Italy) SSRS format, Italian report layout, menu item

[Italian sales tax books](../localizations/italy/emea-ita-fiscal-books.md)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Replaced with a new value-added tax (VAT) declaration design, [Configure and report Italian sales tax books](../localizations/italy/emea-ita-sales-tax-books.md). | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By March 1, 2025, we plan to no longer support the Sales tax (Italy) SSRS format, Italian report layout, menu item. New **VAT Declaration PDF (IT)** Electronic reporting (ER) formats are introduced under the **Tax declaration** model. |

## Features removed or deprecated in the Finance 10.0.38 release

### Financial Dimension data model changes  

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Replaced 22 existing fields starting with SystemGenerated* with three new fields in the DimensionAttributeValueCombination table and DimensionAttributeValueSet table. |
| **Replaced by another feature?**   | N/A |
| **Product areas affected**         | Developer |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By December 22, 2023. These 22 fields and related indexes were removed on December 27, 2024 to improve performance and reduce storage costs. All access to these fields should be internal only to the core Financial dimension APIs and no action is required if using our APIs. If any direct access to these fields is enabled using a customization, make the necessary changes to remove these direct references ASAP. The fields are removed in Dynamics 365 Finance release 10.0.42 in December of 2024.|


### Electronic Invoicing integration using Microsoft Dataverse

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | This feature is no longer required in the new version of the globalization feature for Indonesia, [Electronic invoicing for Indonesia](../localizations/indonesia/e-invoicing-id-get-started.md). | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Finance 10.0.38 release no longer supports **Electronic Invoicing integration using Microsoft Dataverse**. This feature is no longer required by the new version of the globalization feature for Electronic invoicing in Indonesia. |


### Dataverse solution for Electronic invoicing

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | This solution is no longer required in the new version of the globalization feature for Indonesia, [Electronic invoicing for Indonesia](../localizations/indonesia/e-invoicing-id-get-started.md). | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Finance 10.0.38 release no longer supports **Dataverse solution for Electronic invoicing**. This plugin isn't required by the new version of the globalization feature for Electronic invoicing in Indonesia. |

### TaxYearlyCom_IT, TaxYearlyComReport_IT tables for Italian Yearly tax communication

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | The `TaxYearlyCom_IT` and `TaxYearlyComReport_IT` tables for Italian Yearly tax communication are replaced with new `TaxYearlyComV2_IT` and `TaxYearlyComReportV2_IT` tables. | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Finance 10.0.38 release no longer supports the `TaxYearlyCom_IT` and `TaxYearlyComReport_IT` tables for Italian Yearly tax communication. They're replaced with new `TaxYearlyComV2_IT` and `TaxYearlyComReportV2_IT` tables for Italian Yearly tax communication. |


## Features removed or deprecated in the Finance 10.0.36 release

### "FTA VAT Audit File (AE)" Electronic reporting (ER) format using the "Standard Audit File model mapping" and "FAF declaration" menu item

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Replaced with a new **FTA Tax Audit File - FAF in TXT (AE)** Electronic reporting (ER) format that uses the **SAF-T General** model mapping and the **Standard Audit File for Tax (SAF-T) electronic report** feature. For more information, see [FTA Tax Audit File (FAF) in TXT format for the United Arab Emirates](../localizations/uae-faf.md). | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By July 1, 2024, Microsoft no longer supports the **FTA VAT Audit File (AE)** ER format that uses the **Standard Audit File** model mapping and the **FAF declaration** menu item (**Tax** \> **Declarations** \> **FAF declaration**). A new **FTA Tax Audit File - FAF in TXT (AE)** ER format was introduced that uses the **SAF-T General** model mapping and can be used with the [Standard Audit File for Tax (SAF-T) electronic report](../general-ledger/standard-audit-file.md) feature. For more information, see [FTA Tax Audit File (FAF) in TXT format for the United Arab Emirates](../localizations/uae-faf.md). |

## Features removed or deprecated in the Finance 10.0.31 release

### EDIFACT PAYMUL (AT) configuration under Payment model

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Replaced with a new format that is based on ISO 20022 pain.001.001.09. | 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: Banks in Austria deprecated EDICFACT-PAYMUL for cross-border payments by November 2022 and replace it with XML version pain.001.001.09N. A new configuration was added under the Global Configuration repository which enables users to complete the cross-border payment request. |

## Features removed or deprecated in the Finance 10.0.30 release

### Revenue recognition

[Revenue recognition](../../finance/accounts-receivable/revenue-recognition-overview.md)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** |Replaced with improved functionality, [Subscription billing](../../finance/accounts-receivable/subscription-billing-summary.md)
| **Replaced by another feature?**   | Yes |
| **Product areas affected** | Application |
| **Deployment option** | All |
| **Status** | Deprecated: After April 2023, the Revenue recognition functionality in Dynamics 365 Finance no longer receives support with bug fixes. Customers are asked to use the improved functionality, [Subscription billing](../../finance/accounts-receivable/subscription-billing-summary.md). After January 2024, the Revenue recognition feature isn't available. Customers are asked to move to the improved Subscription billing functionality. The bundle feature, which is part of revenue recognition, was replaced and released as a separate feature available in 10.0.36.|


## Features removed or deprecated in the Finance 10.0.29 release

### Stock transfer orders that have tax on the transfer price

[Stock transfer orders that have tax on the transfer price](../../finance/localizations/apac-ind-gst-stock-transfer-transactions.md)

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** | Replaced by improved functionality, [Stock transfer orders for India](../../finance/localizations/apac-ind-stock-transfer.md)|
| **Replaced by another feature?**   | Yes |
| **Product areas affected** | Application |
| **Deployment option** | All |
| **Status** | Deprecated: After April 2023, the **Stock transfer orders that have tax on the transfer price** functionality no longer receives support with bug fixes and security fixes. Customers are asked to use the improved functionality, [Stock transfer orders for India](../../finance/localizations/apac-ind-stock-transfer.md). After October 2023, the **Stock transfer orders that have tax on the transfer price** functionality is no longer available, and customers are asked to move to the improved functionality. |

### Bank statement import and export of positive pay file

| &nbsp;  | &nbsp;  |
|---|---|
| **Reason for deprecation/removal** |Replaced by improved functionality, import bank statements and export positive pay files.| 
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: XSLT functionality for importing and exporting files no longer receives support with bug fixes and security fixes. Customers are asked to use the improved functionality: [Set up positive pay files by using Electronic reporting](../../finance/accounts-payable/set-up-positive-pay-er.md) and [Set up advanced bank reconciliation import by using Electronic reporting](../../finance/accounts-payable/import-bai2-er.md). After September 2022, the XSLT functionality is no longer available, and customers are asked to move to the improved functionality.|


## Features removed or deprecated in the Finance 10.0.26 release

### Sales tax report for Finland (design based on reporting codes)

[Sales tax report for Finland](../localizations/emea-fin-sales-tax-payment-report-finland.md)

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with a new VAT declaration design, [VAT declaration for Finland](../localizations/emea-fin-vat-declaration.md). |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By March 1, 2023, we plan to no longer support the Sales tax report for Finland (Finnish report layout). New **VAT declaration TXT (FI**) and **VAT declaration Excel (FI)** Electronic reporting (ER) formats are introduced under the **Tax declaration** model. |

## Features removed or deprecated in the Finance 10.0.24 release

### Sales tax report for Sweden (design based on reporting codes)

[Sales tax report for Sweden](../localizations/emea-swe-sales-tax-payment-report-sweden.md)

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with a new VAT declaration design, [VAT declaration for Sweden](../localizations/emea-swe-vat-declaration-sweden.md) |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By December 1, 2022, we plan to no longer support the Sales tax report for Sweden (Swedish report layout). New **VAT declaration XML (SE**) and **VAT declaration Excel (SE)** Electronic reporting (ER) formats are introduced under the **Tax declaration** model. |

### VAT statement for Austria (design based on reporting codes)

[VAT statement details for Austria](../localizations/emea-aut-vat-statement-details.md)

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with a new VAT declaration design, [VAT declaration for Austria](../localizations/emea-aut-vat-declaration-austria.md) |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By December 1, 2022, we plan to no longer support the **VAT declaration (AT)** Electronic reporting (ER) format under **VAT declaration model**. New **VAT declaration XML (AT)** and **VAT declaration Excel (AT)** formats are introduced under the **Tax declaration** model. |

### ELSTER declaration for Germany (design based on reporting codes), \"Electronic tax declaration log\" menu item and page, \"Electronic tax declaration setup\" menu item and page, German report layout (TaxReport_DE) SSRS format

[VAT statement](../localizations/emea-de-vat-declaration.md)</br>
[Set up electronic Tax declaration for Germany](../../fin-ops-core/dev-itpro/analytics/tasks/setup-electronic-tax-declaration-germany.md)</br>

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with a new VAT declaration design, [VAT declaration for Germany](../localizations/emea-deu-vat-declaration-germany.md) |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By December 1, 2022, Microsoft no longer supports the **Elster (DE)** Electronic reporting (ER) format and **Elster model**. New **VAT declaration XML (DE)** and **VAT declaration Excel (DE)** ER formats are introduced under the **Tax declaration** model. Microsoft also no longer supports the **Tax** \> **Declarations** \> **Sales tax** \> **Electronic tax declaration log** menu item and page, the **Tax** \> **Setup** \> **Sales tax** \> **Electronic tax declaration setup** menu item and page, the **Tax** \> **Setup** \> **Sales tax** \> **Electronic tax certificates** menu item and page, and the German report layout (TaxReport\_DE) SQL Server Reporting Services (SSRS) format. The process of VAT reporting in Germany is supported in [Electronic messaging](../general-ledger/electronic-messaging.md) functionality. For more information, see [VAT declaration for Germany](../localizations/emea-deu-vat-declaration-germany.md). |

### OB declaration for Netherlands (design based on reporting codes), \"Electronic OB declaration\" menu item and page, Dutch report layout (TaxReport_NL) SSRS format

[OB declaration](../localizations/emea-nl-vat-declaration.md)

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with a new VAT declaration design, [VAT declaration for Netherlands](../localizations/emea-nl-vat-declaration-netherlands.md) |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By December 1, 2022, Microsoft no longer supports the **OB declaration (NL)** Electronic reporting (ER) format and **OB declaration model**. New **VAT declaration XML (NL)** and **VAT declaration Excel (NL)** ER formats are introduced under the **Tax declaration** model. The **Tax** \> **Declarations** \> **Sales tax** \> **Electronic OB declaration** menu item and page, and the Dutch report layout (TaxReport_NL) SSRS format are no longer supported. The process of VAT reporting in the Netherlands is supported in [Electronic messaging](../general-ledger/electronic-messaging.md) functionality. For more information, see [VAT declaration for Netherlands](../localizations/emea-nl-vat-declaration-netherlands.md). |

## Features removed or deprecated in the Finance 10.0.20 release

### "RTIR Query Invoice Data Request (HU)" Electronic reporting (ER) format configuration

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Excluded from electronic messaging processing of interoperation with Hungarian online invoicing system |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By April 15, 2022, we plan to no longer support "RTIR Query Invoice Data Request (HU)" format configuration. |

### "French FEC audit file" Electronic reporting (ER) format for France under "German audit file output" format

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with new "FEC audit file (FR)" format |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: by May 1, 2022, we plan to no longer support "French FEC audit file" Electronic reporting (ER) format for France under "German audit file output" format. New FEC audit file (FR) format is introduced instead under the "Data export model." |

## Features removed or deprecated in the Finance 10.0.17 release

### LCS repository as a storage option for Electronic reporting configurations

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with the new Regulatory Configuration Service (RCS) Global repository |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Dynamics 365 Finance, Supply Chain Management, and Project Operations products|
| **Deployment option**              | All |
| **Status**                         | Deprecated: By April 01, 2022, we plan to no longer support the Microsoft Dynamics Lifecycle Services (LCS) repository as a storage option for Electronic reporting (ER) configurations. New Microsoft ER configurations are published for download exclusively from the Global repository. The Global repository can be accessed from the Dynamics 365 products and RCS. For more information, see [Import ER configurations from RCS](../../fin-ops-core/dev-itpro/analytics/tasks/import-configuration-rcs.md) and [Regulatory Configuration Service - Lifecycle Services storage deprecation](../localizations/rcs-lcs-repo-dep-faq.md). |

## Features removed or deprecated in the Finance 10.0.16 release

### "VAT declaration (CZ)" and "Control statement export (CZ)" Electronic reporting formats for Czech Republic

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with new formats |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By January 22, 2022, we plan to no longer support "VAT declaration (CZ)," "Control statement export (CZ)" Electronic reporting (ER) formats. New VAT declaration XML (CZ), VAT declaration Excel (CZ), VAT control statement XML (CZ) formats are introduced instead under the "Tax declaration" model. |

### "Ledger transaction export format (BE)" Electronic reporting format and respective "Ledger transaction export (BE)" model for Belgium

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with new ER format under "Standard Audit File (SAF-T)" model.  |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By December 1, 2021, we plan to no longer support the "Ledger transaction export format (BE)" Electronic reporting (ER) format and respective "Ledger transaction export (BE)" model. A new "General ledger data export (BE)" format together with "General ledger data model mapping" are introduced instead under the "Standard Audit File (SAF-T)" model. |

### "VAT 100" report for the United Kingdom in SSRS format

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced with new ER format - "VAT Declaration Excel (UK)" format under "Tax declaration model."  |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By December 1, 2021, we plan to no longer support the "VAT 100 report" in SSRS format. A new "VAT Declaration Excel (UK)" format under "Tax declaration model" was introduced in the [MTD VAT feature](../localizations/emea-gbr-mtd-vat-integration.md). |

## Features removed or deprecated in the Finance 10.0.15 release

### Internet Explorer 11 support for Dynamics 365 is deprecated

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Effective December 2020, Microsoft Internet Explorer 11 support for all Dynamics 365 products is deprecated, and Internet Explorer 11 won’t be supported after August 2021.<br><br>This impacts customers who use Dynamics 365 products designed to use through an Internet Explorer 11 interface. After August 2021, Internet Explorer 11 won't be supported for such Dynamics 365 products. |
| **Replaced by another feature?**   | We recommend that customers transition to Microsoft Edge.|
| **Product areas affected**         | All Dynamics 365 products |
| **Deployment option**              | All|
| **Status**                         | Deprecated. Internet Explorer 11 won’t be supported after August 2021.|

## Features removed or deprecated in the Finance 10.0.12 release

### Not deprecated: Polish SSRS reports: Sales VAT register, Purchase VAT register, EU summary VAT register – Feature reference PL-00014

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Not legally required.  |
| **Replaced by another feature?**   | Yes (Excel format for Standard Audit File with VAT declaration - JPK_VDEK) |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Not deprecated: As of April 27, 2021, we plan to continue to support the SSRS reports: **Sales VAT register, Purchase VAT register, EU summary VAT register – Feature reference PL-00014**. Excel format example for Standard Audit File with VAT declaration (JPK_VDEK) was introduced. |

## Features removed or deprecated in the Finance 10.0.11 release

### Norwegian Standard main accounts

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Redesign  |
| **Replaced by another feature?**   | Yes (Replaced with ER format application-specific parameters) |
| **Product areas affected**         | Application |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By April 1, 2021, we plan to no longer support functionality related to Standard main accounts: Reference field, related table, data entity. |

## Features removed or deprecated in the Finance 10.0.7 release

### Workflow request change dialog box no longer includes user selection drop-down list

| &nbsp; | &nbsp; |
|------------|--------------------|
| **Reason for deprecation/removal** | Changed to the feature with account groups selection.  |
| **Replaced by another feature?**   | Yes |
| **Product areas affected**         | Workflow |
| **Deployment option**              | All |
| **Status**                         | Deprecated: By December 1, 2020, we plan to no longer support Chinese voucher types set up without Account groups selection. Find more details about the new design in [What's new in 10.0.7](../dev-itpro/whats-new-changed-10-0-7.md). |

## Previous announcements about removed or deprecated features
To learn more about features that are removed or deprecated in previous releases, see [Removed or deprecated features in previous releases](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

