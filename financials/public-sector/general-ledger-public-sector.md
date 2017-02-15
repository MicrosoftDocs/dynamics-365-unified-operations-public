---
# required metadata

title: General ledger in the public sector
description: This topic describes the General ledger functionality that is available for the public sector.
author: rschloma
manager: AnnBe
ms.date: 2015-12-13 05 - 19 - 30
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AdvancedLedgerEntry, JournalizingDefinition, LedgerDerivedFinHierarchies, LedgerFundType, LedgerParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 27211
ms.assetid: 9a5b980a-976c-45a1-b063-b0a41b11a62c
ms.search.region: Global
ms.search.industry: Public sector
ms.author: brpotter
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# General ledger in the public sector

This topic describes the General ledger functionality that is available for the public sector.

How do General ledger parameters need to be set for public sector organizations?
--------------------------------------------------------------------------------

Most General ledger parameters are set the same way for public sector and private sector organizations. In addition, there are public sector parameters that are used for the year-end process for funds. Set these parameters on the **General ledger parameters** page, in the **Ledger** section, on the **Fiscal year close** FastTab:

-   Select **Create closing transactions during transfer** to generate the closing and opening balance entries. When this is selected, on subsequent runs of this process, the system deletes transactions from previous runs and generates new closing and opening entries. If this is not selected, the system will calculate the net change and generate only that transaction for closing entries and opening balances. **Note**: This option requires the use of posting definitions. To learn more, see [Posting definitions in the public sector](posting-definitions-public-sector.md).
-   Select **Use Fund dimension for year-end transactions** to enable the public sector version of the **Opening transactions** page.
-   Select **Use Fund dimension to carry forward purchase orders** to enable the ability to set year-end processing options for specific funds.

To learn more about the year-end process for funds, see [Year-end processing in the public sector](year-end-processing-public-sector.md).

## What fund classes and fund types are available?
Governmental, proprietary, and fiduciary fund classes are available for public sector organizations, along with a Memo class. You’ll create the fund types your organization needs. To learn more, see [Funds in the public sector](funds-public-sector.md).

## How are financial dimensions used with funds?
Fund numbers are used as dimension values in financial account numbers where a dimension has been mapped to a fund. Public sector organizations usually require balanced entries for financial dimensions related to funds.

## What is the easiest way to adjust or reverse ledger entries?
You can use advanced ledger entries to create, adjust, and reverse ledger entries. For example, advanced ledger entries can be used to reclassify expenditures if invoices are mistakenly posted to the wrong account or project. To learn more, see [Advanced ledger entries in the public sector](advanced-ledger-entries-public-sector.md) and [Posting definitions in the public sector](posting-definitions-public-sector.md).

## Why should I use posting definitions?
You can use posting definitions to create subledger journal lines for originating transactions that meet selected criteria - for example, to generate multiple balanced ledger entries based on attributes such as transaction types and accounts. Posting definitions provide granular control over the general ledger updates created by source documents in contrast to the broadly applied updates of posting profiles. General ledger posting definitions are required if you use advanced ledger entries. Posting definitions are used in the year-end processing of general ledger accounts. Posting definitions can be used to close the accounts to fund balances or retained earnings, based on the fund class and the account close type. Posting definitions are required to close the general ledger accounts and to transfer balances to the opening period in the new fiscal year. To learn more, see [Posting definitions in the public sector](posting-definitions-public-sector.md).

## How do I collect and analyze data to meet the Common Governmentwide Accounting Classification (CGAC) requirements?
You can use derived financial hierarchies to collect and analyze posted transaction data for specific main account numbers, full account numbers, and financial dimension values. To learn more, see [Derived financial hierarchies in the public sector](derived-financial-hierarchies-public-sector.md).

See also
--------

[General ledger](general-ledger.md)

