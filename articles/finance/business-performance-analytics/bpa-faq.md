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
# Business performance analystics FAQ

This article answers frequently asked questions about business performance analytics.

>[!NOTE]
>The functionality noted in this article is available as part of a preview release. The content and the functionality are subject to change. 
>For more information about participating in public preview for business performance analytics, contact bpateam@microsoft.com. 

### How to sign up for Business performance analytics gated public preview?  

We are implementing a gated public preview to ensure that we can provide a successful experience for our customers and obtain valuable feedback on transaction volumes.
Our initial focus is on customers with transaction volumes ranging from millions to less than 10 million rows, and we aim to expand to hundreds of thousands of rows by 
June. We want to avoid onboarding customers with high transaction volumes before we have the necessary capability to support them effectively. 

### What is the estimated time required to set up business performance analytics? 

Business performance analytics set up will take around 30 minutes, but it will take 12 to 24 hours for data to be available in reports. 

### I got an error during the installation of business performance analytics. How do I fix the error? 

The following errors are likely to happen if another operation is in progress during the installation of business performance analytics. If these errors persist, you 
may retry the installation. 
 1. There is another [RibbonMetadataGeneration] running at this moment 
 2. Issues with enabling Change tracking: msdyn_BpaTablesVirtualEntities 
 3. Import Failed - errorCode: 0Description: Unable to complete updates to the Track changes option for table.
 4. Flight EnableSqlRowVersionChangeTracking not enabled. The functionality requires enabling sql row version change tracking feature. Enable flight EnableSqlRowVersionChangeTracking.

### How do I retry the installation of business performance analytics if it fails?  

 1. Go to the Power Platform Admin Center and login with Dataverse admin credentials. 
 2. Go to **Environments**, click **Dynamics 365 Apps**.  
 3. Find **Business performance analytics** and click **Installation failed**. 
 4. Click the retry installation link and monitor the app installation. 

### When will data be available in reports after first time app installation? 

Data will be available within 12 to 24 hours once app installation is done. 

### How will I know when data is available in reports? 

We suggest you check after 24 hours after business performance analytics is complete. 

### How many years of data will be available in reports? 

Business performance analytics will have Previous 2 Years + Current Fiscal Year of data. 

### After business performance analytics set up is complete, how often is the data refreshed?  
Data will be refreshed once in 24 hours daily at 00:00:00 AM GMT hours. 

### How long does it take for fresh data to be available daily in Business performance analytics reports? 

It depends on the volume of data, you should be able to see fresh data every 24 hours.  

### How to uninstall business performance analytics? 

Business performance analytics can be uninstalled manually from Power Platform Admin Center using process below. It needs to be manually deleted in order below from the Power Platform Admin Center. Approximate time to delete all solutions is about 20 mins. 

| No | Solution Name                                                                            |
| -- | ---------------------------------------------------------------------------------------- |
| 1  | Business performance analytics performance analytics anchor solution                     |
| 2  | Business performance analytics performance analytics plugins solution                    |
| 3  | Business performance analytics performance analytics solution                            |
| 4  | Business performance analytics performance analytics permissions TIP                     |
| 5  | Business performance analytics performance analytics tables                              |
| 6  | Business performance analytics performance analytics controls                            |
| 7  | Business performance analytics performance analytics tables anchor solution              |
| 8  | Business performance analytics performance analytics pipeline plugins solution           |
| 9  | Business performance analytics performance analytics tables user roles TIP               |
| 10 | Business performance analytics performance analytics analytical tables                   |
| 11 | Business performance analytics performance analytics tables transformation job flows TIP |
| 12 | Business performance analytics performance analytics data processing configuration TIP   |
| 13 | Business performance analytics performance analytics tables data lake synchronization    |
| 14 | Business performance analytics performance analytics tables standard entities            |
| 15 | Business performance analytics performance analytics virtual entities                    |
| 16 | Business performance analytics performance analytics managed data lake TIP               |
| 17 | Business performance analytics performance analytics tables security TIP                 |

To delete, follow the steps below on the **Solution** tab in the maker portal:  
 1. Select the solution you want to uninstall, click **Delete**.
 2. Click **Delete** again to confirm. 
 4. Wait for the **Deleting** dialog to disappear. 
 5. **Successfully deleted solution** message confirms that the deletion is successful. 

### How often will updates for business performance analytics be released?  

New features: Monthly once [30th of every month] 
Bugs: Bi-weekly 
Hot fixes: On demand  

### Is there any cost to install and use Business performance analytics in public preview? 
No, and the years of data are restricted to Current year and the last two fiscal years. 

### How do I know when a new business performance analytics release is available? 
Any updates that are available for business performance analytics can be seen through Power Platform Admin Center. You need to login to the environment and go to the 
installed apps.  

### What should I do when a new Business performance analytics release is available? 
When new Business performance analytics release is available, you can go to Power Platform Admin Center and update the package. 
1. Login to Power Platform Admin Center. 
2. Go to **Installed apps** in your environment.
3. Click **Update available**.   

### During public preview, what can I expect when data is restored from Production to Sandbox every time?  

As a customer you might want to restore data from production to sandbox to validate new data as part of business performance analytics. After data is restored, the data 
pipeline will continue to run on it's defined schedule. 






