---
title: Posting definitions
description: Learn about posting definitions, and how to define and link them. You can use posting definitions instead of posting profiles to classify main accounts.
author: kweekley
ms.author: kweekley
ms.topic: concept-article
ms.date: 07/31/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: JournalizingDefinition, JournalizingDefinitionTrans, LedgerParameters
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 1495e7e0-2e39-464c-8da9-f55b1ca1c6bb
---

# Posting definitions

[!include [banner](../includes/banner.md)]

This article provides information about posting definitions, and how to define and link them.
For supported posting types and documents, use posting definitions instead of posting profiles to classify main accounts and financial dimensions on accounting entries. You can view the supported documents and posting types on the **Transaction posting definitions** page.

To start using posting definitions, select the **Use posting definitions** option on the **General ledger parameters** page. Even when you use posting definitions, you must still define posting profiles for the originating entries and non-supported posting types and documents.

You must use posting definitions to enable encumbrance accounting for purchase orders and pre-encumbrance accounting for purchase requisitions.

## Defining posting definitions

Use the **Posting definitions** page to specify the match criteria and define the entries that should be generated when a match occurs. The system evaluates the match criteria for the originating entries as accounting distributions.

On the **Posting definitions** page, you can also assign priority numbers to entry lines to control the order in which the lines are evaluated. The system evaluates the lines that have the lowest priority number first. For example, the system evaluates all lines that have a priority of 1, and then lines that have a priority of 2, and so on. When the system finds a match, it ignores the other match criteria. Additionally, only the criteria in the group that match the originating transaction create generated entries.

You can validate your posting definitions by using the **Test posting definition** wizard. After you define a sample originating entry for a posting definition, you see the generated entries.

You can use posting definition versions together with effective dates. For example, you can create a future version of a posting definition to post to a different ledger account in a new fiscal year.

Use the **Transaction posting definitions** page to assign posting definitions to transaction types.

## Linking posting definitions

You can link one posting definition to another when you create posting definitions. The system considers the criteria for the linked definition along with the criteria for the current posting definition. This feature helps you save time because you don't have to reenter criteria on the **Entries** FastTab on the **Posting definitions** page for the current posting definition if you already entered those lines for another definition.

In the diagrams or tables, include any links that you might use. To avoid conflicts with the current posting definition, make sure that the lines in any posting definitions that you link to are unique.

The following restrictions apply when you create links in posting definitions:

- A given posting definition can either link to another posting definition or be linked to from another posting definition, but not both. However, a posting definition can link to multiple posting definitions.
- You can set up links only among posting definitions that are in the same module.
- You can assign a posting definition to any transaction type, but the transaction type must be in the same module as the posting definition. Use the **Transaction posting definitions** page to see what module a transaction type is in.

For more information, see [Posting definition examples](example-posting-definitions.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
