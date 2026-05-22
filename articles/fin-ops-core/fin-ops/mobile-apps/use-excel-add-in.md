---
title: View and update entity data with Excel 
description: Learn about how to open entity data in Microsoft Excel, and then view, update, and edit the data by using the Microsoft Dynamics Excel add-in.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.update-cycle: 1095-days
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: 4e6c7194-a059-4057-bd62-ec0c802c36fd
ms.custom: 
  - bap-template
  - evergreen
---

# View and update entity data with Excel

[!include [applies to](../../dev-itpro/includes/applies-to-commerce-finance-scm.md)]

[!include [banner](../../../finance/includes/banner.md)]

This article explains how to open entity data in Microsoft Excel, and then view, update, and edit the data by using the Microsoft Dynamics Excel add-in. To open entity data, you can start from either Excel or finance and operations apps.

By opening entity data in Excel, you can quickly and easily view and edit the data by using the Excel add-in. This add-in requires Microsoft Excel 2016 or later.

> [!NOTE]
> If your Microsoft Entra ID (Azure AD) tenant is configured to use Active Directory Federation Services (AD FS), you must make sure that the May 2016 update for Office is applied, so that the Excel add-in can correctly sign you in.

To learn more about how to use the Excel add-in, watch the short [Create an Excel template for header and line patterns](https://youtu.be/RTicLb-6dbI) video.

## Open entity data in Excel when you start from a finance and operations app

1. On a page in a finance and operations app, select **Open in Microsoft Office**.

    If the root data source (table) for the page is the same as the root data source for any entities, default **Open in Excel** options are generated for the page. You can find **Open in Excel** options on frequently used pages, such as **All vendors** and **All customers**.

1. Select an **Open in Excel** option, and open the workbook that is generated. This workbook has binding information for the entity, a pointer to your environment, and a pointer to the Excel add-in.
1. In Excel, select **Enable editing** to enable the Excel add-in to run. The Excel add-in runs in a pane on the right side of the Excel window.
1. If you're running the Excel add-in for the first time, select **Trust this Add-in**.
1. If you're prompted to sign in, select **Sign in**, and then sign in by using the same credentials that you used to sign in to the finance and operations app. The Excel add-in uses a previous sign-in context from the browser and automatically signs you in, if it can. (For information about the browser that is used based on the operating system, see [Browsers used by Office add-ins](/office/dev/add-ins/concepts/browsers-used-by-office-web-add-ins). To ensure that sign-in was successful, verify the user name in the upper-right corner of the Excel add-in.

The Excel add-in automatically reads the data for the entity that you selected. The workbook contains no data until the Excel add-in reads it in.

## Open entity data in Excel when you start from Excel

1. In Excel, on the **Insert** tab, in the **Add-ins** group, select **Store** to open the Office Store.
1. In the Office Store, search on the keyword **Dynamics**, and then select **Add** next to **Microsoft Dynamics Office Add-in** (the Excel add-in).
1. If you're running the Excel add-in for the first time, select **Trust this Add-in** to enable the Excel add-in to run. The Excel add-in runs in a pane on the right side of the Excel window.
1. Select **Add server information** to open the **Options** pane.
1. In your browser, copy the URL of your target finance and operations app instance, paste it into the **Server URL** field, and then delete everything after the host name. The resulting URL should have only the host name.

    For example, if the URL is `https://xxx.dynamics.com/?cmp=usmf&amp;mi=CustTableListPage`, delete everything except `https://xxx.dynamics.com`.

1. Select **OK**, and then select **Yes** to confirm the change. The Excel add-in restarts and loads metadata.

    The **Design** button is now available. If the Excel add-in has a **Load applets** link, you likely aren't signed in as the correct user. For more information on addressing this issue, see the [Load applets](../../dev-itpro/office-integration/office-integration-troubleshooting.md#issue-the-excel-add-in-loads-but-instead-of-showing-data-it-displays-load-applets-in-the-task-pane) troubleshooting entry.

1. Select **Design**. The Excel add-in retrieves entity metadata.
1. Select **Add table**. A list of entities appears. The entities are listed in "Name - Label" format.
1. Select an entity in the list, such as **Customer - Customers**, and then select **Next**.
1. To add a field from the **Available fields** list to the **Selected fields** list, select the field, and then select **Add**. Alternatively, double-click the field in the **Available fields** list.
1. After you finish adding fields to the **Selected fields** list, make sure that the cursor is in the correct place in the worksheet (for example, cell A1), and then select **Done**. Then select **Done** to exit the designer.
1. Select **Refresh** to pull in a set of data.

## View and update entity data in Excel

After the Excel add-in reads entity data into the workbook, you can update the data at any time by selecting **Refresh** in the Excel add-in.

## Edit entity data in Excel

You can change entity data as needed and then publish it back to finance and operations apps by selecting **Publish** in the Excel add-in. To edit a record, select a cell in the worksheet, and then change the cell value. To add a new record, follow one of these steps:

- Click anywhere in the data sources table, and then select **New** in the Excel add-in.
- Click anywhere in the last row of the data sources table, and then press the Tab key until the cursor moves out of the last column of that row and a new row is created.
- Click anywhere in the row immediately below the data sources table, and start to enter data in a cell. When you move the focus out of that cell, the table expands to include the new row.
- For field bindings of header records, select one of the fields, and then select **New** in the Excel add-in.

You can create a new record only if the worksheet binds all the key and mandatory fields, or if default values are filled in by using the filter condition.

To delete a record, follow one of these steps:

- Right-click the row number next to the worksheet row that you want to delete, and then select **Delete**.
- Right-click anywhere in the worksheet row that you want to delete, and then select **Delete** &gt; **Table Rows**.

If you add data sources as related data sources, the header publishes before the lines. If dependencies exist between other data sources, you might need to change the default publishing order. To change the publishing order, in the Excel add-in, select the **Options** button (the gear symbol). On the **Data Connector** FastTab, select **Configure publish order**.

## Add or remove columns

Use the designer to adjust the columns that the worksheet automatically adds.

> [!NOTE]
> If the **Design** button doesn't appear below the **Filter** button in the Excel add-in, you must enable the data source designer. Select the **Options** button (the gear symbol), and then select the **Enable design** check box.

1. In the Excel add-in, select **Design**. All the data sources are listed.

:::image type="content" source="media/select-design.png" alt-text="Screenshot of the Excel add-in showing the Design button.":::

1. Next to the data source, select the **Edit** button (the pencil symbol).

:::image type="content" source="media/select-edit-icon.png" alt-text="Screenshot of the Excel add-in showing the Edit (pencil) icon.":::

1. In the **Selected fields** list, adjust the list of fields as you require:

    - To add a field from the **Available fields** list to the **Selected fields** list, select the field, and then select **Add**. Alternatively, double-click the field in the **Available fields** list.
    - To remove a field from the **Selected fields** list, select the field, and then select **Remove**. Alternatively, double-click the field.
    - To change the order of fields in the **Selected fields** list, select a field, and then select **Up** or **Down**.

:::image type="content" source="media/select-add-dimension-column.png" alt-text="Screenshot of the Excel add-in showing Add dimension column.":::

1. To apply your changes to the data source, select **Update**. Then select **Done** to exit the designer.
1. If you added a field (column), select **Refresh** to pull in an updated set of data.

:::image type="content" source="media/refresh-dimension-data.png" alt-text="Screenshot of the Excel add-in showing Refreshing dimension data.":::

## Change the publish batch size

When users publish changes to data records by using the Excel add-in, the updates are submitted in batches. The default and maximum publish batch size is 100 rows. However, the **Allow configuration of the publish batch size in the Excel add-in** feature gives you flexibility in lowering the publish batch size, especially if you see time outs when attempting to publish updates from Excel.

System administrators can specify a system-wide limit on the publish batch size for "Open in Excel" workbooks by setting the **Publish batch limit** field in the **App parameters** section of the **Office app parameters** page.

You can also change the publish batch size for an individual workbook by using the Excel add-in.

1. Open the workbook in Excel.
1. Select the **Option** (gear) button in the upper right of the Excel add-in.
1. Set the **Publish batch size** field as desired. The value that you set must be less than the system-wide publish batch limit.
1. Select **OK**.
1. Save the workbook. If you don't save the workbook after you make changes to the add-in settings, those changes don't persist when the workbook is reopened.

Excel workbook template authors can use the same procedure to set the publish batch size for templates before they upload them into the system.

## Copy environment data

The data that is read into the workbook from one environment can be copied to another environment. However, you can't just change the connection URL, because the data cache in the workbook will continue to treat the data as existing data. Instead, you must use the Copy Environment Data functionality to publish the data to a new environment as new data.

1. Select the **Options** button (the gear symbol). On the **Data Connector** FastTab, select **Copy Environment Data**.
1. Enter the server URL for the new environment.
1. Select **OK**, and then select **Yes** to confirm the action. The Excel add-in restarts and connects to the new environment. The existing data in the workbook is treated as new data.

1. After the Excel add-in restarts, a message box states that the workbook is in Environment copy mode.

1. To copy the data into the new environment as new data, select **Publish**. To cancel the environment copy operation and review the existing data in the new environment, select **Refresh**.

## Troubleshooting

There are a few issues that can be resolved through some easy steps.

- **The "Load applets" link appears** – For more information about this problem, see [Load applets](../../dev-itpro/office-integration/office-integration-troubleshooting.md#issue-the-excel-add-in-loads-but-instead-of-showing-data-it-displays-load-applets-in-the-task-pane).
- **You receive a "Forbidden" message** – If you receive a "Forbidden" message while the Excel add-in is loading metadata, the account that is signed in to the Excel add-in doesn't have permission to use the targeted service, instance, or database. To resolve this problem, verify that the correct user name appears in the upper-right corner of the Excel add-in. If an incorrect user name appears, select it, sign out, and then sign back in.
- **A blank webpage appears over Excel** – If a blank webpage opens during the sign-in process, the account requires AD FS, but the version of Excel that is running the Excel add-in isn't recent enough to load the sign-in dialog box. To resolve this problem, update the version of Excel that you're using. To update the version of Excel when you're in an enterprise that is on the deferred channel, use the [Office deployment tool](/deployoffice/overview-office-deployment-tool) to [move from the deferred channel to the current channel](/deployoffice/overview-update-channels).
- **You receive a timeout while you publish data changes** – If you receive timeout messages while you're trying to publish data changes to an entity, consider reducing the publish batch size for the affected workbook. Entities that trigger larger amounts of logic on record changes might require updates to be sent in smaller batches to help prevent timeouts.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
