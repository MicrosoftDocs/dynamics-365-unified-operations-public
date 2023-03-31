---
title: Modify formats to generate documents that have application data
description: This article describes how to design reporting configurations to generate an electronic document and update application data.
author: kfend
ms.date: 06/19/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Modify formats to generate documents that have application data

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, you must first complete the procedure, "ER Generate documents with application data update (Part 3: Modify model and mapping)".

The steps in this procedure explain how to design Electronic reporting (ER) configurations to generate an electronic document and update application data. In this procedure, you will modify the ER configurations to not just use them to generate electronic documents, but also to update application data. This procedure is created for users with the assigned role of system administrator or electronic reporting developer. These steps can be completed using the DEMF dataset.


## Modify format to collect details of reporting
1. Go to Organization administration > Electronic reporting > Configurations.
2. In the tree, expand 'Intrastat (model)'.
3. In the tree, select 'Intrastat (model)\Intrastat (format)'.
4. Click Designer.
5. In the tree, expand 'File'.
6. In the tree, expand 'File\Declaration'.
7. In the tree, select 'File\Declaration\Data'.
8. In the Multiplicity field, select 'One many'.
    * Configure this format element to archive details of the Intrastat reporting process. This item represents the archive's header record.  
9. In the tree, expand 'File\Declaration\Data'.
10. In the tree, select 'File\Declaration\Data\Item'.
11. In the Multiplicity field, select 'Zero many'.
    * Configure this format element to archive details of the Intrastat reporting process. This item will represent the list of archived lines.  
12. In the tree, expand 'File\Declaration\Data\Item'.
13. In the tree, select 'File\Declaration\Data\Item\Dim1'.
14. Select Yes in the Excluded field.
    * You will not archive this data, so you can exclude this format element from the data source of Intrastat reporting details.  
15. In the tree, expand 'File\Declaration\Data\Item\Dim1'.
16. In the tree, select 'File\Declaration\Data\Item\Dim1\property'.
17. Select Yes in the Excluded field.
18. In the tree, select 'File\Declaration\Data\Item\Dim1\date'.
19. Select Yes in the Excluded field.
20. In the tree, select 'File\Declaration\Data\Item\Dim2'.
21. Select Yes in the Excluded field.
22. In the tree, expand 'File\Declaration\Data\Item\Dim2'.
23. In the tree, select 'File\Declaration\Data\Item\Dim2\property'.
24. Select Yes in the Excluded field.
25. In the tree, select 'File\Declaration\Data\Item\Dim2\code'.
26. Select Yes in the Excluded field.
27. In the tree, select 'File\Declaration\Data\Item\Dim3'.
    * Several format elements can have the same name. For example, Dim. You cannot explicitly recognize them when you use this format as a data source for archiving Intrastat reporting details, so you need to define the alternative names for these format elements.   
28. In the Name field, type 'Amount'.
    * Amount  
29. In the Multiplicity field, select 'Exactly one'.
30. In the tree, select 'File\Declaration\Data\Item\Dim4'.
31. In the Name field, type 'Item'.
    * Item  
32. In the Multiplicity field, select 'Exactly one'.
    * In addition to the design format elements, the following Intrastat reporting details must be archived: unique record identification of each reported commodity item and name of the generated file. Because this data will not be populated in the Intrastat report, you need to add the format that is related to these detail elements as data source items.  
33. In the tree, select 'File\Declaration\Data'.
34. Click Add to open the drop dialog.
35. In the tree, select 'Data source\Item'.
36. In the Name field, type 'File name'.
    * File name  
37. In the Data type field, select 'String'.
38. Click OK.
39. In the tree, select 'File\Declaration\Data\Item'.
40. Click Add Item.
41. In the Name field, type 'Commodity rec ID'.
    * Commodity rec ID  
42. In the Data type field, select 'Int64'.
43. Click OK.
44. Click the Mapping tab.
45. In the tree, select 'File\Declaration\Data\File name'.
46. Click Bind.
47. In the tree, expand 'model'.
48. In the tree, expand 'model\Transactions'.
49. In the tree, select 'File\Declaration\Data\Item =  model.Transactions\Commodity rec ID'.
50. In the tree, select 'model\Transactions\Commodity rec ID'.
51. Click Bind.
52. Click Save.

## Modify format to memorize details of reporting

1. Click Map format to model.
2. Click New.
3. In the Definition field, enter or select the 'For application data update' root item.
    * For application data update.
4. In the Name field, type 'Mapping to update data'.
    * Mapping to update data  
5. Click Save.
    * This mapping defines how the details of the Intrastat report are collected in the data model, the structure of which is specified by the selected root item 'For application data update'. These details, the model mapping with same root item 'For application data update', and the direction 'To destination' will be used for the application data update. The application data update starts immediately after the outgoing Intrastat report is generated. The application data update can be skipped at run-time, but the data model must be empty (containing empty record list).
6. Click Designer.
    * The outgoing Intrastat report format is added by default as a data source for this model mapping.  
    * Bind elements of the designed report (presented as data source) to elements of the data model, which is filtered based on the selected model's root item.  
7. In the tree, expand 'Archive header'.
8. In the tree, expand 'Archive header\Archive lines'.
9. In the tree, expand 'format'.
10. In the tree, expand 'format\Declaration: XML Element(Declaration)'.
11. In the tree, expand 'format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)'.
12. In the tree, expand 'format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)'.
13. In the tree, expand 'format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)\Dim3: XML Element 1..1 (Amount)'.
14. In the tree, expand 'format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)\Dim4: XML Element 1..1 (Item)'.
15. In the tree, select 'Archive header\Number of lines'.
16. Click Edit.
17. In the tree, select 'List\COUNT'.
18. Click Add function.
19. In the tree, expand 'format'.
20. In the tree, expand 'format\Declaration: XML Element(Declaration)'.
21. In the tree, expand `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)`.
22. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)`.
23. Click Add data source.
24. In the Formula field, enter 'COUNT(format.Declaration.Data.Item)'.
    * COUNT(format.Declaration.Data.Item)  
25. Click Save.
26. Close the page.
27. In the tree, select 'Archive header\File name'.
28. In the tree, select 'format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\File name: Item String(File name)'.
29. Click Bind.
30. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)\Dim4: XML Element 1..1 (Item)\number: String(number)`.
31. In the tree, select 'Archive header\Archive lines\Item number'.
32. Click Bind.
33. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)\Dim3: XML Element 1..1 (Amount)\value: Numeric Real(value)`.
34. In the tree, select 'Archive header\Archive lines\Amount'.
35. Click Bind.
36. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)\Commodity rec ID: Item Int64(Commodity rec ID)`.
37. In the tree, select 'Archive header\Archive lines\Commodity rec ID'.
38. Click Bind.
39. In the tree, select 'Archive header\Archive lines'.
40. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)\Item: XML Element 0..* (Item)`.
41. Click Bind.
42. In the tree, select 'Archive header'.
43. In the tree, select `format\Declaration: XML Element(Declaration)\Data: XML Element 1..* (Data)`.
44. Click Bind.
45. Click Save.
46. Close the page.
47. Close the page.
48. Close the page.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
