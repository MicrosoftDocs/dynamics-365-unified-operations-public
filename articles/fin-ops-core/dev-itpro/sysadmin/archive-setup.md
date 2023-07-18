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
- *(Preview) Archive data to Dataverse managed data lake and purge* – <!-- KFM: Description needed -->
- *(Preview) Archive sales order from history tables to Dataverse managed data lake and purge* – <!-- KFM: Description needed -->
- *(Preview) Purge archived inventory transactions* – <!-- KFM: Description needed -->

## Set up long term data retention

### <a name="app-registration"></a>Create an app registration in Azure

<!-- KFM: Briefly describe what we are about to do and why. Confirm each of the following steps (copied from another topic) -->

1. Sign in to the [Azure portal](https://portal.azure.com).
1. From the **Home** page, go to **Azure Active Directory**.
1. In the navigation pane, select **App registrations**.
1. On the toolbar, select **New registration**.
1. On the **Register an application** page, set the following fields:
    - **Name** – Enter a name.
    - **Supported account types** – Select *Accounts in this organizational directory only (Microsoft only - Single tenant)*.
1. Select **Register**.
1. The new app registration is opened. In the **Essentials** section, select **Add a certificate or secret**.
1. The **Certificates & secrets** page opens. Open the **Client secrets** tab and select **New client secret**.
1. In the **Add a client secret** dialog box, make the following settings:
    - **Description** – Enter a short description for your new client secret (for example, *Supply Chain Management archive solution*).
    - **Expires** – Select an expiration date that meets your needs.
1. Select **Add**.
1. The **Certificates & secrets** tab now shows details about the new client secret. These details will be shown only once and will be hidden when the is page reloaded. Therefore, you must copy them now. Copy the **Value** value, and paste it into a text file. You'll need this value later when you [configure Supply Chain Management to connect to and use long term data retention](#scm-connect).

<!-- KFM: I suspect we don't need the rest of this procedure. Please confirm... 

1. On the navigation pane, under **Manage**, select **Authentication**.
1. The **Authentication** page opens. Select **Add a platform**.
1. In the **Configure platforms** dialog box, select the **Mobile and desktop applications** tile.
1. In the **Configure Desktop + devices** dialog box, select the checkbox for each redirect URL that you want to use. (You can probably select all of them.) Then select **Configure**.
1. On the **Overview** tab, copy the **Application (client) ID** and **Directory (tenant) ID** values, and paste them into the text file where you previously pasted the client secret value. You'll need all three of these values later.

-->

### Enable long term data retention in Dataverse

<!-- KFM: Briefly describe what we are about to do and why. Confirm each of the following steps (copied from draft) -->

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/home).
1. Go to the **Setting** of your environments. <!-- KFM: Open **Environments** first? I don't have any. -->
1. Expand **Products** and then select **Features**.
1. Enable the feature called **Long term data retention in Dataverse (Preview)**.
1. In the **Setting** under **Users + permissions**, create new application users (use the application created in the previous section) and then add the *System administrator* and *Bulk Archival Role* security roles. <!-- KFM: Much more detail is needed here. -->

### <a name="portal"></a>Make a portal in Power Apps

<!-- KFM: Briefly describe what we are about to do and why. Confirm each of the following steps (copied from draft) -->

1. Sign in to the [Power Apps make portal](https://make.powerapps.com/). <!-- KFM: Right name for this? -->
1. Select **Settings** (gear icon) to open a dialog box and then select the **Advanced settings**.
1. Select the Filter icon. <!-- KFM: I don't see this... -->
1. Filter for Available Finance and Operation Entities that contain the word *Archive* in the name.
1. Result will show the `SalesOrderLineArchiveEnityt`, `SalesOrderHeaderArchiveEntity`, and `InventTransArchiveEntity`.
1. Select each entity record to set the **Visible** properties which make the entity available as a virtual entity in Dataverse.
1. Repeat the previous step for each record.
1. In the make portal, click on the Tables and then select All.
1. Filter for the newly created virtual entities that contains the word *Archive* in the name.
1. Then click per record and navigate to properties.
1. In the advance option of the properties, select the **Track Changes** check box and the **Long Term Data retention** check box. The select **Save**.
1. Repeat for each of the three entities (`SalesOrderLineArchiveEnityt`, `SalesOrderHeaderArchiveEntity`, and `InventTransArchiveEntity`).

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
