---
# required metadata

title: Financial dimensions
description: This topic describes the various types of financial dimensions and how they are set up.
author: aprilolson
manager: AnnBe
ms.date: 08/24/2017
ms.topic: article
ems.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: DimensionDetails, DimensionValueDetails, SysTranslationDetail
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 25871
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Financial dimensions

[!include [banner](../includes/banner.md)]

This topic explains the various types of financial dimensions and how they are set up.

Use the **Financial dimensions** page to create financial dimensions that you can use as account segments for charts of accounts. There are two types of financial dimensions: custom dimensions and entity-backed dimensions. Custom dimensions are shared across legal entities, and the values are entered and maintained by users. For entity-backed dimensions, the values are defined somewhere else in the system, such as Customers or Stores entities. Some entity-backed dimensions are shared across legal entities, whereas other entity-backed dimensions are company-specific. 

After you've created the financial dimensions, use the **Financial dimension values** page to assign additional properties to each financial dimension. 

You can use financial dimensions to represent legal entities. You don't have to create the legal entities in Microsoft Dynamics 365 for Finance and Operations. However, financial dimensions aren’t designed to address the operational or business requirements of legal entities. The interunit accounting functionality in Finance and Operations is designed to address only the accounting entries that are created by each transaction. 

Before you set up financial dimensions as legal entities, evaluate your business processes in the following areas to determine whether this setup will work for your organization:

- Inventory
- Sales and purchases between financial dimensions and legal entities
- Sales tax calculation and reporting
- Operational reporting

Here are some of the limitations:

- You can use sales tax functionality only with legal entities, not with financial dimensions.
- Some reports don't include financial dimensions. Therefore, to report by financial dimension, you might have to modify the reports.

## Custom dimensions

To create a user-defined financial dimension, in the **Use values from** field, select **&lt; Custom dimension &gt;**. You can also specify an account mask to limit the amount and type of information that you can enter for dimension values. You can enter characters that remain the same for each dimension value, such as letters or a hyphen (-). You can also enter number signs (\#) and ampersands (&) as placeholders for letters and numbers that will change every time that a dimension value is created. Use a number sign (\#) as a placeholder for a number and an ampersand (&) as a placeholder for a letter. The field for the format mask is available only when you select **&lt; Custom dimension &gt;** in the **Use values from** field.

**Example**

To limit the dimension value to the letters "CC" and three numbers, enter **CC-\#\#\#** as the format mask.

## Entity-backed dimensions

To create an entity-backed financial dimension, in the **Use values from** field, select a system-defined entity to base the financial dimension on. Financial dimension values are then created from that entity. For example, to create dimension values for projects, select **Projects**. A dimension value is then created for each project name. The **Financial dimension values** page shows the values for the entity. If those values are company-specific, the page also shows the company.

## Activating dimensions

When you activate a financial dimension, the table is updated so that it includes the name of the financial dimension. Deleted dimensions are removed. You can enter dimension values before you activate a financial dimension. However, a financial dimension can't be consumed anywhere until it's activated. For example, you can't add a financial dimension to an account structure until the financial dimension has been activated. When you click **Activate**, all dimensions are updated and show status changes. 

## Translations

On the **Text translation** page, you can enter text for the selected financial dimension in various languages. On the **Main account translation** page, you can enter text for the main account in various languages. 

## Legal entity overrides

Not all dimensions are valid for all legal entities. Additionally, some dimensions might be relevant only for a specific period. In these cases, you can use the **Legal entity overrides** section to specify the companies that the dimension should be suspended for, the owner, and the period when the dimension is active.

## Deleting financial dimensions

To help maintain referential integrity of the data, financial dimensions can rarely be deleted. If you try to delete a financial dimension, the following criteria are evaluated:

- Has the financial dimension been used on any posted or unposted transactions, or any type of dimension value combination?
- Is the financial dimension used in any active account structure, advanced rule structure, or financial dimension set?
- Is the financial dimension part of a default financial dimension integration format?
- Has the financial dimension been set up as a default dimension?

If any of the criteria are met, you can't delete the financial dimension.

## Defaulting dimensions

You can use values from master records such as customer and vendor to populate a new dimension. The dimension values for those master records will be populated with the master record ID when you create it. For example, when you create a new customer, the customer dimension will be populated with the customer ID. When you create sales orders, invoices or other documents that require a customer ID, the existing defaulting rules will be used and the customer ID will be added to the document. 

This feature is controlled by a setting in the dimension called "Copy values to this dimension on each new DimensionName created", where DimensionName is the name of the dimension. The feature is turned off by default and can be enabled at any time. If records already exist for the dimension, then the master records will be updated at the time that you enable the feature. Existing documents and transactions will not be updated.

## Derived dimension

You can configure a dimension so that other dimensions are populated when you enter that dimension into a document. For example, if you enter cost center 10, then the dimension for department is populated with the value 20 automatically.

You can set up the derived values from within the dimension form. 
1)  Select a dimension and then click on the Derived dimensions menu. 
2)  A new form will appear with the selected dimension segment as the first column. 
3)  Add the segments that you want to be derived. They will appear as columns. 

Enter the dimension combinations that will be derived from the dimension in the first column. For example, if you using cost center as the dimension from which the department and location will be derived, enter cost center 10, department 20, and location 30. When you enter cost center 10 into a master record or transaction page, department 20 and location 30 will default in.

The derived dimension process will not override existing values for derived dimensions. For example, if you enter cost center 10 and no other dimension is populated, then it will default department with 20 and location with 30. However, if you change the cost center to something else, then it will not change the values that are already established. This enables you to establish defaults dimensions on master records that will not be changed by derived dimensions.

### Derived dimensions and entities

You can set up the derived dimensions segments and values using entities
1)  The Derived dimensions entity will set up the driving dimension and the segments that will be used for those dimensions
2)  The DerivedDimensionValue entity allows you to import the values that will be derived for each driving dimension.

When you use an entity to import data and that entity imports dimensions, it will also apply the derived dimension rules during the import.

For more information, see the following topics:
- [Define financial dimensions](tasks/define-financial-dimensions.md)
- [Maintain financial dimension default templates](tasks/maintain-financial-dimension-default-templates.md)
