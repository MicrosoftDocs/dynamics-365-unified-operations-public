---
# required metadata

title: Funds in the public sector
description: This article explains how public sector entities can use funds to demonstrate their fiscal accountability. A fund is a self-balancing set of financial books that's used to control and monitor the planned use of resources, often in compliance with legal and administrative requirements.
author: v-kiarnd
ms.date: 08/07/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerFund, LedgerFundType
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: c746c09f-dc9e-4381-ae92-e1af484064b6
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Funds in the public sector

[!include [banner](../includes/banner.md)]

A fund is a self-balancing set of financial books that is used to control and monitor the planned use of resources, often in compliance with legal and administrative requirements. Public-sector organizations use funds to demonstrate their fiscal accountability.

## What General ledger parameters should be set for funds?

To learn about the General ledger parameters required for funds, see [General ledger in the public sector](general-ledger-public-sector.md).

## What fund classes and fund types do I need to set up?
The Governmental Accounting Standards Board (GASB) recommends a set of Generally Accepted Accounting Principles (GAAP) for state and local governmental accounting. The GAAP identifies eight fund types that are categorized under the three fund classes:

-   Governmental funds
    -   General fund
    -   Special revenue funds
    -   Capital project funds
    -   Debt service funds
-   Proprietary, or business-type, funds
    -   Enterprise funds
    -   Internal service funds
-   Fiduciary funds
    -   Trust funds
    -   Agency funds

The three GAAP fund classes, plus a **Memo** class, are predefined options in Dynamics 365 Finance. 

Fund types are defined according to the needs of the organization. In most cases, you’ll set up the eight GAAP fund types. The fund types group funds for detailed fiscal tracking and reporting. Many funds can be included in a single high-level report, but each fund remains a separate fiscal and accounting entity with its own general ledger, income statements, and balance sheet reports. 

Each fund must have a unique fund number. Fund numbers are used as dimension values in financial account numbers where a dimension has been mapped to a fund. When an account number is linked to a particular fund, it belongs to the set of financial books that are contained by that fund.

### Example

Here’s a list of some of the funds that might be used by a town government:

-   General Fund
-   School of Technology
-   Information Technology
-   Farmers Market
-   Utilities Commission
-   Courier Service
-   Worker’s Compensation Fund
-   Comprehensive Major Medical Plan
-   Deferred Compensation
-   Local Sales Tax Collections
-   Clerk of Courts

The following table shows these funds grouped by fund class and fund type.

| Fund class | Fund type          | Fund number | Fund name                    |
|----------------|------------------------|-----------------|----------------------------------|
| Governmental   | General Fund           | 1103            | General Fund                     |
|                | Special Revenue Funds  | 1343            | School of Technology             |
|                |                        | 1372            | Information Technology           |
| Proprietary    | Enterprise Funds       | 2501            | Farmers Market                   |
|                |                        | 2541            | Utilities Commission             |
|                | Internal Service Funds | 2723            | Courier Service                  |
|                |                        | 2738            | Worker’s Compensation Fund       |
| Fiduciary      | Pension Trust Funds    | 3320            | Comprehensive Major Medical Plan |
|                |                        | 3324            | Deferred Compensation            |
|                | Agency Funds           | 3912            | Local Sales Tax Collections      |
|                |                        | 3914            | Clerk of Courts                  |

## How are financial dimensions used with funds?
Each fund must have a unique fund number. Fund numbers are used as dimension values in financial account numbers where a dimension has been mapped to a fund. When an account number is linked to a particular fund, it belongs to the set of financial books that are contained by that fund. 

Public sector organizations usually require balanced entries for financial dimensions related to funds. When a financial dimension or a combination of dimensions is marked to require balanced entries, the system will not post a transaction where debits do not equal credits for the financial dimension.

## How do I set a fund balance to carry over to the new year?
To learn about year-end processing for funds, see [Year-end processing in the public sector](year-end-processing-public-sector.md).


For more information, see the following topics:

[Create a fund type](tasks/create-fund-type-public-sector.md)

[Set up a fund](tasks/set-up-fund-public-sector.md)






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
