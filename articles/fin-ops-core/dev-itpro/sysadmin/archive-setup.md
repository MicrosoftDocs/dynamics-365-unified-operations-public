---
title: Set up the archive solution
description: This article describes how to set up your system to support archiving of different types of records.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 06/13/2023
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
- *(Preview) Archive data to Dataverse managed data lake and purge* – <!-- KFM: Description needed , platform piece that enables the movement-->
- *(Preview) Archive sales order from history tables to Dataverse managed data lake and purge* – <!-- KFM: Description needed -->
- *(Preview) Purge archived inventory transactions* – <!-- KFM: Description needed -->

## Set up long term data retention

<!-- KFM: Briefly describe what this is. -->

### <a name="app-registration"></a>Create an app registration in Azure

To enable Supply Chain Management to authenticate with Dataverse, you must create an app registration in Azure Active Directory. To do so, follow these steps:

1. Sign in to the [Azure portal](https://portal.azure.com).
1. From the **Home** page, go to **Azure Active Directory**.
1. In the navigation pane, select **App registrations**.
1. On the toolbar, select **New registration**.
1. On the **Register an application** page, set the following fields:
    - **Name** – Enter a name.
    - **Supported account types** – Select *Accounts in this organizational directory only (Microsoft only - Single tenant)*.
1. Select **Register**.
1. Select **Certificates & Secrets** in navigation pane.
1. The **Certificates & secrets** page opens. Open the **Client secrets** tab and select **New client secret**.
1. In the **Add a client secret** dialog box, make the following settings:
    - **Description** – Enter a short description for your new client secret (for example, *Supply Chain Management archive solution*).
    - **Expires** – Select an expiration date that meets your needs.
1. Select **Add**.
1. The **Certificates & secrets** tab now shows details about the new client secret. These details will be shown only once and will be hidden when the is page reloaded. Therefore, you must copy them now. Copy the **Value** value, and paste it into a text file. You'll need this value later when you [configure Supply Chain Management to connect to and use long term data retention](#scm-connect).
1. Go to **Overview** and copy the values shown for **Display name** and **Application (client) ID** and paste them into a text file. You'll need these values later when you [configure Supply Chain Management to connect to and use long term data retention](#scm-connect).

### Enable long term data retention in Dataverse

By default, long term data retention is turned off in Dataverse. Follow these steps to turn it on.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/home).
1. Go to **Environments** and open the environment associated with your Supply Chain Management environment.
1. Select **Settings**.
1. Expand **Products** and then select **Features**.
1. Enable the feature called **Long term data retention in Dataverse (Preview)**.
1. Select **Save**.
1. Go back to the **Settings** page.
1. Expand **Users + permissions** and then select **Application users**.
1. Select **New app user**.
1. The **Create a new app user** dialog opens. Select **Add an app**.
1. The **Add an app from Azure Active Directory** dialog opens. Use the search form to find the app you registered in the [previous section](#app-registration) (search for the application **Display name**, which you should have copied during that procedure). Select the app registration and then select **Add**.
1. Set **Business unit** to the name of the environment that you're working with.
1. Select the **Edit** button for the **Security roles** field. Then use the Add security roles dialog to add the *System administrator* and *Bulk Archival Role* security roles.
1. Select **Create** in the **Create a new app user** dialog.

### <a name="portal"></a>Enable long term data retention for the required entities in Dataverse

You must enable long term data retention on each of the data entities that needs it. To do so, follow these steps:

1. Sign in to the [Power Apps make portal](https://make.powerapps.com/).
1. Select **Settings** (gear icon) to open a dialog box and then select **Advanced settings**.
1. Select **Advanced find** (filter icon) in the top bar. The **Advanced find** dialog opens. Use it to search for Finance and Operation Entities that contain the word *Archive* in the name. The results should include `SalesOrderLineArchiveEntity`, `SalesOrderHeaderArchiveEntity`, and `InventTransArchiveEntity`.
1. Select the first of these three entities to open a dialog box. Then select the **Visible** and **Refresh** check boxes, which make the entity available as a virtual entity in Dataverse. Then select **Save and close**.
1. Repeat the previous step for each of the other two entities.
1. Select **Results** in the **Advanced find** dialog and confirm that the three entities now show a value of *Yes* in the **Visible** column. Then close the dialog.
1. In the make portal, on the navigation pane, select **Tables** to open the **Tables** page and then open the **All** tab.
1. In the search field, enter "(mserp)" and press return. The search results should now show the following three tables: *Archived sales order line (mserp)*, *Archived sales order header (mserp)*, and *Archived inventory transaction (mserp)*.
1. Select *Archived sales order line (mserp)* and then select **Properties**. The **Edit table** dialog opens. Expand **Advanced options** and mark the **Track changes** and **Enable long term retention** check boxes. Then select **Save**.
1. Repeat the previous step for the *Archived sales order header (mserp)* table.
1. Repeat the previous step for the *Archived inventory transaction (mserp)* table.

    > [!NOTE]
    > Your must edit the tables in the suggested order because of their parent/child relationships. You'll get an error if you try to set them up in a different order

### <a name="scm-connect"></a> Configure Supply Chain Management to connect to and use long term data retention

<!-- KFM: Briefly describe what we are about to do and why. Confirm each of the following steps (copied from draft) -->

1. Sign in to Supply Chain Management.
1. Go to **System administration \> Setup \> Archive parameters**. <!-- KFM: Confirm path -->
1. In the **App registration** field,  <!-- KFM: Use literal field names and specify which values to paste from earlier procedure. -->
1. Set **Enable data archival to data lake** to *Yes*.
1. Go to **System administration \> Setup \> Azure Active Directory application**. <!-- KFM: Confirm path -->
1. Make the following settings:
    - **Client id** – Enter the app ID that you copied when you [created the app registration in Azure](#app-registration)
    - **Name** – Select *Long Term Data Retention*.
    - **UserId** – Select *Admin*.

### Set up the scheduled task

<!-- KFM: Briefly describe what we are about to do and why. Much more detail is needed here. -->

1. Go to the **Archive** workspace and schedule move to history Schedule purge.

### Provide access to view data in long term data retention

To allow administrators and/osr auditors to view the data in long term data retention, create an app in Dataverse that queries data using the virtual entities that you set up earlier in the [Make a portal in Power Apps](#portal) section. For instructions, see [View long term retained data](/power-apps/maker/data-platform/data-retention-view).

## Next steps

- [Extend the archive solution to support custom tables and fields](archive-customizations.md)
- [Archive sales orders](archive-sales-orders.md)
- [Archive general ledger data](archive-general-ledger.md)
