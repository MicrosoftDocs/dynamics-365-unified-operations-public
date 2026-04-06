---
title: Default dimensions
description: Learn how default dimension values are configured and applied, including fixed dimensions on main accounts, copying values from master records, and the order in which defaults are applied during posting.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 04/05/2026
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerChartofAccounts,DimensionDetails
ms.dyn365.ops.version: July 2017 update
---

# Default dimensions

[!include [banner](../includes/banner.md)]

Default dimensions are preset financial dimension values that the system automatically applies to transactions. They reduce manual data entry and help ensure consistency across financial records. Default dimensions come from various places, such as master records (for example, customer or vendor records), document headers, and the main account.

This article explains how default and fixed dimension values work on main accounts and how dimensions are applied during posting. For information about how account structures, advanced rules, and balancing dimensions define valid combinations of main accounts and dimension values, see [Financial dimensions](financial-dimensions.md).


## Entering default dimensions

More than 250 pages let you enter default financial dimensions. The dimensions are shown on a FastTab that lists them together with values and descriptions. In standard demo data, more than 30 dimensions are available. However, the following example of a **Financial dimensions** FastTab shows just five dimensions: BusinessUnit, CostCenter, Department, ItemGroup, and Project.

![Screenshot of Financial dimensions FastTab.](./media/DefaultDimensionEntry.png)

### Dimensions list

The system first filters the dimensions based on the list of all active account structures that are associated with the ledger of the current company or the company that you specify on the page. Next, the system gets a union of all the dimensions in those account structures, plus all active advanced rules that are associated with those structures.

![Screenshot of Financial dimensions list.](./media/FinancialDimensionList.png)

### Ledger page

On the **Ledger** page (**General Ledger \> Setup \> Ledger**), you can maintain the account structures for a company.

![Screenshot of Ledger page for the USMF company.](./media/LedgerStructureConfiguration.png)

### Account structures where the number of dimensions varies

To determine how many dimensions an account structure uses, select it on the **Ledger** page, select **Configure account structure** above the grid, and then count the columns. The following illustrations show one account structure that uses three dimensions and another account structure that uses five dimensions.

**Account structure that uses three dimensions**

![Screenshot of setup of the Balance sheet account structure for the USMF company.](./media/BalanceSheetAccountStructureSetup.png)

**Account structure that uses five dimensions**

![Screenshot of setup of the Profit and loss account structure for the USMF company.](./media/PandLAccountStructureSetup.png)

Between the two account structures that are shown in the preceding illustrations, there are four unique dimensions: BusinessUnit, Department, CostCenter, and ItemGroup. These four dimensions appear in the list of default dimensions. In addition, dimensions from advanced rule structures that are linked to the account structures through advanced rules are examined. In this example, the examination of dimensions from advanced rule structures causes a fifth dimension, Project, to be added to the list of default dimensions.

The following illustration shows the advanced rule that causes the Project dimension to be included in the list of default dimensions.

![Screenshot of advanced rule that is linked to the Profit and loss account structure.](./media/AdvancedRuleLinked.png)

The following illustration shows the rule structure.

![Screenshot of rule structure for Project.](./media/RuleStructure.png)

> [!NOTE]
> The MainAccount dimension doesn't appear in most lists of default dimensions. However, Budgeting is the exception. It explicitly includes the MainAccount dimension in the list of default dimensions.

## Default and fixed financial dimensions on the main account

You can define whether a main account has a **Not fixed** or **Fixed** value for each financial dimension that is used across all account structures for the ledger. If a financial dimension is **Not fixed**, it uses a default value, but that value can be overwritten. This behavior applies to all default values in the system, even default values that come from master records. If a financial dimension is set to a **Fixed** value, that value is always applied, regardless of whether it came from somewhere as a default value or the user entered it.

## Copy default dimension values from master records

In addition to fixed and default dimensions on main accounts, you can configure dimensions to automatically copy values from master records such as customers and vendors. When a dimension value is copied, it becomes the default on documents that reference that master record. For example, when you create a new customer, the customer ID is entered in the customer dimension. When you then create sales orders or invoices for that customer, the system defaults the customer ID into the customer dimension on the document.

### Enable the setting

A setting on the financial dimension controls this feature: **Copy values to this dimension on each new [Dimension name] created**, where **[Dimension name]** is the name of the dimension. By default, this setting is turned off. You can turn it on at any time.

If records already exist for the dimension when you enable this setting, the system updates the master records. However, existing documents and transactions aren't updated.

### Template considerations

If you use a template to create master records, make sure the template value for the master dimension is blank. For example, if you create customers from a template, leave the customer dimension in the template blank. The customer dimension value then defaults from the new customer number when you create the customer.

### Blank dimension values

You can intentionally default a dimension value to blank by assigning a fixed dimension value of blank on a main account (via *Legal entity overrides*).

If you don't intend for a blank dimension value to be defaulted, ensure that the dimension's fixed value is set to **Not fixed**, or provide a valid fixed value that complies with the account structure.

### Supported entities for copy values on create

The **Copy values to this dimension on each new [DimensionName] created** toggle is only available for entity-backed dimensions that you configure to support this feature. The toggle appears disabled (greyed out) on the dimension details form for dimensions that don't support it.

The following entity-backed dimensions support copy values on create out of the box:

- Asset
- Bank account
- Customer group
- Customer
- Position
- Worker
- Item
- Project invoice
- Project
- Retail channel
- Retail store
- Retail terminal
- Vendor

Custom dimensions and entity-backed dimensions that aren't in this list don't support this feature by default. To enable copy values on create for a custom or unsupported entity-backed dimension, a developer must configure the dimension to support it. For more information, see [Enable copy values on create for financial dimensions](/dynamics365/fin-ops-core/dev-itpro/financial/enable-copy-values-dimension-on-create.md).

## Additional resources

For information about how defaults cascade during journal entry, see [Default dimension values in financial journals](/dynamics365/finance/general-ledger/dimensions-default-values).

For information about the order in which default dimensions are applied during posting, including examples with fixed dimensions, balancing dimensions, and advanced rules, see [Financial dimensions and posting](/dynamics365/finance/general-ledger/default-dimensions#order-in-which-default-dimensions-are-applied-during-posting).

For more information about default dimensions in customizations, see [Default financial dimensions](/dynamics365/fin-ops-core/dev-itpro/financial/dimension-defaulting).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
