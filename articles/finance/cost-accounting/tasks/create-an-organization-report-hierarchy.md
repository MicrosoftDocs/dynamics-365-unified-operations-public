--- 
title: Create an organization report hierarchy
description: Use this procedure to create a report hierarchy for organization reporting, including a step-by-step process for creating the hierarchy.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/06/2026
ms.custom: 
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0 
---

# Create an organization report hierarchy

[!include [banner](../../includes/banner.md)]

Use this procedure to create a report hierarchy for organization reporting. The purpose of this recording is to guide you through the dimension hierarchy so that you can continue until the whole organization reporting structure is created. This recording uses the USP2 demo data company.

1. Go to **Cost accounting > Dimensions > Dimension hierarchies**.
1. Select **New**.
1. In the **HierarchyTypeComboBox** field, select **Dimension classification hierarchy**.
    * The **Dimension classification hierarchy** type defines rules and supports reporting for all dimensions, such as cost objects, cost elements, and statistical dimensions.  
1. Select **Create**.
1. In the **Dimension hierarchy name** field, enter **Oganization USP2**.
1. In the **Dimension** field, enter or select a value.
    * Select **Cost centers**.  
1. Select **Save**.
1. Select **View hierarchy**.
1. Select **New**.
1. In the **Node name** field, enter **CEO**.
1. Select **Save**.
1. Select **New**.
1. In the **Node name** field, enter **CEO cost centers**.
1. Select **Save**.
1. Select **New**.
1. In the **Node name** field, enter **Region East**.
1. Select **Save**.
1. Select **New**.
1. In the list, select the row.
1. In the **From dimension member** field, enter or select a value.
    * Select the dimension member that corresponds to the node.  
1. Select **Save**.
1. In the tree, select **Oganization USP2\CEO\CEO cost centers**.
1. Select **New**.
1. In the **Node name** field, enter **Region West**.
1. Select **Save**.
1. Select **New**.
1. In the list, select the row.
1. In the **From dimension member** field, enter or select a value.
    * Select the dimension member that corresponds to the node.  
1. Select **Save**.
1. In the tree, select **Oganization USP2\CEO**.
1. Select **New**.
1. In the **Node name** field, enter **CFO cost centers**.
1. Select **Save**.
1. Select **New**.
1. In the **Node name** field, enter **Marketing campa**.
1. In the **Node name** field, enter **Marketing campaign**.
1. Select **Save**.
1. Select **New**.
1. In the list, select the row.
1. In the **From dimension member** field, enter or select a value.
    * Select the dimension member that corresponds to the node.  
1. Select **Save**.
1. In the tree, select **Organization USP2\CEO\CFO cost centers**.
1. Select **New**.
1. In the **Node name** field, enter **Trade shows**.
1. Select **Save**.
1. Select **New**.
1. In the list, select the row.
1. In the **From dimension member** field, enter or select a value.
    * Select the dimension member that corresponds to the node.  
49. Click **Save**.
50. In the tree, select `Oganization USP2\CEO`.
51. In the **Node name** field, type `CIO cost centers`.
52. Click **Save**.
53. Click **New**.
54. In the **Node name** field, type `Call centers`.
55. Click **Save**.
56. Click **New**.
57. In the list, mark the selected row.
58. In the **From dimension member** field, enter or select a value.
    * Select the dimension member that corresponds to the node.  
59. Click **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
