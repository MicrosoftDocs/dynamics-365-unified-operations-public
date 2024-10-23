---

title: Connect Business performance analytics data to Microsoft Fabric (preview)
description: This article explains how to link your Business performance analytics data to Microsoft Fabric.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 8/28/2024
ms.topic: article
ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
ms.application-unique-name: msdyn_BusinessPerformanceAnalytics
---

# Connect Business performance analytics data to Microsoft Fabric (preview)

[This article is prerelease documentation and is subject to change.].

Business performance analytics enables organizations to extend their existing data warehouse by using Microsoft Fabric shortcuts to connect the Business performance analytics dimensional data model to it.

Business performance analytics uses Dataverse direct integration with Fabric and provides the following benefits:

- You don't have to export data, build data pipelines, or use third-party integration tools.
- You don't have to transform the data in the star schema. Business performance analytics does this transformation for you.
- Shortcuts from Business performance analytics directly to OneLake enable data to stay in Dataverse while authorized users work with data in Fabric.

As part of this capability, Business performance analytics generates an enterprise-ready lakehouse, a SQL analytics endpoint, and a default semantic model (Power BI dataset) for your organization's Business performance analytics dimensional data. Data analysts, data engineers, and database administrators can then more easily combine Business performance analytics data with data that's present in OneLake by using Spark, Python, or SQL.

As data is updated, changes are automatically reflected in your lakehouse.

## Prerequisites

Before you install Fabric and use it with business performance analytics, the following prerequisites must be completed:

1. You must have a Power BI premium capacity license or Fabric capacity. For more information, see [Link your Dataverse environment to Microsoft Fabric and unlock deep insights
](/power-apps/maker/data-platform/azure-synapse-link-view-in-fabric#prerequisites) for the list of premium capacity Power BI SKUs. When setting up a Fabric workspace, this translates to a Pro, Trial, or Premium per-user capacity.
2. The workspace that's linked to Dataverse must be assigned to premium or Fabric capacity in the same region as your Business performance analytics Dataverse environment. If you create a new workspace, you must have access to Power BI or Fabric premium capacity in the same region as your Dataverse environment. To confirm that you have access to the required premium capacity, follow these steps:

    1. In Power BI (https://app.powerbi.com), open the workspace.
    2. Select **Workspace settings** \> **Premium**.
    3. Confirm that **Trial** or **Premium** is selected as the capacity.

3. Your Dataverse environment must be linked to a Fabric tenant. In Power BI, go to **Power BI settings** \> **Manage connections and gateways**, and verify that your environment has an established connection. If your environment isn't linked, follow these steps to link it:

    1. Go to **Power BI settings** \> **Manage connections and gateways**.
    2. Select **New**, and then select **Cloud**.
    3. In the **Connection type** field, select **Dataverse**.
    4. In the **Environment domain** field, enter the environment URL of the environment where Business performance analytics is installed. You can find the environment URL on the **Environment details** page in Power Platform admin center.
    6. In the **Authentication method** field, select **OAuth2.0**.
    7. Select **Edit credentials**, and complete authentication.
    8. In the **Encrypted connection** field, select **Encrypted**.
    9. In the **Privacy level** field, select **Organizational**.
    10. Select **Create**.

    > [!NOTE]
    > In prerequisite 3.4, the enrivonment URL should not start with "https://" and should not end in "/" If your URL does, please delete this prefix and suffix.

## Link Business performance analytics data to the organization's Fabric workspace

To link Business performance analytics data to your organization's Fabric workspace, follow these steps.

1. In Business performance analytics, select the **Administration** tab.
2. Go to **Link with Microsoft Fabric**, and select **Manage**.
3. Select **Link Fabric**.
4. Specify the Fabric workspace ID to create the lake shortcut for the Business performance analytics dimensional model. Confirm that the workspace is linked to your Business performance analytics Dataverse environment.

    > [!NOTE]
    > The workspace must be in the same Azure region as the Dataverse environment.

5. Select **Connect**.

    The creation of Fabric shortcuts takes a few minutes. After the shortcuts are created, the **Fabric status** value is **Created**. If the shortcuts aren't created, the value is **Failed**. In this case, repeat steps 3 through 5 to try again.

6. After the **Fabric status** value is **Created**, select **View in Microsoft Fabric** to go to the linked lakehouse in your Fabric workspace.
7. You should now be able to access Business performance analytics dimensional model tables via shortcuts in your Fabric workspace.

    > [!NOTE]
    > No updates or deletions on the dimensional model tables are permitted from the Fabric workspace.

    The lakehouse, an SQL analytics endpoint, and a default semantic model are created, and Business performance analytics tables are linked to the lakehouse via shortcuts.

8. Before you share the data with others, you can secure it in the Fabric workspace.

The lakehouse, SQL endpoint, and Power BI dataset are updated with new data as changes occur in Dataverse.

When a new Business performance analytics update is released, it might contain new tables or new columns in the Business performance analytics dimensional model. (This type of change is known as a *metadata change*.) To make Fabric reflect the changes, in Business performance analytics, select the **Administration** tab, go to **Connect with Microsoft Fabric**, select **Manage**, and then select **Refresh Fabric tables**. You might have to review the report and the downstream data flows to ensure that they aren't affected by the changes.

If you no longer need the shortcuts, select **Unlink** on the **Manage** page in Business performance analytics. The link from the Fabric workspace to your Dataverse environment is removed. When you unlink Business performance analytics data from the Fabric workspace, the Fabric lakehouse, SQL analytics endpoint, and default semantic model are removed.

> [!IMPORTANT]
> Business performance analytics manages the shortcuts. Don't delete or remove them directly in Fabric.
 
## Extend the Business performance analytics dataset with your own data sources

This section shows how you can create a custom Power BI dataset that extends the Business performance analytics dataset with your own data sources. This functionality lets you use the Business performance analytics dataset as part of your own reporting capabilities in Power BI. In this way, you can create more comprehensive and tailored reports that harness the power of Business performance analytics and your own customized business insights.

### Publish the Business performance analytics dataset in Power BI Desktop to Fabric

> [!NOTE]
> Before you begin this procedure, you must link Business performance analytics data to your Fabric workspace as described earlier in this article.

1. Download the Business performance analytics dataset
    a.	Log into https://make.powerapps.com/.
    b.	Go to **All** and search for msdyn_BpaReports solution.
2. Click on finance and operations dataset.
3. From the report details page, click **Actions** > **Download report**. Note the download location.
4. Upload the Business performance analytics dataset:
    -	In https://app.powerbi.com, go to your workspace and upload the Business performance analytics dataset from the location in Step 3.
5. Connect Dataset to Lakehouse:
    -	Find the SQL Analytics Endpoint in the workspace (under the Lakehouse) and copy the SQL connection string.
    -	In the Semantic Model, go to **Settings** > **Parameters** and enter the connection string.
    -	Note: Reload the page and re-enter the credentials.
6.	Validate the connection:
    -	Refresh settings and edit data source credentials, ensuring OAuth authentication.
    -	Refresh the dataset to see the tables from Business performance analytics.


### Use the Business performance analytics dataset in Power BI desktop

1. Open the downloaded .pbix file in Power BI Desktop, select **Transform data** \> **Edit Parameters**.
2. Find the SQL Analytics Endpoint in the workspace (under the Lakehouse), copy the SQL connection string.
3. Enter SQL Connection string as CDSOrgURL 
4. Select **OK** and refresh.
5. Follow any authentication prompts that appear. Sign in as the same user who published the Business performance analytics dataset to Fabric.
6. Validate that data is being refreshed from the dataset. You receive an initial notification that the refresh is in progress. You then receive a notification that indicates whether the refresh was successful or unsuccessful.
7. You now have a dataset that you can extend so that it includes other data sources and create new measures on. 
8. To includes other data sources in your Fabric workspace, find the second lakehouse that you want to include in the custom dataset, and then find the SQL analytics endpoint that is nested under it. Select the ellipsis (**&hellip;**) next to the name of the endpoint, and then select **Copy SQL connection string**.
9. In Power BI Desktop, select **Get data** \> **SQL server**.
10. When you're notified that a Direct Query connection is required, select **Add a local model**.
11. In the prompt that appears, select the entire dataset, and then select **Submit**.
12. When you're prompted for the server, enter the SQL Server connection string that you copied earlier.
13. Select **Direct query**, and then select **OK**.
14. Find the custom lakehouse that you added earlier, expand it, and select the tables to include.
15. Select **Load**.
16. When you're warned about the potential security risk, select **OK**.
17. You should notice that the new data is being loaded.
18. Select **File** \> **Save** to save the new dataset as a PBIX file.

> [!NOTE]
> Authentication issues: Ensure you are using OAuth 2.0 for authentication when creating connections.
> Refresh delays: After each configuration, allow up to 2 minutes for the dataset or Lakehouse to refresh.
> Dataset not loading: Double-check the SQL Connection String and parameters in Power BI and BPA.

