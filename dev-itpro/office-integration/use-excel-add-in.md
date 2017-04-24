---
# required metadata

title: Use the Excel add-in
description: This topic explains how to open entity data in Microsoft Excel, and then view, update, and edit the data by using the Microsoft Dynamics Office add-in for Excel. To open the entity data, you can start from either Excel or Microsoft Dynamics 365 for Operations.
author: ChrisGarty
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: AX 7.0.0, Operations, Core
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

This topic explains how to open entity data in Microsoft Excel, and then view, update, and edit the data by using the Microsoft Dynamics Office add-in for Excel. To open the entity data, you can start from either Excel or Microsoft Dynamics 365 for Operations.

By opening entity data in Microsoft Excel, you can quickly and easily view and edit the data by using the Microsoft Dynamics Office add-in for Excel. This add-in requires Microsoft Excel 2016. **Note:** If your Microsoft Azure Active Directory (Azure AD) tenant is configured to use Active Directory Federation Services (AD FS), you must make sure that the May 2016 update has been applied, so that the Excel add-in can correctly sign you in.

## Open entity data in Excel when you start from Dynamics 365 for Operations
1.  On a page in Microsoft Dynamics 365 for Operations, click **Open in Microsoft Office**. If the root data source (table) for the page is the same as the root data source for any entities, default **Open in Excel** options are generated for the page. **Open in Excel** options can be found on frequently used pages, such as **All vendors** and **All customers**.
2.  Click an **Open in Excel** option, and open the workbook that is generated. This workbook has binding information for the entity, a pointer to your environment, and a pointer to the Excel add-in.
3.  In Excel, click **Enable editing** to enable the Excel add-in to run. The Excel add-in runs in a pane on the right side of the Excel window.
4.  If you're running the Excel add-in for the first time, click **Trust this Add-in**.
5.  If you're prompted to sign in, click **Sign in**, and then sign in by using the same credentials that you used to sign in to Dynamics 365 for Operations. The Excel add-in will use a previous sign-in context from Internet Explorer and automatically sign you in, if it can. Therefore, verify the user name in the upper-right corner of the Excel add-in.

The Excel add-in automatically reads the data for the entity that you selected. Note that there will be no data in the workbook until the Excel add-in reads it in.

## Open entity data in Excel when you start from Excel
1.  In Excel, on the **Insert** tab, in the **Add-ins** group, click **Store** to open the Office Store.
2.  In the Office Store, search on the keyword "Dynamics," and click **Add** next to the **Microsoft Dynamics Office Add-in** (the Excel add-in).
3.  If you're running the Excel add-in for the first time, click **Trust this Add-in** to enable the Excel add-in to run. The Excel add-in runs in a pane on the right side of the Excel window.
4.  Click **Add server information** to open the **Options** pane.
5.  Copy the browser URL from your target Dynamics 365 for Operations instance, paste it into the **Server URL** field, and then delete everything after the host name. The resulting URL should have just the host name.
For example, if the URL is https://xxx.dynamics.com/?cmp=usmf&amp;mi=CustTableListPage, delete everything except **https://xxx.dynamics.com**.
6.  Click **OK**, and then click **Yes** to confirm the change. The Excel add-restarts and loads metadata. The **Design** button is now available. If the Excel add-in has a **Load applets** button, you probably aren't signed in as the correct user. For more information, see "The Load applets button is shown" in the "Troubleshooting" section of this topic.
7.  Click **Design**. The Excel add-in retrieves entity metadata.
8.  Click **Add table**. A list of entities appears. The entities are listed in "Name - Label" format.
9.  Select an entity in the list, such as **Customer - Customers**, and then click **Next**.
10. To add a field from the **Available fields** list to the **Selected fields** list, click the field, and then click **Add**. Alternatively, double-click the field.
11. After you've finished adding fields to the **Selected fields** list, make sure that the cursor is in the correct place in the worksheet (for example, cell A1), and then click **Done**. Then click **Done** to exit the designer.
12. Click **Refresh** to pull in a set of data.

## View and update entity data in Excel
After the Excel add-in reads entity data into the workbook, you can update the data at any time by clicking **Refresh** in the Excel add-in.

## Edit entity data in Excel
You can change entity data as you require and then publish it back by clicking **Publish** in the Excel add-in. To edit a record, select a cell in the worksheet, and then change the cell value. To add a new record, follow one of these steps:

-   Click anywhere in the data sources table, and then click **New** in the Excel add-in.
-   Click in the last row of the data sources table, and then press the Tab key until the cursor moves out of the last column of that row and a new row is created.
-   Click in the row immediately below the data sources table, and start to enter data in a cell. When you move the focus out of that cell, the table expands to include the new row.
-   For field bindings of header records, click one of the fields, and then click **New** in the Excel add-in..

Note that a new record can be created only if all the key and mandatory fields are bound in the worksheet, or if default values were filled in by using the filter condition.
To delete a record, follow one of these steps:

-   Right-click the row number next to the worksheet row to delete, and then click **Delete**.
-   Right-click in the worksheet row to delete, and then click **Delete** &gt; **Table Rows**.
If data sources have been added as related, the header is published before the lines. If there are dependencies between other data sources, you might have to change the default publish order. To change the publish order, in the Excel add-in, click the **Options** button (the gear symbol). Then, on the **Data Connector** FastTab, click **Configure publish order**.

## Add or remove columns
You can use the designer to adjust the columns that are automatically added to the worksheet.

1.  Start the data source designer of the Excel add-in by clicking the **Options** button (the gear symbol) and then selecting the **Enable design** check box.
2.  Click **Design** in the Excel add-in. All the data sources are listed.
3.  Next to the data source, click the **Edit** button (the pencil symbol).
4.  Adjust the list in the **Selected fields** list as you require:
    -   To add a field from the **Available fields** list to the **Selected fields** list, click the field, and then click **Add**. Alternatively, double-click the field.
    -   To remove a field from the **Selected fields** list, click the field, and then click **Remove**. Alternatively, double-click the field.
    -   To change the order of fields, click the field in the **Selected fields** list, click a field, and then click **Up** or **Down**.

5. To apply your changes to the data source, click **Update**. Then click **Done** to exit the designer. 
6. If you added a field (column), click **Refresh** to pull in an updated set of data.

## [](https://powerapps.microsoft.com/enus/tutorials/dataplatforminteractiveexcel/#troubleshooting)Troubleshooting
There are a few issues that can be resolved through some easy steps.

-   **The Load applets button is shown.** If the Excel add-in has a **Load applets** button after sign-in, you probably aren't signed in as the correct user. To resolve this issue, verify that the correct user name appears in the upper-right corner of the Excel add-in. If an incorrect user name appears, click it, sign out, and then sign back in.
-   **You receive a "Forbidden" message.** If you receive a "Forbidden" message while the Excel add-in is loading metadata, the account that is signed in to the Excel add-in doesn't have permission to use the targeted service, instance, or database. To resolve this issue, verify that the correct user name appears in the upper-right corner of the Excel add-in. If an incorrect user name appears, click it, sign out, and then sign back in.
-   **A blank webpage is shown over Excel.** If a blank webpage opens during the sign-in process, the account requires AD FS, but the version of Excel that is running the add-in isn't recent enough to load the sign-in dialog box. To resolve this issue, update the version of Excel that you're using. To update the version of Excel when you're in an enterprise that is on the deferred channel, use the [Office deployment tool](https://technet.microsoft.com/library/jj219422.aspx) to [move from the deferred channel to the current channel](https://technet.microsoft.com/library/mt455210.aspx).


