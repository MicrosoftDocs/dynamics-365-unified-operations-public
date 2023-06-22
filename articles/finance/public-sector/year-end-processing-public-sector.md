---
# required metadata

title: Year-end processing in the public sector
description: This article provides information about year-end processing for public sector organizations.
author: v-kiarnd
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PurchYearEndClose
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: ba9a7abc-bd18-47c2-b745-96cdcec8ac98
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Year-end processing in the public sector

[!include [banner](../includes/banner.md)]

This article provides information about year-end processing for public sector organizations.

This article describes the year-end functionality available for the public sector. At the end of a fiscal year, you must generate closing transactions and prepare your accounts for the next fiscal year.  Public sector clients have the following capabilities:

-   Select accounts by fund for year-end closing.
-   Close funds to different accounts. For example, you can close nominal accounts that are associated with governmental funds to fund balances. You can also close nominal accounts that are associated with proprietary funds to retained earnings.
-   Set up year-end closing for all funds and non-funds. Non-funds don't have a fund dimension in the account structure.
-   Set up multiple closing periods to segregate different types of closing entries, such as general year-end closing and audit adjustments.

## Can the year-end process be run more than one time on the same data?
Yes, the year-end process can be run multiple times for the same set of data. Typically, if additional transactions must be processed after a general ledger year-end process is run, the year-end process can be run again to close out the nominal accounts and correctly set the opening balances in the new year.

## How do I set up funds for year-end processing?
Year-end processing of general ledger balances is controlled by fund configuration settings in two places:

-   The year-end process of closing ledger balances in the old year and establishing opening balances in the new year is done by using the **Opening transactions** page. A single fund or range of funds is required for processing.
-   The year-end processing option for purchase order encumbrances is set on the **Purchase order year-end process** page. You can override the option on a specific fund, provided that the general ledger parameters have been set to allow for overrides. To learn more about the parameter settings, see [General ledger in the public sector overview](general-ledger-public-sector.md).

## How do I set up main accounts for year-end processing?
You must select a close type for every account in your chart of accounts. The close type determines how the year-end process handles that main account. There are four close types:

-   **Real** – The balance is used to establish opening balances in the new year.
-   **Nominal** – The account is closed by the year-end process.
-   **Nominal – no close** – The account is managed by other closing processes, such as encumbrance accounts for purchase order close.
-   **Not applicable** – The account isn't included in year-end processing.

Posting definitions govern the accounting that occurs on the closing entries, and they also help create the opening transactions for the new year. To learn more, see [Posting definitions in the public sector](posting-definitions-public-sector.md).





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
