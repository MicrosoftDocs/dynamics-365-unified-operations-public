---
title: Resolve issues after entity store maintenance
description: Learn about procedures that must be completed after entity store maintenance, including if you are using application analytical workspaces.
author: MilindaV2
ms.author: milindav
ms.topic: article
ms.date: 04/09/2021
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global for most topics. Set Country/Region name for localizations
ms.search.validFrom: 2018-03-30
ms.dyn365.ops.version: Platform update 15
---

# Resolve issues after entity store maintenance

[!include[banner](../includes/banner.md)]

When maintenance is performed on the entity store, it impacts the following components:

- Application analytical workspaces.
- Entity store-based reports that have been deployed to PowerBI.com.

To resolve issues with these components, complete the procedures in this article.

> [!NOTE]
> There will be **no impact** to the normal operation of your application.

## If you are using application analytical workspaces

Application analytical workspaces and reports may not render data after certain maintenance operations are completed. The following screenshot shows an example of this.

![Analytical report is blank.](media/blank-powerbi.png)

To resolve this issue:

1. Sign in to the application.
2. Go to **System administration** > **Inquiries** > **Batch jobs**.
3. On the **Batch jobs** page, delete all pending batch jobs associated with the entity store. These batch jobs:

    - Will have a status of **Waiting**.
    - Will typically have a description of **Deploy measurement**, **Full reset**, or **Incremental update**.

    > [!NOTE]
    > The default description is **Deploy measurement** in older versions and **Full reset** in newer versions. If Data Lake integration is enabled with the option, **Trickle update Data Lake**, a batch job with the description, **Incremental update** is created. If the description has been customized, you can verify whether a batch job is associated with the entity store by looking at the class name. Batch jobs associated with the entity store will have a class name of **BIMeasurementDeployManagementEntityBatchJob**, **BIMeasurementProcessorFull**, or **BIMeasurementProcessorIncremental**.

4. Go to the **Entity store** page (**System Administration \> Setup \> Entity Store**).
5. Select all measurements that need to be refreshed.
6. Click **Refresh**, and then click **OK**.

After the refresh completes, the application analytical workspaces and reports will render data.

## If you have deployed entity store-based reports to PowerBI.com and are using the reports within PowerBI.com

Refresh the Entity store measurements as described above.

The reports deployed to PowerBI.com may produce errors like below,

- The credentials provided for the SQL source are invalid
- Login failed for user <user_name>
- A connection could not be made to the data source with the Name of '{"protocol":"tds","address":{"server":"spartan-srv-tip-d365opstip-074e5b077b83.database.windows.net","database":"db_d365opstip_hxqtcbpvlskm_edw_20250401_09155818_bf4d"},"authentication":null,"query":null}'.
Please try again later or contact support. If you contact support, please provide these details.

These errors may occur when the credentials of Entity store database got rotated and PowerBI.com reports still configured with old credentials.

To resolve this issue, user can follow either one of the solution mentioned below

1. Deploy a sample report using **Deploy Power BI report files** page by selecting **System Administration** \> **Setup** \> **Deploy Power BI files**. This will fix the above errors for any other Entity store based reports in PowerBI.com
   - You can use the sample report - 
   - This action need to be performed by all the PowerBI.com users who got this issue.

2. Redeploy the report that have this issue using the **Deploy Power BI report files** page by selecting **System Administration** \> **Setup** \> **Deploy Power BI files**.

> [!NOTE]
> For any other errors with PowerBI.com reports after the maintenance activity or above solution didn't fix the issue, you may need to delete the report and the related dataset, and then redeploy the report using the **Deploy Power BI report files** page by selecting **System Administration** \> **Setup** \> **Deploy Power BI files**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
