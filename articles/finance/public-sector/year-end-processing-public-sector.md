---
title: Year-end processing in the public sector
description: Learn about year-end processing for public sector organizations, including answers to various frequently asked questions.
author: v-kiarnd
ms.author: twheeloc
ms.topic: article
ms.date: 06/22/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.industry: Public sector
ms.search.validFrom: 2016-02-28
ms.search.form: PurchYearEndClose
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: ba9a7abc-bd18-47c2-b745-96cdcec8ac98
---

# Year-end processing in the public sector

[!include [banner](../includes/banner.md)]

This article provides information about year-end processing for public sector organizations.

This article describes the year-end functionality available for the public sector. At the end of a fiscal year, you must generate closing transactions and prepare your accounts for the next fiscal year. Public sector clients have the following capabilities:

- Select accounts by fund for year-end closing.
- Close funds to different accounts. For example, you can close nominal accounts that are associated with governmental funds to fund balances. You can also close nominal accounts that are associated with proprietary funds to retained earnings.
- Set up year-end closing for all funds and non-funds. Non-funds don't have a fund dimension in the account structure.
- Set up multiple closing periods to segregate different types of closing entries, such as general year-end closing and audit adjustments.

## Can I run the year-end process more than once on the same data?

Yes, you can run the year-end process multiple times for the same set of data. Typically, if you need to process additional transactions after running a general ledger year-end process, you can run the year-end process again to close out the nominal accounts and correctly set the opening balances in the new year.

## How do I set up funds for year-end processing?

Year-end processing of general ledger balances is controlled by fund configuration settings in two places:

- Use the **Opening transactions** page to close ledger balances in the old year and establish opening balances in the new year. You must process a single fund or range of funds.
- Set the year-end processing option for purchase order encumbrances on the **Purchase order year-end process** page. You can override the option on a specific fund, if the general ledger parameters are set to allow for overrides. To learn more about the parameter settings, see [General ledger in the public sector overview](general-ledger-public-sector.md).

## How do I set up main accounts for year-end processing?

Select a close type for every account in your chart of accounts. The close type determines how the year-end process handles that main account. Choose from four close types:

- **Real** – The balance is used to establish opening balances in the new year.
- **Nominal** – The account is closed by the year-end process.
- **Nominal – no close** – The account is managed by other closing processes, such as encumbrance accounts for purchase order close.
- **Not applicable** – The account isn't included in year-end processing.

Posting definitions govern the accounting that occurs on the closing entries. They also help create the opening transactions for the new year. For more information, see [Posting definitions in the public sector](posting-definitions-public-sector.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
