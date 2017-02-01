---
# required metadata

title: Financial report components | Microsoft Docs
description: This article describes how the components, or building blocks, of report definitions are used in financial reporting. These building blocks include row definitions, column definitions, and reporting tree definitions. The article explains how to organize and lock building blocks, and how to work with building block groups. 
author: RobinARH
manager: AnnBe
ms.date: 2016-03-07 18:54:02
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: FinancialReports
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: RobinARH
ms.suite: Released- Dynamics AX application 7.0.1
# ms.tgt_pltfrm: 
ms.custom: 59071
ms.assetid: 7112a149-c030-4acb-9208-a1c0e05d18b8
ms.region: Global
# ms.industry: 
ms.author: aolson

---

# Financial report components

This article describes how the components, or building blocks, of report definitions are used in financial reporting. These building blocks include row definitions, column definitions, and reporting tree definitions. The article explains how to organize and lock building blocks, and how to work with building block groups. 

The design philosophy behind financial report designer is to break information down into the smallest component or building block, and then mix and match the components as required. Therefore, your report formatting is separate from your financial data, and you can change the design of a report without modifying the financial data in your Microsoft Dynamics ERP system. By using this building block approach, you can combine text, amounts, and calculations to produce the reports that you require. Additionally, this flexibility encourages creativity by making it easy for you to view your operations in different ways. The individual building blocks of a report definition are similar to a three-dimensional spreadsheet, but they have more power. A report definition specifies the row definition, column definition, and optional reporting tree definition that should be used for the report. It also includes information about where to store the report that is generated and how to format it. For better reusability and sharing, you can create a building block group, which is a collection of existing report definitions, row definitions, column definitions, reporting tree definitions, and dimension sets that are associated with a company in.

## Building blocks of a report
| Building block            | Description                                                                                                                                                                                                                                                                              | For more information                                                                                                 |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Row definition            | A row definition defines the descriptive lines (for example, salaries or sales) on a report. It also lists the segment values or dimensions that contain the values for each line item, and includes row formatting and calculations.                                                    | [Row definitions](http://ax.help.dynamics.com/en/wiki/row-definitions-in-management-reporter/)                       |
| Column definition         | A column definition defines the period to use when data is extracted from the financial dimensions. It also includes column formatting and calculations.                                                                                                                                 | [Column definitions](http://ax.help.dynamics.com/en/wiki/column-definitions-in-management-reporter-reports/)         |
| Reporting tree definition | A reporting tree definition resembles an organizational chart. It contains individual reporting units that represent each box in the chart. The units can be either individual departments from the financial data or higher-level units that summarize data from other reporting units. | [Reporting tree definitions](http://ax.help.dynamics.com/en/wiki/reporting-tree-definitions-in-management-reporter/) |
| Report definition         | A report definition uses a row definition, a column definition, and an optional reporting tree definition to build a report. It also provides additional options and settings that you can use to customize a report.                                                                    | [Report definition](http://ax.help.dynamics.com/en/wiki/report-definitions-in-management-reporter/)                  |

If you're new to designing reports, you might find want to use the report wizard to quickly create a report definition that you can customize later. If you have experience with designing reports and want more flexibility for report design, you can combine new or existing building blocks to create a new report definition. You don't have to fully understand all the available report definition options to produce quality reports. As you become familiar with designing reports, you can expand your report definitions to take advantage of more advanced features. After you've created a basic report, you can customize the report definition and any of the building blocks in the report definition.

## Organize the building blocks
Use folders to organize your building blocks in Report Designer. All folders are specific to the type of building block that they contain. For example, all folders that contain row definitions are located in the **Row Definitions** pane in Report Designer.

### Create a folder

1.  In Report Designer, select the type of building block to organize in the navigation pane. For example, to sort a row definition, click **Row Definitions**.
2.  In the navigation pane, select the existing folder to create the new folder under, and then follow one of these steps:
    -   Right-click the parent folder, and then click **New Folder**.
    -   Select the parent folder, click **File**, and then click **New Folder**.

3.  When the new folder appears, enter the name of the new folder, and then press Enter.

## Lock a building block
You can create a password to lock and help protect a building block. In this way you can add a level of security to a report component without securing the whole system. A password can help protect building block information that is important to your month-end reporting process. A user in any role can lock a building block. However, other users always have read-only access to a locked component. Users can open, change, and save the locked component under a new name. A user who has the role of administrator can always access and change a locked building block.
1.  In Report Designer, open the report component to lock, such as a row definition, column definition, report definition, or reporting tree definition.
2.  On the **Tools** menu, click **Protect/Unprotect**. You can also click **Protect/Unprotect** (the lock icon) on the toolbar.
3.  In the **Protect** dialog box, enter and confirm a password, and then click **OK**. The lock icon on the toolbar is highlighted when an open building block is locked.

To unlock a locked building block, open the building block, and then click **Protect/Unprotect** on the toolbar. Alternatively, on the **Tools** menu, click **Unprotect**.
Building block groups
---------------------

Building blocks are the row definitions, column definitions, reporting tree definitions, and report definitions that you create for a report. Building block groups are collections of the definitions and dimension sets that are associated with a company. Building block groups can be company-specific, or several companies can share the same set of building blocks. If some of your companies have a different chart of accounts, you might want to use a different building block group for each company. Alternatively, you might want to name all your individual building blocks to reflect the company that they are compatible with.
### Create a building block group

1.  In Report Designer, on the **Company** menu, click **Building block groups**.
2.  In the **Building block groups** dialog box, click **New**.
3.  Enter a unique name and description for the building block group. Each field can contain a maximum of 256 characters. (This number includes spaces.)
4.  Click **OK** to create the new building block group.

### Assign a building block group

After you a create block group, you must assign it to at least one company. You can then create report, row, column, and reporting tree definitions, and save them in the building block group. You must close all building blocks before you start the following procedure.
1.  In Report Designer, on the **Company** menu, click **Companies**.
2.  In the **Companies** dialog box, select the company to assign a building block group to.
3.  Click **Modify**.
4.  In the **Modify Company** dialog box, in the **Building block group** field, select the building block group to assign to the company, or click **New** to create a new building block group.
5.  Click **OK** to assign the building block group.
6.  Click **Close** to close the **Companies** dialog box. The building block group that you selected is now assigned to the company. Now, all new row definitions, column definitions, and so on, that are created will be part of the building block group that is assigned to this company. You can also import a .tdbx file or report from another system.

### View a building block group

After a building block group has been created and is being used, you can view all the building blocks that are assigned to it. You can also export or import a building block group, and perform additional maintenance on building block groups.
1.  In Report Designer, on the **Company** menu, click **Building Block Groups**.
2.  In the **Building Block Groups** dialog box, select the building block to view.
3.  Click **View** to open the **View Building Block Group** dialog box, where you can view the contents of the building block group.
4.  Click **Close** to close the dialog boxes.

### Save a building block group under a new name

You can save an existing building block group under a new name. You can then modify the new building block group without changing the original building block group.
1.  In Report Designer, on the **Company** menu, click **Building Block Groups**.
2.  In the **Building Block Groups** dialog box, select the building block group to save under a new name.
3.  Click **Save As**.
4.  Enter a new name and description for the building block group.
5.  Click **OK**. The new building block group appears in the **Building Block Groups** dialog box.

### Export a building block group

You can export a building block group or specific report building blocks in a building block group. You can use the exported building block group as a backup. You can also copy the exported data between building block groups or Dynamics AX installations. Report designer includes the referenced font styles and dimension sets together with the building block group.
1.  In Report Designer, on the **Company** menu, click **Building Block Groups**.
2.  In the **Building Block Groups** dialog box, select the building block group to export, and then click **Export**.
3.  In the **Export** dialog box, select the report definitions to export:
    -   To export all your report definitions and the associated building blocks, click **Select All**.
    -   To export specific reports, rows, columns, trees, or dimension sets, click the appropriate tab, and then select the items to export. Press and hold the Ctrl key to select multiple items on a tab. **Note:** When you select reports to export, the associated rows, columns, trees, and dimension sets are selected.

4.  When you've finished selecting items to export, click **Export**.
5.  In the **Save As** dialog box, select a location to export the building block group to.
6.  In the **File Name** field, enter a name for the file. Report designer automatically adds a .tdbx file name extension.
7.  Click **Save**. The building block group is saved to the location that you specified.

### Import a building block group

You can import a building block group into an existing building block group, or you can create a new building block group for the data. All imported building block groups retain their original font styles and company references, and include the relevant dimension sets.
1.  In Report Designer, on the **Company** menu, click **Building Block Groups**.
2.  In the **Building Block Groups** dialog box, select the building block to import a building block group into, and then click **Import**.
3.  In the **Open** dialog box, select the building block group to import, and then click **Open**.
4.  In the **Import** dialog box, select the report definitions to import:
    -   To import all the report definitions and the supporting building blocks, click **Select All**.
    -   To import specific reports, rows, columns, trees, or dimension sets, select the reports, rows, columns, trees, or dimension sets to import.

5.  When you've finished selecting items to import, click **Import**.

### Undo a checkout of a building block

When you open a building block, other users have read-only access that building block. Sometimes, users forget to close a building block, or they shut down their system without closing the building block. Therefore, the building block remains checked out, and no other users can open it. In these situations, a financial reporting administrator can use the **Checked Out Items** dialog box to check in building blocks that users have left checked out. **Note:** You must have the role of administrator to check in building blocks by using the **Checked Out Items** dialog box.
1.  In Report Designer, on the **Tools** menu, click **Checked Out Items**.
2.  In the **Checked Out Items** dialog box, select **Show items from all users**. The list is updated to display all building blocks that are checked out and the users who have checked them out.
3.  Select a building block, and then click **Undo Checkout**.
4.  Click **Yes** to check in the building block.



See also
--------

[Financial reporting for Microsoft Dynamics ERP](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics-bi-reporting/management-reporter-for-microsoft-dynamics-erp)

