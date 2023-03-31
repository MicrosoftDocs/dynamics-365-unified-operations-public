---
title: (RCS) Import files in XML format with optional attributes
description: This article provides information about how a user can design ER format configuration to import files in XML format containing optional attributes.
author: kfend
ms.date: 07/01/2019
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2019-07-28
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
---
# (RCS) Import files in XML format with optional attributes

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can design ER format configuration to import files in XML format containing optional attributes. To complete these steps, you must first complete the steps in the "Create a configuration provider and mark it as active" procedure. Before you begin, download and save locally the IncomingDocumentToLearnHowToHandleOptionalAttributes.xml file from [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=874684).

1.    Go to **All workspaces** > **Electronic reporting**.
2.    Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the procedure [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).
3.    Click **Reporting configurations**.

## Create a new data model configuration
1.    Click **Create configuration** to open the drop dialog.
2.    In the **Name** field, type 'Model to import xml file'.
3.    Click **Create configuration**.
4.    Click **Designer**.
5.    Click **New** to open the drop dialog.
6.    In the **Name** field, type 'Root'.
7.    Click **Add**.
8.    Click **New** to open the drop dialog.
9.    In the **Name** field, type 'List'.
10.    In the **Item type** field, select **Record list**.
11.    Click **Add**.
12.    Click **New** to open the drop dialog.
13.    In the **Name** field, type 'Code'.
14.    In the **Item type** field, select **String**.
15.    Click **Add**.
16.    Click **Save**.
17.    Close the page.
18.    Click **Change status**.
19.    Click **Complete**.
20.    Click **OK**.

## Create a format for data import
1.    Click **Create configuration** to open the drop dialog.
2.    In the **New** field, enter 'Format based on data model Model to import xml file'.
3.    In the **Name** field, type 'Format to import xml file'.
4.    Select **Yes** in the **Supports data import** field.
5.    Click **Create configuration**.

## Design a format to parse incoming file in xml format
1.    Click **Designer**.
2.    Click **Add root** to open the drop dialog.
3.    In the tree, select **XML\Element**.
4.    In the **Name** field, type 'root'.
5.    Click **OK**.
6.    Click **Add** to open the drop dialog.
7.    In the tree, select **XML\Element**.
8.    In the **Name** field, type 'document'.
9.    In the **Multiplicity** field, select **One many**.
10.    Click **OK**.
11.    In the tree, select **root\document**.
12.    Click **Add** to open the drop dialog.
13.    In the tree, select **XML\Attribute**.
14.    In the **Name** field, type 'ID'.
15.    Click **OK**.
16.    Click **Save**.

## Design a format mapping to save parsed information to data model
1. Click **Map format to model**.
2. Click **New**.
3. In the **Definition** field, enter or select a value.
4. In the list, click the link in the selected row.
5. In the **Name** field, type 'Mapping'.
6. Click **Save**.
7. Click **Designer**.
8. In the tree, expand **format**.
9. In the tree, expand **format\root: XML Element(root)**.
10.    In the tree, select **format\root: XML Element(root)\document: XML Element 1..* (document)**.
11.    Click **Bind**.
12.    In the tree, expand **format\root: XML Element(root)\document: XML Element 1..* (document)**.
13.    In the tree, select **format\root: XML Element(root)\document: XML Element 1..* (document)\id**.
14.    In the tree, expand **List = format.root.document**.
15.    In the tree, select **List = format.root.document\Code**.
16.    Click **Bind**.
17.    Click **Save**.
18.    Close the page.
 
## Run format mapping
1. Click **Run**.
2. Click **Browse** and select **IncomingDocumentToLearnHowToHandleOptionalAttributes.xml**.
3. Click **OK**.

> [!NOTE]
> The selected file has not been imported as the format design assumes the existence of 'id' attribute for the 'document' element, but the imported file contains no such attribute.

## Modify format structure to handle xml attribute as optional
1. Close the page.
2. In the tree, expand **root\document**.
3. In the tree, select **root\document\id**.
4. Select **Yes** in the **Empty string for missing attribute** field.
5. Click **Save**.
 
## Run format mapping to test changes
1. Click **Map format to model**.
2. Click **Run**.
3. Click **Browse** and select the **IncomingDocumentToLearnHowToHandleOptionalAttributes.xml** file.
4. Click **OK**.
5. Review the generated file. 

> [!NOTE]
> The same file has been imported as the format design now consider the 'id' attribute for the 'document' element as optional.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
