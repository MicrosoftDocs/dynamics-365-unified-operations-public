---
title: Modify models and mappings to generate documents that have application data
description: This article describes how to design reporting configurations to generate an electronic document and update application data. (Part 2 - Generate documents).
author: kfend
ms.date: 02/24/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---

# Modify models and mappings to generate documents that have application data

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, you must first complete the procedure, [Design configurations to generate documents that have application data](er-generate-documents-application-data-update-part-2-generate-documents.md).

The steps in this procedure explain how to design Electronic reporting (ER) configurations to generate an electronic document and update application data. In this procedure, you modify the ER configurations to start using them to generate electronic documents and update application data. This procedure is created for users with the assigned role of system administrator or electronic reporting developer. These steps can be completed using the DEMF dataset.

## Modify data model

1. Go to **Organization administration > Electronic reporting > Configurations**.
2. In the tree, select **Intrastat (model)**.
    * You can extend how you use the data model. Besides using it as data source to generate the Intrastat report, the data model is used to collect details about the Intrastat reporting process. The details are then used to update application data.  
3. Select **Designer**.
4. Select **New** to open the drop dialog.
5. In the New node as a field, enter **Model root**.
6. In the Name field, type **For application data update**.
    * For application data update  
7. Select **Add**.
8. In the tree, select **For application data update**.
    * This new root item is added to specify the data flow for moving data from the Intrastat report (used as a data source) to the application tables (the update destination). Different root items must be used for getting data that is posted to the outgoing document and for getting data from the document that is used to update application data.   
9. Select **New** to open the **Drop** dialog.
10. In the **Name** field, type **Archive header**.
    * Archive header  
11. In the **Item type** field, select **Record list**.
12. Select **Add**.
    * Because you are creating a record for each generated Intrastat report, you must accordingly create a new item.  
13. Select **New** to open the **Drop** dialog.
14. In the **Name** field, type **File name**.
    * File name  
15. In the **Item type** field, select **String**.
16. Select **Add**.
17. Select **New** to open the **Drop** dialog.
18. In the **Name** field, type **Number of lines**.
    * Number of lines  
19. In the **Item type** field, select **Integer**.
20. Select **Add**.
    * Add this item to represent the number of Intrastat transactions reported during the current reporting process.  
21. Select **New** to open the **Drop** dialog.
22. In the **Name** field, type **Archive lines**.
    * Archive lines  
23. In the **Item type** field, select **Record list**.
24. Select **Add**.
    * Add this item to represent the list of Intrastat transactions reported during the current reporting process.  
25. Select **New** to open the **Drop** dialog.
26. In the **Name** field, type **Amount**.
    * Amount  
27. In the **Item type** field, select **Real**.
28. Select **Add**.
29. Select **New** to open the **Drop** dialog.
30. In the **Name** field, type **Commodity rec id**.
    * Commodity rec id  
31. In the **Item type** field, select **Int64**.
32. Select **Add**.
33. Select New to open the drop dialog.
34. In the **Name** field, type **Item number**.
    * Item number  
35. In the **Item type** field, select **String**.
36. Select **Add**.
37. Select **Save**.
38. Close the page.

## Modify model mapping

1. In the tree, expand **Intrastat (model)**.
2. In the tree, select **Intrastat (model)\Intrastat (mapping)**.
    * Modify the existing model mapping to start using it for the application data update and to archive Intrastat reporting details.  
3. Select **Designer**.
4. Select **New**.
5. In the **Name** field, type **Update archive**.
    * Update archive  
6. In the **Direction** field, select **To destination**.
7. Select **Save**.
    * This new mapping specifies the data flow for moving data (Intrastat reporting details) from the data model to the application tables (the update destination). You must use the root items of different models to get data from the application for the reporting process and then use the data from the data model for the application data update.
8. Select **Designer**.
9. In the tree, select **Data model\Data model**.
    * Add the required data source. This is the data model that contains details of the reported Intrastat transactions to archive.  
10. Select **Add root**.
11. In the **Name** field, type **model**.
    * model  
12. In the **Definition** field, enter or select the value **For application data update**.
    * For application data update  
13. Select **OK**.
14. In the tree, expand **model**.
15. In the tree, select **Functions\Calculated field**.
16. In the tree, select **model\Archive header**.
17. Select **Add**.
    * Because you want to enumerate reported Intrastat transactions for archiving, ensure that you add the appropriate data source.  
18. In the **Name** field, type **Enumerated lines**.
    * Enumerated lines  
19. Select **Edit** formula.
20. In the tree, select **List\ENUMERATE**.
21. Select **Add** function.
22. In the tree, expand **model**.
23. In the tree, expand **model\Archive header**.
24. In the tree, select **model\Archive header\Archive lines**.
25. Select **Add data source**.
26. In the **Formula** field, enter **ENUMERATE(model.'Archive header'.'Archive lines')**.
    * ENUMERATE(model.'Archive header'.'Archive lines')  
27. Select **Save**.
28. Close the page.
29. Select **OK**.
30. Select **Add destination**.
    * Add application tables as required destinations that require updates to archive details of reported Intrastat transactions.  
31. In the **Name** field, type **Archive**.
    * Archive  
32. In the **Table name** field, type **IntrastatArchiveGeneral**.
    * IntrastatArchiveGeneral  
    * Keep the record action **Insert** so you can add records during the detail archiving of each Intrastat reporting process.  
33. In the **Record infolog** field, select **Yes**.
    * To get information about issues with the application data update, select **Yes**.  
34. In the **Skip record action validation** field, select **Yes**.
    * To suppress validation errors about the empty **Intrastat archive ID** field, Select **Yes** . These errors are suppressed after the addition of records, based on the sequence number settings configured for this table in the **Foreign trade parameters** form.  
35. Select **OK**.
    * Bind elements of the added data source (the filtered model based on the selected root item) with elements from the added destination.  
36. In the tree, expand **Archive**.
37. In the tree, expand **Archive\<Relations**.
38. In the tree, expand **Archive\<Relations\IntrastatArchiveDetail**.
39. In the tree, select **Archive\<Relations\IntrastatArchiveDetail\Amount(AmountMST)**.
40. In the tree, expand **model\Archive header\Enumerated lines**.
41. In the tree, expand **model\Archive header\Enumerated lines\Value**.
42. In the tree, select **model\Archive header\Enumerated lines\Value\Amount**.
43. Select **Bind**.
44. In the tree, select **Archive\<Relations\IntrastatArchiveDetail\Commodity(IntrastatCommodity)**.
45. In the tree, select **model\Archive header\Enumerated lines\Value\Commodity rec id**.
46. Select **Bind**.
47. In the tree, select **Archive\<Relations\IntrastatArchiveDetail\Item number(ItemId)**.
48. In the tree, select **model\Archive header\Enumerated lines\Value\Item number**.
49. Select **Bind**.
50. In the tree, select **Archive\<Relations\IntrastatArchiveDetail\Line number(LineNumber)**.
51. In the tree, select **model\Archive header\Enumerated lines\Number**.
52. Select **Bind**.
53. In the tree, select **Archive\<Relations\IntrastatArchiveDetail**.
54. In the tree, select **model\Archive header\Enumerated lines**.
55. Select **Bind**.
56. In the tree, select **Archive\File name(FileName)**.
57. In the tree, select **model\Archive header\File name**.
58. Select **Bind**.
59. In the tree, select **Archive\Number of lines(NumberOfLines)**.
60. In the tree, select **model\Archive header\Number of lines**.
61. Select **Bind**.
62. In the tree, select **Archive**.
63. In the tree, select **model\Archive header**.
64. Select **Bind**.
65. Select **Save**.
66. Close the page.
67. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
