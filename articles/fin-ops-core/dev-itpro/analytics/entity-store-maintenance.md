---
title: Resolve issues after entity store maintenance
description: Learn about procedures that must be completed after entity store maintenance, including if you're using application analytical workspaces.
author: MilindaV2
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/15/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global for most topics. Set Country/Region name for localizations
ms.search.validFrom: 2018-03-30
ms.dyn365.ops.version: Platform update 15
---

# Resolve problems after entity store maintenance

[!include[banner](../includes/banner.md)]

When you perform maintenance on the entity store, it affects the following components:

- Application analytical workspaces.
- Entity store-based reports deployed to PowerBI.com.

To resolve problems with these components, follow the procedures in this article.

> [!NOTE]
> There's no impact to the normal operation of your application.

## If you're using application analytical workspaces

Application analytical workspaces and reports might not show data after certain maintenance operations. The following screenshot shows an example of this problem.

:::image type="content" source="media/blank-powerbi.png" alt-text="Screenshot of analytical report is blank.":::

To fix this problem:

1. Sign in to the application.
1. Go to **System administration** > **Inquiries** > **Batch jobs**.
1. On the **Batch jobs** page, delete all pending batch jobs that are associated with the entity store. These batch jobs:

    - Have a status of **Waiting**.
    - Typically have a description of **Deploy measurement**, **Full reset**, or **Incremental update**.

    > [!NOTE]
    > The default description is **Deploy measurement** in older versions and **Full reset** in newer versions. If you enable Data Lake integration by using the **Trickle update Data Lake** option, an **Incremental update** batch job is created. You can verify whether a batch job is associated with the entity store by looking at the class name if the description is customized. Batch jobs associated with the entity store have a class name of **BIMeasurementDeployManagementEntityBatchJob**, **BIMeasurementProcessorFull**, or **BIMeasurementProcessorIncremental**.

1. Go to the **Entity store** page (**System Administration \> Setup \> Entity Store**).
1. Select all measurements that need to be refreshed.
1. Select **Refresh**, and then select **OK**.

After the refresh finishes, the application analytical workspaces and reports show data.

## Deployed entity store-based reports to PowerBI.com and using the PowerBI.com reports

Refresh the Entity store measurements as described above.

The reports deployed to PowerBI.com may receive the following errors:

- The credentials provided for the SQL source are invalid.
- Login failed for user <user_name>.
- A connection couldn't be made to the data source with the Name of '{"protocol":"tds","address":{"server":"testsqlserver.database.windows.net","database":"test_edw_database"},"authentication":null,"query":null}'.
Try again later or contact support. When you contact support, provide these details:

:::image type="content" source="media/EntityStore-PowerBI-Creds-Issue.png" alt-text="Screenshot of PowerBI.com report with connection issue.":::

These errors can occur if the credentials of Entity store database are rotated and PowerBI.com reports are configured with old credentials.

To resolve this issue, follow one of the following solutions:

1. Redeploy the reports where the error occurred. Go to **System Administration** \> **Setup** \> **Deploy Power BI files**.
   - This action overwrites the current report and any customizations not in Microsoft Dynamics Lifecycle Services as PBIX are lost. If there are customizations in PowerBI.com, export the report as a PBIX file and upload it to Microsoft Dynamics Lifecycle Services for redeployment.

1. Deploy a [sample report](https://download.microsoft.com/download/4990e70d-1c68-45ab-9d23-2475a2b99596/Samplereport.pbix) Go to **System Administration** \> **Setup** \> **Deploy Power BI files**. This fixes the above errors for any Entity store based reports in PowerBI.com
   - Users encountering this issue need to perform this action individually.
     

> [!NOTE]
> For errors with the PowerBI.com reports after maintenance activity or if the above solution didn't resolve the issue, you may need to delete the report and the related dataset, and redeploy the report. To redeploy the report, go to **System Administration** \> **Setup** \> **Deploy Power BI files**. Any customizations not in Microsoft Dynamics Lifecycle Services as PBIX are lost.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
