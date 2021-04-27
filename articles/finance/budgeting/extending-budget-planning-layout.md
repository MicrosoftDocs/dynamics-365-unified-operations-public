---
# required metadata

title: Extend the budget planning layout
description: This topic explains how to extend the number of columns in the BudgetPlanLineActiveView table to accommodate additional data in the budget plan layout.
author: panolte
ms.date: 07/24/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Developer
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: panolte
ms.search.validFrom: 2019-07-31 
ms.dyn365.ops.version: 10.0.4
---

# Extend the budget planning layout

[!include [banner](../includes/banner.md)]

This topic describes the process for extending the number of columns in the BudgetPlanLineActiveView table to accommodate additional data in the budget plan layout. This process might be required if you're comparing information over multiple years, if many scenarios are being evaluated, or if weekly or daily periods are being evaluated. This topic was written for a developer audience.

- **BudgetPlanLineActiveView table** – This table contains the pivoted budget planning data. Out of the box, it contains 36 monetary columns and 36 quantity columns. This default configuration lets users manipulate the budget plan layout so that they can show and compare up to three years of monthly planning data.
- **BudgetPlanWorksheetEntity entity** – This entity is a counterpart of the BudgetPlanLineActiveView table and serves as a data source for the Microsoft Excel worksheet. The columns in this entity map to the columns in the BudgetPlanLineActiveView table. Any changes in the table must be replicated in the entity.

## Extend the columns in the BudgetPlanLineActiveView table

You can extend the columns in the BudgetPlanLineActiveView table by using a four-step process. After you complete these steps, you must build the project and validate your changes. 

### Step 1: Add columns to the BudgetPlanLineActiveView table

You begin the process by creating a new extension, adding fields, and setting the data type for the fields that you add.

1. Open Microsoft Visual Studio
2. Open Application explorer.
3. Create an extension on the **BudgetPlanLineActiveView** table to a new project.
4. Open the table in designer mode. 
5. Right-click **Fields**, and then select **New \> Real**.
6. Name the field by using the next available name, where the suffix is incremented (for example, **TransactionCurrencyAmount37**).
7. Set the extended data type to **BudgetPlanCurrencyAmount**.
8. Right-click **Fields**, and then select **New \> Real**.
9. Name the field by using the next available name, where the suffix is incremented (for example, **Quantity37**).
10. Set the extended data type to **BudgetPlanQuantity**.
11. Repeat steps 5 through 10 for all the additional columns of each extended data type that you require.
12. Optional: Add the monetary columns added to the **Monetary** field group quantity columns to the **Quantity** field group.

### Step 2: Add columns to the BudgetPlanWorksheetEntity entity

To add columns to the BudgetPlanWorksheetEntity entity, follow these follow steps.

1. Create an extension on the **BudgetPlanWorksheetEntity** entity to the existing project.
2. Open the entity extension in designer mode.
3. Drag the columns from the data sources node into the fields node.

### Step 3: Create an extension for the BudgetPlan form

To update the **BudgetPlan** form so that it includes the new columns, follow these steps.

1. Create an extension on the **BudgetPlan** form.
2. Replicate any events or customizations in a new event handler that exists on the **TransactionCurrencyAmount**, or **Quantity** fields, onto the new fields. The following example shows the standard events that currently exist for both **CurrencyAmount** and **Quantity**. These events must be created for anything beyond the original 36 **CurrencyAmount** and **Quantity** values.

    ```xpp
    [FormDataFieldEventHandler(formDataFieldStr(BudgetPlan, BudgetPlanLineActiveView, TransactionCurrencyAmount37), FormDataFieldEventType::Modified)]
    publicstaticvoid transactionCurrencyAmount37\_OnModified(FormDataObject \_sender, FormDataFieldEventArgs \_e)
    {
        Object budgetPlanLineActiveView\_ds = \_sender.datasource() asFormDataSource;
        budgetPlanLineActiveView\_ds.updateTransactionCurrencyAmount(fieldNum(BudgetPlanLineActiveView, TransactionCurrencyAmount37));
    }
    [FormDataFieldEventHandler(formDataFieldStr(BudgetPlan, BudgetPlanLineActiveView, Quantity37), FormDataFieldEventType::Modified)]
    publicstaticvoid quantity37\_OnModified(FormDataObject \_sender, FormDataFieldEventArgs \_e)
    {
        Object budgetPlanLineActiveView\_ds = \_sender.datasource() asFormDataSource;
        budgetPlanLineActiveView\_ds.updateQuantity(fieldNum(BudgetPlanLineActiveView, Quantity37));
    }
    ```

3. Verify that a modified event handler exists for every copy that you've created of a **TransactionCurrencyAmount** or **Quantity** column.
4. In the search fields above the form designer, enter **LineViewLinesGrid**, find the node, and expand it. 

    Cancel the search by selecting the **X** at the end of the search field. The lines view grid will remain expanded and in view.

5. Drag all the new columns that you added onto **LineViewLinesGrid** (the grid).
6. Rename the new fields so that they follow the existing naming pattern (for example, **TransactionCurrencyAmount37** and **Quantity37**).
7. Reorder the fields so that they are in order for **Quantity** and **TransactionCurrencyAmounts**.
8. Save your changes.

### Step 4: Update the BudgetPlanLineFieldActiveViewMapping class via a delegate

To extend the mapping between the BudgetPlanLineActiveView and BudgetPlanLine tables, follow this step.

- Create a new class, and paste in the event handler method from the **gettingBudgetPlanLineFieldName** delegate. There should be a statement for each **TransactionCurrencyAmount** and **Quantity** field that you extended.

    ```xpp
    [SubscribesTo(classStr(BudgetPlanLineFieldActiveViewMapping), staticDelegateStr(BudgetPlanLineFieldActiveViewMapping, gettingBudgetPlanLineFieldName))]
    publicstaticvoid BudgetPlanLineFieldActiveViewMapping\_gettingBudgetPlanLineFieldName(FieldName \_budgetPlanLineActiveViewFieldName, EventHandlerResult \_result)
    {
        FieldName budgetPlanLineFieldName;
        switch (\_budgetPlanLineActiveViewFieldName)
        {
            case
                fieldStr(BudgetPlanLineActiveView, TransactionCurrencyAmount37), fieldStr(BudgetPlanLineActiveView, TransactionCurrencyAmount38):
                budgetPlanLineFieldName = fieldStr(BudgetPlanLine, TransactionCurrencyAmount);
                break;
            case
                fieldStr(BudgetPlanLineActiveView, Quantity37), fieldStr(BudgetPlanLineActiveView, Quantity38):
                budgetPlanLineFieldName = fieldStr(BudgetPlanLine, Quantity);
                break;
        }
        \_result.result(budgetPlanLineFieldName);
    }
    ```

## Build the project

Build your project, and synchronize the database.

## Validate your changes

To validate your changes, you must create a layout in budget planning beyond 36 monetary and/or quantity columns. If you completed all the steps correctly, you should be able to enter a value in every column, save the value, and edit it in Excel.

After the changes are verified, the extension can be published and promoted beyond the local development environment. 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]