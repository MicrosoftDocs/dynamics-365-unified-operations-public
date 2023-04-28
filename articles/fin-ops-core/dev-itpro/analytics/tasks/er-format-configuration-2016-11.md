---
title: ER Create a format configuration (November 2016)
description: This article explains how to create a format configuration for Electronic reporting (ER).
author: kfend
ms.date: 08/02/2019
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionCreateDropDialog, EROperationDesigner, ERComponentTypeDropDialog
---
# ER Create a format configuration (November 2016)

[!include [banner](../../includes/banner.md)]

This article explains how a user in the System Administrator or Electronic Reporting Developer role can create a format configuration for Electronic reporting (ER). This format configuration will define the format of electronic documents that are used for processing payments. In this example, you will create a format configuration for sample company, Litware, Inc. To complete these steps, you must first complete the steps in the "Map model to selected datasources" procedure.


## Create a new format configuration
1. Go to **Organization administration > Workspaces > Electronic reporting**.
2. Click **Reporting configurations**.
3. In the tree, select **Payments (simplified model)**.
4. Click **Create configuration** to open the drop dialog.

 > [!NOTE]
 > If you don't see **Create configuration**, you must enable design mode on the **Electronic reporting parameters** page. 
 
5. In the **New** field, enter **Format based on data model PaymentModel**.
6. In the **Name** field, type **BACS (UK fictitious)**.
7. In the **Description** field, type **BACS vendor payment format (UK fictitious)**.
    * The active configuration provider is automatically entered here. This provider will be able to maintain this configuration. Other providers can use this configuration, but will not be able to maintain it.  
    * A particular format of electronic document can be defined. Leave this field blank if you want to select a format at run-time.  
8. In the **Data model definition** field, enter or select a value.
9. Click **Create configuration**. A new configuration has been created. The draft version can be used to store the design format for managing electronic documents.  

## Design the format of an electronic document
1. Click **Designer**.
2. Click **Add root** to open the drop dialog.
3. In the tree, select **Common\File**.
4. In the **Name** field, type **Xml**.
5. In the **Encoding** field, type **UTF-8**.
6. Click **OK**.
7. Click **Add**.
8. In the tree, select **XML\Element**.
9. In the **Name** field, type **Message**.
10. Click **OK**.
11. In the tree, select **Xml\Message**.
12. Click **Add Element**.
13. In the **Name** field, type **ProcessingDate**.
14. Click **OK**.
15. Click **Add Element**.
16. In the Name field, type **MessageId**.
17. Click **OK**.
18. Click **Add Element**.
19. In the **Name** field, type **Payments**.
20. Click **OK**.
21. In the tree, select **Xml\Message\Payments**.
22. Click **Add Element**.
23. In the **Name** field, type **Item**.
24. Click **OK**.
25. In the tree, select **Xml\Message\Payments\Item**.
26. Click **Add**.
27. In the tree, select **XML\Attribute**.
28. In the Name field, type **Id**.
29. Click **OK**.
30. Click **Add**.
31. In the tree, select **XML\Element**.
32. In the Name field, type **Vendor**.
33. Click **OK**.
34. In the tree, select **Xml\Message\Payments\Item\Vendor**.
35. Click **Add Element**.
36. In the Name field, type **Name**.
37. Click **OK**.
38. Click **Add Element**.
39. In the **Name** field, type **Bank**.
40. Click **OK**.
41. In the tree, select **Xml\Message\Payments\Item\Vendor\Bank**.
42. Click **Add Element**.
43. In the **Name** field, type **RoutingNumber**.
44. Click **OK**.
45. Click **Add Element**.
46. In the **Name** field, type **AccountNumber**.
47. Click **OK**.
48. In the tree, select **Xml\Message\Payments\Item\Vendor**.
49. Click **Copy**.
50. In the tree, select **Xml\Message\Payments\Item**.
51. Click **Paste**.
52. In the **Name** field, type **Payer**.
53. In the tree, select **Xml\Message\Payments\Item**.
54. Click **Add Element**.
55. In the **Name** field, type **Currency**.
56. Click **OK**.
57. Click **Add Element**.
58. In the **Name** field, type **Description**.
59. Click **OK**.
60. Click **Add Element**.
61. In the Name field, type **TransDate**.
62. Click **OK**.
63. Click **Add Element**.
64. In the Name field, type **Amount**.
65. Click **OK**.

## Prepare format components for mapping to data model elements
1. In the tree, select **Xml\Message\ProcessingDate**.
2. Click **Add** to open the drop dialog.
3. In the tree, select **Text\DateTime**.
4. In the **Format** field, type **yyyy-MM-dd**.
5. Click **OK**.
6. In the tree, select **Xml\Message\Payments\Item\TransDate**.
7. Click **Add DateTime**.
8. In the **Format** field, type **yyyy-MM-dd**.
9. In the **DateTime** type field, select **Date**.
10. Click **OK**.
11. In the tree, select **Xml\Message\MessageId**.
12. Click **Add** to open the drop dialog.
13. In the tree, select **Text\String**.
14. Click **OK**.
15. In the tree, select **Xml\Message\Payments\Item\Vendor\Name**.
16. Click **Add String**.
17. Click **OK**.
18. In the tree, select **Xml\Message\Payments\Item\Vendor\Bank\RoutingNumber**.
19. Click **Add String**.
20. Click **OK**.
21. In the tree, select **Xml\Message\Payments\Item\Vendor\Bank\AccountNumber**.
22. Click **Add String**.
23. Click **OK**.
24. In the tree, select **Xml\Message\Payments\Item\Payer\Name**.
25. Click **Add String**.
26. Click **OK**.
27. In the tree, select **Xml\Message\Payments\Item\Payer\Bank\RoutingNumber**.
28. Click **Add String**.
29. Click **OK**.
30. In the tree, select **Xml\Message\Payments\Item\Payer\Bank\AccountNumber**.
31. Click **Add String**.
32. Click **OK**.
33. In the tree, select **Xml\Message\Payments\Item\Currency**.
34. Click **Add String**.
35. Click **OK**.
36. In the tree, select **Xml\Message\Payments\Item\Description**.
37. Click **Add String**.
38. Click **OK**.
39. In the tree, select **Xml\Message\Payments\Item\Amount**.
40. Click **Add String**.
41. Click **OK**.
42. Click **Save**.
43. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
