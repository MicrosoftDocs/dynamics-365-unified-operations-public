---
# required metadata

title: Budget planning templates for Excel
description: This topic describes how to create Microsoft Excel templates that can be used with budget plans.
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2231
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 261794
ms.assetid: 1d8e99c1-b70d-41ba-991e-ab50b16797e0
ms.search.region: Global
# ms.search.industry: 
ms.author: sigitac
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Budget planning templates for Excel

[!include[banner](../includes/banner.md)]


This topic describes how to create Microsoft Excel templates that can be used with budget plans.

This topic shows how to create Excel templates that will be used with budget plans using the standard demo data set and the Admin user login. For more information about budget planning, see [Budget planning overview.](budget-planning-overview-configuration.md) 
You can also follow the [Budget planning 101](budget-plan.md) tutorial to learn basic module configuration and usage principles.

## Generate a worksheet using budget plan document layout
Budget plan documents can be viewed and edited using one or more layouts. Each layout can have an associated budget plan document template to view and edit the budget plan data in an Excel worksheet. In this topic, a budget plan document template will be generated using an existing layout configuration. Open the **Budget plans list** (**Budgeting**&gt; **Budget plans**). Click **New** to create a new budget plan document. [![bpt1](./media/bpt11-1024x552.png)](./media/bpt11.png) 

Use the **Add** line option to add lines. Click **Layouts** to view the budget plan document layout configuration. 
[![bpt2](./media/bpt2-1024x274.png)](./media/bpt2.png) 

You can review the layout configuration and adjust it as needed. Go to **Template** &gt; **Generate** to create an Excel file for this layout. After the template is generated, go to **Template** &gt; **View** to open and review the budget plan document template. You can save the Excel file to your local drive. [![bpt3](./media/bpt3-1024x545.png)](./media/bpt3.png) 

> [!NOTE] 
> The Budget plan document layout cannot be edited after an Excel template is associated with it. To modify the layout, delete the associated Excel template file and regenerate it. This is required to keep the fields in the layout and the worksheet synchronized. 

The Excel template will contain all of the elements from the budget plan document layout, where the **Available in Worksheet** column is set to True. Overlapping elements are not allowed in the Excel template. For example, if the layout contains Request Q1, Request Q2, Request Q3, and Request Q4 columns, and a total request column that represents a sum of all 4 quarterly columns, only the quarterly columns or total column is available to be used in the Excel template. The Excel file cannot update overlapping columns during the update because data in the table could become out of date and inaccurate.

[![bpt4](./media/bpt4-1024x615.png)](./media/bpt4.png)

> [!NOTE] 
> To avoid potential issues with viewing and editing budget plan data using Excel, the same user should be logged into both Microsoft Dynamics 365 for Finance and Operations, Enterprise edition and the Microsoft Dynamics Office Add-in Data Connector.

## Add a header to budget plan document template
To add header information, select the top row in the Excel file and insert empty rows. Click **Design** in the **Data Connector** to add header fields to the Excel file.

[![bpt5](./media/bpt5-1024x615.png)](./media/bpt5.png) 

In the **Design** tab,** **click **Add** fields, and then select **BudgetPlanHeader** as the entity data source.

[![bpt6](./media/bpt6-1024x615.png)](./media/bpt6.png)

Point the cursor to the desired location in the Excel file. Click **Add label** to add the field label to the selected location. Select **Add Value** to add the value field to the selected place. Click **Done** to close the designer.

## [![bpt7](./media/bpt7.png)](./media/bpt7.png)

Add a calculated column to budget plan document template table
--------------------------------------------------------------

Next, calculated columns will be added to generated budget plan document template. A **Total request** column, which summarizes Request Q1: Request Q4 columns, and an **Adjustment** column, which recalculates the **Total Request** column by a predefined factor.

Click **Design** in the **Data connector** to add columns to the table. Click **Edit** next to **BudgetPlanWorksheet** data source to start adding columns.

[![bpt8](./media/bpt8-1024x301.png)](./media/bpt8.png) 

The selected field group displays the columns that are available in the template. Click **Formula** to add a new column. Name the new column and then paste the formula into the **Formula** field. Click **Update** to insert the column.

[![bpt12](./media/bpt12-1024x565.png)](./media/bpt12.png)

> [!NOTE] 
> To define the formula, create the formula in the spreadsheet, and then copy it to the **Design** window. A Finance and Operations bound table will typically be named "AXTable1". For example, to summarize Request Q1 : Request Q4 columns in the spreadsheet, the formula = AxTable1\[Request Q1\]+AxTable1\[Request Q2\]+AxTable1\[Request Q3\]+AxTable1\[Request Q4\].

Repeat these steps to insert the **Adjustment** column. Use formula = AxTable1\[Total request\]\*$I$1 for this column. This will take the value in cell I1 and multiply the values in the **Total request** column to calculate adjustment amounts.

Save and close the Excel file. Return to Finance and Operations, and in **Layouts**, click **Template &gt; Upload** to upload the saved Excel template to be used for the budget plan. 

[![bpt10](./media/bpt10-1024x352.png)](./media/bpt10.png) 

Close the **Layouts** slider. In **Budget plan** document, click **Worksheet** to view and edit the document in Excel. Note that the adjusted Excel template was used to create this budget plan worksheet and calculated columns are updated using the formulas that were defined in the previous steps. 

[![bpt11](./media/bpt111-1024x431.png)](./media/bpt111.png)

## Tips & tricks for creating budget plan templates
### Can I add and use additional data sources to a budget plan template?

Yes, you can use the **Design** menu to add additional entities to the same or other sheets in the Excel template. For example, you can add the **BudgetPlanProposedProject** data source to create and maintain a list of proposed projects at the same time when working with budget plan data in Excel. Note that including high-volume data sources might impact performance of the Excel workbook. 

You can use the **Filter** option in the **Data Connector** to add desired filters to additional data sources.

### Can I hide the Design option in the Data connector for other users?

Yes, open the **Data Connector** options to hide the **Design** option from other users.

[![bpt13](./media/bpt13-1024x565.png)](./media/bpt13.png)

Expand **Data connector options** and clear the **Enable design** check box. This will hide the **Design** option from the **Data connector**.

[![bpt14](./media/bpt14-1024x592.png)](./media/bpt14.png)

### Can I prevent users from accidently closing the Data connector while working with data?

We recommend locking the template to prevent users from closing it. To turn on the lock, click the **Data connector**, in the top right corner an arrow appears. 

[![bpt15](./media/bpt15-1024x285.png)](./media/bpt15.png) 

Click the arrow for an additional menu. Select **Lock**.

### [![bpt16](./media/bpt16-1024x614.png)](./media/bpt16.png)

### Can I use other Excel features, like cell formatting, colors, conditional formatting, and charts with my budget plan templates?

Yes, most of the standard Excel capabilities will work in budget plan templates. We recommend using color-coding for users to distinguish between read-only and editable columns. Conditional formatting can be used to highlight problematic areas of the budget. Column totals can easily be presented by using standard Excel formulas above the table.

You can also create and use pivot tables and charts for additional groupings and visualizations of budget data. On the **Data** tab, in the **Connections** group, click **Refresh All**, and then click **Connection Properties**. Click the **Usage** tab. Under **Refresh**, select the **Refresh data when opening the file** check box. 

[![bpt17](./media/bpt17-1024x614.png)](./media/bpt17.png)



