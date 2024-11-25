---
title: Consolidate online templates
description: Learn how to set up the consolidation templates to use with the Consolidate online functionality, including an outline on financial dimensions.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 04/23/2024
ms.custom: 539093
ms.reviewer: twheeloc
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form:  
ms.dyn365.ops.version: 10.0.24
---

# Consolidate online templates

[!include [banner](../includes/banner.md)]

This article describes online financial consolidations in General ledger. Before you read this article, be sure to read the [Financial consolidations and currency translation overview](financial-consolidations-currency-translation.md) article.

In Microsoft Dynamics 365 Finance version 10.0.40, templates were added to improve the Consolidate online experience. After you set up the consolidation information one time in the templates, you can use the templates whenever you must run the consolidation process. You no longer have to set up or change the information each time that you want to consolidate accounts. The templates contain all the information that was on the **Consolidate \[Online\]** page. Therefore, you can quickly run the process by selecting dates and a template.

To use the templates, enable the **Consolidate online using templates** feature in the **Feature management** workspace.

Use the **Consolidation online templates** page (**Consolidations** \> **Setup** \> **Consolidation online template setup**) to create multiple templates that you can use in Consolidate online in Finance. For each template that you create, you enter a name and a description. The consolidation period isn't defined in the template. Instead, it's entered when the consolidation is processed.

On the **Consolidation online templates** page, you can also edit, delete, and copy templates.

## General

On the **General** FastTab of the **Consolidation online templates** page, you define the accounts and the type of data that's being consolidated.

- **Main account** – Use the fields in this section to define the main accounts that should be processed.

    - **From** and **To** – Specify a range of accounts to process. If you leave these fields blank, all accounts from all companies are moved to the consolidation company. Therefore, if you're consolidating four companies, and each company has a different chart of accounts, all accounts from all four companies are created in the consolidation company.

- **Use consolidation account** – If you set this option to **Yes**, the **Select consolidation account from** field becomes available. In that field, select whether all accounts should be consolidated to the consolidation account that's set on the **Main accounts** page, or whether you want to select the account from one of the consolidation account groups.

    - **Consolidation account group** – Select the group to use for the main account mapping for the consolidation.

- **Include actual amounts** – Set this option to **Yes** to consolidate your actual data.

## Financial dimensions

On the **Financial dimensions** FastTab, you define the dimensions that should be included in the consolidation company.

To select a dimension, set the **Specification** field to **Dimension**. Then use the **Segment order** field to define the order of the dimension in the consolidation company.

Regardless of the order that you define, **Main account** is always the first segment.

## Legal entities

On the **Legal entities** FastTab, you define the companies that should be included in the consolidation company. You also define the ownership percentage of those companies. If you specify less than 100-percent ownership, the specified percentage is rolled up to the consolidation company.

For any translation differences, the **Account type for conversion differences** field is used to select the main account from the setup on the **Accounts for automatic transactions** page.

![Screenshot of the Accounts for automatic transactions page.](./media/accounts-for-automatic-cons.png "Screenshot of the Accounts for automatic transactions page")

## Elimination

On the **Elimination** FastTab, you have three options for processing eliminations:

- Select the elimination rule, and then, in the **Proposal options** field, select **Proposal only**. This option processes the elimination during the consolidation process, but it doesn't post everything in one step. You can post the journal later.
- Select the elimination rule, and then, in the **Proposal options** field, select **Post only**. This option processes the elimination during the consolidation process and posts everything in one step.
- Use the elimination journal to run an elimination proposal separately from the consolidation process.

For more information about eliminations, see [Elimination rules](./elimination-rules.md).

## Currency translation

On the **Currency translation** FastTab, you define the legal entity, the account and exchange rate type, and the rate. If the consolidation company is mapped to different main accounts than the source company, you must enter the consolidation company's main accounts in the **From account** and **To account** fields, not the source company's main accounts. Even though the account lookup shows the source company accounts, you must enter the consolidation company's main accounts.

- **Select consolidation amount from**

    - Select **Accounting currency** to use the accounting currency amounts from the source companies to update the accounting currency amounts in the consolidation company. When this value is selected, use the **Consolidate accounting currency** field to define how the accounting currencies in the consolidation company are calculated.
    - Select **Reporting currency** to use the reporting currency amounts from the source companies to calculate the accounting currency amounts in the consolidation company.

        - If the reporting currency from the source company is the same as the accounting currency of the consolidation company, the reporting currency amounts are copied from the source company to the consolidation company.
        - If the reporting currency from the source company differs from the accounting currency of the consolidation company, the values are translated by using the exchange information that's defined on the **Currency translation** tab of this page to calculate the consolidation company values.

- **Consolidate accounting currency** – This field is available only if the **Select consolidation amount from** field is set to **Accounting currency**. Use it to specify whether the accounting currency amounts from the source companies are translated through exchange rates or copied to the consolidation company.

    - Select **Use currency translation** to use the exchange rate information that's defined on the **Currency translation** tab to calculate the consolidation accounting balances.
    - Select **Use accounting currency amount** to copy the accounting currency amounts from the source companies to the consolidation company.

        - If the accounting currency from the source company is the same as the accounting currency of the consolidation company, the currency amounts are copied from the source company to the consolidation company.
        - If the accounting currency from the source company differs from the accounting currency of the consolidation company, the values are translated by using the exchange information that's defined on the **Currency translation** tab to calculate the consolidation company values.

For each row of legal entity and main accounts, the following options are available in the **Apply exchange rate from** field. All three options require that you enter an exchange rate type.

- **Consolidation date** – The date that's defined in the **Consolidation period To** field on the **Consolidations period** tab for the consolidation is used to get the exchange rate. This rate is equivalent to the spot or month-end rate.
- **Transaction date** – The date of each transaction is used to select an exchange rate. This option is most often used for fixed assets and is often referred to as a historical rate. You can't see a preview of the rate, because there will be many rates for the various transactions in the account range.
- **User defined rate** – After you select this option, you can enter the exchange rate that you want. This option can be useful for average exchange rates or if you're consolidating against a fixed exchange rate.

## Budget

On the **Budget** FastTab, set the **Include budget amounts** option to **Yes** to include budget data in the consolidations.

- **From** and **To** – Specify the range of models to use.
- **Budget rate type** – Select the type of budget rate to use for currency translation of budget data.

## Additional resources

For more information about consolidation and currency translations, see the parent article of this article, [Financial consolidations and currency translation overview](./financial-consolidations-currency-translation.md).

For information about scenarios where you might generate consolidate financial statements, see [Generate consolidated financial statements](./generating-consolidated-financial-statements.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
