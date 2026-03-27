---
title: Financial dimensions and tags
description: Learn about the various types of financial dimensions and tags and how they're set up.
author: anaborges02
ms.author: aolson
ms.topic: article
ms.date: 01/30/2026
ms.update-cycle: 1095-days
ms.custom: evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-10-31
ms.search.form: DimensionDetails, DimensionValueDetails, SysTranslationDetail
ms.dyn365.ops.version: 8.1
---

# Financial dimensions

[!include [banner](../includes/banner.md)]
[!INCLUDE [lcs-freeze-banner](../../includes/lcs-freeze-banner.md)]

Use financial dimensions to further categorize financial transactions. Financial dimension values become segments within the ledger account and you can use them for further analysis, such as generating a profit and loss financial statement by a dimension or a trial balance by dimension.

Financial tags (tags) are an alternative to financial dimensions. An organization can create up to 20 user-defined financial tags and enter values for them on transactions. For more information, see [Financial tags](financial-tag.md). Also, explore the differences between the two in the document Differences between financial tags and financial dimensions.

This article explains the various types of financial dimensions and their key properties. For step-by-step creation instructions, see [Define financial dimensions](tasks/define-financial-dimensions.md).

## Financial dimension types

Financial dimensions that you create on the **Financial dimensions** page are used as account segments for charts of accounts. There are two types of financial dimensions: custom dimensions and entity-backed dimensions.

### Custom dimensions

A custom dimension is a financial dimension that reflects your organization's specific business needs — for example, an internal cost center classification, fleet identifier, or expense purpose. Unlike entity-backed dimensions, custom dimension values don't come from an existing table in the system — you create and maintain the available values manually on the **Financial dimension values** page. In addition, custom dimensions are always shared across legal entities. 

### Entity-backed dimensions

An entity-backed financial dimension is based on a system-defined entity that you select in the **Use values from** field. For entity-backed dimensions, the values are defined somewhere else in the system, such as in Customers or Stores entities. Some entity-backed dimensions are shared across legal entities, whereas other entity-backed dimensions are company-specific. Dimensions that are company-specific (also known as company-striped dimensions) are only visible when accessed as a user from the associated company.

For example, to create dimension values for projects, select **Projects**. This allows any value from the project table to be used as a dimension value directly.
A dimension value is then created for each project name. The **Financial dimension values** page shows the values for the entity. If those values are company-specific, the page also shows the company.

Entity-backed dimension values aren't available in the dimension framework until the value has been used in a transaction, posting profile, journal, or similar context. A record that exists in the source entity (for example, a new customer) won't appear as a selectable dimension value until it has been referenced in one of these areas.

If you want to rename or delete dimension values from entity-backed dimensions, do this from the source entity rather than from the **Financial dimension values** page. For more information, see [Modifying and deleting financial dimensions](modifying-deleting-financial-dimensions.md).

## Financial dimension values

After you create a financial dimension, use the **Financial dimension values** page to create, view, or assign additional properties to each financial dimension value.

For a custom financial dimension, use this page to create and edit dimension values. You can only enter or edit the **Dimension value** and **Description** fields for custom dimensions. Dimension values have a maximum length of 30 characters.

For an entity-backed financial dimension, you can't create dimension values from the **Financial dimension values** page. You also can't edit the dimension value and descriptions from within the page. For example, let's say you created the Project financial dimension previously described. On the **Financial dimension values** page, you can't edit the project **Dimension value** or **Description**. This information is taken directly from the project setup. If a new project value is necessary, you must create it from the **Project** page.

To validate whether a ledger account or default dimension combination is structurally valid, use the **Dimension data validation** page. For more information, see [Dimension data validation](financial-dimension-data-validation.md).

## Legal entity overrides

All custom dimensions and some entity-backed dimensions, such as dimensions created from an operating unit, are global. When you use global values, all dimension values for that dimension are active for all legal entities that include that dimension in their account structure.

But, not all dimensions or main accounts are valid for all legal entities. Additionally, some might be relevant only for a specific period. In these cases, use the **Legal entity overrides** section to specify the companies that the dimension or main account should be suspended for, the owner, and the period when the dimension is active. The overrides at the shared level can't be more restrictive than the overrides at the legal entity level.

### Example

Department has dimension values of 100, 200, and 300. USMF, USSI, and DEMF all use the Department dimension. DEMF is only permitted to use department 100 and 200. To restrict DEMF from using Department 300, create a legal entity override where you mark the dimension value as Suspended. USMF and USSI still have full access to departments 100, 200, and 300.

## Financial dimensions as legal entities

You can use financial dimensions to represent legal entities. You don't need to create the legal entities in Dynamics 365 Finance. However, financial dimensions aren't designed to address the operational or business requirements of legal entities. The intercompany accounting functionality in Finance is designed to address only the accounting entries that each transaction creates.

Before you set up financial dimensions as legal entities, evaluate your business processes in the following areas to determine if this setup works for your organization:

- Inventory
- Sales and purchases between financial dimensions and legal entities
- Sales tax calculation and reporting
- Operational reporting

Here are some of the limitations:

- You can use sales tax functionality only with legal entities, not with financial dimensions.
- Some reports don't include financial dimensions. Therefore, to report by financial dimension, you might have to modify the reports.

## Financial dimension service

You can access the Financial dimension service add-in in your Microsoft Dynamics Lifecycle Services environment. It provides improved performance when you use the Data management framework to import a journal that has a large number of lines. To use the service, you must enable it on the **Financial dimension service parameters** page. Currently, the service works only on imported journals. In addition, it can currently process only general journals where the **Ledger** account type is set on the journal lines. Other account types on journal lines, such as **Customer**, **Vendor**, and **Bank**, aren't currently supported. This service isn't invoked when derived dimensions are set up in the system.

The Financial dimension service provides improved performance when you import journals by using a new service that runs in parallel to the data import. It runs only on the main account and financial dimension data in the journal, and it generates the dimension combinations that are specified in the ledger account string field on the journal lines. The processing converts this string into the structured data storage that the Financial dimension framework uses throughout the rest of the product for validation, summary reporting, and inquiries. For more information about summary reporting of financial dimension data, see [Financial dimension sets](financial-dimension-sets.md).

For more information, see the following topics:

- [Define financial dimensions](tasks/define-financial-dimensions.md)
- [Maintain financial dimension default templates](tasks/maintain-financial-dimension-default-templates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
