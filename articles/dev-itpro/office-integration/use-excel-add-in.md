---
# required metadata

title: Use the Excel add-in
description: This topic explains how to open entity data in Microsoft Excel, and then view, update, and edit the data by using the Microsoft Dynamics Office add-in for Excel. 
author: ChrisGarty
manager: AnnBe
ms.date: 11/30/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 267914
ms.assetid: 4e6c7194-a059-4057-bd62-ec0c802c36fd
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Use the Excel add-in

[!include[banner](../includes/banner.md)]

This topic explains how to open entity data in Microsoft Excel, and then view, update, and edit the data by using the Microsoft Dynamics Office add-in for Excel. To open the entity data, you can start from either Excel or Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.

By opening entity data in Excel, you can quickly and easily view and edit the data by using the Excel add-in. This add-in requires Microsoft Excel 2016.

> [!NOTE]
> If your Microsoft Azure Active Directory (Azure AD) tenant is configured to use Active Directory Federation Services (AD FS), you must make sure that the May 2016 update for Office has been applied, so that the Excel add-in can correctly sign you in.

## Open entity data in Excel when you start from Finance and Operations
1. On a page in Finance and Operations, select **Open in Microsoft Office**.

    If the root data source (table) for the page is the same as the root data source for any entities, default **Open in Excel** options are generated for the page. **Open in Excel** options can be found on frequently used pages, such as **All vendors** and **All customers**.
 
2. Select an **Open in Excel** option, and open the workbook that is generated. This workbook has binding information for the entity, a pointer to your environment, and a pointer to the Excel add-in.
3. In Excel, select **Enable editing** to enable the Excel add-in to run. The Excel add-in runs in a pane on the right side of the Excel window.
4. If you're running the Excel add-in for the first time, select **Trust this Add-in**.
5. If you're prompted to sign in, select **Sign in**, and then sign in by using the same credentials that you used to sign in to Finance and Operations. The Excel add-in will use a previous sign-in context from Internet Explorer and automatically sign you in, if it can. Therefore, verify the user name in the upper-right corner of the Excel add-in.

The Excel add-in automatically reads the data for the entity that you selected. Note that there will be no data in the workbook until the Excel add-in reads it in.

## Open entity data in Excel when you start from Excel
1. In Excel, on the **Insert** tab, in the **Add-ins** group, select **Store** to open the Office Store.
2. In the Office Store, search on the keyword **Dynamics**, and then select **Add** next to **Microsoft Dynamics Office Add-in** (the Excel add-in).
3. If you're running the Excel add-in for the first time, select **Trust this Add-in** to enable the Excel add-in to run. The Excel add-in runs in a pane on the right side of the Excel window.
4. Select **Add server information** to open the **Options** pane.
5. In your browser, copy the URL of your target Finance and Operations instance, paste it into the **Server URL** field, and then delete everything after the host name. The resulting URL should have only the host name.

    For example, if the URL is `https://xxx.dynamics.com/?cmp=usmf&amp;mi=CustTableListPage`, delete everything except `https://xxx.dynamics.com`.

6. Select **OK**, and then select **Yes** to confirm the change. The Excel add-in is restarted and loads metadata.

    The **Design** button is now available. If the Excel add-in has a **Load applets** button, you probably aren't signed in as the correct user. For more information, see "The Load applets button is shown" in the [Troubleshooting](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/office-integration/use-excel-add-in#troubleshooting) section of this topic.

7. Select **Design**. The Excel add-in retrieves entity metadata.
8. Select **Add table**. A list of entities appears. The entities are listed in "Name - Label" format.
9. Select an entity in the list, such as **Customer - Customers**, and then select **Next**.
10. To add a field from the **Available fields** list to the **Selected fields** list, select the field, and then select **Add**. Alternatively, double-click the field in the **Available fields** list.
11. After you've finished adding fields to the **Selected fields** list, make sure that the cursor is in the correct place in the worksheet (for example, cell A1), and then select **Done**. Then select **Done** to exit the designer.
12. Select **Refresh** to pull in a set of data.

## View and update entity data in Excel
After the Excel add-in reads entity data into the workbook, you can update the data at any time by selecting **Refresh** in the Excel add-in.

## Edit entity data in Excel
You can change entity data as you require and then publish it back by selecting **Publish** in the Excel add-in. To edit a record, select a cell in the worksheet, and then change the cell value. To add a new record, follow one of these steps:

- Click anywhere in the data sources table, and then select **New** in the Excel add-in.
- Click anywhere in the last row of the data sources table, and then press the Tab key until the cursor moves out of the last column of that row and a new row is created.
- Click anywhere in the row immediately below the data sources table, and start to enter data in a cell. When you move the focus out of that cell, the table expands to include the new row.
- For field bindings of header records, select one of the fields, and then select **New** in the Excel add-in.

Note that a new record can be created only if all the key and mandatory fields are bound in the worksheet, or if default values were filled in by using the filter condition.

To delete a record, follow one of these steps:

- Right-click the row number next to the worksheet row that should be deleted, and then select **Delete**.
- Right-click anywhere in the worksheet row that should be deleted, and then select **Delete** &gt; **Table Rows**.

If data sources have been added as related data sources, the header is published before the lines. If there are dependencies between other data sources, you might have to change the default publishing order. To change the publishing order, in the Excel add-in, select the **Options** button (the gear symbol), and then, on the **Data Connector** FastTab, select **Configure publish order**.

## Add or remove columns
You can use the designer to adjust the columns that are automatically added to the worksheet.

> [!NOTE]
> If the **Design** button doesn't appear below the **Filter** button in the Excel add-in, you must enable the data source designer. Select the **Options** button (the gear symbol), and then select the **Enable design** check box.

1. In the Excel add-in, select **Design**. All the data sources are listed.
2. Next to the data source, select the **Edit** button (the pencil symbol).
3. In the **Selected fields** list, adjust the list of fields as you require:

    - To add a field from the **Available fields** list to the **Selected fields** list, select the field, and then select **Add**. Alternatively, double-click the field in the **Available fields** list.
    - To remove a field from the **Selected fields** list, select the field, and then select **Remove**. Alternatively, double-click the field.
    - To change the order of fields in the **Selected fields** list, select a field, and then select **Up** or **Down**.

4. To apply your changes to the data source, select **Update**. Then select **Done** to exit the designer.
5. If you added a field (column), select **Refresh** to pull in an updated set of data.

## Copy environment data

The data that is read into the workbook from one environment can be copied to another environment. However, you can't just change the connection URL, because the data cache in the workbook will continue to treat the data as existing data. Instead, you must use the Copy Environment Data functionality to publish the data to a new environment as new data.

1. Select the **Options** button (the gear symbol), and then, on the **Data Connector** FastTab, select **Copy Environment Data**. 
2. Enter the server URL for the new environment. 
3. Select **OK**, and then select **Yes** to confirm the action. The Excel add-in is restarted and connects to the new environment. Any existing data in the workbook is treated as new data.

    After the Excel add-in is restarted, a message box states that the workbook is in Environment copy mode.

4. To copy the data into the new environment as new data, select **Publish**. To cancel the environment copy operation and review the existing data in the new environment, select **Refresh**.

## Troubleshooting
There are a few issues that can be resolved through some easy steps.

- **The Load applets button is shown** – If the Excel add-in has a **Load applets** button after sign-in, you probably aren't signed in as the correct user. To resolve this issue, verify that the correct user name appears in the upper-right corner of the Excel add-in. If an incorrect user name appears, select it, sign out, and then sign back in.
- **You receive a "Forbidden" message** – If you receive a "Forbidden" message while the Excel add-in is loading metadata, the account that is signed in to the Excel add-in doesn't have permission to use the targeted service, instance, or database. To resolve this issue, verify that the correct user name appears in the upper-right corner of the Excel add-in. If an incorrect user name appears, select it, sign out, and then sign back in.
- **A blank webpage is shown over Excel** – If a blank webpage is opened during the sign-in process, the account requires AD FS, but the version of Excel that is running the Excel add-in isn't recent enough to load the sign-in dialog box. To resolve this issue, update the version of Excel that you're using. To update the version of Excel when you're in an enterprise that is on the deferred channel, use the [Office deployment tool](https://technet.microsoft.com/library/jj219422.aspx) to [move from the deferred channel to the current channel](https://technet.microsoft.com/library/mt455210.aspx).
