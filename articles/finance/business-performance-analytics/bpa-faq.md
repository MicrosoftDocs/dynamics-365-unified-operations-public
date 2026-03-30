---
title: Business performance analytics FAQ
description: This article answers some frequently asked questions about Business performance analytics, including questions about signing up for public previews of analytics.
author: yashkv1
ms.author: yvishwa
ms.topic: faq
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 12/15/2025

---

# Business performance analytics FAQ

This article answers frequently asked questions about Business performance analytics.

## Installation and initial setup

### I received an error during the installation of Business performance analytics. How do I fix it?

The following errors are likely to occur if another operation is in progress during the installation of Business performance analytics. If these errors persist, retry the installation.

- "There's another \[RibbonMetadataGeneration\] running at this moment."
- "Issues with enabling change tracking: msdyn\_BpaTablesVirtualEntities."
- "Import failed - errorCode: 0Description: Unable to complete updates to the Track changes option for table."
- "Flight EnableSqlRowVersionChangeTracking isn't enabled. The functionality requires enabling sql row version change tracking feature. Enable flight EnableSqlRowVersionChangeTracking."

### How do I retry the installation of Business performance analytics if it fails?

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Microsoft Dataverse admin credentials.
1. Go to **Environments**, and select **Dynamics 365 Apps**.
1. Find **Business performance analytics**, and select **Installation failed**.
1. Select the link to retry the installation, and monitor the app installation process.

### I received an "unexpected error occurred" message in Power Platform admin center. How do I resolve it?

This error might be caused by a truncation problem. Follow these steps to check if this problem applies and to fix it.

#### Check if it's a truncation error

1. Go to [Power Apps](https://make.powerapps.com).
1. Select the affected environment in the environment picker (upper right corner).
1. Go to **Solutions**.
1. In the ribbon at the top, select **See history**.
1. In the search bar in the upper right corner of the screen, search for **msdyn_bpa**.
1. Look for a solution that shows **Failure** in the results column.
1. If the failed solution is **msdyn_BpaTablesVirtualEntities**, continue to the next step.
1. Select the solution name to open a slider panel.
1. Check if the error matches this pattern: `Failed to sync entity metadata for entity '<entity name>'. Exception details: CreateRequest failed with error: String or binary data would be truncated in table '{0}', column '{1}'. Truncated value: {2}.`

#### Fix the problem

1. Find the **Available Finance and Operations Virtual entities** table.
1. Mark the entity referenced in the error message as visible.
1. Save your changes.
1. Repeat this process if the error occurs for more entities.

### How long does it take to set up Business performance analytics?

Setting up the Business performance analytics app takes up to 60 minutes. However, it might take up to 24 hours before your data is available in Business performance analytics after installation is completed.

## Accessing the App

### I'm having trouble opening Business performance analytics. What can I do?

If you're accessing Business performance analytics from the maker portal, select **Play** in the upper right corner to avoid viewing the app in editor mode.

### Why am I unable to sign in to Business performance analytics even though I have the correct roles?

Some users might encounter authentication problems when accessing Business performance analytics because of conflicting cached credentials. This problem is especially common if users previously signed in to multiple environments or tenants. The problem prevents the correct authentication token from being used and results in access errors.
Use **InPrivate** or **Incognito** modes as a workaround.

If users can't isolate their session by using private browsing, follow these steps to ensure correct permissions are applied:

1. Go to the Power Platform Admin Portal and sign in as an admin.
1. Locate the user account used to sign in to Microsoft services.
1. Assign the BPA Admin or BPA User role to this account. For more information, see [Access Business performance analytics](access-bpa.md).
1. Wait a few minutes for the role assignment to propagate.
1. Refresh the page or sign out and sign back in by using the correct account.

This process ensures the correct permissions are set, even if private browsing isn't available.

## Data visibility and history

### Why isn't my data showing up in Business performance analytics?

To maintain the accuracy of report data, Business performance analytics assesses the quality of the source data. If the assessments don't meet defined rules, Business performance analytics logs information in the **Bpa self help logs** table in Dataverse. To learn more, see [Business performance analytics self-help](/troubleshoot/dynamics-365/finance/business-performance-analytics/business-performance-analytics-self-help-overview).

Some customers might reach the storage capacity limits of their Power BI Embedded SKU by default. Business performance analytics uses the A3 tier. When the storage capacity is reached, the underlying dataset can't be refreshed or updated. This problem is exacerbated by the current Direct Lake import mode. Microsoft plans to transition to Direct Lake query by the end of the year to offload storage requirements and ensure uninterrupted dataset updates.

### How many years of data are available on reports?

Business performance analytics has data for the most recent eight quarters. This data availability is limited until the transition to Direct Lake mode at year end.

## Data refresh

### After setting up Business performance analytics, how often is the data refreshed?

Data refreshes twice per day, at 12:00:00 AM and 12:00:00 PM (Coordinated Universal Time). To see when a report's data was last refreshed, open the report. Near the top of the page, the rightmost item shows when the data for the report was last refreshed.

## Demo database swap after installing Business performance analytics

If you swap a demo database in sandbox or production after installing Business performance analytics, profile rehydration is required to reset the metadata that the transform jobs rely on. Contact support to reset the metadata after the swap.

## Reports

### What should I do if reports in Business performance analytics suddenly stop working and keep showing errors?

If you encounter a full-page error with the message "An unknown error has occurred. Try again or contact your app administrator" while opening reports, the following steps might help resolve it. These steps don't address problems like no data displayed, refresh errors, or blank pages.

>[!Note]
> These steps are safe to execute and prevent data loss.
> You don't need to set up Business performance analytics again.

1. Go to <https://make.powerapps.com/>.
1. From the **Environment picker** (upper right hand side), select the affected organization.
1. Go to **Solutions**.
1. Find the "msdyn_bpaanchor" and "msdyn_bpareports" solutions and uninstall them in that order.
1. Reinstall Business performance analytics. For more information, see [Install Business performance analytics](install-bpa.md#install-business-performance-analytics-1).
1. Follow steps one through four.
After installation is complete, it takes 12-24 hours before reports are available.

## Storage and capacity

### Why does Business performance analytics’ managed data lake storage keep growing, and how is it cleaned up?

Each time Business performance analytics refreshes, it transforms your source data into files in the Dataverse managed data lake without immediately deleting prior files. Older files are purged automatically after 30 days or earlier if usage hits 50 percent. In earlier releases, staging-table references sometimes blocked file deletion, so transform outputs accumulated until Microsoft engineers manually cleaned up every two weeks. As of the January 2025 update (v2.0.29241185+), those dependencies are removed and a three day retention policy is added via the autocleanup flight flag, which regularly clears out old files and dramatically reduces manual intervention.

> [!IMPORTANT]
> Customers affected by storage capacity growth after updating to Business performance analytics version 2.0.29241185 or later should contact support and request to enable the temporary files cleanup routine for their environment.

## BI entity customization

You can't customize BI entities. If you modify a BI entity with a custom view or custom data sources, the Business performance analytics installation fails.

## Uninstall

### How do I uninstall Business performance analytics?

You can uninstall Business performance analytics by using either code-based uninstallation or manual uninstallation. For detailed instructions, see [Uninstall Business performance analytics](uninstall-bpa.md).

> [!NOTE]
> If you uninstall and then reinstall Business performance analytics, you don't save any new reports that you created.

## Updates and releases

### How often are updates for Business performance analytics released?

New features and bug fixes are released every eight weeks.  

### How do I know when a new release of Business performance analytics is available?

You can view any updates that are available for Business performance analytics through Power Platform admin center. Sign in to the environment, and go to **Installed apps**.

### What should I do when a new release of Business performance analytics is available?

When a new release of Business performance analytics is available, you can update the package through Power Platform admin center.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. In your environment, go to **Installed apps**.
1. Select **Update available**.

### Is there any cost to install and use Business performance analytics during public preview?

No. Business performance analytics is included in the cost of your Dynamics 365 finance and operations license but is currently limited to the previous eight quarters and twice a day refresh.

## Calendar configurations

### Can Business performance analytics support multiple calendar configurations?

Yes, Business performance analytics supports multiple calendar configurations, including fiscal calendars such as 4-4-5, 4-5-4, and other custom non-Gregorian structures.

Business performance analytics’s semantic model includes a flexible date dimension (`Dim - Date (Accounting)`) with a `CalendarType` attribute that allows data to be analyzed according to a customer's preferred calendar setup. This design supports consistent financial and operational reporting across varying fiscal calendars.

>[!Note]
>Some native Power BI visuals like slicers with the *"Between"* style - only work with continuous Gregorian `DateTime` columns and might not reflect fiscal calendar logic. This limitation is of the visual, not the data model.

#### Recommendations

- Use the dropdown or list slicers for fiscal periods, years, or weeks.
- Use the `CalendarType` filter to dynamically adjust time context in reports.
- Design visuals and DAX measures to respond to the selected calendar configuration.

This approach ensures Business performance analytics remains adaptable to your business’s timekeeping practices while maintaining modeling best practices and analytic clarity.

### Flow ownership  

#### How do I reassign flow ownership when the original owner leaves the organization?

If flows in Business performance analytics become orphaned because the original owner left the organization, you need to reassign ownership. For more information, see [Reassign Business performance analytics flow ownership](bpa-flow-owner.md).

## Support and news

### How do I receive the latest news about Business performance analytics?

To get the latest updates about Business performance analytics, join the [Business performance analytics](https://engage.cloud.microsoft/main/org/microsoft.com/groups/eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIyMzc3NDU0NTUxMDQifQ) community on Microsoft Viva Engage.
