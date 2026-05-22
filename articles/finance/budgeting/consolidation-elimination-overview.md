---
title: Consolidation and elimination overview
description: Learn about the consolidation and elimination process, including outlines on options for consolidating data and answers to some frequently asked questions.
author: twheeloc
ms.author: twheeloc
ms.topic: overview
ms.date: 04/01/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerConsolidate
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9d8f55cb-b2cf-4e01-89cf-0e21f5c8ae1f
---

# Consolidation and elimination overview

[!include [banner](../includes/banner.md)]

This article provides general information about the consolidation and elimination process. It includes answers to some frequently asked questions.

When you consolidate data, you combine the financial results for multiple subsidiary companies into results for a single, consolidated company. Subsidiaries might be on different versions or systems, they might not be fully owned, and they might use different currencies. You have multiple options for consolidating data:

- **Consolidate online** – This option consolidates daily balances by the selected accounts and dimensions, and stores them in a consolidation company.
- **Financial reporting** – This option enables consolidation of transactions and balances, and you can generate it at any time. You can create multiple levels of hierarchies, and view multiple reporting currencies.
- **Consolidate with import** – This option imports balances into a consolidation company.
- **Export company balances** – This option provides an export file of company balances. You can then import the file into other instances or systems. You can also use financial reporting to export the balances to a Microsoft Excel file.

You can report eliminations in multiple ways:

- Set up elimination rules in the system, and then process them during the consolidation process or through an elimination proposal. You can post the rules to any company that has **Use for financial elimination process** selected in the legal entity setup.
- Create a separate company to manually determine and post elimination transactions. You can use this company in the consolidation process or in financial reporting.
- Filter the accounts and financial dimensions that are used to determine intercompany activity on a row definition or column definition in Financial reporting, and use full drill-down capabilities. You can then use a calculated column or row to remove the accounts and financial dimensions from the consolidated total.

There are many consolidation scenarios, and each method can handle the scenarios in different ways.

## Frequently asked questions

I prefer to post eliminations in a database. What are my options?

- You have multiple options. You can use the **Consolidate online** option, and include eliminations during the process or as a proposal. The transactions are posted in the consolidation company. Alternatively, you can use a separate company that you manually create the eliminations in, and then use that company in Financial reporting or in the consolidation process.

We need our consolidated results in multiple reporting currencies.

- The **Financial reporting** option has unlimited reporting currencies. The data is translated during report generation, based on the exchange rate type and currency translation method that you set on the main account. However, because the **Consolidate online** option has only one reporting currency, a consolidated company is required for each reporting currency if you use that option. The **Financial reporting** option is the recommended method.

I want to see transaction-level detail for each company.

- The **Financial reporting** option is the solution, because you can view transaction-level detail for as many companies as are included in the reporting tree definition.

We are using budget planning or budget control, and it must be consolidated.

- The **Financial reporting** option is the solution to consolidate any budget planning or budget control data.

Our subsidiaries are spread throughout the world, and we have multiple charts of accounts. What is the best method for consolidating our data?

- You have multiple options when you must handle multiple charts of accounts. You can use the **Consolidate online** option, and then choose to use either the consolidation account that you define on the main account or a consolidation account group. You can also use the **Financial reporting** option, include multiple links to the financial dimensions in the row definition, and map the accounts.

We require multiple levels of consolidation. In other words, we first consolidate all our European subsidiaries to the British pound (GBP). We then take that data and translate the consolidated amount to US dollars. How can we do this?

- When multiple levels of consolidation are required, and different currencies are used at each level, you must use the **Consolidate online** option. Multiple consolidation companies must be created that differ in their accounting and reporting currencies. The consolidation must then be run multiple times. The **Financial reporting** option always translates from each source company's accounting currency to the selected currency.

We have subsidiaries on a different system. How can we consolidate them?

- Use the **Consolidate with import** option to bring the balances into a consolidation company.

Some of our subsidiaries aren't fully owned. What is the best method for consolidating them?

- You have multiple options for partially owned subsidiaries. By using the **Financial reporting** option, you can define a reporting tree definition and the ownership. You can also use a calculated row or column to represent the partially owned amount. You can even show the minority interest as its own row on a report. You can also use the **Consolidate online** option. The **Legal entities** tab has an **Ownership** column, where you can define the percentage that the parent company owns.

Our organization must show consolidations by business unit or wants to use the organization hierarchies.

- The **Financial reporting** option is the solution. Organization hierarchies that have legal entities or financial dimensions in them can be reported on in Financial reporting. You can also create your own multilevel hierarchies by using a reporting tree definition that has a combination of legal entities and dimension values.

We have more than one instance of the system.

- By using the **Export company balances** option to export from one instance and then using the **Consolidate with import** option on the other instance, you can consolidate the data.

Can I do a Consolidation with my budget in **DRAFT** status?

- You can't process or complete your budgets in the consolidation company. Use Financial Reporting to consolidate draft budgets.

For more information, see [Currency revaluation in a consolidation company](../general-ledger/currency-revaluation-consolidation-company.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
