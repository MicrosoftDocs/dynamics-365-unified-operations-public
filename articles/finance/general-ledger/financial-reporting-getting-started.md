---
# required metadata

title: Financial reporting overview
description: This topic describes where to access financial reporting in Microsoft Dynamics 365 Finance and how to use the financial reporting capabilities. It includes a description of the default financial reports that are provided.
author: aprilolson
manager: AnnBe
ms.date: 07/23/2020
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

You can find the **Financial reporting** menu in the following locations:

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

## Granting security access to Financial Reporting
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

After a user is added or a role is changed, the user should be able to access financial reporting within a few minutes. 

> [!NOTE]
> The sysadmin role is added to all roles in financial reporting.

## Report deletions and expirations
Users who generate a report can delete their own reports. Users with the **Maintain financial reporting security** duty can delete other's reports. 

In release 10.0.8, the concept of expiration dates was introduced. A new required feature is enabled in the **All** page within the feature management workspace. The **Financial report retention policies** feature contains the following changes:
* Newly generated reports will automatically be marked as having an expiration date of 90 days from when they are generated
* Any existing reports from before the feature was installed will be given a 90-day expiration period. The date may show as blank for a short period of time until the financial reporting service is running, a report is generated, and the service performs the update to existing reports with a blank expiration date. 
* Users with **Maintain financial reporting security** have access to this functionality. Any user in the **Maintain financial report** duty granted the **Maintain financial report expiration** privilege will also have the ability to modify the expiration period. Currently there are two retention options available: 
  * An expiration of 90 days.
  * An option to set the report to never expire.
  
When an expiration, such as 90 days, is selected, it's applied 90 days from today. This is different behavior than the 90 days from the original generation date set when the report was generated. 
  
Additional options will be considered in future functionality. The expiration of 90 days will be the default, and users with appropriate permissions can override the default on the **Financial reports** list page.    

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
When you select the **Financial reporting** menu, the list of default financial reports for the company is shown. You can then open or modify a report. To open one of the default reports, select the report name. The first time that a report is opened, it's automatically generated for the previous month. For example, if you open a report for the first time in August 2019, the report is generated for July 31, 2019. After a report is opened, you can start exploring it by drilling down on specific pieces of data and changing report options.

## Creating and modifying financial reports
From the financial reports list, you can create a new report or modify an existing report. If you have the appropriate permissions, you can create a new financial report by selecting **New** on the Action Pane. A report designer program is downloaded to your device. After the report designer starts you can then create the new report. After you save the new report, it appears in the financial reports list. The list shows only reports that were created for the company that you're using in Dynamics 365 Finance. 

## Troubleshooting issues opening Report Designer
There are a few common issues that can cause problems when you open Report Designer. Those issues and the steps to resolve them are as follows.

Issue 1: Report Designer doesn't start when you select **New** or **Edit**.

* In Internet Explorer, select **Settings**, then select **Internet Options**. Select the **Security** tab. Select Trusted Sites and then select **Sites**. In the **Add this website to zone**, enter "\*\.dynamics.com" (without quotation marks), and then select **Add**. 
* In Internet Explorer, select **Settings**, then select **Internet Options**. Select the **Security** tab. Select Trusted Sites. In the area labeled Security level for this zone, change the option to **Medium-Low**.
* Disable the pop-up blocker in your browser.
* Workstations are required to install Visual Studio .NET 4.6.2 or higher.

This version of the Microsoft .NET Framework can be downloaded and installed from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53345).
* If you use the Chrome browser, you must install a ClickOnce extension in order to download the Report Designer client. If you are running incognito mode, make sure the ClickOnce extension is enabled for incognito mode. If you are unable to sign in with Chrome, try following the setup steps described in Issue 1 using Internet Explorer or Edge. 

Issue 2: The user hasn't been assigned the required permissions to use Financial Reporting. 

* To verify if the user does not have permission, select **Yes** on the error, “Unable to connect to the Financial Reporting server. Select Yes if you want to continue and specify a different server address.” Then select **Test Connection**. If you don't have permission, you will see a message that says, "Connection attempt failed. User does not have appropriate permissions to connect to the server. Contact your system administrator.”
* Required permissions are listed above in [Granting security access to Financial Reporting](#granting-security-access-to-financial-reporting). Security in Financial Reporting is based on these privileges. You won't have access unless these privileges (or another security role that includes these privileges) are assigned to you. 
* The **Company Users Provider to Company** integration task (which is also responsible for and known as user integration) runs on a 5-minute interval. It may take up to 10 minutes for any permission changes to take effect in Financial Reporting. 
  If another user can open Report Designer, select **Tools**, and then select **Integration Status**. Verify that the integration map, "Company Users Provider to Company," has run successfully because you were assigned permission to use Financial Reporting. 
* It may be possible that another error has prevented **Dynamics user to Financial Reporting user integration** from finishing. Or it's possible that a datamart reset has been initiated and not yet completed, or that another system error has occurred. Try running the process again later. If the problem persists, contact your system admin.

Issue 3: You can proceed past the ClickOnce Report Designer signin page, but are unable to complete sign in within Report Designer. 

* The time set on your local computer when you enter your login credentials must be within five minutes of the time on the Financial Reporting server. If there is a difference of more than five minutes, the system will not allow signin. 
* In this case, we recommend enabling the Windows option to set your PC's time automatically. 

## Additional resources
- [View financial reports](view-financial-reports.md)
