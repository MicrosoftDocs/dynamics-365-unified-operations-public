Overview

This article describes how to extend the number of columns in the BudgetPlanLineActiveView table to accommodate additional data in the budget plan layout. These steps may be necessary if multiple years are being compared, the number of scenarios being evaluated are very large, or weekly or daily periods are being evaluated. This is written from a developer audience perspective.

**BudgetPlanLineActiveView table** - The BudgetPlanLineActiveView table contains the pivoted budget planning data. Out of box, this table contains 36 monetary columns and 36 quantity columns. This default configuration enables the user to manipulate the budget plan layout to display and compare up to 3 years of monthly planning data.

**BudgetPlanWorksheetEntity entity** - The BudgetPlanWorksheetEntity entity is a counterpart of the BudgetPlanLineActiveView and serves as a datasource for the Excel worksheet. The columns in this entity, map to the columns in the BudgetPlanLineActiveView table. Any changes that happen to the table must also be replicated in the entity.

**Extending the columns on BudgetPlanLineActiveView**

**Step 1: Add columns to BudgetPlanLineActiveView table**

  1. Open Visual Studio
  2. Open Application explorer.
  3. Create a new extension on BudgetPlanLineActiveView to a new project.
  4. Open the table in designer mode. (Right-click -\&gt; Open).
  5. Right click on Fields and select New -\&gt; Real
  6. Name the field with the next available name with the suffix incremented. Example: TransactionCurrencyAmount37.
  7. Set the Extended Data type to BudgetPlanCurrencyAmount
  8. Right click on Fields and select New - \&gt; Real
  9. Name the field with the next available name with the suffix incremented. Example: Quantity37. Set the extended data type to BudgetPlanQuantity.
  10. Repeat steps 5 through 8 for as many columns required of each type.
  11. Optionally, add the monetary columns added to the Monetary field group quantity columns  to the Quantity field group.

**Extending the columns on BudgetPlanLineActiveView**

**Step 2: Add columns to BudgetPlanWorksheetEntity entity**

To add columns to the BudgetPlanWorksheetEntity entity, follow the steps below:

  1. Create an extension on  BudgetPlanWorksheetEntity to the existing project
  2. Open the entity extension in designer mode
  3. Drag and drop the columns from the data sources node into the fields node.



**Extending the BudgetPlan form**

**Step 3: Creating an extension for the BudgetPlan form**

To update the BudgetPlan form with the new columns, follow the steps below:

  1. Create an extension on the  BudgetPlan form
  2. Replicate any events/customizations in a new event handler that exist on the TransactionCurrencyAmount or Quantity fields onto the new fields. Below are the events for both CurrencyAmount and Quantity that are standard as of the when this document was authored. These events will be need to be created for anything beyond the original 36 CurrencyAmount and Quantity values.

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


  3.  Before finishing, verify that a modified event handler exists for every TransactionCurrencyAmount or Quantity column copy you&#39;ve created.


  4. Type &#39;LineViewLinesGrid&#39; in the search window above the form designer and expand the node once found. See figure 4 below.

Cancel search by clicking the &#39;x&#39; at the end of the search window. The lines view grid will remain expanded and in view.

  5. Drag and drop all the new columns added onto the LineViewLinesGrid (grid).
  6. Rename the new fields to follow the existing pattern for example TransactionCurrencyAmount37 and Quantity37.
  7. Reorder the fields so they are in order for quantity and TransactionCurrencyAmounts
  8. Save the changes.

**Extending the columns on BudgetPlanLineFieldActiveViewMapping**

**Step 4: Update the BudgetPlanLineFieldActiveViewMapping class via a Delegate**

To extend the mapping between the BudgetPlanLineActiveView and BudgetPlanLine tables, follow the steps below:

Create a new class and paste in the event handler method from the gettingBudgetPlanLineFieldName delegate. There should be a statement for each of the TransactionCurrencyAmount and Quantity fields you extended.

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

**Build and Synchronize**

Synchronize your database and build your project.

**Validation**

To validate, you&#39;ll need to create a layout in budget planning beyond 36 monetary and/or quantity columns. If everything was done correctly you should be able to enter a value in every column, save the value, and edit the value in Excel as well.
