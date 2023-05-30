---
# required metadata

title: Financial dimensions
description: This article describes the various types of financial dimensions and how they are set up.
author: aprilolson
ms.date: 03/07/2022
ms.topic: article
ems.prod: 
ms.technology: 

# optional metadata

ms.search.form: DimensionDetails, DimensionValueDetails, SysTranslationDetail
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Financial dimensions

[!include [banner](../includes/banner.md)]

This article explains the various types of financial dimensions and how they are set up.

Use the **Financial dimensions** page to create financial dimensions that you can use as account segments for charts of accounts. There are two types of financial dimensions: custom dimensions and entity-backed dimensions. Custom dimensions are shared across legal entities, and the values are entered and maintained by users. For entity-backed dimensions, the values are defined somewhere else in the system, such as in Customers or Stores entities. Some entity-backed dimensions are shared across legal entities, whereas other entity-backed dimensions are company-specific.

After you've created the financial dimensions, use the **Financial dimension values** page to assign additional properties to each financial dimension.

You can use financial dimensions to represent legal entities. You don't have to create the legal entities in Dynamics 365 Finance. However, financial dimensions aren't designed to address the operational or business requirements of legal entities. The interunit accounting functionality in Finance is designed to address only the accounting entries that are created by each transaction.

Before you set up financial dimensions as legal entities, evaluate your business processes in the following areas to determine whether this setup will work for your organization:

- Inventory
- Sales and purchases between financial dimensions and legal entities
- Sales tax calculation and reporting
- Operational reporting

Here are some of the limitations:

- You can use sales tax functionality only with legal entities, not with financial dimensions.
- Some reports don't include financial dimensions. Therefore, to report by financial dimension, you might have to modify the reports.

## Custom dimensions

To create a user-defined financial dimension, in the **Use values from** field, select **Custom dimension**.

You can also specify an account mask to limit the amount and type of information that can be entered for dimension values. You can enter characters that remain the same for each dimension value, such as letters or a hyphen (-). You can also enter number signs (\#) and ampersands (&) as placeholders for characters that will change every time that a dimension value is created. Use a number sign (\#) as a placeholder for a number and an ampersand (&) as a placeholder for a letter. The field for the format mask is available only when you select **Custom dimension** in the **Use values from** field.

**Example**

To limit the dimension value to the letters "CC" and three numbers, enter **CC-\#\#\#** as the format mask.

## Entity-backed dimensions

To create an entity-backed financial dimension, in the **Use values from** field, select a system-defined entity to base the financial dimension on. Financial dimension values are then created from that entity. For example, to create dimension values for projects, select **Projects**. A dimension value is then created for each project name. The **Financial dimension values** page shows the values for the entity. If those values are company-specific, the page also shows the company.

## Activating dimensions

When you activate a financial dimension, the table is updated so that it includes the name of the financial dimension. Deleted dimensions are removed. You can enter dimension values before you activate a financial dimension. However, a financial dimension can't be consumed anywhere until it's activated. For example, you can't add a financial dimension to an account structure until the financial dimension has been activated. When you select **Activate**, all dimensions are updated and show status changes.

## Translations

On the **Text translation** page, you can enter text for the selected financial dimension in various languages. On the **Main account translation** page, you can enter text for the main account in various languages. 

## Legal entity overrides

Not all dimensions are valid for all legal entities. Additionally, some dimensions might be relevant only for a specific period. In these cases, you can use the **Legal entity overrides** section to specify the companies that the dimension should be suspended for, the owner, and the period when the dimension is active.

## Deleting financial dimensions

To help maintain referential integrity of the data, financial dimensions can rarely be deleted. If you try to delete a financial dimension, the following criteria are evaluated:

- Has the financial dimension been used on any posted or unposted transactions, or in any type of dimension value combination?
- Is the financial dimension used in any active account structure, advanced rule structure, or financial dimension set?
- Is the financial dimension part of a default financial dimension integration format?
- Has the financial dimension been set up as a default dimension?
- Has the financial dimension been unselected from the Financial Reporting setup? 

If any of the criteria are met, you can't delete the financial dimension.

> [!NOTE]
> Starting in Finance version 10.0.27, financial dimensions will no longer be automatically selected for financial reporting setup as they are created.

## Default dimension values

You can use values from master records, such as customer and vendor, as default values in new dimensions. When the new dimensions are created, the master record ID is entered in the dimension values for those master records. For example, when you create a new customer, the customer ID is entered in the customer dimension. When you create sales orders, invoices, or other documents that require a customer ID, the existing defaulting rules are used, and the customer ID is added to the document.

This feature is controlled by a setting in the dimension. This setting is named **Copy values to this dimension on each new DimensionName created**, where **DimensionName** is the name of the dimension. By default, the feature is turned off. However, it can be turned on at any time.

If records already exist for the dimension, the master records are updated when you turn the feature on. However, existing documents and transactions aren't updated.

If you are using a template to create a master record, make sure that the template value for the master dimension is blank. For example, if you're creating customers from a template, make sure that the customer dimension in the template is blank. The customer dimension value will default from the new customer number when you create the new customer.  

## Derived dimensions

You can configure a dimension so that information for other dimensions is automatically entered when you enter that dimension in a document. For example, if you enter cost center 10, a value of **20** can be automatically entered in the department dimension.

You can set up derived values on the dimensions page.

1. Select a dimension and then select **Derived dimensions**.

    The **Derived dimensions** page includes a grid. The selected dimension segment is the first column in this grid.

2. Add the segments that should be derived. Each segment appears as a column.

Enter the dimension combinations that should be derived from the dimension in the first column. For example, to use the cost center as the dimension that the department and location are derived from, enter cost center 10, department 20, and location 30. Then, when you enter cost center 10 in a master record or on a transaction page, department 20 and location 30 are entered by default.

### Overriding existing values with derived dimensions
 
By default, the derived dimension process doesn't override existing values for derived dimensions. For example, if you enter cost center 10, and no other dimension is entered, department 20 and location 30 are entered by default. However, if you change the cost center, the values that have already been established aren't changed. Therefore, you can establish default dimensions on master records, and those dimensions won't be changed by derived dimensions.

You can change the behavior of derived dimensions to override existing values by selecting the **Replace existing dimension values with derived values** check box on the **Derived dimensions** page. If this field is selected, you can enter a dimension with derived dimension values and those derived dimension values will override any values that already exist. Using the previous example, if you enter cost center 10, and no other dimension is entered, department 20 and location 30 are entered by default. However, if the values were already department 50 and location 60, the values will now be changed to department 20 and location 30.
 
Derived dimensions with this setting do not automatically replace the existing default dimensions values when dimension values are defaulted. Dimension values will only be overridden when you enter a new dimension value on a page and there are existing derived values for that dimension on the page.

### Preventing changes with derived dimensions
 
When you use **Add segment"** on the **Derived dimensions page** to add a segment as a derived dimension, an option is provided at the bottom of the **Add segment** page that allows you to prevent changes to that dimension when it is derived on a page. The default setting is off, so it does not prevent the derived dimension values from being changed. Change the setting to **Yes** if you want to prevent the dimension from being changed after it has been derived. For example, if the value for the Department dimension is derived from the value of the Cost center dimension, the Department value cannot be changed if the **Prevent changes** setting is **Yes**. 
 
The setting does not prevent changes if the dimension value is valid but it is not listed in the derived dimensions list. For example, if Department 20 is derived from Cost center 10 and you enter Cost center 10, then you will not be able to edit Department 20. However, if you enter Cost center 20 and it is not in the list of derived dimensions for Cost center, then you can edit the Department value. 
 
In all cases, the account value and all dimensions values will still be validated against the account structures after the derived dimensions values have been applied. If you use derived dimensions and they fail validation when used on a page, you must change the derived dimensions values on the derived dimensions page before you can use them in transactions. 
 
When you change dimensions on the **Financials dimensions** FastTab, the dimension that is marked to prevent changes will not be editable. If you are entering an account and dimensions into the segmented entry control on a page, the dimensions are editable. However, when you move the highlight off the segmented entry control and move to another field or take an action, the account and dimensions will be validated against the derived dimensions list and the account structures to ensure that you have entered the appropriate values. 

### Derived dimensions and entities

You can set up the derived dimensions segments and values by using entities.

- The Derived dimensions entity sets up the driving dimensions and the segments that are used for those dimensions.
- The Derived dimensions value entity lets you import the values that should be derived for each driving dimension.

When you use an entity to import data, if that entity imports dimensions, the derived dimension rules are applied during the import unless the entity specifically overrides those dimensions.

## Financial dimension service

The Financial dimension service add-in is available in your Microsoft Dynamics Lifecycle Services environment. It provides improved performance when you use the Data management framework to import a journal that has a large number of lines. To use the service, you must enable it on the **Financial dimension service parameters** page. Currently, the service works only on imported journals that have 500 lines or more. In addition, it can currently process only general journals where the **Ledger** account type is set on the journal lines. Other account types on journal lines, such as **Customer**, **Vendor**, and **Bank**, aren't currently supported. This service won't be invoked when derived dimensions are set up in the system.

The Financial dimension service provides improved performance when journals are imported by using a new service that runs in parallel to the data import. It runs only on the main account and financial dimension data in the journal, and it generates the dimension combinations that are specified in the ledger account string field on the journal lines. The processing converts this string into the structured data storage that the Financial dimension framework uses throughout the rest of the product for validation, summary reporting, and inquiries. For more information about summary reporting of financial dimension data, see [Financial dimension sets](financial-dimension-sets.md).

For more information, see the following topics:

- [Define financial dimensions](tasks/define-financial-dimensions.md)
- [Maintain financial dimension default templates](tasks/maintain-financial-dimension-default-templates.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
