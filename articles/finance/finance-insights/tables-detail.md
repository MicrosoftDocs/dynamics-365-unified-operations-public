---
title: Tables used by Payment Prediction and Cashflow Forecast
description: Learn about the key data tables leveraged by the Payment Prediction and Cashflow Forecast features in Dynamics 365 Finance.
author: wei-msft
ms.author: zhuw
ms.topic: article
ms.date: 03/28/2025
ms.reviewer: shpandey
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2019-11-06
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.8
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
---

# Tables used by Payment Prediction and Cashflow Forecast

[!include [banner](../includes/banner.md)]

This article outlines the data tables used by the **Payment Prediction** and **Cashflow Forecast** features in Dynamics 365 Finance. These features are part of Finance Insights and help financial professionals forecast customer payments and manage future cash positions using AI-driven models.

## Payment Prediction Tables

Payment Prediction uses machine learning to forecast whether customer invoices will be paid on time, late, or very late. The prediction model uses a variety of tables to collect historical data on transactions, payment terms, and customer behavior.

| Table name | Description |
|------------|-------------|
| `CustTable` | Contains master data for customer accounts. |
| `DirPartyTable` | Stores party-related data such as names and organization details. |
| `LogisticsLocation` | Provides details about customer address locations. |
| `LogisticsPostalAddress` | Captures postal addresses for logistics purposes. |
| `LogisticsAddressCountryRegion` | Contains country and region information linked to addresses. |
| `CustSettlement` | Stores records of settled invoices and payments. |
| `EnumIdTable` | Stores metadata about enumerations in the system. |
| `EnumValueTable` | Holds the actual values for each enumeration. |
| `TableIdTable` | Maps table IDs to their corresponding table names. |
| `CustTrans` | Transactional data related to customer invoices and payments. |
| `CashDisc` | Holds information about cash discount terms. |
| `CustDisputeHistory` | Captures records of historical disputes between the customer and the organization. |
| `Ledger` | General ledger entries used for financial reconciliation. |
| `PayPredParameters` | Stores configuration settings for the payment prediction model. |
| `CustTransOpen` | Represents open customer transactions not yet settled. |
| `PayPredProjectedInvoice` | Contains projected payment predictions at the invoice level. |

These tables collectively provide the data required to train and run the model, improving its accuracy over time.

## Cashflow Forecast Tables

The Cashflow Forecast feature estimates future liquidity by modeling expected inflows and outflows based on historical and projected financial data. The system leverages the following tables:

| Table name | Description |
|------------|-------------|
| `CashFlowForecastLedgerDimensionReference` | Links forecast lines with financial dimensions. |
| `DirPartyTable` | Provides party-related data for entity and vendor identification. |
| `EnumIdTable` | Stores metadata definitions for enumerations. |
| `EnumValueTable` | Stores the values used within enumerations. |
| `FiscalCalendarPeriod` | Defines the financial calendar periods used in forecasting. |
| `GeneralJournalAccountEntry` | Stores account-specific ledger postings. |
| `GeneralJournalEntry` | Header-level journal entry records. |
| `Ledger` | Financial ledger used for liquidity calculations. |
| `LedgerLiquidity` | Stores liquidity forecast data. |
| `TableIdTable` | Helps resolve table ID references in model processing. |

These tables are used by forecasting jobs to project expected cash availability and to help finance teams plan more effectively.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
