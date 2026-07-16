---
title: View financial reports
description: Learn how to view and explore financial reports in Microsoft Dynamics 365 Finance, including outlines on various options that you can apply to financial reports.
author: kweekley
ms.author: kweekley
ms.topic: article
ms.date: 06/01/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: FinancialReports
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: d20f435f-fb65-4068-ab09-7efc7be683a6
---

# View financial reports

[!include [banner](../includes/banner.md)]

This article describes how to view and explore financial reports. It includes information about the various options that you can apply to financial reports to change their appearance and the data that they include.

## Financial reporting overview

## Open a financial report

To open a report, select the report name. The first time that a report is opened, it’s automatically generated for the previous month. For example, if you open a report for the first time in August 2025, the report is generated for July 31, 2025. After a report is opened, you can start exploring it by drilling down on specific pieces of data and changing report options.

## Drill down on a financial report

Financial reports can include multiple levels of detail. The financial level is the first level that you see when you open a financial report. To go to the account level, select the data to drill down on. For example, to view the account details for sales, select the sales data that you want to explore. From the account level, you can drill down to view the transactions that make up the account balance. There are two ways to view transactions: report transactions and voucher transactions.

- **Report transactions** – Transactions appear in a formatted view that's included on the financial report. To view transactions in the formatted view, select the data to drill down on, and then select **Drill to report transaction level**.
- **Voucher transactions** – A voucher transaction inquiry opens, where you can view transactions. To view transactions in the voucher transaction inquiry, select the data to drill down on, and then select **Open account transactions**.

If the data is budget data, you can choose to open budget account entries. To close any of the levels of the report and return where you started, press the Esc key or select the **Close** button (**X**) in the upper right.

## Change report options

You can apply attribute and dimension filters, or change the budget scenario on an **Actual versus budget** report. On the Action Pane, select **Report options**, and then follow one or more of these steps:

- To apply attribute filters to a report, select **Add an attribute filter**. Select the attribute, type the attribute value, and then select **OK**. For example, if you select the **Account Category** attribute, enter **SALES** as the attribute value. To remove an attribute filter, select **Clear**.
- To apply dimension filters to a report, select **Add a dimension filter**. Select the dimension, and then either type the dimension ID or select the dimension in the list. To remove a dimension filter, select **Clear**.
- To change the scenario on an **Actual versus budget** report, select a new scenario, and then select **OK**. If the selected scenario is for a different fiscal year, there won't be any results returned. For example, if a report is generated for FY2020 and the current scenario is for FY2025 and the new scenario selected is for FY2021, no results are returned. If a new scenario for a different fiscal year is needed, generate a new version of the report for the fiscal year related to the scenario.

When you select **OK**, the report applies all the selected options. If you decide that you don't want to apply the selected options, select **Cancel**.

## Update a financial report

You can generate (update) a financial report to display the most recent data for the period and year that the report was generated for. For example, if you update a financial report that was generated for October 2025, the report reflects any new transactions that have been posted for October 2025. To update a financial report, on the Action Pane, select **Generate**.

## Display a financial report in a different currency

A financial report can be displayed in any currency at any time. To display a report in a different currency, on the Action Pane, select **Currency**, and then select a currency. The report is translated into that currency, and the results are displayed. Any currency codes or symbols that are included as part of the report design are updated to reflect the new currency. The currencies that appear in the list are the reporting currencies that are configured in Finance.

## Display a summarized view of the financial report

A financial report can contain detail lines and summary lines. Detail lines are lines that contain main accounts or dimensions. Summary lines are description, total, and calculation lines. To display just the summary lines of a report, select **Show**, and then select **Summary lines only**. The report is collapsed and displays only the summary lines. To view the detail lines together with the summary lines, select **Show**, and then select **Summary lines only** again.

## Print a financial report

Printing a financial report creates a PDF file that can then be manually printed. To create a printable financial report, on the Action Pane, select **Print**, and then follow one or more of these steps to set the print options:

- To include various detail levels in the printed report, set the slider to **Yes** or **No**. If a report uses a reporting tree, you can choose to include all reporting units or just the current reporting unit.
- To set the page size, select a page size in the list.
- To set the page layout, select a layout in the list. If you want the report content to fit the width that you selected, set the slider to **Yes**.
- To set the page margins, type the size of the top, bottom, left, and right margins in inches.

After you finish setting the print options, select **Print** to continue. You're prompted to download the file, or save the file to OneDrive or SharePoint. If you decide that you don't want to continue, select **Cancel** instead. Once you continue, the report begins rendering on the server and you're prompted to download the report in PDF format. You can now view the report in your PDF viewer. From here, you can select the printer to send the report to, and make any further adjustments for the print options.

## Export a financial report

To export a financial report, on the Action Pane, select **Export**. The report is exported to Microsoft Excel, and your browser prompts you to open or save the exported file. The export settings that are defined in the report design are applied to the exported report.

## Additional resources

[Financial reporting](../../fin-ops-core/dev-itpro/analytics/financial-reporting-intro.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
