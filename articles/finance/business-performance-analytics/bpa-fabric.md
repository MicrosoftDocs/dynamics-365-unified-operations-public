---

title: Connect business performance analytics data to Microsoft Fabric (preview)
description: This article explains how to link your business performance analytics data to Microsoft Fabric.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 7/02/2024
ms.topic: article
ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
ms.application-unique-name: msdyn_BusinessPerformanceAnalytics
---

# Connect business performance analytics data to Microsoft Fabric (preview)

[This article is prerelease documentation and is subject to change.].

Business performance analytics enables organizations to extend their existing data warehouse by using Microsoft Fabric shortcuts to connect the business performance analytics dimensional data model to it.

Business performance analytics uses Dataverse direct integration with Fabric and provides the following benefits:

- You don't have to export data, build data pipelines, or use third-party integration tools.
- You don't have to transform the data in the star schema. Business performance analytics does this transformation for you.
- Shortcuts from business performance analytics directly to OneLake enable data to stay in Dataverse while authorized users work with data in Fabric.

As part of this capability, business performance analytics generates an enterprise-ready lakehouse, a SQL analytics endpoint, and a default semantic model (Power BI dataset) for your organization's business performance analytics dimensional data. Data analysts, data engineers, and database administrators can then more easily combine business performance analytics data with data that's present in OneLake by using Spark, Python, or SQL.

As data is updated, changes are automatically reflected in your lakehouse.

## Prerequisites

Before you install Fabric and use it with business performance planning, the following prerequisites must be in place:

1. You must have a Power BI premium capacity license or Fabric.
2. The workspace that's linked to Dataverse must be assigned to premium or fabric capacity in the same region as your business performance analytics Dataverse environment. If you create a new workspace, you must have access to Power BI or Fabric premium capacity in the same region as your Dataverse environment. To confirm that you have access to the required premium capacity, follow these steps:

    1. In Power BI, open the workspace.
    2. Select **Workspace settings** \> **Premium**.
    3. Confirm that **Trial** or **Premium** is selected as the capacity.

3. Your Dataverse environment must be linked to a Fabric tenant. In Power BI, go to **Power BI settings** \> **Manage connections and gateways**, and verify that your environment has an established connection. If your environment isn't linked, follow these steps to link it:

    1. Go to **Power BI settings** \> **Manage connections and gateways**.
    2. Select **New**, and then select **Cloud**.
    3. In the **Connection type** field, select **Dataverse**.
    4. In the **Environment domain** field, enter the environment URL of the environment where business performance analytics is installed. You can find the environment URL on the **Environment details** page in Power Platform admin center.
    5. In the **Authentication method** field, select **OAuth2.0**.
    6. Select **Edit credentials**, and complete authentication.
    7. In the **Encrypted connection** field, select **Encrypted**.
    8. In the **Privacy level** field, select **Organizational**.
    9. Select **Create**.

### Link business performance analytics data to the organization's Fabric workspace

To link business performance analytics data to your organization's Fabric workspace, follow these steps.

1. In business performance analytics, select the **Administration** tab.
2. Go to **Connect with Microsoft Fabric**, and select **Manage**.
3. Select **Link Fabric**.
4. Specify the Fabric workspace ID to create the lake shortcut for the business performance analytics dimensional model. Confirm that the workspace is linked to your business performance analytics Dataverse environment.

    > [!NOTE]
    > The workspace must be in the same Azure region as the Dataverse environment.

5. Select **Connect**.

    The creation of Fabric shortcuts takes a few minutes. After the shortcuts are created, the **Fabric status** value is **Created**. If the shortcuts aren't created, the value is **Failed**. In this case, repeat steps 3 through 5 to try again.

6. After the **Fabric status** value is **Created**, select **View in Microsoft Fabric** to go to the linked lakehouse in your Fabric workspace.
7. You should now be able to access business performance analytics dimensional model tables via shortcuts in your Fabric workspace.

    > [!NOTE]
    > No updates or deletions on the dimensional model tables are permitted from the Fabric workspace.

    The lakehouse, an SQL analytics endpoint, and a default semantic model are created, and business performance analytics tables are linked to the lakehouse via shortcuts.

8. Before you share the data with others, you can secure it in the Fabric workspace.

The lakehouse, SQL endpoint, and Power BI dataset are updated with new data as changes occur in Dataverse.

When a new business performance analytics update is released, it might contain new tables or new columns in the business performance analytics dimensional model. (This type of change is known as a *metadata change*.) To make Fabric reflect the changes, in business performance analytics, select the **Administration** tab, go to **Connect with Microsoft Fabric**, select **Manage**, and then select **Refresh Fabric tables**. You might have to review the report and the downstream data flows to ensure that they aren't affected by the changes.

If you no longer need the shortcuts, select **Unlink** on the **Manage** page in business performance analytics. The link from the Fabric workspace to your Dataverse environment is removed. When you unlink business performance analytics data from the Fabric workspace, the Fabric lakehouse, SQL analytics endpoint, and default semantic model are removed.

> [!IMPORTANT]
> Business performance analytics manages the shortcuts. Don't delete or remove them directly in Fabric.
