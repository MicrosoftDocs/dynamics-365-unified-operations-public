**Dimensions**

Dimensions are descriptors that define your fact data. The structure of a dimension is comprised of columns, that are referred to as attributes of the dimension. These columns can be used for creating hierarchical structures in your analysis. For example, a dimension may include the columns of date, month name and year. This would allow analyzation of data by drilling down from year, to month, to date. Common dimensions are people, product, places, and time.

There are two types of dimensions within planning; linked dimensions and standard dimensions. Linked dimensions are connected to Dataverse tables. Standard dimensions are non-dynamic dimensions that must be updated manually be either adding new rows or uploading new data via Excel.

Within Business process planning, dimensions can be created three ways:

1.  From the current environment (linked dimensions)
2.  From Excel
3.  Manually added

**Creating a dimension from current environment:**

When creating a new dimension, you can choose to create a dimension from an existing Dataverse table. This is referred to as a linked dimension. To create a new linked dimension in planning navigate to **‘Create dimension’ .**

**Name the dimension:** The dimension must have a name. Spaces and special characters can be used.

**Table Name:** This is the name of the table that will be created in Dataverse. This will also be the table name that is displayed in Power BI when working with the visuals.

**Select to add columns from the current environment.**  The current environment is the Power Platform environment in which planning was deployed. Once this is selected, the Linked table drop list becomes enabled. Note: Native Dataverse tables and enabled virtual entity tables will be displayed in the list. Learn more about enabling virtual entities here: [Enable Microsoft Dataverse virtual entities - Finance & Operations \| Dynamics 365 \| Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/enable-virtual-entities)

**Select the columns that you want to include in the dimension.** You can select which columns from the Dataverse table to include in the dimension. The selected columns will display in Power BI and can be used for sorting and filtering data in the planning visuals. For example, the **Account** table is selected for the dimension. There are multiple columns in that table that you may want to filter or sort data on. However, there are also columns that may not provide value to your analysing of data such as **Created by** or **Modified by**. Therefore, these columns have been automatically removed. Select the columns that you would like to include in the dimension.

**!important** – When creating a dimension, the dimension must have a primary key to ensure that there are unique records within the dimension table. To accomplish this, the planning application will automatically select the Primary column from the source table. The column that is used for the primary column is displayed at the top of the form in the Select Columns step of the wizard.

**!Note** – to select a column that you want included in the dimension, you must select the circle to the left of the column name. This doesn’t show by default until you hover to the left side of the column name.

![](media/b9cd3c03b7809cecf174bfee3f68cccd.png)

**Adjust columns**

You can adjust the column name for the columns that you have selected to include in the dimension. For example, you may have selected to include the Address 1: City column in the entity, but would like it display as City. You can adjust the column name to be City.

Once the information above has been entered, you can create the dimension.

**Creating a dimension from Excel**

When creating a new dimension, you can choose to create a dimension from an Excel file. To create a new dimension in Planning navigate to **‘Create dimension’ .**

**Name the dimension:** The dimension must have a name. Spaces and special characters can be used.

**Table Name:** This is the name of the table that will be created in Dataverse. This will also be the table name that is displayed in Power BI when working with the visuals.

**Select to add columns from Excel.**  Once this is selected, the **Upload an Excel** file option becomes enabled.

If your spreadsheet has multiple tabs, you can select which tab to use when creating the dimension.

**Select the columns that you want to include in the dimension.** You can select which columns from the Excel file to include in the dimension.

**!important** – When creating a dimension, the dimension must have a primary key to ensure that there are unique records within the dimension table. To accomplish this, please select the column that would ensure that the records are unique. The column that is used for the primary column is displayed at the top of the form in the **Select Columns** step of the wizard.

**!Note** – To select a column that you want included in the dimension, you must select the circle to the left of the column name. This doesn’t show by default until you hover to the left side of the column name.

![A screenshot of a computer Description automatically generated](media/b9cd3c03b7809cecf174bfee3f68cccd.png)

**Adjust columns**

You can adjust the column name for the columns that you have selected to include in the dimension. For example, you may have selected to include the Address 1: City column in the Excel sheet, but would like it display as City. You can adjust the column name to be City.

Once the information above has been entered, you can create the dimensions.

**Creating a dimension by Manually adding**

When creating a new dimension, you can choose to create a dimension manually. To create a new dimension in Planning navigate to **‘Create dimension’ .**

**Name the dimension:** The dimension must have a name. Spaces and special characters can be used.

**Table Name:** This is the name of the table that will be created in Dataverse. This will also be the table name that is displayed in Power BI when working with the visuals.

**Columns:** Enter the name of the columns that you want included in the dimension, separated by a comma.

**Select columns –**  This step in the wizard is skipped, as the columns that were entered are automatically selected for inclusion in the creation of the dimension.

**!important** – When creating a dimension, the dimension must have a primary key to ensure that there are unique records within the dimension table. To accomplish this, the planning application will automatically create a name column for manually created dimensions and use that as the primary column. The column that is used for the primary column is displayed at the top of the form in the Select Columns step of the wizard.

**Adjust columns**

This step in the wizard is skipped, as the display names of the column will be what was used when the dimension was created in the General section.

Once the information above has been entered, you can create the dimension.

**Maintaining dimensions**

After creating the dimensions, you may want to add more dimension values or add more columns to the dimension. You can take these actions from within the planning app or by using the Table Edit visual in Power BI or the Excel Add-in (Available after GA). Learn more about how to maintain dimensions in the Table Edit visual here.

The following actions can be taken on dimensions within the planning app:

Edit in Excel

Add a new column of data

Delete a column of data

Delete the dimension

**Edit data in Excel**

Users can add new rows of data to a dimension in the planning app by navigating to the Dimensions form and selecting **Edit data in Excel** . After selecting Edit in Excel, select to open the spreadsheet. Once, the spreadsheet is open, **Enable editing** must be selected.

When creating a new row, user will be able to add values for the columns within a row, except for the Source type and read only fields. If data was entered in read-only fields, the fields will be reset upon publish. Users can also edit a specific cell of data within the dimension, except for the Source Type value and read-only fields.

After adding or editing data, the user must choose to **publish** the data. If the user closes Excel before publishing the changes, the user will be prompted to save their changes.

After publishing changes from Excel, select refresh on the dimension table to see the updates to the dimension.

**Important!** For every dimension there is a **Source** column . The values can either be User or System. Rows with a source type of System will be updated with the values from the linked Dataverse table upon a refresh. Rows that were created via the Table edit visual in Power BI will have a source type of User and will not be overwritten with any data updates.

When creating a new row of data or editing a cell value, you must select to refresh your data in Power BI to view the additional dimension values, rows, or columns.

**Add a new column of data**

Users can add a new column of data to any dimension by navigating to the dimensions form and selecting **new column.** You will need to provide a name for the column, and the column will be added as the last column within the dimension. Note, if you add a new column to a linked dimension and populate the new column with data, the data will remain after refreshing the data.

New columns added to a dimension are saved automatically.

**Delete a column of data**

Users can delete a column of data within a dimension.

Important! When a column of data in a dimension is deleted, the cube will not be updated. However, the Power BI visuals may be impacted.

**Delete the dimension**

Users can delete a dimension that is not being used in a cube. Users can navigate to the Dimensions form and select the dimension in the left preview pane. Once the appropriate dimension is selected, select Delete.

**Important!** When a dimension is deleted, the cube will not be updated. However, the Power BI visuals may be impacted.
