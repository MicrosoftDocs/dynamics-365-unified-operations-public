---
title: Import files in XML format with optional attributes
description: Learn about designing ER formats which specify XML attributes to parse incoming electronic documents in XML format.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 04/08/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: global
ms.search.validFrom: 
ms.search.form: EROperationDesigner
ms.dyn365.ops.version: 
---

# Import files in XML format with optional attributes

[!include [banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats to parse incoming electronic documents in XML format. You can specify certain attributes of XML elements as optional in the designed ER format. This option allows you to handle incoming files with and without these XML attributes properly. You can then use the content from these files to update application data.

To learn more about this feature, complete the steps in the article, [(RCS) Import files in XML format with optional attributes](tasks/import-files-xml-format-optional-attributes.md), which is part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process. You can download this task guide and associated sample files from the [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=874684).

| Content description       | File                                                         |
|---------------------------|--------------------------------------------------------------|
| Sample file in XML format | IncomingDocumentToLearnHowToHandleOptionalAttributes.xml     |
| Task guide                | RCS Import files in XML format with optional attributes.axtr |

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can design ER format configuration to import files in XML format containing optional attributes. To complete these steps, you must first complete the steps in the procedure, [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md). Before you begin, download and save locally the IncomingDocumentToLearnHowToHandleOptionalAttributes.xml file from Microsoft Download Center (<https://go.microsoft.com/fwlink/?linkid=874684> ).

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the article, [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md).
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
1. In the **Name** field, type *id*.
1. Select **OK**.
1. Select **Save**.

## Design a format mapping to save parsed information to data model

1. Select **Map format to model**.
1. Select **New**.
1. In **Definition**, enter or select a value.
1. In **Name**, type `Mapping`.
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
1. Select **Browse**, and select the file **IncomingDocumentToLearnHowToHandleOptionalAttributes.xml**.
1. Select **OK**.

> [!NOTE]
> The selected file isn't imported as the format design assumes the existence of `id` attribute for the `document` element, but the imported file contains no such attribute.

## Modify format structure to handle XML attribute as optional

1. Close the page.
1. In the tree, expand **root\document**.
1. In the tree, select **root\document\id**.
1. In the **Empty string for missing attribute** field, select **Yes**.
1. Select **Save**.

## Run format mapping to test changes

1. Select **Map format to model**.
1. Select **Run**.
1. Select **Browse**, and select the file **IncomingDocumentToLearnHowToHandleOptionalAttributes.xml**.
1. Select **OK**.
1. Review the generated file. The same file is imported as the format design now considers the `id` attribute for the `document` element as optional.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
