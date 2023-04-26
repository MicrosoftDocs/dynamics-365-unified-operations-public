---
# required metadata

title: Business performance analytics FAQ
description: This article answers frequently asked questions about business performance analytics.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 04/24/2023
ms.topic: faq
ms.prod: 
ms.technology:
ms.custom:

---
# Business performance analytics FAQ

This article answers frequently asked questions about business performance analytics.

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpateam@microsoft.com>.

### How do I sign up for the gated public preview of business performance analytics?

We're implementing a gated public preview to ensure that we can provide a successful experience for our customers and obtain valuable feedback about transaction volumes. Our initial focus is on customers who have transaction volumes in the millions, but fewer than 10 million rows. We aim to expand to hundreds of thousands of rows by June. We want to avoid onboarding customers who have high transaction volumes before we can effectively support them.

### What's the estimated time that's required to set up business performance analytics?

The setup of business performance analytics will take about 30 minutes. However, it will take 12 to 24 hours for data to be available on reports.

### I received an error during the installation of business performance analytics. How do I fix it?

The following errors are likely to occur if another operation is in progress during the installation of business performance analytics. If these errors persist, retry the installation.

- "There's another \[RibbonMetadataGeneration\] running at this moment."
- "Issues with enabling Change tracking: msdyn\_BpaTablesVirtualEntities."
- "Import Failed - errorCode: 0Description: Unable to complete updates to the Track changes option for table."
- "Flight EnableSqlRowVersionChangeTracking isn't enabled. The functionality requires enabling sql row version change tracking feature. Enable flight EnableSqlRowVersionChangeTracking."

### How do I retry the installation of business performance analytics if it fails?

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Microsoft Dataverse admin credentials.
2. Go to **Environments**, and select **Dynamics 365 Apps**.
3. Find **Business performance analytics**, and select **Installation failed**.
4. Select the link to retry the installation, and monitor the app installation process.

### When will data be available in reports after the app is installed for the first time?

Data will be available within 12 to 24 hours after app installation is completed.

### How will I know when data is available on reports?

We recommend that you check 24 hours after the installation of business performance analytics is completed.

### How many years of data will be available on reports?

Business performance analytics will have data for the current fiscal year plus the previous two years.

### After business performance analytics is set up, how often is the data refreshed?

Data will be refreshed once per day, at 00:00:00 AM (UTC).

### How long does it take for fresh data to be available daily on business performance analytics reports?

The amount of time that's required depends on the volume of data. However, there should be fresh data every 24 hours.

### How do I uninstall business performance analytics?

Business performance analytics can be manually uninstalled through Power Platform admin center. The solutions must be manually deleted in the following order through Power Platform admin center. The approximate time that's required to delete all the solutions is 20 minutes.

1. Business performance analytics performance analytics anchor solution
2. Business performance analytics performance analytics plugins solution
3. Business performance analytics performance analytics solution
4. Business performance analytics performance analytics permissions TIP
5. Business performance analytics performance analytics tables
6. Business performance analytics performance analytics controls
7. Business performance analytics performance analytics tables anchor solution
8. Business performance analytics performance analytics pipeline plugins solution
9. Business performance analytics performance analytics tables user roles TIP
10. Business performance analytics performance analytics analytical tables
11. Business performance analytics performance analytics tables transformation job flows TIP
12. Business performance analytics performance analytics data processing configuration TIP
13. Business performance analytics performance analytics tables data lake synchronization
14. Business performance analytics performance analytics tables standard entities
15. Business performance analytics performance analytics virtual entities
16. Business performance analytics performance analytics managed data lake TIP
17. Business performance analytics performance analytics tables security TIP

To delete each of the preceding solutions, follow these steps.

1. In the maker portal, on the **Solution** tab, select the solution to delete, and then select **Delete**.
2. Select **Delete** again to confirm the operation.
3. Wait for the **Deleting** message box to disappear. If the operation is successful, you receive the following message: "Successfully deleted solution."

### How often will updates for business performance analytics be released?

- **New features:** Once per month (the thirtieth of every month)
- **Bugs:** Bi-weekly 
- **Hotfixes:** On demand

### Is there any cost to install and use business performance analytics during public preview?

No. The data is restricted to the current fiscal year plus the previous two years.

### How do I know when a new release of business performance analytics is available?

You can view any updates that are available for business performance analytics through Power Platform admin center. Sign in to the environment, and go to **Installed apps**.

### What should I do when a new release of business performance analytics is available?

When a new release of business performance analytics is available, you can update the package through Power Platform admin center.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
2. In your environment, go to **Installed apps**.
3. Select **Update available**.

### During public preview, what can I expect each time that data is restored from production to sandbox?

As a customer, you might want to restore data from your production environment to a sandbox environment, so that you can validate new data as part of business performance analytics. After data is restored, the data pipeline will continue to run on its defined schedule.
