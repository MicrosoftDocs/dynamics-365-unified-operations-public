---
title: ER Create a format configuration (November 2016)
description: This article explains how to create a format configuration for Electronic reporting (ER).
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionCreateDropDialog, EROperationDesigner, ERComponentTypeDropDialog
---

# ER Create a format configuration (November 2016)

[!include [banner](../../includes/banner.md)]

This article explains how a user in the System Administrator or Electronic Reporting Developer role can create a format configuration for Electronic reporting (ER). This format configuration defines the format of electronic documents that are used for processing payments. In this example, you create a format configuration for sample company, Litware, Inc. To complete these steps, you must first complete the steps in the "Map model to selected datasources" procedure.

## Create a new format configuration

1. Go to **Organization administration > Workspaces > Electronic reporting**.
1. Select **Reporting configurations**.
1. In the tree, select **Payments (simplified model)**.
1. Select **Create configuration** to open the dialog.

 > [!NOTE]
 > If you don't see **Create configuration**, you must enable design mode on the **Electronic reporting parameters** page.

1. In **New**, enter **Format based on data model PaymentModel**.
1. In **Name**, type **BACS (UK fictitious)**.
1. In **Description**, type **BACS vendor payment format (UK fictitious)**.
    * The active configuration provider is automatically entered here. This provider can maintain this configuration. Other providers can use this configuration, but can't maintain it.  
    * You can define a particular format of electronic document. Leave this field blank if you want to select a format at run-time.  
1. In **Data model definition**, enter or select a value.
1. Select **Create configuration**. You created a new configuration. Use the draft version to store the design format for managing electronic documents.    

## Design the format of an electronic document

1. Select **Designer**.
1. Select **Add root** to open the drop dialog.
1. In the tree, select **Common\File**.
1. In the **Name** field, type **Xml**.
1. In the **Encoding** field, type **UTF-8**.
1. Select **OK**.
1. Select **Add**.
1. In the tree, select **XML\Element**.
1. In the **Name** field, type **Message**.
1. Select **OK**.
1. In the tree, select **Xml\Message**.
1. Select **Add Element**.
1. In the **Name** field, type **ProcessingDate**.
1. Select **OK**.
1. Select **Add Element**.
1. In the **Name** field, type **MessageId**.
1. Select **OK**.
1. Select **Add Element**.
1. In the **Name** field, type **Payments**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments**.
1. Select **Add Element**.
1. In the **Name** field, type **Item**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item**.
1. Select **Add**.
1. In the tree, select **XML\Attribute**.
1. In the **Name** field, type **Id**.
1. Select **OK**.
1. Select **Add**.
1. In the tree, select **XML\Element**.
1. In the **Name** field, type **Vendor**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Vendor**.
1. Select **Add Element**.
1. In the **Name** field, type **Name**.
1. Select **OK**.
1. Select **Add Element**.
1. In the **Name** field, type **Bank**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Vendor\Bank**.
1. Select **Add Element**.
1. In the **Name** field, type **RoutingNumber**.
1. Select **OK**.
1. Select **Add Element**.
1. In the **Name** field, type **AccountNumber**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Vendor**.
1. Select **Copy**.
1. In the tree, select **Xml\Message\Payments\Item**.
1. Select **Paste**.
1. In the **Name** field, type **Payer**.
1. In the tree, select **Xml\Message\Payments\Item**.
1. Select **Add Element**.
1. In the **Name** field, type **Currency**.
1. Select **OK**.
1. Select **Add Element**.
1. In the **Name** field, type **Description**.
1. Select **OK**.
1. Select **Add Element**.
1. Enter **TransDate** in the Name field.
1. Select **OK**.
1. Select **Add Element**.
1. Enter **Amount** in the Name field.
1. Select **OK**.

## Prepare format components for mapping to data model elements

1. In the tree, select **Xml\Message\ProcessingDate**.
1. Click **Add** to open the drop dialog.
1. In the tree, select **Text\DateTime**.
1. In the **Format** field, type **yyyy-MM-dd**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\TransDate**.
1. Click **Add DateTime**.
1. In the **Format** field, type **yyyy-MM-dd**.
1. In the **DateTime** type field, select **Date**.
1. Select **OK**.
1. In the tree, select **Xml\Message\MessageId**.
1. Click **Add** to open the drop dialog.
1. In the tree, select **Text\String**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Vendor\Name**.
1. Click **Add String**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Vendor\Bank\RoutingNumber**.
1. Click **Add String**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Vendor\Bank\AccountNumber**.
1. Click **Add String**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Payer\Name**.
1. Click **Add String**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Payer\Bank\RoutingNumber**.
1. Click **Add String**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Payer\Bank\AccountNumber**.
1. Click **Add String**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Currency**.
1. Click **Add String**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Description**.
1. Click **Add String**.
1. Select **OK**.
1. In the tree, select **Xml\Message\Payments\Item\Amount**.
1. Click **Add String**.
1. Select **OK**.
1. Click **Save**.
1. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
