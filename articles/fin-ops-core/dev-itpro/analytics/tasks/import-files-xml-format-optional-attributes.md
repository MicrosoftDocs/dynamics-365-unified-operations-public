---
title: (RCS) Import files in XML format with optional attributes
description: This article provides information about how a user can design ER format configuration to import files in XML format containing optional attributes.
author: kfend
ms.date: 04/09/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2019-07-28
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
---

# (RCS) Import files in XML format with optional attributes

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can design ER format configuration to import files in XML format containing optional attributes. To complete these steps, you must first complete the steps in the "Create a configuration provider and mark it as active" procedure. Before you begin, download and save locally the IncomingDocumentToLearnHowToHandleOptionalAttributes.xml file from [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=874684).

1. Go to **All workspaces** > **Electronic reporting**.
1. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the procedure [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).
1. Click **Reporting configurations**.

## Create a new data model configuration

1. Select **Create configuration** to open the form.
1. In the **Name** field, enter *Model to import xml file*.
1. Select **Create configuration**.
1. Select **Designer**.
1. Select **New** to open the form.
1. In the **Name** field, enter *Root*.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, enter *List*.
1. In the **Item type** field, select **Record list**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, enter *Code*.
1. In the **Item type** field, select **String**.
1. Select **Add**.
1. Select **Save**.
1. Close the page.
1. Select **Change status**.
1. Select **Complete**.
1. Select **OK**.

## Create a format for data import

1. Select **Create configuration** to open the form.
1. In the **New** field, enter *Format based on data model Model to import xml file*.
1. In the **Name** field, type *Format to import xml file*.
1. Select **Yes** in the **Supports data import** field.
1. Select **Create configuration**.

## Design a format to parse incoming file in XML format

1. Select **Designer**.
1. Select **Add root** to open the form.
1. In the tree, select **XML\Element**.
1. In the **Name** field, type *root*.
1. Select **OK**.
1. Select **Add** to open the form.
1. In the tree, select **XML\Element**.
1. In the **Name** field, type *document*.
1. In the **Multiplicity** field, select **One many**.
1. Select **OK**.
1. In the tree, select **root\document**.
1. Select **Add** to open the form.
1. In the tree, select **XML\Attribute**.
1. In the **Name** field, type *ID*.
1. Select **OK**.
1. Select **Save**.

## Design a format mapping to save parsed information to data model

1. Select **Map format to model**.
1. Select **New**.
1. In the **Definition** field, enter or select a value.
1. In the list, select the link in the selected row.
1. In the **Name** field, type `Mapping`.
1. Select **Save**.
1. Select **Designer**.
1. In the tree, expand **format**.
1. In the tree, expand **format\root: XML Element(root)**.
1. In the tree, select **format\root: XML Element(root)\document: XML Element 1..* (document)**.
1. Select **Bind**.
1. In the tree, expand **format\root: XML Element(root)\document: XML Element 1..* (document)**.
1. In the tree, select **format\root: XML Element(root)\document: XML Element 1..* (document)\id**.
1. In the tree, expand **List = format.root.document**.
1. In the tree, select **List = format.root.document\Code**.
1. Select **Bind**.
1. Select **Save**.
1. Close the page.

## Run format mapping

1. Select **Run**.
1. Select **Browse** and select **IncomingDocumentToLearnHowToHandleOptionalAttributes.xml**.
1. Select **OK**.

> [!NOTE]
> The selected file isn't imported as the format design assumes the existence of `id` attribute for the `document` element, but the imported file contains no such attribute.

## Modify format structure to handle xml attribute as optional

1. Close the page.
1. In the tree, expand **root\document**.
1. In the tree, select **root\document\id**.
1. Select **Yes** in the **Empty string for missing attribute** field.
1. Select **Save**.

## Run format mapping to test changes

1. Select **Map format to model**.
1. Select **Run**.
1. Click **Browse** and select the **IncomingDocumentToLearnHowToHandleOptionalAttributes.xml** file.
1. Select **OK**.
1. Review the generated file.

> [!NOTE]
> The same file is imported as the format design now considers the 'id' attribute for the 'document' element as optional.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
