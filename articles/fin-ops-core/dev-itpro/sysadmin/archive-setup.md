---
title: Set up the archive solution
description: This article describes how to set up your system to support archiving of different types of records.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/21/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up the archive solution

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until further notice -->

## <a name="install-addin"></a>Install the Archive add-in from Lifecycle Services

Before you can enable the archive solution, you must install the *Archive* add-in from Microsoft Dynamics Lifecycle Services.

1. Sign in to [Lifecycle Services](https://lcs.dynamics.com/).
1. Open the environment details page for your environment.
1. On the **Power Platform integration** FastTab, select **Install a new add-in**.
1. In the list of add-ins, select **(Preview) Archive**.
1. Follow the on-screen instructions.

## <a name="enable-features"></a>Enable the features that you need

After you install the *(Preview) Archive* add-in from Lifecycle Services, you can enable the archiving features that you need. Use the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace to enable the following features as you require:

- *(Preview) Archive* – This feature is required for all archiving scenarios. It provides basic archiving support and adds the **Archive** workspace.
- *(Preview) Ledger archive automation* – This feature moves general ledger records to the relevant history tables. After the data is copied to the history tables, the matching data from the day-to-day general ledger tables is purged. For more information about how to use this feature, see [Archive general ledger data](archive-general-ledger.md).
- *(Preview) Archive sales orders to history tables* – This feature is required for archiving of sales orders. It provides a framework for moving sales orders from day-to-day transaction tables to local history tables. For more information about how to use this feature, see [Archive sales orders](archive-sales-orders.md).
- *(Preview) Archive sales orders to history tables using archive service* – This feature is required for archiving of sales orders. It moves sales orders from day-to-day transaction tables to history tables. After the data is copied to the history tables, the matching data from the day-to-day transaction tables is purged. For more information about how to use this feature, see [Archive sales orders](archive-sales-orders.md).

<!--
- *(Preview) Archive data to Dataverse managed data lake and purge* – This feature provides the archival framework to do rules-based archiving of historical data. The archived records are removed from your day-to-day working environment and stored in your Dataverse-managed data lake. In this way, the feature helps improve system performance and lower operating costs while it also keeps your historical records so that they're available (as read-only data) when you need them.
- *(Preview) Archive sales order from history tables to Dataverse managed data lake and purge* – This feature completes the last step in the archival process for sales orders: archiving data from history tables to your Dataverse-managed data lake. For more information about how to use this feature, see [Archive sales orders](archive-sales-orders.md).
- *(Preview) Purge archived inventory transactions* – This feature completes the last step in the archival process for inventory transactions: archiving data from history tables to your Dataverse-managed data lake. You must ensure that the schema of `InventTransArchive` and the schema of `InventTransArchiveEntity` are identical. Otherwise, some data might be lost during synchronization to Dataverse. For more information about how to use this feature, see [Move inventory transactions history to long-term data retention](archive-inventory-purge.md).
-->

<!--
## Set up long-term data retention

After you move your old records to the history table, you can help lower your data storage costs and further improve system performance by moving the data to a Dataverse-managed data lake for long-term data retention. The action of moving data from a history table to long-term data retention is also known as *purging*, because the data is purged from Dynamics 365 Supply Chain Management. Purging is a permanent action that can't be reversed. To use long-term data retention, you must complete the procedure in each of the following subsections.

### <a name="app-registration"></a>Create an app registration in Azure

To enable Supply Chain Management to authenticate with Dataverse, you must create an app registration in Azure Active Directory (Azure AD).

1. Sign in to the [Azure portal](https://portal.azure.com).
1. From the **Home** page, go to **Azure Active Directory**.
1. On the navigation pane, select **App registrations**.
1. On the toolbar, select **New registration**.
1. On the **Register an application** page, set the following fields:

    - **Name** – Enter a name.
    - **Supported account types** – Select *Accounts in this organizational directory only (Microsoft only - Single tenant)*.

1. Select **Register**.
1. On the navigation pane, select **Certificates & Secrets**.
1. On the **Certificates & secrets** page, on the **Client secrets** tab, select **New client secret**.
1. In the **Add a client secret** dialog box, set the following fields:

    - **Description** – Enter a short description of your new client secret (for example, *Supply Chain Management archive solution*).
    - **Expires** – Select an expiration date that meets your needs.

1. Select **Add**.
1. The **Certificates & secrets** tab now shows details about the new client secret. These details will be shown only once and will be hidden when the page is reloaded. Therefore, you must copy them now. Copy the **Value** value, and paste it into a text file. You'll need this value later when you [configure Supply Chain Management to connect to and use long-term data retention](#scm-connect).
1. On the navigation pane, select **Overview**. Copy the **Display name** and **Application (client) ID** values, and paste them into a text file. You'll need these values later when you [configure Supply Chain Management to connect to and use long-term data retention](#scm-connect).

### Enable long-term data retention in Dataverse

By default, long-term data retention is turned off in Dataverse. Follow these steps to turn it on.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/home).
1. On the navigation pane, select **Environments**. Then open the environment that's associated with your Supply Chain Management environment.
1. Select **Settings**.
1. Expand **Products**, and then select **Features**.
1. Enable the feature that's named *Long term data retention in Dataverse (Preview)*.
1. Select **Save**.
1. Go back to the **Settings** page.
1. Expand **Users \+ permissions**, and then select **Application users**.
1. Select **New app user**.
1. In the **Create a new app user** dialog box, select **Add an app**.
1. In the **Add an app from Azure Active Directory** dialog box, use the search form to find the app that you registered in the [previous section](#app-registration). (Search for the application by the **Display name** value that you copied during that procedure.) Select the app registration, and then select **Add**.
1. Set the **Business unit** field to the name of the environment that you're working with.
1. Select the **Edit** button for the **Security roles** field. Then use the **Add security roles** dialog box to add the *System administrator* and *Bulk Archival Role* security roles.
1. In the **Create a new app user** dialog box, select **Create**.

### <a name="portal"></a>Enable long-term data retention for the required entities in Dataverse

After you've turned on the long-term data retention feature for Dataverse, you must enable it for each data entity that needs it.

1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/).
1. Select the **Settings** button (gear symbol) on the top bar, and then select **Advanced settings**.
1. Select the **Advanced find** button (filter symbol) on the top bar. Then use the **Advanced find** dialog box to search for finance and operations entities that contain the word *Archive* in the name. The results should include the following entities:

    - *SalesOrderLineArchiveEntity*
    - *SalesOrderHeaderArchiveEntity*
    - *InventTransArchiveEntity*

1. Select the first of the three entities. In the dialog box that appears, select the **Visible** and **Refresh** checkboxes to make the entity available as a virtual entity in Dataverse. Then select **Save and close**.
1. Repeat the previous step for each of the other two entities.
1. In the **Advanced find** dialog box, select **Results**, and confirm that the three entities now show a value of *Yes* in the **Visible** column.
1. Close the **Advanced find** dialog box.
1. In the maker portal, on the navigation pane, select **Tables**.
1. On the **Tables** page, on the **All** tab, in the search field, enter **(mserp)**. The search results should show the following three tables:

    - *Archived sales order line (mserp)*
    - *Archived sales order header (mserp)*
    - *Archived inventory transaction (mserp)*

1. Select the *Archived sales order line (mserp)* table, and then select **Properties**. In the **Edit table** dialog box, expand **Advanced options**, and select the **Track changes** and **Enable long term retention** checkboxes. Then select **Save**.
1. Repeat the previous step for the *Archived sales order header (mserp)* table and then for the *Archived inventory transaction (mserp)* table.

    > [!IMPORTANT]
    > Because of the parent/child relationships between the three tables, you must edit them in the order that's described here. Otherwise, you receive an error.

### <a name="scm-connect"></a>Configure Supply Chain Management to connect to and use long-term data retention

Long-term data retention is now fully set up for the required entities in Dataverse. The next step is to configure Supply Chain Management to connect to Dataverse and use it for long-term data retention.

1. Sign in to Supply Chain Management.
1. Use the company picker to select a legal entity where you want to enable long-term data retention.
1. Go to **System administration \> Setup \> Archive parameters**.
1. Set the following fields:

    - **Enable data archival to data lake** – Set this option to *Yes*.
    - **Azure application name** – Enter the **Display name** value that you copied when you [created the app registration in Azure](#app-registration).
    - **Application ID** – Enter the **Application (client) ID** value that you copied when you [created the app registration in Azure](#app-registration).
    - **Application secret** – Enter the client secret **Value** value that you copied when you [created the app registration in Azure](#app-registration).

    The **Linked Dataverse environment URL** field should already be set to the URL of the linked Dataverse environment.

1. On the Action Pane, select **Save**.
1. Repeat steps 2 through 5 for each additional legal entity where you want to enable long-term data retention.
1. Go to **System administration \> Setup \> Azure Active Directory applications**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Client ID** – Enter the **Application (client) ID** value that you copied when you [created the app registration in Azure](#app-registration).
    - **Name** – Enter a name (for example, *Long term data retention*).
    - **User ID** – Select *Admin*.

1. On the Action Pane, select **Save**.

### Provide access to view data in long-term data retention

To enable administrators and/or auditors to view the data in long-term data retention, create an app in Dataverse that queries the data by using the virtual entities that you set up in the [Enable long-term data retention for the required entities in Dataverse](#portal) section. For instructions, see [View long term retained data](/power-apps/maker/data-platform/data-retention-view).

-->

## Next steps

- [Extend the archive solution to support custom tables and fields](archive-customizations.md)
- [Archive sales orders](archive-sales-orders.md)
- [Archive general ledger data](archive-general-ledger.md)
