---
title: What's new or changed in Finance and Operations version 10.0 (April 2019)
description: This article describes features that are in preview in Microsoft Dynamics 365 Finance and Operations version 10.0. This version will be released in April 2019.
author: sericks007
ms.date: 10/15/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2019-04-01
ms.dyn365.ops.version: Release 10
ms.custom: 
ms.assetid: a362a31d-44df-45c5-b698-64c5264c592e
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Finance and Operations version 10.0 (April 2019)

[!include [banner](../includes/banner.md)]

This article describes features that are new or changed in Microsoft Dynamics 365 Finance and Operations version 10.0. This version has a build number of 10.0.8. For more information about version 10.0, see [Additional resources](whats-new-changed-10.md#additional-resources).

To learn about the features in Retail, see [What's new or changed in Dynamics 365 for Retail (April 2019)](../../../commerce/get-started/april-whats-new.md).

## Extensibility enhancements

In this release of Finance and Operations, numerous extensibility enhancements have been made to support extensibility including enhancements to enumerations, metadata, and methods. For detailed information, see [Extensibility changes in Dynamics 365 Finance and Operations version 10.0](../../dev-itpro/extensibility/extensibility-changes-10.md).

## Catch weight product processing with warehouse management
This feature allows you to use catch weight products within warehouse management processes. This feature is only available to a limited audience for this release. 

For more information, see [Catch weight product processing with warehouse management](../../../supply-chain/warehousing/catch-weight-processing.md).

## Master planning stability and recovery improvements

Master planning will be made more resilient to failures and connectivity issues through multiple, incremental improvements. This will enhance the ability for master planning to recover from exceptions without being stopped.

If master planning is stopped, it has been necessary to restart the master planning run. This process has been improved so that master planning will now restart automatically from where it was stopped. This will be a significant improvement for customers where master planning is a time-critical process.

##  Improved removal of obsolete planning data

After a successful master planning run, a clean-up job is scheduled to remove planning data that is no longer needed. In some cases, such as a failed master planning run, the data would not be cleaned up thereby incurring risk of aggregating unnecessary data.

The clean-up job has now been enhanced to remove data from previously failed master planning runs, and the design has been optimized to never block other threads, leaving all helpers available for the master planning run. These improvements also apply to intercompany master planning.

## Realize the conditional tax when postdated checks are drawn

Conditional tax is cash basis value-added tax (VAT) that is required in some countries/regions. This tax can be deducted until you have paid the invoice. If the payment method is posted checks, you now have the option to realize the tax during payment or when the posted checks are drawn. To enable this option, go to **Cash and bank management parameters > Postdated checks > Realize the conditional tax when postdated checks are drawn**. For more information, see [Conditional tax](../../../finance/general-ledger/indirect-taxes-overview.md#conditional-sales-tax). 

## Non-GST transactions for India 
This feature allows you to create non-GST transactions with the Tax engine. To create a non-GST transaction, select the **Non-GST** check box in the **Tax information** of each taxable transaction line. You also need to make sure that there is a **Number sequence code** for **Bill of supply** in the **Reference number sequence group**. These transactions will be identified as non-GST transactions in the GST return (GSTR). 

## Tax engine

> [!NOTE]
> The tax engine (GTE) is currently only available for India.

This release includes the following features for the Tax engine.

### Improving tax configuration usability with reduced number of lookups

While configuring tax using the Tax engine (GTE), you can define multiple tables to look up tax rates, non-deductible percentages, tax components, tax periods, and more. This feature reduces the number of lookup tables by combining them. For example, data model properties such as **Country/Region of Origin**, **Consumption of Country/Region**, and **Product type** determine the nature of the tax transaction, which can be reused in many places. In this release, you can add a string-type measure at the line level, which can be a lookup. This measure can be further used in other lookups, such as reporting and rate.

This feature will dramatically reduce the number of lookups that you need to maintain and will improve the tax configuration usability. This line-level string-type measure will also be shown in the tax document user interface.

### Simplifying tax setup maintenance with Excel integration

Maintaining tax setup parameters (such as tax rates and non-deductible percentages) for tax configurations can be an effort-intensive task for users in some countries/regions and for some types of businesses. Now you can maintain these parameters in Microsoft Excel files that are automatically generated based on tax lookup tables and are integrated with the tax setup.

### Enabling tax configuration with tax currency and sales tax codes

Sales tax code is a mandatory setup for GTE to integrate with Finance and Operations. Previously, GTE created the sales tax code with the same name as the tax component when synchronizing the tax configuration, and it used the accounting currency for the auto-create sales tax codes.

Companies with multiple tax registration across the world need to maintain different tax currencies for tax components used in different countries/regions. With the release of this feature, users can do the following.

- Maintain the sales tax code in tax setup.
- Map the tax component to the sales tax code in lookup tables.
- Maintain tax currency and settlement period of these sales tax codes.

With the tax setup, GTE will use the mapped sales tax code, tax currency, and settlement period for posting the tax transactions.

## Expanded regional coverage for Regulatory Configuration Service (RCS) deployments
As part of the ongoing enhancements to RCS, we are increasing the breadth of regional coverage where service environments can be deployed through end-user selection. As part of this release, users can host their RCS environments in the following countries or regions:

- United States 
- India 
- Europe (Preview)
- China (Preview)

## Tax functionality updates for China

In China, official tax invoices can only be issued via two government-authorized invoicing software (Aisino and BaiWang). This feature lets you export the issued invoices into the .TXT and .XML file formats so you can import the files into the authorized invoicing software of Aisino and BaiWang providers accordingly. 

You can also maintain the tax classification and codes in Finance and Operations, which is in alignment with tax integration interface 3.0. The exported invoice file will include commodity codes (classification of goods and services) which is mandatory for China. 

The standard category hierarchy setting functionality is used to include the commodity codes in the invoice lines of the exported file.

The following updates are included in this release:

- There is a new interface with BaiWang provider software that lets you export issued invoices in .XML format and you can import files from BaiWang software in .TXT and .XML formats.
- We updated the structure of the issued invoice that is exported and you can import .TXT file for interface with Aisino provider software.

For more information, see [Configure tax integration for China](../../../finance/localizations/apac-chn-tax-integration.md).

## Electronic reporting (ER)

This release includes the following features for Electronic reporting (ER).

### Performance optimization of customer-built configurations
A functional consultant persona can enable tracing of execution of electronic reporting configuration. This consultant can also analyze a generated trace and optimize electronic reporting configuration performance by setting caching on frequently used nodes.

Before this release, caching supported only a flat list of records, which meant that any related records were not cached. This feature allows caching of nested records. It also allows users to enable “lazy” caching, when only referenced records are being cached, not the whole list.

### Setting up parameters by legal entity

This feature allows you to configure an ER format that includes an abstract data source and lets you specify how this data source can be filled in by a business user. The business user can then use the Finance and Operations user interface to set up an ER format with master data from a specific legal entity. This can be done for any legal entity that might control execution of the corresponding ER format.

This feature also enables a business user to export an ER format with master data for a specific company from one Finance and Operations instance and import it to another one.

### Specify a custom storage location for generated documents

A new ER extensibility point is introduced allowing you to write a custom code in which you can subscribe to an event giving you access to any of the documents that ER formats generate. This feature lets you extend the list of storage locations that are supported by ER framework to keep generated documents.

For more information, see [Specify a custom storage location for generated documents](../../dev-itpro/analytics/er-custom-storage-generated-documents.md).

### Post-processing of imported files

Import functionality in Electronic reporting (ER) uses SharePoint folders to get the next set of files for processing. In previous releasess there was no automatic process to manage processed files. For example, successfully processed files were automatically deleted from a SharePoint source folder and couldn't be moved to another location. This resulted in additional manual work and potential errors. With this feature, there is a process to automatically manage processed files, which allows you to configure the post-processing actions. By changing the source settings of an ER format, you can configure the following actions:

For successfully processed files:
- Delete files from the source SharePoint folder.
- Move files to another SharePoint folder.
For files that are processed with warnings:
- Keep files in the source SharePoint folder.
- Move files to another SharePoint folder.
For files that failed to process:
- Keep files in the source SharePoint folder.
- Move files to another SharePoint folder.

### Generate documents in PDF format by filling in PDF templates

This feature allows you to use a fillable PDF document as a template for generating reports in the PDF format. You can import the PDF at design time to a configured ER format which automatically generates new elements of this ER format for discovered fields that need to be filled in. By adding bindings to generated elements of an ER format, you can fill in necessary fields of the PDF template by running this ER format. With this feature, you can also configure an ER format generating multiple PDF documents and automatically merge them into a single, final PDF document.

## Russian features

### Cash flow management 

This functionality allows you to do the following:
- Obtain a cash flow forecast and perform an analysis.
- Manage payments on a daily basis using payment schedule journals.
- Control the company’s cash position.
- Maintain the company’s cash flows with centralized control.

For more information, see [Cash flow management (Russia)](../../../finance/localizations/rus-cash-flow.md).

### Other incomes and expenses profit tax registers

The following tax registers are available:

- Current period incomes
- Tax expenses
- Other expenses of current period
- Unrealized expenses of current period
- Other unrealized expenses

### Localization of process industries

Basic localization in the following two areas is available:
- Correspondence of accounts for all new general ledger postings.
- Functional coexistence of process industries features and Russian country/region context.

## Additional resources

### Bug fixes
For information about the bug fixes included in each of the updates that are part of Finance and Operations version 10.0, sign in to Lifecycle Services (LCS) and view the [KB article](https://go.microsoft.com/fwlink/?linkid=2080156). 

## Regulatory updates
For information about the regulatory updates for Finance and Operations, see [Localization and Regulatory features – Regulatory updates](../../../finance/localizations/regulatory-updates.md). Alternatively, you can sign in to Lifecycle Services (LCS) and view the planned regulatory updates using the issue search tool, where you can search by country/region, type of feature, and release.

### Platform update 24
Microsoft Dynamics 365 Finance and Operations version 10.0 includes Platform update 24. To learn more about Platform update 24, see [What's new or changed in Finance and Operations platform update 24 (March 2019)](whats-new-platform-update-24.md).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features for finance and operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article describes features that have been removed or deprecated for Dynamics 365 Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features for finance and operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically these are functional updates that need to made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

