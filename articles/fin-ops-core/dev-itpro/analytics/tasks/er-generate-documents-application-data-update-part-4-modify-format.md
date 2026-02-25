---
title: Modify formats to generate documents that have application data
description: This article describes how to design reporting configurations to generate an electronic document and update application data.
author: kfend
ms.date: 02/25/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---

# Modify formats to generate documents that have application data

[!include [banner](../../includes/banner.md)]

Before you start, finish the procedure, [Modify models and mappings to generate documents that have application data](er-generate-documents-application-data-update-part-3-modify-model-mapping.md).

This procedure shows how to design Electronic reporting (ER) configurations to generate an electronic document and update application data. Change the ER configurations so they generate electronic documents and update application data. This procedure is for users with the system admin or electronic reporting developer role. Use the DEMF dataset for these steps.


## Modify format to collect details of reporting

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. In the tree, expand **Intrastat (model)**.
1. In the tree, select **Intrastat (model)\Intrastat (format)**.
1. Select **Designer**.
1. In the tree, expand **File**.
1. In the tree, expand **File\Declaration**.
1. In the tree, select **File\Declaration\Data**.
1. In the **Multiplicity** field, select **One many**.
    * Configure this format element to archive details of the Intrastat reporting process. This item represents the archive's header record.  
1. In the tree, expand **File\Declaration\Data**.
1. In the tree, select **File\Declaration\Data\Item**.
1. In the **Multiplicity** field, select **Zero many**.
    * Configure this format element to archive details of the Intrastat reporting process. This item represents the list of archived lines.  
1. In the tree, expand **File\Declaration\Data\Item**.
1. In the tree, select **File\Declaration\Data\Item\Dim1**.
1. Select **Yes** in the **Excluded** field.
    * Don't archive this data, so you can exclude this format element from the data source of Intrastat reporting details.  
1. In the tree, expand **File\Declaration\Data\Item\Dim1**.
1. In the tree, select **File\Declaration\Data\Item\Dim1\property**.
1. Select **Yes** in the **Excluded** field.
1. In the tree, select **File\Declaration\Data\Item\Dim1\date**.
1. Select **Yes** in the **Excluded** field.
1. In the tree, select **File\Declaration\Data\Item\Dim2**.
1. Select **Yes** in the **Excluded** field.
1. In the tree, expand **File\Declaration\Data\Item\Dim2**.
1. In the tree, select **File\Declaration\Data\Item\Dim2\property**.
1. Select **Yes** in the **Excluded** field.
1. In the tree, select **File\Declaration\Data\Item\Dim2\code**.
1. Select **Yes** in the **Excluded** field.
1. In the tree, select **File\Declaration\Data\Item\Dim3**.
    * Several format elements can have the same name. For example, Dim. You can't explicitly recognize them when you use this format as a data source for archiving Intrastat reporting details, so you need to define the alternative names for these format elements.  
1. In the **Name** field, type **Amount**.
    * Amount  
1. In the **Multiplicity** field, select **Exactly one**.
1. In the tree, select **File\Declaration\Data\Item\Dim4**.
1. In the **Name** field, type **Item**.
    * Item  
1. In the **Multiplicity** field, select **Exactly one**.
    * In addition to the design format elements, archive the following Intrastat reporting details: unique record identification of each reported commodity item, and the name of the generated file. Because this data isn't in the Intrastat report, add the format related to these detail elements as data source items.
1. In the tree, select **File\Declaration\Data**.
1. Select **Add** to open the **Drop** dialog.
1. In the tree, select **Data source\Item**.
1. In the **Name** field, type **File name**.
    * File name  
1. In the **Data type** field, select **String**.
1. Select **OK**.
1. In the tree, select **File\Declaration\Data\Item**.
1. Select **Add Item**.
1. In the **Name** field, type **Commodity rec ID**.
    * Commodity rec ID  
1. In the **Data type** field, select **Int64**.
1. Select **OK**.
1. Select the **Mapping** tab.
1. In the tree, select **File\Declaration\Data\File name**.
1. Select **Bind**.
1. In the tree, expand **model**.
1. In the tree, expand **model\Transactions**.
1. In the tree, select **File\Declaration\Data\Item =  model.Transactions\Commodity rec ID**.
1. In the tree, select **model\Transactions\Commodity rec ID**.
1. Select **Bind**.
1. Select **Save**.

## Modify format to memorize details of reporting

1. Select **Map format to model**.
1. Select **New**.
1. In the **Definition** field, enter or select the **For application data update** root item.
    * For application data update.
1. In the **Name** field, type **Mapping to update data**.
    * Mapping to update data  
1. Select **Save**.
    * This mapping defines how the details of the Intrastat report are collected in the data model, which uses the selected root item 'For application data update'. These details, the model mapping with the same root item 'For application data update', and the direction 'To destination' are used for the application data update. The application data update starts immediately after the outgoing Intrastat report is generated. You can skip the application data update at run time, but the data model must be empty (containing an empty record list).
1. Select **Designer**.
    * The outgoing Intrastat report format is added by default as a data source for this model mapping.  
    * Bind elements of the designed report (presented as data source) to elements of the data model, which is filtered based on the selected model's root item.  
1. In the tree, expand **Archive header**.
1. In the tree, expand **Archive header\Archive lines**.
1. In the tree, expand `format`.
1. In the tree, expand `format\Declaration: XML Element(Declaration)`.
1. In the tree, expand `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)`.
1. In the tree, expand `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)`.
1. In the tree, expand `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)\Dim3: XML Element 1..1 (Amount)`.
1. In the tree, expand `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)\Dim4: XML Element 1..1 (Item)`.
1. In the tree, select **Archive header\Number of lines**.
1. Select **Edit**.
1. In the tree, select **List\COUNT**.
1. Select **Add function**.
1. In the tree, expand `format`.
1. In the tree, expand `format\Declaration: XML Element(Declaration)`.
1. In the tree, expand `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)`.
1. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)`.
1. Select **Add data source**.
1. In the **Formula** field, enter `COUNT(format.Declaration.Data.Item)`.
    * COUNT(format.Declaration.Data.Item)  
1. Select **Save**.
1. Close the page.
1. In the tree, select **Archive header\File name**.
1. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\File name: Item String(File name)`.
1. Select **Bind**.
1. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)\Dim4: XML Element 1..1 (Item)\number: String(number)`.
1. In the tree, select **Archive header\Archive lines\Item number**.
1. Select **Bind**.
1. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)\Dim3: XML Element 1..1 (Amount)\value: Numeric Real(value)`.
1. In the tree, select **Archive header\Archive lines\Amount**.
1. Select **Bind**.
1. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)\Commodity rec ID: Item Int64(Commodity rec ID)`.
1. In the tree, select **Archive header\Archive lines\Commodity rec ID**.
1. Select **Bind**.
1. In the tree, select **Archive header\Archive lines**.
1. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)`.
1. Select **Bind**.
1. In the tree, select **Archive header**.
1. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)`.
1. Select **Bind**.
1. Select **Save**.
1. Close the page.
1. Close the page.
1. Close the page.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
