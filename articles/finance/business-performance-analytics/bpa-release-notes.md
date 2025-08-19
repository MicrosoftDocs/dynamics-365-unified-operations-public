---
title: What's new or changed in Business performance analytics
description: Learn about features that are either new or changed in business performance analytics.
author: jinniew
ms.author: jiwo
ms.topic: article
ms.date: 08/11/2025
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# What's new or changed in Business performance analytics

[!include [banner](../includes/banner.md)]

This article provides information about what's new or changed in Business performance analytics.  

## June 2025

The June release of Business performance analytics version 2.3.30982 and contains the following features.

### Feature enhancements

| Category | Feature | Description |
| --- |--- |--- |
|Data model additions and changes | Detect data changes in the PBI dataset | Enhanced Power BI dataset refresh performance by detecting data changes using commit_timestamp in the facts. |
|Data model additions and changes| Add SalesInvoiceTaxAmount Lines in Sales invoice fact |Included SalesInvoiceTaxAmount and SalesInvoiceAllocatedTaxAmount in SalesInvoiceFact for completeness. |
|Data model additions and changes| Wrong field used for calendar filter with regard to SalesOrderFact| Corrected calendar filtering logic in SalesOrderFact to improve data accuracy. |
|Data model additions and changes| Add SellingPartyGroup in the Selling party dimension| Added BuyingPartyGroup to the BuyingPartyDimension to enhance dimensional analysis. |
|Data model additions and changes| Change BudgetFact partitionId field| Updated BudgetFact to include future dated budget data in incremental refresh. |
|Data model additions and changes| Update Existing O2C Fact - Sales payment matching|Enhanced O2C fact with updated Sales payment matching logic. |
|Data model additions and changes| Add LedgerKey into PickingList fact |Added LedgerKey to PickingList fact to support financial traceability.| 
|Other changes| Purchase invoice charge and tax isn't pulling in numbers - P2P| Resolved issue with missing charge and tax values in purchase invoice for P2P scenarios. |
|Other changes| Business performance analytics error messages should be enhanced| Improved Business performance analytics self help logs with Microsoft documentation links for better troubleshooting. |
|Other changes| Balance sheet page filters not set correctly |Corrected filters on Dim - General ledger account. Type to display all values properly. |
|Other changes| Provide easy way to download Power BI dataset |Enabled Fabric SQL connection for easier Power BI dataset downloads. |
|Dimension security changes | Dimension security enhancement to enables security by default| Dimension security is now secure by default. Previously, if fact tables weren't related to a secured dimension, their rows defaulted to visible. The default behavior is updated to hide rows from unrelated Fact tables instead. Users can now select up to eight dimensions.| 
|Other changes| Update UI for new RLS implementation| Refreshed user interface to align with updated role-based security implementation. |
|Report changes| Rename Dim-Ledger attributes| Updated labels for **Accounting currency** and **Reporting currency** fields in 'Dim - Ledger'. |
|Report changes| Key fields not exposed in Power BI dataset| Exposed key fields in Fact tables to support extension scenarios. |
|Report changes| Incorrect format for Journal line number in Budget Fact| Changed Journal line number format from currency to whole number. |
|Report changes| Inconsistent or missing metrics folders |Added missing metrics folders to key Facts in Power BI semantic layer. |
|Report changes| Replace deprecated measures in Business performance analytics reports| Replaced deprecated measures with updated metrics in Microsoft Business performance analytics reports.| 
|Report changes| Balance sheet report missing editable filter| Enabled editable filter for account type in Balance sheet to support custom category names. |
|Report changes| Fact - General Ledger.Company Group format issue| Corrected data type of Company group in Fact - General Ledger from currency to whole number. |
|Report changes| Promote Category filter for profit loss report| Promoted account type filter to page/report level in profit and loss report for customization. |
| Platform optimization  | Automated cleanup of Dataverse temp files | Implemented automated cleanup of temporary files left by Athena ingestion. Only analytical outputs from transforms are retained, reducing Dataverse storage usage and improving refresh performance. |

