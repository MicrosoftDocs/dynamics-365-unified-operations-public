--- 
# required metadata 
 
title: Set up containerization
description: This topic describes how to automate the containerization of loads in Warehouse management. 
author: ShylaThompson
manager: AnnBe 
ms.date: 07/22/19
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSWaveTemplateTable, InventLocationIdLookup, WHSContainerType, WHSContainerGroup, WHSContainerizationTable, WHSContainerizationBreak, WHSCreateContainerBreak   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up containerization

[!include [banner](../../includes/banner.md)]

This topic describes how to automate the containerization of loads in Warehouse management. Automated containerization creates containers and the picking work for shipments when a wave is processed and work lines can be split into quantities that fit the containers. This helps warehouse workers to pick the items directly into the chosen container. Compared to the manual packing process, tasks such as creating containers, assigning items, and closing containers are automated by the system. This procedure uses the USMF demo company and is performed by a Warehouse manager.


## Set up a wave template
1. In the navigation pane, go to **Modules > Warehouse management > Setup > Waves > Wave templates**.
2. Select **New**.
3. In the **Wave template name** field, type a value.
4. In the **Wave template description** field, type a value.
5. In the **Site** field, enter or select a value.
6. In the **Warehouse** field, enter or select a value.
7. Expand the **Methods** section. The **Selected methods** pane lists the methods for the selected wave template type. The wave template must include the containerize method.  
8. In the **Wave step code** field, type a value. Enter a Wave step code for the added method, which can be any code. It's possible to add the method more than once and assign different wave step codes. To do this, select **Repeatable for this method** in the **Wave process methods** page.  
9. Select **Save**.
10. Close the page.

## Set up a container type
1. In the navigation pane, go to **Modules > Warehouse management > Setup > Containers > Container types**. You can define your containers in the **Container types** page. You can configure the physical dimensions of containers including tare weight, maximum weight, maximum volume, length, width, and height. In this example, we have three different sizes of boxes.  
2. Select **New**.
3. In the **Container type code** field, type a value.
4. In the **Tare weight** field, enter a number.
5. In the **Maximum weight** field, enter a number.
6. In the **Volume** field, enter a number.
7. In the **Length** field, enter a number.
8. In the **Width** field, enter a number.
9. In the **Height** field, enter a number.
10. In the **Description** field, type a value.
11. Select **Save**.
13. Repeat steps 2-11 two more times to make three total container types.
14. Close the page.

## Set up a container group
1. In the navigation pane, go to **Modules > Warehouse management > Setup > Containers > Container groups**.
2. In the action pane, select **New**. You can set up logical groups of container types. For each group, you can specify the sequence in which to pack the containers and the percentage of the containers to fill.The size dimensions of the item is used to determine whether it will fit in a container. The container that is closest to the size dimensions of the item is used. If you have multiple container types in a group, we recommend that you arrange the sequence by size, so that the largest container is first, number 1 in the sequence, and the smallest container is last.    
3. In the **Container group ID** field, type a value that you created earlier.
4. In the **Description field**, type a value.
5. Repeat steps 2-4 for all three container types you created earlier.
6. Select **Save**.
7. Close the page.

## Set up a container build template
1. In the navigation pane, go to **Modules > Warehouse management > Setup > Containers > Container build templates**.
2. Select **New**. The container build template is based on which of the containerization processes are performed. Each container build template defines one containerization process that will be used by a wave template. The **Edit query** option allows you to define the conditions on which the selected template will be processed. For example, you may want to only run containerization for specific customers, products, or warehouses or you can add the corresponding query ranges to the template. The **Wave step code** field is how a container build template is linked to steps in a wave template. When a wave is executed, it determines which container build template(s) are used to initiate containerization. The Base query type field determines what to pack and what to base the filter query on. 
3. In the **Container template ID** field, type a value.
4. In the **Container group ID** field, enter or select a value.
5. In the **Wave step code** field, type a value.
6. Select the **Allow split picks** check box.
7. Select **Save**.
8. Select **Containier mixing constraints**. Mixing logic breaks allows you to set up rules for packing allocation lines in containers. For example, if you add the **Item number field**, when items are assigned to containers, a new container will be created when there is a new item number. This is will prevent workers from packing allocations lines for two different customers in the same container.  
9. Select **New**.
10. In the **Table** field, select an option.
11. In the **Field Select** field, enter or select a value.
12. Select **OK**.

