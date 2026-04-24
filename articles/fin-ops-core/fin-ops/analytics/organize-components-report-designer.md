---
title: Organize report components in report designer
description: Learn about how to organize existing reports, building blocks, and objects in report designer, with an overview on renaming folders or building blocks.
author: aprilolson
ms.author: aolson
ms.topic: how-to
ms.date: 03/12/2026
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.search.form: FinancialReports
ms.dyn365.ops.version: Version 1611
ms.assetid: 32e728c5-3b06-4049-8070-ade01e951d49
---

# Organize report components in report designer

[!include [banner](../../../finance/includes/banner.md)]

After you design building blocks and generate reports, organize these objects so that users can easily locate them. This article explains how to organize existing reports, building blocks, and objects in report designer.

You can rename folders, reports, building blocks, and other objects in Report designer to help organize your files. Depending on the type of object that you rename, you might need to update associations with that object.

## Rename a folder or building block in Report designer

In Report designer, you can rename folders, report definitions, row definitions, column definitions, and reporting tree definitions.

### Rename a folder or building block in Report designer

1. In Report designer, use the navigation pane to locate the folder or object to rename.
1. Right-click the folder or object, and then select **Rename**. The **Name** field in the navigation pane becomes available.
1. Type a new name, and then press **Enter**.
1. If the building block is a row definition, column definition, or reporting tree definition, you must update other building blocks that are associated with it. Right-click the building block that you renamed in step 3, select **Associations**, and then select an item in the list to update it.
1. Repeat step 4 until you update all associated items.

## Create and manage report groups

You can group report definitions to generate multiple reports at the same time. To create, modify, delete, and generate report groups, you must have the designer or administrator role. Users who have the generator role can generate report groups and can also modify the user report definitions setting for report groups.

### Create a report group

1. In Report designer, in the navigation pane, select **Report groups**.
1. On the **File** menu, select **New** > **Report group definition** to open a new report group in the viewer window. Alternatively, select the **Report group** button :::image type="icon" source="../../dev-itpro/analytics/media/report-group.gif" border="false"::: on the toolbar.
1. Select the **Report group** tab. To override the information on the individual report definitions for the generation of this report, select the **Override company, detail, and date settings from individual report definitions** checkbox. The company name, detail level, provisional setting, and date information are entered automatically, but you can make updates.
1. To generate multiple reports that show the reporting currencies, select the **Include all reporting currencies** checkbox. You can then access multiple views by selecting the **Currency** button in the Web Viewer when you view the report.
1. In the **Reports in group** field, select **Add** to select the reports to include in the report group. To select multiple reports in the **Add** dialog box, hold down the Ctrl key while you select reports. When you finish selecting reports, select **OK**.
1. Select **File** > **Save** to save the new report group.

### Modify a report group

1. In Report designer, in the navigation pane, select **Report groups**.
1. Open the report group to modify.
1. On the **Report group** tab, make the changes that you want.
1. On the **File** menu, select **Save** to save the modified report group. Alternatively, select the **Save** button :::image type="icon" source="../../dev-itpro/analytics/media/save.gif" border="false"::: on the toolbar.

> [!NOTE]
> If you schedule reports so that they're generated at set intervals, you can override those settings and generate a report immediately.

### Generate a report group report

1. In Report designer, in the navigation pane, select **Report groups**.
1. Open the report group to generate.
1. Select the **Generate report** button :::image type="icon" source="../../dev-itpro/analytics/media/generate-report.gif" border="false"::: to generate reports.

### Delete a report group

1. In Report designer, in the navigation pane, select **Report groups**.
1. Right-click the report group to delete, and then select **Delete**.
1. When a confirmation message appears, select **Yes**.

## Report group tab controls

The following table describes the controls on the **Report group** tab.

| Control | Description |
|---|---|
| Override company, detail, and date settings from individual report definitions | Select this checkbox to override individual report definitions of the reports in this report group for the generation of these reports only. |
| Company name | Select the company to use for the reports. |
| Detail level | Specify the level of detail that the reports include. **Financial** − A high-level summary report. You can't drill down to accounts and dimensions, except for those accounts and dimensions that you add through a reporting tree. **Financial & Account** − A report that contains a high-level summary and account details. **Financial, Account, & Transaction** − A report that contains a high-level summary and transaction details. |
| Provisional | Specify the types of activity that the reports include. **Posted activity only** − Include only the transactions and balances that are posted in your financial data. **Posted and unposted activity** − Include all the transactions and balances that are entered and posted in your financial data. **Unposted activity only** − Include only the transactions that are entered, but not yet posted, in your financial data. |
| Include all reporting currencies | Any additional reporting currencies that you configure in your Microsoft Dynamics 365 Finance system are listed here. Select this checkbox to generate additional reports in the currencies that are indicated. To view these reports in the Web Viewer, select the **Currency** button, and then select a currency. |
| Date information not saved with report definition | Base period, Base year, Period covered. Only default base period settings are saved with the report definition. |
| Date information saved with report definition | Report date, Default base period |
| Reports in group | Add, remove, and re-order reports in the report group. To add report definitions to the report group, open the report group by double selecting it, and then select **Add**. Select the reports to include in the report group, and then select **OK**. To remove a report from the report group, select it, and then select **Remove**. To modify the order that the reports are generated in, select a report in the list, and then select **Move up** or **Move down**. |

## Additional resources

[Financial reporting](financial-reporting-intro.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
