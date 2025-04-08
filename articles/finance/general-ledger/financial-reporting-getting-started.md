---
title: Financial reporting overview
description: Learn about where to access financial reporting in Microsoft Dynamics 365 Finance and how to use the financial reporting capabilities.
author: aprilolson
ms.author: aolson
ms.topic: article
ms.date: 05/20/2024
ms.reviewer: twheeloc
ms.collection: get-started 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: FinancialReports
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 3eae6dc3-ee06-4b6d-9e7d-1ee2c3b10339
---

# Get started with financial reporting 

[!include [banner](../includes/banner.md)]

This article describes where to access financial reporting and how to use the financial reporting capabilities. It also includes a description of the default financial reports that are provided.

> [!NOTE]
> Financial reporting is now available through an add-in. Therefore, the default availability of Financial reporting through Microsoft Dynamics 365 Finance has changed. If you're an existing customer, Microsoft provides the new Financial reporting add-in in your Microsoft Dynamics Lifecycle Services environment. If you're currently using the **Financial reporting** module, there's no impact on your environments or your organization's ability to run financial reports.

## Install the Financial reporting add-in

The Financial reporting add-in lets financial and business professionals create, maintain, deploy, and view financial statements. Financial reporting includes dimension support. Therefore, account segments or dimensions are immediately available. No additional tools or configuration steps are required after installation.
	
1. In Lifecycle Services, confirm that the Power Platform integration is configured and available. For more information, see [Configure Microsoft Power Platform](../business-performance-analytics/configure-bpa.md#configure-microsoft-power-platform) 
2. Select **Install a new add-in**, and search for **Financial reporting**.
3. Agree to the terms, and then select **Install**.

## Uninstall the Financial reporting add-in

> [!IMPORTANT]
> If you uninstall the Financial reporting add-in, you remove resources that have been used for Financial reporting. This action permanently deletes any previously created reports, report designs, and configurations. Recovery isn't supported.

1. In Lifecycle Services, find the Financial reporting add-in in the **Environment add-ins** section under **Power Platform Integration**.
2. Select **Uninstall** and then **Agree**.

## Accessing Financial reporting

You can find the **Financial reporting** menu in the following locations:

- **General Ledger** > **Inquiries and reports**
- **Budgeting** > **Inquires and reports** > **Basic budgeting**
- **Budgeting** > **Inquiries and reports** > **Budget planning**
- **Budgeting** > **Inquiries and reports** > **Budget control**
- Consolidations

To create and generate financial reports for a legal entity, you must set up the following information for that legal entity:

- Fiscal calendar
- Ledger
- Chart of accounts
- Currency
- Post a transaction to at least one account
- MainAccount is listed in the **Selected** column on the **Financial reporting setup** page (**General ledger > Ledger setup > Financial reporting setup**)

## Granting security access to Financial reporting

The financial reporting functions are available to users who have the appropriate privileges and duties assigned to them through their security roles. The following sections list these privileges and duties, together with the associated roles.

### Duties

| Duty label                            | Description                                                             | AOT name                         |
|---------------------------------------|-------------------------------------------------------------------------|----------------------------------|
| Maintain financial reporting security | Maintain Financial reporting security and perform administrative tasks. | FinancialReportsSecurityMaintain |
| Maintain financial reports            | Design and maintain financial reports.                                  | FinancialReportsMaintain         |
| Generate financial reports            | Generate and refresh financial reports.                                 | FinancialReportsGenerate         |
| Review financial performance          | Review and analyze financial performance.                               | FinancialReportsPerfReview       |

### Privileges

| Privilege label                       | Description                                                             | AOT name                         |
|---------------------------------------|-------------------------------------------------------------------------|----------------------------------|
| Maintain financial reporting security | Maintain Financial reporting security and perform administrative tasks. | FinancialReportsSecuritySystemMaintain |
| Maintain financial reports            | Design and maintain financial reports.                                  | FinancialReportsMaintainReports  |
| Generate financial reports            | Generate and refresh financial reports.                                 | FinancialReportsGenerateReports  |
| View financial reports                | View financial reports.                                                 | FinancialReportsView             |

### Roles

| Privilege label                       | Duty                                  | Roles                                                                           |
|---------------------------------------|---------------------------------------|---------------------------------------------------------------------------------|
| Maintain financial reporting security | Maintain Financial reporting security | Security administrator                                                          |
| Maintain financial reports            | Maintain financial reports            | Accounting Manager, Accounting Supervisor, Financial Controller, Budget Manager |
| Generate financial reports            | Generate financial reports            | CEO, CFO, Accountant                                                            |
| View financial reports                | Review financial performance          | None assigned                                                                   |

After a user is added or a role is changed, the user should be able to access Financial reporting within a few minutes. 

> [!NOTE]
> The sysadmin role is added to all roles in financial reporting.

## Report deletions and expirations

Users who generate a report can delete their own reports. Users with the **Maintain financial reporting security** duty can delete other's reports. 

In release 10.0.8, the concept of expiration dates was introduced. A new required feature is enabled in the **All** page within the feature management workspace. The **Financial report retention policies** feature contains the following changes:
* Newly generated reports will automatically be marked as having an expiration date of 90 days from when they're generated.
* Any existing reports from before the feature was installed will be given a 90-day expiration period. The date might show as blank for a short period of time until the Financial reporting service is running, a report is generated, and the service performs the update to existing reports with a blank expiration date. 
* Users with **Maintain financial reporting security** have access to this functionality. Any user in the **Maintain financial report** duty granted the **Maintain financial report expiration** privilege will also have the ability to modify the expiration period. Currently there are two retention options available: 

    * An expiration of 90 days.
    * An option to set the report to never expire.

When an expiration, such as 90 days, is selected, it's applied 90 days from today. This is different behavior than the 90 days from the original generation date set when the report was generated. 

Additional options will be considered in future functionality. The expiration of 90 days will be the default, and users with appropriate permissions can override the default on the **Financial reports** list page.

## Default reports

Financial reporting provides 22 default financial reports. Every report uses the default main account categories. You can use these reports as is or as a starting point for your financial reporting needs. In addition to the traditional financial statements, such as Income statement and Balance sheet, these default reports include reports that show the different types of financial reports that you can create. 

<!--Each report in the following table links to an Office Mix presentation about the report.-->

| Default report                           | Description                                                         |
|-------------------------------------------|--------------------------------------------------------------------------------|
| 12 Month Rolling Single Column Income Statement – Default | View an organization's profitability for the past 12 months in a single column.            |
| 12 Month Trend Income Statement – Default                 | View an organization's profitability for each of the last 12 months. These 12 months can span more than one fiscal year.                    |
| Actual vs Budget – Default                                | View detailed balance information for all accounts for the original budget, and compare the revised budget to actuals that have a variance.    |
| Audit Details – Default                                  | View detailed balance information for all accounts. This report shows debit and credit balances in the reporting currency and the local currency, together with additional transaction information, such as the user ID, the user who last modified the data, the date of the last modification, and the journal ID. |
| Balance List – Default                                   | View detailed balance information for all accounts. This report shows opening and closing balances, and debit and credit balances for the current period and year to date, together with additional transaction information, such as the voucher.                          |
| Balance Sheet – Default                                   | View the organization's financial position for the year.                      |
| Balance Sheet and Income Statement Side by Side - Default | View the organization's financial position and profitability for the year side by side.     |
| Cash Flow – Default                                       | Gain insight into the cash that's coming in to and going out of the organization.                 |
| Detailed JE and TB Review – Default                      | View opening balance and activity information for all accounts.                      |
| [Detailed Trial Balance - Default](trial-balance-financial-reports.md)| View balance information for all accounts that have debit and credit balances, and the net of these balances, together with the transaction date, voucher, and journal description.                                                                                 |
| Expenses Three Year Quarterly Trend – Default             | Gain insight into expenses for the past 12 quarters over the previous three years.       |
| Financial Captions JE and TB Review – Default            | See an overview of the balances and activity for the asset, liability, owner's equity, revenue, expense, gain, or loss financial captions.   |
| [Income Statement – Default](income-statement-financial-report.md)| View the organization's profitability for the current period and the year to date.          |
| Ledger Transaction List – Default                        | View detailed balance information for all accounts. This report shows debit and credit balances, together with additional transaction information, such as the transaction date, journal number, voucher, posting type, and trace number.                |
| Ratios – Default                                          | View the solvency, profitability, and efficiency ratios for the organization for the year.       |
| Rolling 12 Month Expenses – Default      | Gain insight into expenses for each of the last 12 months. These 12 months can span more than one fiscal year.        |
| Rolling Quarter Income Statement – Default               | View the organization's profitability on a quarterly basis for the past year and the year to date.    |
| Side by Side Balance Sheet – Default                      | View the organization's financial position for the year. This report shows assets and liability, and shareholder equity side by side.               |
| [Summary Trial Balance – Default](trial-balance-financial-reports.md)| View balance information for all accounts that have opening and closing balances, and debit and credit balances together with their net difference.                                      |
| [Summary Trial Balance Year Over Year – Default](trial-balance-financial-reports.md)| View balance information for all accounts that have opening and closing balances, and debit and credit balances together with their net difference for the current year and the past year.                  |
| Weekly Sales and Discounts - Default                     | Gain insight into sales and discounts for each week in a month. This report includes a four-week total.   |
| Budget Funds Available - Default|View a detailed comparison of revised budget, actual expenditures, budget reservations, and budget funds available for all accounts.|

## Opening financial reports

When you select the **Financial reporting** menu, the list of default financial reports for the company is shown. You can then open or modify a report. To open one of the default reports, select the report name. The first time that a report is opened, it's automatically generated for the previous month. For example, if you open a report for the first time in August 2019, the report is generated for July 31, 2019. After a report is opened, you can start exploring it by drilling down on specific pieces of data and changing report options.

## Creating and modifying financial reports

From the financial reports list, you can create a new report or modify an existing report. If you have the appropriate permissions, you can create a new financial report by selecting **New** on the Action Pane. A report designer program is downloaded to your device. After the report designer starts you can then create the new report. After you save the new report, it appears in the financial reports list. The list shows only reports that were created for the company that you're using in Dynamics 365 Finance. 

## Reporting tree definitions

One of the components that's used to build financial reports is a reporting tree definition. A reporting tree definition helps define the structure and hierarchy of your organization. It's a cross-dimensional hierarchical structure that's based on the dimensional relationships in your financial data. It provides information at the reporting unit level and at a summary level for all units in the tree.

You can create an unlimited number of reporting trees to display your organization's data in various ways. Each reporting tree can contain any combination of departments and summary units, but a report definition can link to only one reporting tree at a time. 

## Update the Financial reporting version through slipstreaming

Finance and operations apps are updated every month. However, Financial reporting isn't necessarily updated on that cadence. Moreover, customers have more options about when they implement updates for finance and operations apps. Financial reporting updates are automatically installed. Financial reporting has a designated version that's consumed in a customer environment when a service update is implemented, when downtime is initiated, or when a customer's environment is in Maintenance mode. This process is known as *slipstreaming* or *true-up*, because all customer implementations are set to the same version of Financial reporting.

Changes that are released in each version can be found in [What's new or changed in Dynamics 365 Finance](../../finance/get-started/whats-new-home-page.md). Platform updates and bug fixes can be found in the "Additional Resources" section at the bottom of the page for each release.

The selected slipstreamed version is a reviewed and validated version of Financial reporting that's ready for production. It's compatible with any previous or future version of Dynamics 365 Finance. For example, Financial reporting can be on the latest 10.0.19 build while the customer is still on application version 10.0.16.

> [!NOTE]
> The only circumstance where customers can move to a previous version (a downgrade scenario) occurs if Microsoft stops a true-up rollout because of an issue. As soon as a fix is available, it will be applied automatically.

The slipstream process is fully automated and doesn't require any customer action. Three topologies consume slipstream, each in a slightly different way:

- **On-premises** – On-premises deployments don't support slipstream and true-up.
- **Infrastructure as a service (IaaS)** – The slipstream logic is applied during any operation that tries to update Financial reporting. It includes binary updates or broadcasts that contain binary updates.
- **Self-service** – Any operation that requires Financial reporting downtime applies the slipstream logic:

    - Binary updates or broadcasts that include binary updates
    - S patching or other infrastructure downtime
    - AOT package deployments


## Additional resources

- [View financial reports](view-financial-reports.md)
- [Reporting tree definitions in financial reports](../../fin-ops-core/dev-itpro/analytics/financial-reporting-tree-definitions.md)
- [Troubleshoot report designer issues with Event Viewer](/troubleshoot/dynamics-365/finance/financial-reporting/troubleshoot-report-designer-with-event-viewer)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

