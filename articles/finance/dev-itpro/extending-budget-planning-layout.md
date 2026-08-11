---
title: Extend the budget planning layout
description: This article explains how to extend the number of columns in the BudgetPlanLineActiveView table to accommodate additional data in the budget plan layout.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/06/2026
ms.custom:
ms.reviewer: twheeloc
audience: Developer
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
ms.search.validFrom: 2019-07-31
ms.search.form:
ms.dyn365.ops.version: 10.0.4
---

# Extend the budget planning layout

[!include [banner](../includes/banner.md)]

This article describes the process for extending the number of columns in the BudgetPlanLineActiveView table to accommodate extra data in the budget plan layout. You might need this process if you're comparing information over multiple years, if you're evaluating many scenarios, or if you're evaluating weekly or daily periods. This article is written for a developer audience.

- **BudgetPlanLineActiveView table** – This table contains the pivoted budget planning data. By default, it contains 36 monetary columns and 36 quantity columns. This default configuration lets users manipulate the budget plan layout so that they can show and compare up to three years of monthly planning data.
- **BudgetPlanWorksheetEntity entity** – This entity is a counterpart of the BudgetPlanLineActiveView table and serves as a data source for the Microsoft Excel worksheet. The columns in this entity map to the columns in the BudgetPlanLineActiveView table. You must replicate any changes in the table to the entity.

## Extend the columns in the BudgetPlanLineActiveView table

You can extend the columns in the BudgetPlanLineActiveView table by using a four-step process. After you complete these steps, you must build the project and validate your changes.

### Step 1: Add columns to the BudgetPlanLineActiveView table

Create a new extension, add fields, and set the data type for the fields that you add.

1. Open Microsoft Visual Studio.
1. Open Application Explorer.
1. Create an extension on the **BudgetPlanLineActiveView** table in a new project.
1. Open the table in designer mode.
1. Right-click **Fields**, and then select **New \> Real**.
1. Name the field by using the next available name, where the suffix is incremented (for example, **TransactionCurrencyAmount37**).
1. Set the extended data type to **BudgetPlanCurrencyAmount**.
1. Right-click **Fields**, and then select **New \> Real**.
1. Name the field by using the next available name, where the suffix is incremented (for example, **Quantity37**).
1. Set the extended data type to **BudgetPlanQuantity**.
1. Repeat steps 5 through 10 for all the extra columns of each extended data type that you require.
1. (Optional) Add the monetary columns to the **Monetary** field group and add the quantity columns to the **Quantity** field group.

### Step 2: Add columns to the BudgetPlanWorksheetEntity entity

To add columns to the BudgetPlanWorksheetEntity entity, follow these steps:

1. Add an extension for the **BudgetPlanWorksheetEntity** entity to the existing project.
1. Open the entity extension in designer mode.
1. Drag the columns from the data sources node into the fields node.

### Step 3: Create an extension for the BudgetPlan form

To update the **BudgetPlan** form so that it includes the new columns, follow these steps:

1. Add an extension for the **BudgetPlan** form.
1. Replicate any events or customizations in a new event handler that exists on the **TransactionCurrencyAmount** or **Quantity** fields, onto the new fields. The following example shows the standard events that currently exist for both **CurrencyAmount** and **Quantity**. You must create these events for anything beyond the original 36 **CurrencyAmount** and **Quantity** values.

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

1. Verify that a modified event handler exists for every copy that you created of a **TransactionCurrencyAmount** or **Quantity** column.
1. In the search fields above the form designer, enter **LineViewLinesGrid**, find the node, and expand it.

    Cancel the search by selecting the **X** at the end of the search field. The lines view grid remains expanded and in view.

1. Drag all the new columns that you added onto **LineViewLinesGrid** (the grid).
1. Rename the new fields so that they follow the existing naming pattern (for example, **TransactionCurrencyAmount37** and **Quantity37**).
1. Reorder the fields so that they are in order for **Quantity** and **TransactionCurrencyAmounts**.
1. Save your changes.

### Step 4: Update the BudgetPlanLineFieldActiveViewMapping class by using a delegate

To extend the mapping between the BudgetPlanLineActiveView and BudgetPlanLine tables, follow this step.

- Create a new class, and paste the event handler method from the **gettingBudgetPlanLineFieldName** delegate. Include a statement for each **TransactionCurrencyAmount** and **Quantity** field that you extended.

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

To validate your changes, create a layout in budget planning with more than 36 monetary and quantity columns. If you completed all the steps correctly, you can enter a value in every column, save the value, and edit it in Excel.

After you verify the changes, you can publish and promote the extension beyond the local development environment.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
