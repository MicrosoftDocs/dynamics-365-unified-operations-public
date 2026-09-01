---
title: Cross-LATAM localization overview
description: Access an overview of functionality specific to Latin American, including an outline on country or region localization availability.
author: MatiasPizmeny01
ms.author: v-mpizmeny
ms.topic: overview
ms.date: 09/01/2026
ms.custom: bap-template
ms.reviewer: johnmichalak  
--- 

# Cross-LATAM localization overview

[!INCLUDE [banner](../../includes/banner.md)]
[!INCLUDE [does not apply to](includes/does-not-apply-to.md)]

Microsoft Dynamics 365 Finance includes cross-LATAM, that provides a common localization framework for supported countries or regions in Latin America. This framework standardizes core legal, tax, treasury, and fiscal processes across the region while supporting country or region-specific regulatory requirements through configuration. By using a shared localization foundation, organizations can maintain consistent business processes, simplify implementation, and support compliance requirements across multiple LATAM countries or regions.

> [!NOTE]
> Out-of-box localization of Dynamics 365 Commerce for LATAM countries or regions is limited to Brazil and Mexico and doesn't include other LATAM countries or regions.

## Country or region overviews

Localization capabilities are available for multiple Latin American countries or regions. Select a country or region overview to learn about the supported features, regulatory requirements, and localization-specific functionality available in Dynamics 365 Finance.

| Country or region | Country or region overview |
| --------------- | --- |
| Chile | [Overview](chile.md) |
| Costa Rica | [Overview](costa-rica.md) |
| Nicaragua | [Overview](nicaragua.md) |
| Panama | [Overview](panama.md) |
| Colombia | [Overview](colombia.md) |
| Guatemala | [Overview](guatemala.md) |
| Paraguay | [Overview](paraguay.md) |
| Uruguay | [Overview](uruguay.md) |
| Bolivia | [Overview](bolivia.md) |
| Ecuador | [Overview](ecuador.md) |
| Dominican Republic | [Overview](ltm-dominican_republic_overview.md) |
| Peru | [Overview](ltm-peru_overview.md) |
| Venezuela | [Overview](venezuela.md) |

For Argentina, visit [Release plans for Dynamics, Power Platform, and Cloud for Industry](/dynamics365/release-plans/).  Delivery timelines can change, and projected functionality might not be released. For more information, see [Microsoft policy](https://go.microsoft.com/fwlink/p/?linkid=2007332).

## Cross-LATAM features

Cross-LATAM in Finance provides a unified framework that helps you configure the legal, tax, and treasury characteristics required by each LATAM country or region. Use these functionalities to set up country or region specific fiscal documents, such as invoices, credit notes, and payment orders, while maintaining a consistent structure across all forms. Although the forms are identical for all countries or regions, the configuration parameters vary depending on local requirements.

The transactional use of localization features is also standardized across LATAM. The same LATAM extension is applied in all countries or regions, with differences arising only in the fields populated based on each country’s or region's configuration. When it comes to reporting, each country or region has its own specific reports. However, all reports are built using Electronic Reporting, ensuring consistent methodology and operational logic across the region.

## Prerequisites for cross-LATAM configuration

Before you begin, ensure you're familiar with the legal, accounting, and tax requirements applicable in the target country or region. LATAM localization articles focus on how to configure and use the product features. They don't cover the underlying regulatory context or the specific reasons behind country or region reporting requirements.

Before starting the configuration, ensure the following conditions are true:

- Users involved in the setup have the required privileges to access the forms involved.
- The LATAM globalization expansion extension in the Feature Management workspace is enabled, along with the country or region specific feature of your target location.

## Key configuration areas

Located under the Supported countries or regions > Latin America folder, documentation articles provide a centralized entry point to LATAM localization content. The sections below summarize the main functional areas supported by the LATAM localization framework.

### Latin America get started

These articles guide you through enabling parameters and getting started with configuring and using the LATAM localization.

Learn more in [Latin America parameters](ltm-core-latam-parameters.md) and [Set up transaction posting for Latin America](ltm-post-transactions.md).

### Tax and legal attributes

These articles focus on configuring the legal and tax-related data required for compliance in LATAM countries or regions. They cover taxpayer classifications, tax ID formats, address structures, and how to configure customers and vendors based on regulatory needs.

Learn more in [Tax and legal attributes for Latin America](ltm-tax-legal-attributes.md).

### Document classification setup

This section provides guidance to help you configure various types of business, internal, and treasury documents required across LATAM countries or regions, such as invoices, delivery notes, payment orders, and others. The articles support the setup of document classes and class types to ensure proper categorization and processing. Other configuration options allow defining document attributes, establishing relationships between classification elements, and aligning with country or region specific legal and reporting requirements.

Learn more in [Document classes for Latin America](ltm-core-document-class.md).

### LATAM extension in transactions

Here, you learn how LATAM-specific settings shape various types of transactions, including sales, purchases, inventory transfers, and payments. These articles provide guidance on using localization during transaction posting and on referencing electronic documents.

For example, learn more about sales transactions in [Sales invoice posting for Latin America](ltm-core-sales-invoice-posting-latam.md).

> [!NOTE]
> LATAM localization uses Electronic Reporting (ER) to generate fiscal, tax, and electronic invoicing reports. The correct output of these reports depends on the proper configuration of the cross-LATAM and the consistent application of the LATAM extension in transactions. Incorrect configurations might result in incomplete or unexpected report behavior.

### LATAM withholding taxes

This section provides an overview of how to configure and apply withholding taxes in LATAM. It includes step-by-step instructions to configure sales tax codes and withholdings, post invoices and payments with withholdings, and ensure accurate tax reporting. These configurations are important to meet fiscal obligations in countries or regions where withholding is mandatory.

Learn more in [LATAM withholding taxes overview](ltm-latam-withholding-taxes-overview.md).

### Inquiries and reports

These articles guide users through the setup and use of Electronic Reporting (ER) for LATAM scenarios. This section provides the necessary configuration steps to generate tax and accounting reports, set up and use electronic invoicing, and ensure proper formatting and printing of fiscal documents. Accurate setup in this area helps present data correctly and supports compliance with local audit and tax regulations.

For example, learn more about the general ledger report in [Printing configuration for General Ledger LATAM](ltm-general-ledger.md).
