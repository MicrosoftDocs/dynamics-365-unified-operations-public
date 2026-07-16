---
title: Latin America overview
description: Access an overview of functionality specific to Latin American, including an outline on country/region localization availability.
author: MatiasPizmeny01
ms.author: v-mpizmeny
ms.topic: overview
ms.date: 06/22/2026
ms.custom: bap-template
ms.reviewer: johnmichalak  
--- 

# Expansion of LATAM localization coverage

[!include [does not apply to](includes/does-not-apply-to.md)]

In Latin America (LATAM), Microsoft Dynamics 365 Finance previously supported out-of-box localizations for Brazil and Mexico. Then, in 2023 release wave 1, Microsoft delivered out-of-box localizations for more countries and regions in Latin America. In future release waves, Microsoft continues to extend the scope of supported countries and regions in Latin America to address the needs of multiple global and local customers.

Tax compliance requirements are complex and change frequently. Companies are looking for more out-of-box geographic coverage and tax compliance automation from Microsoft. By releasing localizations for more LATAM countries and regions, Microsoft significantly extends its country and region support. It also gives customers more consistent out-of-box regulatory compliance coverage in multiple areas, including tax reporting and electronic invoicing.

> [!NOTE]
> Out-of-box localization of Dynamics 365 Commerce for LATAM countries and regions is limited to Brazil and Mexico and doesn't include other LATAM countries and regions.

## Get started with LATAM localization in Finance

Before you use Finance in any of the currently supported LATAM countries and regions (Chile, Costa Rica, Panama, Nicaragua, Uruguay, Paraguay, Guatemala, Colombia, Ecuador, Bolivia, Peru, Dominican Republic, Venezuela), users must first configure the Cross-LATAM functionalities. These foundational settings are essential to enable the legal, tax, and treasury features required for each country and region, ensuring compliance and proper system behavior across the region.

## Prerequisites

Before starting the configuration, ensure the following conditions are true:

- Users involved in the setup have the required privileges to access the forms involved.
- The **LATAM globalization expansion** extension in the **Feature Management** workspace is enabled, along with the country and region specific feature of your target location.
- **Before you begin, make sure you're familiar with the legal, accounting, and tax requirements applicable in the target country/region**. LATAM localization articles focus on how to configure and use the product features. They don't cover the underlying regulatory context or the specific reasons behind country and region reporting requirements.

## Why Cross-LATAM configuration is required

The Cross-LATAM functionalities in Finance provide a unified framework that helps users configure the legal, tax, and treasury characteristics required by each LATAM country and region. These functionalities enable the setup of country and region specific fiscal documents, such as invoices, credit notes, and payment orders, while maintaining a consistent structure across all forms. Although the forms are identical for all countries and regions, the configuration parameters vary depending on local requirements.

The transactional use of localization features is also standardized across LATAM. The same LATAM extension is applied in all countries, with differences arising only in the fields populated based on each country’s and regions's configuration. When it comes to reporting, each country and region has its own specific reports. However, all reports are built using Electronic Reporting, ensuring consistent methodology and operational logic across the region.

## Key configuration areas

Located under **Dynamics 365 Finance > Supported countries/regions > Latin America** in **Microsoft Learn**, articles provide a centralized entry point to LATAM localization content. The sections below summarize the main functional areas supported by the LATAM localization framework.

### Latin America get started

These articles guide you through enabling parameters and getting started with configuring and using the LATAM localization.

Learn more in [Set up transaction posting for Latin America](ltm-post-transactions.md).

### Tax and legal attributes

These articles focus on configuring the legal and tax-related data required for compliance in LATAM countries and regions. They cover taxpayer classifications, tax ID formats, address structures, and how to configure customers and vendors based on regulatory needs.

Learn more in [Tax and legal attributes for Latin America](ltm-tax-legal-attributes.md).

### Document classification configurations

This section provides guidance to help you configure various types of business, internal, and treasury documents required across LATAM countries and regions, such as invoices, delivery notes, payment orders, and others. The articles support the setup of document classes and class types to ensure proper categorization and processing. Other configuration options allow defining document attributes, establishing relationships between classification elements, and aligning with country and region specific legal and reporting requirements.

Learn more in [Document classes for Latin America](ltm-core-document-class.md).

### LATAM extension in transactions

Here, you learn how LATAM-specific settings shape various types of transactions, including sales, purchases, inventory transfers, and payments. These articles provide guidance on using localization during transaction posting and on referencing electronic documents.

For example, learn more about sales transactions in [Sales invoice posting for Latin America](ltm-core-sales-invoice-posting-latam.md).

> [!NOTE]
> LATAM localization uses Electronic Reporting (ER) to generate fiscal, tax, and electronic invoicing reports. The correct output of these reports depends on the proper configuration of the cross-LATAM functionalities and the consistent application of the LATAM extension in transactions. Misconfigurations might result in incomplete or unexpected report behavior.

### LATAM withholding taxes

This section provides an overview of how to configure and apply withholding taxes in LATAM. It includes step-by-step instructions to configure sales tax codes and withholdings, post invoices and payments with withholdings, and ensure accurate tax reporting. These configurations are important to meet fiscal obligations in countries and regions where withholding is mandatory.

Learn more in [LATAM withholding taxes overview](ltm-latam-withholding-taxes-overview.md).

### Inquiries and reports

These articles guide users through the setup and use of Electronic Reporting (ER) for LATAM scenarios. This section provides the necessary configuration steps to generate tax and accounting reports, set up and use electronic invoicing, and ensure proper formatting and printing of fiscal documents. Accurate setup in this area helps present data correctly and supports compliance with local audit and tax regulations.

For example, learn more about the general ledger report in [Printing configuration for General Ledger LATAM](ltm-general-ledger.md).

## Country overviews

Use the following list to explore country and region specific guidance and understand how localization features apply in each case.
Some of the functionality referred to in this article might not yet be available for LATAM countries or regions. To learn more about planned release dates, see the detailed entries per country and region in the [Release plans for Dynamics, Power Platform, and Cloud for Industry](/dynamics365/release-plans/). Delivery timelines can change, and projected functionality might not be released. For more information, see [Microsoft policy](https://go.microsoft.com/fwlink/p/?linkid=2007332).

| Country or region | Public preview | General availability (GA) | Country or region overview |
| --------------- | ---------------- | ---- | --- |
| Cross-LATAM features | Available | Available | - |
| Chile | Available | Available | [Overview](chile.md) |
| Costa Rica | Available | Available | [Overview](costa-rica.md) |
| Nicaragua | Available | Available | [Overview](nicaragua.md) |
| Panama | Available | Available | [Overview](panama.md) |
| Colombia | Available | Available | [Overview](colombia.md) |
| Guatemala | Available | Available | [Overview](guatemala.md) |
| Paraguay | Available | Available | [Overview](paraguay.md) |
| Uruguay | Available | Available | [Overview](uruguay.md) |
| Bolivia | Not planned | Available | [Overview](bolivia.md) |
| Ecuador | Not planned | Available | [Overview](ecuador.md) |
| Dominican Republic | Not planned | Available | [Overview](ltm-dominican_republic_overview.md) |
| Peru | Not planned | Available | [Overview](ltm-peru_overview.md) |
| Venezuela | Not planned | Available | [Overview](venezuela.md) |
| Argentina | 2026 wave 2 | To be determined | - |
