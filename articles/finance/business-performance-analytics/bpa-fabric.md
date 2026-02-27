---

title: Connect Business performance analytics data to Microsoft Fabric
description: This article explains how to link your Business performance analytics data to Microsoft Fabric.
author: yvishwa
ms.author: yvishwa
ms.reviewer: twheeloc 
ms.date: 2/27/2026
ms.topic: how-to
ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
ms.application-unique-name: msdyn_BusinessPerformanceAnalytics
---

# Connect Business performance analytics data to Microsoft Fabric

Business performance analytics enables organizations to extend their existing data warehouse by using Microsoft Fabric shortcuts to connect the Business performance analytics dimensional data model to it.

Business performance analytics uses Dataverse direct integration with Fabric and provides the following benefits:

- You don't have to export data, build data pipelines, or use third-party integration tools.
- You don't have to transform the data in the star schema. Business performance analytics handles this transformation.
- By using shortcuts from Business performance analytics directly to OneLake, data stays in Dataverse while authorized users work with data in Fabric.

As part of this capability, Business performance analytics generates an enterprise-ready lakehouse, a SQL analytics endpoint, and a default semantic model (Power BI dataset) for your organization's Business performance analytics dimensional data. Data analysts, data engineers, and database administrators can then more easily combine Business performance analytics data with data that's present in OneLake by using Spark, Python, or SQL.

As you update data, changes automatically reflect in your lakehouse.

## Prerequisites

Before you install Fabric and use it with business performance analytics, complete the following prerequisites:

1. You must have a Power BI premium capacity license or Fabric capacity. For more information, see [Link your Dataverse environment to Microsoft Fabric and unlock deep insights](/power-apps/maker/data-platform/azure-synapse-link-view-in-fabric#prerequisites) for the list of premium capacity Power BI SKUs. When setting up a Fabric workspace, this requirement translates to a Pro, Trial, or Premium per-user capacity.
1. Assign premium or Fabric capacity in the same region as your Business performance analytics Dataverse environment to the workspace that's linked to Dataverse. If you create a new workspace, you must have access to Power BI or Fabric premium capacity in the same region as your Dataverse environment. To confirm that you have access to the required premium capacity, follow these steps:

    1. In [Power BI](https://app.powerbi.com/), open the workspace.
    1. Select **Workspace settings** \> **Premium**.
    1. Confirm that **Trial** or **Premium** is selected as the capacity.

1. Link your Dataverse environment to a Fabric tenant. In Power BI, go to **Power BI settings** \> **Manage connections and gateways**, and verify that your environment has an established connection. If your environment isn't linked, follow these steps to link it:

    1. Go to **Power BI settings** \> **Manage connections and gateways**.
    1. Select **New**, and then select **Cloud**.
    1. In the **Connection type** field, select **Dataverse**.
    1. In the **Environment domain** field, enter the environment URL of the environment where Business performance analytics is installed. You can find the environment URL on the **Environment details** page in Power Platform admin center.

        > [!NOTE]
        > The environment URL that you enter shouldn't start with "https://" or end with a slash (/). Delete these elements if they're included.

    1. In the **Authentication method** field, select **OAuth2.0**.
    1. Select **Edit credentials**, and complete authentication.
    1. In the **Encrypted connection** field, select **Encrypted**.
    1. In the **Privacy level** field, select **Organizational**.
    1. Select **Create**.

## Link Business performance analytics data to the organization's Fabric workspace

To link Business performance analytics data to your organization's Fabric workspace, follow these steps:

1. In Business performance analytics, select the **Administration** tab.
1. Go to **Link with Microsoft Fabric**, and select **Manage**.
1. Select **Link Fabric**.
1. Specify the Fabric workspace ID to create the lake shortcut for the Business performance analytics dimensional model. Confirm that the workspace is linked to your Business performance analytics Dataverse environment.

    > [!NOTE]
    > The workspace must be in the same Azure region as the Dataverse environment.

    > [!IMPORTANT]
    > Confirm that you're using the correct workspace ID. The workspace ID is the GUID found in the URL when you open the workspace. Don't use a workspace identity ID, as it's not the same and causes problems with Business performance analytics linking and results in **Workspace not found** errors.

1. Select **Connect**.

    The creation of Fabric shortcuts takes a few minutes. After the shortcuts are created, the **Fabric status** value is **Created**. If the shortcuts aren't created, the value is **Failed**. In this case, repeat steps 3 through 5 to try again.

1. After the **Fabric status** value is **Created**, select **View in Microsoft Fabric** to go to the linked lakehouse in your Fabric workspace.
1. You can now access Business performance analytics dimensional model tables via shortcuts in your Fabric workspace.

    > [!NOTE]
    > You can't update or delete dimensional model tables from the Fabric workspace.

    The lakehouse, an SQL analytics endpoint, and a default semantic model are created, and Business performance analytics tables are linked to the lakehouse via shortcuts.

1. Before you share the data with others, you can secure it in the Fabric workspace.

The lakehouse, SQL endpoint, and Power BI dataset are updated with new data as changes occur in Dataverse.

When a new Business performance analytics update is released, it might contain new tables or new columns in the Business performance analytics dimensional model. This type of change is known as a *metadata change*. To make Fabric reflect the changes, in Business performance analytics, select the **Administration** tab, go to **Connect with Microsoft Fabric**, select **Manage**, and then select **Refresh Fabric tables**. You might have to review the report and the downstream data flows to ensure that they aren't affected by the changes.

If you no longer need the shortcuts, select **Unlink** on the **Manage** page in Business performance analytics. The link from the Fabric workspace to your Dataverse environment is removed. When you unlink Business performance analytics data from the Fabric workspace, the Fabric lakehouse, SQL analytics endpoint, and default semantic model are removed.

> [!IMPORTANT]
> Business performance analytics manages the shortcuts. Don't delete or remove them directly in Fabric.

## Extend the Business performance analytics dataset with your own data sources

This section shows how to create a custom Power BI dataset that extends the Business performance analytics dataset with your own data sources. By using this functionality, you can use the Business performance analytics dataset as part of your own reporting capabilities in Power BI. You can create more comprehensive and tailored reports that harness the power of Business performance analytics and your own customized business insights.

### Publish the Business performance analytics dataset in Power BI Desktop to Fabric

> [!NOTE]
> Before you begin this procedure, link Business performance analytics data to your Fabric workspace as described earlier in this article.

### Step 1: Download the Business performance analytics semantic (.pbix)

1. Go to the **Administration** home page within the Business performance analytics app.
1. On the **Download semantic model** card, select **Download**.

### Step 2: Open the dataset in Power BI Desktop

1. Launch **Power BI Desktop**.
1. Open the downloaded `.pbix` file.

### Step 3: Update dataset parameters

1. In Power BI Desktop, go to **Home > Transform data > Edit parameters**.
1. Update the following parameters:
   - `CdsOrgUrl` → Paste the SQL Analytics Endpoint connection string from your Fabric Lakehouse.
   - `AnalyticalDataDatabase` → Enter the name of your Lakehouse (should include `"far_workspace"`).
1. Select **OK**, then **Close and apply** to confirm the changes.

### Step 4 (Optional): Publish the dataset to Fabric

1. In Power BI Desktop, select **File > Publish > Publish to Power BI**.
1. Choose the Fabric-backed workspace where you want the dataset to reside.
1. After publishing, go to <https://app.powerbi.com> to verify the dataset appears in the workspace.

    You now have a dataset that you can extend so that it includes other data sources. You can also create new measures on it.

> [!NOTE]
> **Authentication problems:** Use OAuth 2.0 for authentication when you create connections.
>
> **Refresh delays:** After each configuration, allow up to two minutes for the dataset or lakehouse to refresh.
>
> **If the dataset doesn't load:** Double-check the SQL connection string and parameters in Power BI and Business performance analytics.
