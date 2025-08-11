---
title: Business performance analytics FAQ
description: This article answers some frequently asked questions about Business performance analytics, including questions about signing up for public previews of analytics.
author: jinniew
ms.author: jiwo
ms.topic: faq
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 06/09/2025
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
2. Go to **Environments**, and select **Dynamics 365 Apps**.
3. Find **Business performance analytics**, and select **Installation failed**.
4. Select the link to retry the installation, and monitor the app installation process.

### What's the estimated time required to set up Business performance analytics?

The setup of the Business performance analytics app takes up to 60 minutes. However, it may take up to 24 hours before your data is available in Business performance analytics after installation is completed. 

## Accessing the App
### I'm having trouble opening Business performance analytics. What can I do? 
If you're accessing Business performance analytics from the maker portal, click **Play** in the top right corner to avoid viewing the app in editor mode.

## Data visibility and history
### Why isn't my data showing up in Business performance analytics?

To maintain the accuracy of report data, Business performance analytics assesses the quality of the source data. If the assessments don't meet defined rules, Business performance analytics logs information in the **Bpa self help logs** table in Dataverse. To learn more, see [Business performance analytics self-help](/troubleshoot/dynamics-365/finance/business-performance-analytics/business-performance-analytics-self-help-overview).

Some customers may reach the storage capacity limits of their Power BI Embedded SKU by default. Business performance analytics uses the A3 tier and when that happens, the underlying dataset can't be refreshed or updated. This is exacerbated by our current Direct Lake import mode. We plan to transition to Direct Lake query by year end to offload storage requirements and ensure uninterrupted dataset updates.

### How many years of data are available on reports?

Business performance analytics has data for the most recent eight quarters. This is limited until the transition to Direct Lake mode at year end.

## Data refresh
### After Business performance analytics is set up, how often is the data refreshed?

Data is refreshed twice per day, at 12:00:00 AM and 12:00:00 PM (Coordinated Universal Time). To view exactly when a report's data was last refreshed, open the report. Near the top of the page, the rightmost item shows when the data for the report was last refreshed.

## Reports

### What should I do if reports in Business performance analytics suddenly stop working and keep showing errors?

If you encounter a full-page error with the message "An unknown error has occurred. Try again or contact your app administrator" while opening reports, the following steps may help resolve it. These steps don't address issues like no data displayed, refresh errors, or blank pages.

>[!Note]
> These steps are safe to execute and prevents data loss
> This doesn't require to set up Business performance analytics again.

1. Go to https://make.powerapps.com/
2. From the **Environment picker** (upper right hand side), select the affected organization.
3. Go to **Solutions**.
4. Find the "msdyn_bpaanchor" and "msdyn_bpareports" solutions and uninstall them in that order.
5. Reinstall Business performance analytics. For more information, see [Install Business performance analytics](install-bpa.md#install-business-performance-analytics-1).
6. Follow steps one through four. 
After installation is complete, it will be 12-24 hours before reports are available.


## Storage and capacity
### Why does Business performance analytics’ managed data lake storage keep growing, and how is it cleaned up?

Each time Business performance analytics refreshes, your source data are transformed into files in the Dataverse managed data lake without immediately deleting prior files. Older files are purged automatically after 30 days or earlier if usage hits 50 percent. In earlier releases, staging-table references sometimes blocked file deletion, so transform outputs accumulated until Microsoft engineers manually cleaned up every two weeks. As of the January 2025 update (v2.0.29241185+), those dependencies are removed and added a three day retention policy via the autocleanup flight flag, which regularly clears out old files and dramatically reduces manual intervention.

> [!IMPORTANT]
> Customers affected by storage capacity growth after updating to Business performance analytics version 2.0.29241185 or later should contact support and request to enable the temporary files cleanup routine for their environment.

## Uninstall
### How do I uninstall Business performance analytics?

There are two ways to uninstall Business performance analytics: using code-based uninstallation or manual uninstallation. For detailed instructions, see [Uninstall Business performance analytics](uninstall-bpa.md).

> [!NOTE]
> If you uninstall and then reinstall Business performance analytics, no new reports that were created are saved.

## Updates and releases
### How often are updates for Business performance analytics released?
New features and bugs are released every eight weeks.  

### How do I know when a new release of Business performance analytics is available?

You can view any updates that are available for Business performance analytics through Power Platform admin center. Sign in to the environment, and go to **Installed apps**.

### What should I do when a new release of Business performance analytics is available?

When a new release of Business performance analytics is available, you can update the package through Power Platform admin center.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
2. In your environment, go to **Installed apps**.
3. Select **Update available**.
   
### Is there any cost to install and use Business performance analytics during public preview?

No. Business performance analytics is included in the cost of your Dynamics 365 finance and operations license but is currently limited to the previous eight quarters and twice a day refresh. 

## Calendar configurations
### Can Business performance analytics support multiple calendar configurations?
Yes, Business performance analytics supports multiple calendar configurations, including fiscal calendars such as 4-4-5, 4-5-4, and other custom non-Gregorian structures.

Business performance analytics’s semantic model includes a flexible date dimension (`Dim - Date (Accounting)`) with a `CalendarType` attribute that allows data to be analyzed according to a customer's preferred calendar setup. This design supports consistent financial and operational reporting across varying fiscal calendars.

>[!Note]
>Some native Power BI visuals like slicers with the *"Between"* style—only work with continuous Gregorian `DateTime` columns and may not reflect fiscal calendar logic. This is a limitation of the visual, not the data model.

#### Recommendations:
- Use the dropdown or list slicers for fiscal periods, years, or weeks.
- Use the `CalendarType` filter to dynamically adjust time context in reports.
- Design visuals and DAX measures to respond to the selected calendar configuration.

This approach ensures Business performance analytics remains adaptable to your business’s timekeeping practices while maintaining modeling best practices and analytic clarity.

## Support and news
### How do I receive the latest news about Business performance analytics?

To receive the latest updates about Business performance analytics, join the Business performance analytics Viva Engage group.
Join the [Business performance analytics Viva Engage](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=73748324352&view=unviewed).
