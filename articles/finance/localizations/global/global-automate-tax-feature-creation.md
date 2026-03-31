---
title: Automate tax feature creation based on tax master data (preview)
description: Learn how to use the Tax Data Migration tool to automatically create a Tax Calculation feature based on existing core tax master data in Microsoft Dynamics 365 Finance.
author: epodkolz
ms.author: epodkolz
ms.date: 03/31/2026
ms.topic: article
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Automate tax feature creation based on tax master data (preview)
[!include [banner](../../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to use the functionality to automatically create a Tax Calculation feature based on existing core tax master data in Microsoft Dynamics 365 Finance.

This feature reduces time and effort for businesses by simplifying the transition from core tax functionality to the advanced [Tax Calculation](global-tax-calcuation-service-overview.md) functionality. An automated tax feature creation process enables customers to adopt and realize the benefits of Tax Calculation faster and with less manual work. It reads existing core tax master data in the legal entity and automatically creates the required records in the Tax feature setup, reusing existing tax codes, sales tax groups, and item sales tax groups. This approach minimizes setup complexity, preserves current configurations, and ensures a smoother transition to the advanced Tax Calculation experience.

> [!NOTE]
> This functionality is supported globally, except for Brazil and India. If the legal entity is in Brazil or India, the **Tax Data Migration** button is not available, and a message informs you that the functionality is not supported in those countries/regions.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

Before you begin, the following prerequisites must be met:

- The latest Tax Configuration must be imported in Electronic reporting > Tax configurations. For instructions, see [Import Electronic reporting (ER) configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse) or [Import Electronic reporting (ER) configurations](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations).
- The **(Preview) Automate tax feature creation based on tax master data** feature must be enabled in the **Feature management** workspace.

## Enable the feature
1. In the **Feature management** workspace, find and enable the **(Preview) Automate tax feature creation based on tax master data** feature.
2. After the feature is enabled, the **Tax Data Migration (preview)** button becomes available in the header of the Tax Calculation workspace in Globalization Studio.

## Create the tax feature
1. Navigate to **Globalization Studio** \> **Tax Calculation**.
2. In the header, select the **Tax Data Migration (preview)** button.

The tool reads the existing tax master data and automatically creates the necessary records in the Tax feature setup to ensure a complete and accurate data transfer. The tax feature is generated based on the existing tax codes, sales tax groups, and item sales tax groups of the current legal entity.

> [!NOTE]
> The tool works only for the currently selected legal entity. You must switch to the correct legal entity before starting the process.

After the process is completed, the system creates the tax feature version in a **Completed** state. The following message is displayed: "The tax feature 'xxx' has been successfully created. You can review the setup in the feature version using the View button. If updates are needed, please create a new version to edit the tax feature."

To review the generated setup, use the **View** button. If changes are needed, create a new version of the feature to make edits.
## Data mapping during tax feature creation

During the tax feature creation process, the tool maps existing core tax settings to the Tax Calculation feature setup. The following tables describe the mapping.

### General ledger parameters to Tax jurisdiction parameters

| General ledger – Sales tax setting | Tax jurisdiction parameter after tax feature creation |
|---|---|
| Reverse sales tax on cash discount | Default Reverse Tax On Cash Discount |
| Deduct cash discount before sales tax calculation | Default Deduct Cash Discount Before Tax Calculation |
| Cash discount is calculated on amount including sales tax (Customer) | Default Calculate Cash Discount On Amount Including Tax – Customer |
| Cash discount is calculated on amount including sales tax (Vendor) | Default Calculate Cash Discount On Amount Including Tax – Vendor |

### Sales tax code origin to Tax code calculation origin

| Sales tax code origin | Tax Calculation feature origin |
|---|---|
| Percentage of gross amount | By Gross Amount |
| Percentage of net amount | By Net Amount |
| Percentage of margin | By Margin |
| Calculate percentage of net amount | By Percentage of Net |
| Amount per unit | By Quantity |
| Percentage of sales tax | Tax on Tax |

## Rounding precision behavior

In the Tax Calculation feature, the rounding precision behaves similarly to the configuration on the **Tax Configuration** page. However, the **Rounding Method** is initially set to **Ordinary**, which functions equivalently to **Normal** rounding.

## After the tax feature is created

After the process is completed, review the following items:

1. **Tax jurisdiction parameters** – Verify that the mapped parameters from the general ledger match your business requirements. If the **Reverse sales tax on cash discount** value differs at the tax group level, manually create rules in the tax feature setup.
2. **Duplicate tax codes** – Review any tax codes that were created with suffixes (\_1, \_2, and so on). Check the tax group assignments in the feature parameters to confirm they are correct.
3. **Tax code settings** – Verify that tax code origins, rates, and other settings were created correctly.
4. **Rounding method** – The default rounding method is set to **Ordinary**. Adjust if your business requires a different rounding method.
5. **No incremental updates** – The tool always creates a tax feature based on the full current tax master data. If you modify tax master data after the tax feature is created (for example, add new tax codes, update tax groups, or change tax code settings), those changes are not automatically reflected in the previously created tax feature. To incorporate the changes, you can either create a new version of the tax feature and update the setup manually, or run the **Tax Data Migration** tool again to recreate the tax feature from scratch based on the current master data.

After you review and, if needed, update the created tax feature, you can assign it to the legal entity and start using it for tax calculation. To do so, follow the steps in [Set up Tax Calculation in Globalization Studio workspace](/dynamics365/finance/localizations/global/global-get-started-with-tax-calculation-service#set-up-tax-calculation-in-globalization-studio-workspace).

If new tax codes, sales tax groups, or item sales tax groups were created during the tax feature creation process (for example, duplicate tax code variants with suffixes), those records are synchronized back to the core tax tables in Dynamics 365 Finance. For more information, see [Sync the tax setup from the Tax Calculation feature to Finance](/dynamics365/finance/localizations/global/global-master-data-sync-tax-calculation-service-finance).

## Additional resources

- [Tax Calculation overview](global-tax-calcuation-service-overview.md)
- [Import Electronic reporting (ER) configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse)
- [Import Electronic reporting (ER) configurations](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations)



