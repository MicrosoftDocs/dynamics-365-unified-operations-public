---
title: Automate tax feature creation based on tax master data (Preview)
description: Learn how to use the Tax Data Migration functionality to automatically create a Tax Calculation feature based on existing sales tax master data in Microsoft Dynamics 365 Finance.
author: epodkolz
ms.author: epodkolzina
ms.date: 04/07/2026
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Automate tax feature creation based on tax master data (Preview)

[!include [banner](../../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to use the functionality to automatically create a Tax Calculation feature based on existing sales tax master data in Microsoft Dynamics 365 Finance.

This feature reduces time and effort for businesses by simplifying the transition from standard sales tax functionality to the advanced [Tax Calculation](global-tax-calcuation-service-overview.md) functionality. An automated tax feature creation process enables you to adopt and realize the benefits of Tax Calculation faster and with less manual work. It reads existing sales tax master data in the legal entity and automatically creates the required records in the Tax feature setup, reusing existing tax codes, sales tax groups, and item sales tax groups. This approach minimizes setup complexity, preserves current configurations, and ensures a smoother transition to the advanced Tax Calculation experience.

> [!NOTE]
> This functionality is supported globally, except for Brazil and India.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

Before you begin, ensure the following prerequisites are met:

- Import the [latest Tax Configuration](global-tax-calcuation-service-overview.md#versions) in **Electronic reporting > Tax configurations**. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](workspace/gsw-import-er-config-dataverse.md) or [Import Electronic reporting (ER) configurations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).
- Enable the **(Preview) Automate tax feature creation based on tax master data** feature in the **Feature management** workspace.

## Enable the Automate tax feature

To enable the Automate tax feature, follow these steps:

1. In the **Feature management** workspace, find and enable the **(Preview) Automate tax feature creation based on tax master data** feature.
1. After you enable the Automate tax feature, the **Tax Data Migration (preview)** button becomes available in the header of the Tax Calculation workspace in Globalization Studio.

## Run the autocreate tax feature process

To run the autocreate tax feature process, follow these steps:

1. Go to **Globalization Studio** > **Tax Calculation**.
1. In the header, select the **Tax Data Migration (preview)** button.

> [!NOTE]
> Although Globalization Studio settings are legal entity agnostic, this functionality works only for the currently selected legal entity. You must switch to the correct legal entity before starting the process.

When the process finishes, the system creates the tax feature version in a **Completed** state. The following message is displayed: **The tax feature 'xxxx' is created successfully. You can review the setup in the feature version by using the View button. If updates are needed, create a new version to edit the tax feature.**

To review the generated setup, use the **View** button. If you need to make changes, create a new version of the feature to make edits. Learn more in [Configure the Tax Calculation feature](global-get-started-with-tax-calculation-service.md#configure-the-tax-calculation-feature).

## Tax feature creation behavior overview

During the tax feature creation process, existing sales tax settings are mapped from the legal entity into the Tax Calculation feature setup. The following sections describe key behaviors.

### Tax group level settings

In standard sales tax, define settings such as cash discount, use tax, reverse charge, and exempt at the tax group level. In Tax Calculation, define these settings at the line level in the tax feature. The functionality considers this setup mapping and creates the appropriate records during the tax feature creation.

#### Tax code variant handling

When you assign a tax code to multiple tax groups with different parameters, the system creates extra tax code variants during the tax feature creation process. For example:

- In Tax Group **Test1**, the same tax code **Test10** is marked as **Exempt**.
- In Tax Group **Test2**, tax code **Test10** has **Use tax** enabled.

The system creates multiple versions of the tax code (for example, Test10, Test10\_1, Test10\_2, and so on). Each version is assigned to the appropriate tax group with the corresponding parameters.

If a tax code name is already at the maximum length (10 characters) and a variant needs to be created, the name is truncated and a suffix is appended. For example, **Test123456** becomes **Test1234\_1**. Despite truncation, the tax codes are correctly assigned to their respective tax groups.

#### Reverse sales tax on cash discount

The system sets the default tax jurisdiction parameters based on the General ledger parameter values. If the **Reverse sales tax on cash discount** value in a sales tax group differs from the General ledger parameter, the system displays the following warning: **The default Reverse tax on cash discount parameter differs from the one set in the group(s): 'xxxx', 'xxxx'. Once the process completes, please manually create rules to ensure proper configuration.**

After the tax feature is created, you must manually maintain the tax jurisdiction parameters to ensure the sales tax group-level parameter scenario works correctly. Learn more in [Tax jurisdiction parameters setup](global-tax-jurisdiction-cash-discount-setup.md).

### Tax group character limit

If a tax group or item tax group contains tax codes whose total length exceeds 1,000 characters, the process stops and one of the following messages is displayed:

- **The tax group 'xxxx' contains too many or excessively long tax codes. The total length must not exceed 1,000 characters. The process has been canceled.**
- **The item tax group 'xxxx' contains too many or excessively long tax codes. The total length must not exceed 1,000 characters. The process has been canceled.**

### Data mapping during tax feature creation

The following tables describe the mapping that applies during the tax feature creation process.

#### General ledger parameters to Tax jurisdiction parameters

| General ledger – Sales tax setting | Tax jurisdiction parameter after tax feature creation |
|---|---|
| Reverse sales tax on cash discount | Default Reverse Tax On Cash Discount |
| Deduct cash discount before sales tax calculation | Default Deduct Cash Discount Before Tax Calculation |
| Cash discount is calculated on amount including sales tax (Customer) | Default Calculate Cash Discount On Amount Including Tax – Customer |
| Cash discount is calculated on amount including sales tax (Vendor) | Default Calculate Cash Discount On Amount Including Tax – Vendor |

#### Sales tax code origin to Tax code calculation origin

| Sales tax code origin | Tax Calculation feature origin |
|---|---|
| Percentage of gross amount | By Gross Amount |
| Percentage of net amount | By Net Amount |
| Percentage of margin | By Margin |
| Calculate percentage of net amount | By Percentage of Net |
| Amount per unit | By Quantity |
| Percentage of sales tax | Tax on Tax |

#### Rounding precision behavior

In the Tax Calculation feature, the rounding precision behaves similarly to the configuration on the **Tax Configuration** page. However, the **Rounding Method** is initially set to **Ordinary**, which functions equivalently to **Normal** rounding.

## After you create the tax feature

When the process finishes, review the following items:

1. **Tax jurisdiction parameters** – Verify that the mapped parameters from the general ledger match your business requirements. If the **Reverse sales tax on cash discount** value differs at the tax group level, manually create rules in the tax feature setup.
1. **Tax code variants** – Review any tax code variants that the process created with suffixes (\_1, \_2, and so on). Check the tax group assignments in the feature parameters to confirm they're correct.
1. **Tax code settings** – Verify that tax code origins, rates, and other settings are correct.
1. **Rounding method** – The default rounding method is set to **Ordinary**. Adjust if your business requires a different rounding method.
1. **No incremental updates** – The process always creates a tax feature based on the full current tax master data. If you modify tax master data after the tax feature is created (for example, add new tax codes, update tax groups, or change tax code settings), those changes aren't automatically reflected in the previously created tax feature. To incorporate the changes, you can either create a new version of the tax feature and update the setup manually, or run the **Tax Data Migration** process again to recreate the tax feature from scratch based on the current master data.

After you review and, if needed, update the created tax feature, assign it to the legal entity and start using it for tax calculation. To do so, follow the steps in [Set up Tax Calculation in Globalization Studio workspace](/dynamics365/finance/localizations/global/global-get-started-with-tax-calculation-service#set-up-tax-calculation-in-globalization-studio-workspace).

If you create new tax codes, sales tax groups, or item sales tax groups during the tax feature creation process (for example, tax code variants with suffixes), the process synchronizes those records back to the standard sales tax tables in Dynamics 365 Finance. Learn more in [Sync the tax setup from the Tax Calculation feature to Finance](/dynamics365/finance/localizations/global/global-master-data-sync-tax-calculation-service-finance).

## Key considerations and known limitations

| Topic | Description |
|---|---|
| One legal entity at a time | The process can only create a tax feature for the legal entity that you're currently signed into. Switch to the correct legal entity before starting the process. |
| Manual adjustments for parameters | If tax code attributes differ from ledger parameters or tax groups, you might need to adjust parameters manually after the tax feature is created. |
| Tax code name limited to 10 characters | Tax codes are limited to a maximum of 10 characters. Longer codes are truncated before a suffix is appended (for example, `Test123456` becomes `Test1234_1`). |
| Tax group character limit of 1,000 | A tax group or item tax group that contains over 1,000 characters causes an error. The process stops and the following message is displayed: "The tax group 'xxxx' contains too many or excessively long tax codes. The total length must not exceed 1,000 characters. The process has been canceled." |
| Reverse Sales Tax on Cash Discount | If the value of **Reverse sales tax on cash discount** in a sales tax group differs from the default General ledger parameter, you must manually create rules after the tax feature is created to ensure proper configuration. [Tax jurisdiction parameters setup](global-tax-jurisdiction-cash-discount-setup.md) |
| Tax code variant handling | If a tax code (for example, VAT0) exists in different tax groups with different settings (such as exempt or use tax), the process creates separate tax code variants with a suffix (for example, VAT0 and VAT0\_1). The suffixes (\_1, \_2, and so on) are assigned in a nondeterministic order, but the parameter mappings remain correct. To identify which tax group a variant belongs to, check the tax group specified in the feature parameters. |
| Brazil and India not supported | The functionality isn't available for legal entities in Brazil and India. |

## Additional resources

- [Tax Calculation overview](global-tax-calcuation-service-overview.md)
- [Import Electronic reporting (ER) configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse)
- [Import Electronic reporting (ER) configurations](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
