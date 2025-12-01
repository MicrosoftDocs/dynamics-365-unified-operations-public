---
title: What's new or changed in Business performance analytics
description: Learn about features that are either new or changed in business performance analytics.
author: Weijiesa 
ms.author: jiwo
ms.topic: article
ms.date: 10/24/2025
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# What's new or changed in Business performance analytics

[!include [banner](../includes/banner.md)]

This article provides information about what's new or changed in Business performance analytics.  

## October 2025

The October release of Business performance analytics version 2.5 and contains the following features.

## Feature enhancements

| Category | Feature | Description |
|----------|---------|-------------|
| Transform changes | Optimize O2C Value Chain - SalesPaymentFact | Improve data transformation performance for SalesPaymentFact. |
| Transform changes | Optimize O2C Value Chain - BankStatementFact | Improved performance for O2C transformations. |
| Transform changes | Optimize O2C Value Chain - ReturnAuthorizationFact | Improved performance for O2C transformations. |
| Transform changes | Enable CDS3 implementation for Business performance analytics | This accelerates the data sync process. |
| Transform changes | SalesPaymentMatchedNumberKey and SalesPaymentMatchingNumberKey use identical value in the transform | The correct customer transaction is related to its corresponding SalesPaymentMatchingFact record. |
| Transform changes | 502 status MEF job led to multiple records and broke flow logic | This prevents the V2 flow from not working in an edge case. |
| Data model additions and changes | Optimize purchase payment fact joins | Optimize purchase payment fact. |
| Reports changes | Deleted or canceled purchase order lines still appearing in reports | Customers can see if the purchase order line has been deleted or not and can adjust the filter to show or hide them. |
| Reports changes | Force full refresh when duplicate is detected on PowerBI refresh | Improve PowerBI refresh reliability by adding dataset clear and refresh when duplicates are detected. |
| Other changes | When turning on row level secruity, the field is off by default on the filter and isn't being returned | When the row level security is turned on, the upgrade fails due to a null reference error. |
| Other changes | Determine if first time setup should be restricted to administrators or remove the restriction | System administrators can now manage users in Business performance analytics without being Business performance analytics administrator. |
| Other changes | Uninstalling Business performance analytics doesn't cleanup temp/FA Tables data | When uninstalling Business performance analytics, there's an option to remove data. |

## August 2025

The August release of Business performance analytics version 2.4 and contains the following features.

## Feature enhancements

| Category                    | Title                                                        | Description                                                                                                        |
|-----------------------------|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
| Data model additions and changes | Add SalesInvoiceTaxAmount Lines in Sales invoice fact    | Added SalesInvoiceTaxAmount and SalesInvoiceAllocatedTaxAmount to the SalesInvoiceFact.               |
| Data model additions and changes | Generate PurchaseInvoiceFact purchaseinvoicesource key from VendInvoiceJour and VendInvoiceTrans | PurchaseInvoiceFact bug fix.                     |
| Data model additions and changes | Remove duplicate primary key in Purchase invoice fact | Address issue where charges that don't have the same currency as the invoice line can lead to duplicate data.        |
| Data model additions and changes | Change GeneralLedgerFact partition to use created on instead of accounting date | Adjust PBI partition key, which was allowing to duplicates in General ledger fact.   |
| Data model additions and changes | Fix deleted or canceled Purchase order lines appear in reports| Customers can adjust the report filter to see if the purchase order line has been deleted or not. |
| Transform changes | Order to cash -  SalesInvoiceFact                          |  Transform performance improvements.                                                                   |
| Transform changes | Order to cash -  SalesSubledgerFact                        | Transform performance improvements.                                                                   |
| Transform changes | Order to cash - BankRegisterFact                           | Transform performance improvements.                                                                   |
| Transform changes | Order to cash - PackingSlipFact                            |  Transform performance improvements.                                                                  |
| Transform changes | Order to cash - PickingListFact                            |  Transform performance improvements.                                                                |
| Transform changes | Order to cash - SalesOrderFact                             |  Transform performance improvements.                                                                   |
| Transform changes | Order to cash - ServiceOrderFact                           |  Transform performance improvements.                                                                |
| Transform changes | Incremental uptake for ReturnAuthorizationFactTransform | Enable incremental sync for returnauthorizationfacttransform. |
| Transform changes | Implement the gatekeeper flow - check and trigger a new transform | This impacts frequency of data refreshes. |
| Other changes               | Excel add-in user permission enhancement | Added permission for nonadmin users of Business performance analytics Excel add-in.                                                  |
| Other changes               | Enable cleanup temp Business performance analytics data         | When uninstalling Business performance analytics, there's an option to remove data.               |
| Other changes| Fix issue where report metadata might update during a solution upgrade | Add override customizations call to the package template file to ensure that reports are updated during import. |
| Other changes      | Copy and adapt the existing Business performance analytics flow  | Customers can have more frequent data refreshes.                                                 |
| Other changes       | Remove unused columns from the input entities      | Improve reliability to handle issues where there are schema mismatches between the Dataverse and Finance apps.    |

## June 2025

The June release of Business performance analytics version 2.3 and contains the following features.

### Feature enhancements

| Category | Feature | Description |
| --- |--- |--- |
|Data model additions and changes | Detect data changes in the PBI dataset | Enhanced Power BI dataset refresh performance by detecting data changes using commit_timestamp in the facts. |
|Data model additions and changes| Add SalesInvoiceTaxAmount Lines in Sales invoice fact |Included SalesInvoiceTaxAmount and SalesInvoiceAllocatedTaxAmount in SalesInvoiceFact for completeness. |
|Data model additions and changes| Wrong field used for calendar filter regarding to SalesOrderFact| Corrected calendar filtering logic in SalesOrderFact to improve data accuracy. |
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
|Report changes| Fact - General ledger - Company group format issue| Corrected data type of Company group in Fact - General Ledger from currency to whole number. |
|Report changes| Promote Category filter for profit loss report| Promoted account type filter to page/report level in profit and loss report for customization. |
| Platform optimization  | Automated cleanup of Dataverse temp files | Implemented automated cleanup of temporary files left by Athena ingestion. Only analytical outputs from transforms are retained, reducing Dataverse storage usage and improving refresh performance. |

