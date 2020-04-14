---
# required metadata

title: Financial reporting overview
description: This topic describes where to access financial reporting in Microsoft Dynamics 365 Finance and how to use the financial reporting capabilities. It includes a description of the default financial reports that are provided.
author: aprilolson
manager: AnnBe
ms.date: 04/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: FinancialReports
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 10444
ms.assetid: 3eae6dc3-ee06-4b6d-9e7d-1ee2c3b10339
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Financial reporting overview

[!include [banner](../includes/banner.md)]

This topic describes where to access financial reporting and how to use the financial reporting capabilities. It also includes a description of the default financial reports that are provided.

Accessing financial reporting
-----------------------------

You can find the **Financial reporting** menu in the following places:

-   **General Ledger** &gt; **Inquiries and reports**
-   **Budgeting** &gt; **Inquires and reports** &gt; **Basic budgeting**
-   **Budgeting** &gt; **Inquiries and reports** &gt; **Budget planning**
-   **Budgeting** &gt; **Inquiries and reports** &gt; **Budget control**
-   Consolidations

To create and generate financial reports for a legal entity, you must set up the following information for that legal entity:

-   Fiscal calendar
-   Ledger
-   Chart of accounts
-   Currency

The financial reporting functions are available to users who have the appropriate privileges and duties assigned to them through their security roles. The following sections list these privileges and duties, together with the associated roles.

### Duties

| Duty label                            | Description                                                             | AOT name                         |
|---------------------------------------|-------------------------------------------------------------------------|----------------------------------|
| Maintain financial reporting security | Maintain financial reporting security and perform administrative tasks. | FinancialReportsSecurityMaintain |
| Maintain financial reports            | Design and maintain financial reports.                                  | FinancialReportsMaintain         |
| Generate financial reports            | Generate and refresh financial reports.                                 | FinancialReportsGenerate         |
| Review financial performance          | Review and analyze financial performance.                               | FinancialReportsPerfReview       |

### Privileges

| Privilege label                       | Description                                                             | AOT name                         |
|---------------------------------------|-------------------------------------------------------------------------|----------------------------------|
| Maintain financial reporting security | Maintain financial reporting security and perform administrative tasks. | FinancialReportsSecuritySystemMaintain |
| Maintain financial reports            | Design and maintain financial reports.                                  | FinancialReportsMaintainReports  |
| Generate financial reports            | Generate and refresh financial reports.                                 | FinancialReportsGenerateReports  |
| View financial reports                | View financial reports.                                                 | FinancialReportsView             |

### Roles

| Privilege label                       | Duty                                  | Roles                                                                           |
|---------------------------------------|---------------------------------------|---------------------------------------------------------------------------------|
| Maintain financial reporting security | Maintain financial reporting security | Security administrator                                                          |
| Maintain financial reports            | Maintain financial reports            | Accounting Manager, Accounting Supervisor, Financial Controller, Budget Manager |
| Generate financial reports            | Generate financial reports            | CEO, CFO, Accountant                                                            |
| View financial reports                | Review financial performance          | None assigned                                                                   |

After a user is added or a role is changed, the user should be able to access financial reporting within a few minutes. **Note:** The sysadmin role is added to all roles in financial reporting.

## Report deletions and expirations
Users who generate a report can delete their own reports. Users with the **Maintain financial reporting security** duty can delete other's reports. 

In version 10.0.8, the concept of expiration dates has been introduced. A new required feature will be enabled in the **All** page within the feature management workspace. The **Financial report retention policies** feature contains the following changes:
* Newly generated reports will automatically be marked as having an expiration date of 90 days from when they are generated
* Any existing reports from before the feature was installed will be given a 90-day expiration period. The date may show as blank for a short period of time until the financial reporting service is running, a report is generated, and the service performs the update to existing reports with a blank expiration date. 
* Users with **Maintain financial reporting security** have access to this functionality. Any user in the **Maintain financial report** duty granted the **Maintain financial report expiration** privilege will also have the ability to modify the expiration period. Currently there are two retention options available. 
  * An expiration of 90 days.
  * An option to set the report to never expire.
  
Additional options will be considered in future functionality. The expiration of 90 days will be the default, and users with appropriate permissions can override the default on the **Financial reports** list page.    
  
When an expiration such as 90 days is selected, it grants 90 days from today, which is different behavior than the 90 days from the original generation date set during report generation. 

## Default reports
Financial reporting provides 22 default financial reports. Every report uses the default main account categories. You can use these reports as is or as a starting point for your financial reporting needs. In addition to the traditional financial statements, such as Income statement and Balance sheet, these default reports include reports that show the different types of financial reports that you can create. 

<!--Each report in the following table links to an Office Mix presentation about the report.-->

| Default report                                                                                         | Description                                                                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 12 Month Rolling Single Column Income Statement – Default | View an organization’s profitability for the past 12 months in a single column.                                                                                                                                                                                                                                      |
| 12 Month Trend Income Statement – Default                 | View an organization’s profitability for each of the last 12 months. These 12 months can span more than one fiscal year.                                                                                                                                                                                             |
| Actual vs Budget – Default                                | View detailed balance information for all accounts for the original budget, and compare the revised budget to actuals that have a variance.                                                                                                                                                                          |
| Audit Details – Default                                  | View detailed balance information for all accounts. This report shows debit and credit balances in the reporting currency and the local currency, together with additional transaction information, such as the user ID, the user who last modified the data, the date of the last modification, and the journal ID. |
| Balance List – Default                                   | View detailed balance information for all accounts. This report shows opening and closing balances, and debit and credit balances for the current period and year to date, together with additional transaction information, such as the voucher.                                                                    |
| Balance Sheet – Default                                   | View the organization's financial position for the year.                                                                                                                                                                                                                                                             |
| Balance Sheet and Income Statement Side by Side - Default | View the organization’s financial position and profitability for the year side by side.                                                                                                                                                                                                                              |
| Cash Flow – Default                                       | Gain insight into the cash that is coming in to and going out of the organization.                                                                                                                                                                                                                                   |
| Detailed JE and TB Review – Default                      | View opening balance and activity information for all accounts.                                                                                                                                                                                                                                                      |
| Detailed Trial Balance - Default                         | View balance information for all accounts that have debit and credit balances, and the net of these balances, together with the transaction date, voucher, and journal description.                                                                                                                                  |
| Expenses Three Year Quarterly Trend – Default             | Gain insight into expenses for the past 12 quarters over the previous three years.                                                                                                                                                                                                                                   |
| Financial Captions JE and TB Review – Default            | See an overview of the balances and activity for the asset, liability, owner’s equity, revenue, expense, gain, or loss financial captions.                                                                                                                                                                           |
| Income Statement – Default                                | View the organization’s profitability for the current period and the year to date.                                                                                                                                                                                                                                   |
| Ledger Transaction List – Default                        | View detailed balance information for all accounts. This report shows debit and credit balances, together with additional transaction information, such as the transaction date, journal number, voucher, posting type, and trace number.                                                                            |
| Ratios – Default                                          | View the solvency, profitability, and efficiency ratios for the organization for the year.                                                                                                                                                                                                                           |
| Rolling 12 Month Expenses – Default                       | Gain insight into expenses for each of the last 12 months. These 12 months can span more than one fiscal year.                                                                                                                                                                                                       |
| Rolling Quarter Income Statement – Default               | View the organization’s profitability on a quarterly basis for the past year and the year to date.                                                                                                                                                                                                                   |
| Side by Side Balance Sheet – Default                      | View the organization's financial position for the year. This report shows assets and liability, and shareholder equity side by side.                                                                                                                                                                                |
| Summary Trial Balance – Default                          | View balance information for all accounts that have opening and closing balances, and debit and credit balances together with their net difference.                                                                                                                                                                  |
| Summary Trial Balance Year Over Year – Default           | View balance information for all accounts that have opening and closing balances, and debit and credit balances together with their net difference for the current year and the past year.                                                                                                                           |
| Weekly Sales and Discounts - Default                     | Gain insight into sales and discounts for each week in a month. This report includes a four-week total.                                                                                                                                                                                                              |
| Budget Funds Available - Default                         | View a detailed comparison of revised budget, actual expenditures, budget reservations, and budget funds available for all accounts                                                                                                                                                                                  |

## Opening financial reports
When you click the **Financial reporting** menu, the list of default financial reports for the company is shown. You can then open or modify a report. To open one of the default reports, select the report name. The first time that a report is opened, it's automatically generated for the previous month. For example, if you open a report for the first time in August 2016, the report is generated for July 31, 2016. After a report is opened, you can start exploring it by drilling down on specific pieces of data and changing report options.

## Creating and modifying financial reports
From the financial reports list, you can create a new report or modify an existing report. If you have the appropriate permissions, you can create a new financial report by clicking **New** on the Action Pane. A report designer program is downloaded to your device. After the report designer starts you can then create the new report. After you save the new report, it appears in the financial reports list. The list shows only reports that were created for the company that you're using in Finance. 

> [!NOTE] 
> The computer that you are downloading the report designer client on must have version 4.6.2 of the Microsoft .NET Framework installed on it. This version of the Microsoft .NET Framework can be downloaded and installed from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53345). If you are using Chrome, you must install a ClickOnce extension in order to download the report designer client. If you are running in incognito mode, make sure the ClickOnce extension is enabled for incognito mode. You can also modify a report that appears in the financial reports list. When the area around the report name is selected, click **Edit** on the Action Pane. The report designer program starts.

## Additional resources
- [View financial reports](view-financial-reports.md)



