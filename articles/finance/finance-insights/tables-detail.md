---
title: Tables used by Customer payment predictions and Cash flow forecasts
description: Learn about the key data tables that are used by the Customer payment predictions and Cash flow forecasts features in Microsoft Dynamics 365 Finance.
author: wei-msft
ms.author: zhuw
ms.topic: article
ms.date: 04/02/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2019-11-06
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.8
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
---

# Tables used by Customer payment predictions and Cash flow forecasts

[!include [banner](../includes/banner.md)]

This article outlines the data tables that are used by the **Customer payment predictions** and **Cash flow forecasts** features in Microsoft Dynamics 365 Finance. These features are part of Finance insights. They help financial professionals use AI-driven models to forecast customer payments and manage future cash positions.

## Customer payment predictions tables

The **Customer payment predictions** feature uses machine learning to forecast whether customer invoices will be paid on time, late, or very late. The prediction model uses the following tables to collect historical data about transactions, payment terms, and customer behavior.

| Table name | Description |
|------------|-------------|
| `CustTable` | Contains master data for customer accounts. |
| `DirPartyTable` | Stores party-related data, such as names and organization details. |
| `LogisticsLocation` | Provides details about customer address locations. |
| `LogisticsPostalAddress` | Captures postal addresses for logistics purposes. |
| `LogisticsAddressCountryRegion` | Contains country and region information that is linked to addresses. |
| `CustSettlement` | Stores records of settled invoices and payments. |
| `EnumIdTable` | Stores metadata about enumerations in the system. |
| `EnumValueTable` | Holds the values for each enumeration. |
| `TableIdTable` | Maps table IDs to their corresponding table names. |
| `CustTrans` | Contains transactional data that is related to customer invoices and payments. |
| `CashDisc` | Holds information about cash discount terms. |
| `CustDisputeHistory` | Captures records of historical disputes between the customer and the organization. |
| `Ledger` | Stores general ledger entries that are used for financial reconciliation. |
| `PayPredParameters` | Stores configuration settings for the payment prediction model. |
| `CustTransOpen` | Represents open customer transactions that aren't settled. |
| `PayPredProjectedInvoice` | Contains projected payment predictions at the invoice level. |

These tables collectively provide the data that is required to train and run the model, and therefore improve its accuracy over time.

## Cash flow forecasts tables

The **Cash flow forecasts** feature estimates future liquidity by modeling expected inflows and outflows, based on historical and projected financial data. The system uses the following tables.

| Table name | Description |
|------------|-------------|
| `CashFlowForecastLedgerDimensionReference` | Links forecast lines with financial dimensions. |
| `DirPartyTable` | Provides party-related data for entity and vendor identification. |
| `EnumIdTable` | Stores metadata definitions for enumerations. |
| `EnumValueTable` | Stores the values that are used in enumerations. |
| `FiscalCalendarPeriod` | Defines the financial calendar periods that are used in forecasting. |
| `GeneralJournalAccountEntry` | Stores account-specific ledger postings. |
| `GeneralJournalEntry` | Stores header-level journal entry records. |
| `Ledger` | Holds the financial ledger that is used for liquidity calculations. |
| `LedgerLiquidity` | Stores liquidity forecast data. |
| `TableIdTable` | Helps resolve table ID references in model processing. |

Forecasting jobs use these tables to project expected cash availability and help finance teams plan more effectively.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
