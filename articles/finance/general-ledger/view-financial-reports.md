---
# required metadata

title: View financial reports
description: This article describes how to view and explore financial reports in Microsoft Dynamics 365 Finance. It includes information about the various options that you can apply to financial reports to change their appearance and the data that they include.
author: kweekley
ms.date: 11/22/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: FinancialReports
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: d20f435f-fb65-4068-ab09-7efc7be683a6
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# View financial reports

[!include [banner](../includes/banner.md)]

This article describes how to view and explore financial reports. It includes information about the various options that you can apply to financial reports to change their appearance and the data that they include.

## Financial reporting overview

## Open a financial report
To open a report, select the report name. The first time that a report is opened, it’s automatically generated for the previous month. For example, if you open a report for the first time in August 2020, the report is generated for July 31, 2020. After a report is opened, you can start exploring it by drilling down on specific pieces of data and changing report options.

## Drill down on a financial report
Financial reports can include multiple levels of detail. The financial level is the first level that you see when you open a financial report. To go to the account level, select the data to drill down on. For example, to view the account details for sales, select the sales data that you want to explore. From the account level, you can drill down to view the transactions that make up the account balance. There are two ways to view transactions: report transactions and voucher transactions.

-   **Report transactions** – Transactions appear in a formatted view that is included on the financial report. To view transactions in the formatted view, select the data to drill down on, and then click **Drill to report transaction level**.
-   **Voucher transactions** – A voucher transaction inquiry opens, where you can view transactions. To view transactions in the voucher transaction inquiry, select the data to drill down on, and then click **Open account transactions**.

If the data is budget data, you can choose to open budget account entries. To close any of the levels of the report and return where you started, you can either press the Esc key or click the **Close** button (**X**) in the upper right.

## Change report options
You can apply attribute and dimension filters, or change the budget scenario on an **Actual versus budget** report. On the Action Pane, click **Report options**, and then follow one or more of these steps:

-   To apply attribute filters to a report, select **Add an attribute filter**. Select the attribute, type the attribute value, and then click **OK**. For example, if you select the **Account Category** attribute, enter **SALES** as the attribute value. To remove an attribute filter, click **Clear**.
-   To apply dimension filters to a report, select **Add a dimension filter**. Select the dimension, and then either type the dimension ID or select the dimension in the list. To remove a dimension filter, click **Clear**.
-   To change the scenario on an **Actual versus budget** report, select a new scenario, and then click **OK**. If the selected scenario is for a different fiscal year, there will not be any results returned. For example, if a report is generated for FY2015 and the current scenario is for FY2020 and the new scenario selected is for FY2016, no results will be returned. If a new scenario for a different fiscal year is needed, generate a new version of the report for the fiscal year related to the scenario.

When you click **OK**, all the options that you selected are applied to the report. If you decide that you don't want to apply the selected options, click **Cancel**.

## Update a financial report
You can refresh (update) a financial report so that it shows the most recent data for the period and year that the report was generated for. For example, if you update a financial report that was generated for October 2020, the report reflects any new transactions that have been posted for October 2020. To update a financial report, on the Action Pane, click **Refresh**. An updated report is available only to the person who updated it. In order for other people to see the same data, the report must be published.

## Publish a financial report
After you update a financial report, you can publish it. Other people in the organization will then be able to view it. To publish a report, on the Action Pane, click **Publish**.

## Display a financial report in a different currency
A financial report can be displayed in any currency at any time. To display a report in a different currency, on the Action Pane, click **Currency**, and then select a currency. The report is translated into that currency, and the results are displayed. Any currency codes or symbols that are included as part of the report design are updated to reflect the new currency. The currencies that appear in the list are the reporting currencies that are configured in Finance.

## Display a summarized view of the financial report
A financial report can contain detail lines and summary lines. Detail lines are lines that contain main accounts or dimensions. Summary lines are description, total, and calculation lines. To display just the summary lines of a report, click **Show**, and then click **Summary lines only**. The report is collapsed and displays only the summary lines. To view the detail lines together with the summary lines, click **Show**, and then click **Summary lines only** again.

## Print a financial report
Printing a financial report will create a PDF file which can then be manually printed. To create a printable financial report, on the Action Pane, click **Print**, and then follow one or more of these steps to set the print options:

-   To include the various detail levels in the printed report, set the slider to **Yes** or **No**. If a report uses a reporting tree, you can choose to include all reporting units or just the current reporting unit.
-   To set the page size, select a page size in the list.
-   To set the page layout, select a layout in the list. If you want the report content to fit the width that you selected, set the slider to **Yes**.
-   To set the page margins, type the size of the top, bottom, left, and right margins in inches.

After you've finished setting the print options, click **Print** to continue and be prompted whether you wish to download the file, or save the file to OneDrive or SharePoint. If you decide that you don’t want to continue, click **Cancel** instead. Once you continue, The report will begin rendering on the server and you will be prompted to download the report in PDF format. You can now view the report in your PDF viewer and from here you can select the printer to send the report to, and make any further adjustments for the print options.

## Export a financial report
To export a financial report, on the Action Pane, click **Export**. The report is exported to Microsoft Excel, and your browser prompts you to open or save the exported file. The export settings that are defined in the report design are applied to the exported report.    

## Additional resources

[Financial reporting](../../fin-ops-core/dev-itpro/analytics/financial-reporting-intro.md)






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
