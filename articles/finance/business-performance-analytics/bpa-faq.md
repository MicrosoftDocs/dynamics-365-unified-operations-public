---
title: Business performance analytics FAQ
description: This article answers some frequently asked questions about Business performance analytics, including questions about signing up for public previews of analytics.
author: jinniew
ms.author: jiwo
ms.topic: faq
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 9/11/2024
---

# Business performance analytics FAQ

This article answers frequently asked questions about Business performance analytics.

### I received an error during the installation of Business performance analytics. How do I fix it?

The following errors are likely to occur if another operation is in progress during the installation of Business performance analytics. If these errors persist, retry the installation.

- "There's another \[RibbonMetadataGeneration\] running at this moment."
- "Issues with enabling change tracking: msdyn\_BpaTablesVirtualEntities."
- "Import failed - errorCode: 0Description: Unable to complete updates to the Track changes option for table."
- "Flight EnableSqlRowVersionChangeTracking isn't enabled. The functionality requires enabling sql row version change tracking feature. Enable flight EnableSqlRowVersionChangeTracking."

### How do I retry the installation of Business performance analytics if it fails?

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Microsoft Dataverse admin credentials.
2. Go to **Environments**, and select **Dynamics 365 Apps**.
3. Find **Business performance analytics**, and select **Installation failed**.
4. Select the link to retry the installation, and monitor the app installation process.

### I am having trouble opening Business Performance Analytics. How do I fix this?
If you are accessing Business Performance Analytics from the maker portal, please click 'Play' in the top right corner to avoid viewing the app in editor mode.

### Why isn't my data showing up in Business performance analytics?

To maintain the accuracy of report data, Business performance analytics assesses the quality of the source data. If the assessments don't meet defined rules, Business performance analytics logs information in the **Bpa self help logs** table in Microsoft Dataverse. To learn more, see [Business performance analytics self-help](/troubleshoot/dynamics-365/finance/business-performance-analytics/business-performance-analytics-self-help-overview).

Some customers might reach the storage capacity limits of their Power BI Embedded SKU. In this case, the Power BI dataset that they need for reports can't be updated. By default, Business performance analytics uses the A3 SKU for Power BI Embedded. We recommend that you scale up your SKU to raise your Power BI Embedded storage capacity. For more information, see [Capacity and SKUs in Power BI embedded analytics](/power-bi/developer/embedded/embedded-capacity).

### Why is Business performance analytics using a lot of managed data lake storage in Dataverse?

As part of the data pipeline for Business performance analytics, your data is transformed to fit our dimensional data model. This process creates files that are saved to the managed data lake. The data transformation process occurs every time Business performance analytics refreshes its data. It generates new files in the managed data lake without deleting the old, obsolete files. The old files are deleted in 30 days, or our team manually deletes them when Business performance analytics uses 50 percent or more of the managed data lake's storage capacity.

### What's the estimated time that's required to set up Business performance analytics?

The setup of the Business performance analytics app takes up to 60 minutes.

### When will data be available in reports after Business performance analytics is installed?

Data will be available 24 hours after installation is completed. The time that's required to load data depends on the data size.

### How many years of data are available on reports?

Business performance analytics has data for the current calendar year plus the previous three calendar years.

### After Business performance analytics is set up, how often is the data refreshed?

Data is refreshed twice per day, at 12:00:00 AM and 12:00:00 PM (Coordinated Universal Time). To view exactly when a report's data was last refreshed, open the report. Near the top of the page, the rightmost item shows when the data for the report was last refreshed.

### How long does it take for fresh data to be available every day on Business performance analytics reports?

The amount of time that's required depends on the volume of data. However, there should be fresh data every 24 hours.

### How often will updates for Business performance analytics be released?

- **New features** – Once per month 
- **Bugs** – Bi-weekly 

### Is there any cost to install and use Business performance analytics during public preview?

No. The data is restricted to the current calendar year plus the previous three calendar years.

### How do I know when a new release of Business performance analytics is available?

You can view any updates that are available for Business performance analytics through Power Platform admin center. Sign in to the environment, and go to **Installed apps**.

### What should I do when a new release of Business performance analytics is available?

When a new release of Business performance analytics is available, you can update the package through Power Platform admin center.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
2. In your environment, go to **Installed apps**.
3. Select **Update available**.

### During public preview, what can I expect each time that data is restored from production to sandbox?

As a customer, you might want to restore data from your production environment to a sandbox environment, so that you can validate new data as part of Business performance analytics. In public preview, data won't be able to move again from production to sandbox. If you want to move data again from production to sandbox, delete the existing environment, create new environment and install Business performance analytics. Any new data changes done in the Dynamics 365 finance and operations apps UI can still be seen in Business performance analytics. The preceding limitation is only for changes via data movement from production to sandbox.

### How do I receive the latest news about Business performance analytics?

To receive the latest updates about Business performance analytics, join the Business performance analytics Yammer group.

1. Complete the [FAR Preview Agreement](https://forms.office.com/r/wfcUBtP67J).
2. Join the [Dynamics 365 and Power Platform Preview Programs](https://www.yammer.com/dynamicsaxfeedbackprograms/#/home).
3. Join the [Business performance analytics Yammer](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=73748324352&view=unviewed).
