--- 
# required metadata 
 
title: Set up containerization
description: This procedure describes how to automate the containerization of loads in Warehouse management. 
author: YuyuScheller
manager: AnnBe 
ms.date: 11/02/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up containerization

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure describes how to automate the containerization of loads in Warehouse management. Automated containerization creates containers and the picking work for shipments when a wave is processed and work lines can be split into quantities that fit the containers. This helps warehouse workers to pick the items directly into the chosen container. Compared to the manual packing process, tasks such as creating containers, assigning items, and closing containers are automated by the system. This procedure uses the USMF demo company and is performed by a Warehouse manager.


## Set up a wave template
1. Go to Warehouse management > Setup > Waves > Wave templates.
2. Click New.
3. In the Wave template name field, type a value.
4. In the Wave template description field, type a value.
5. In the Site field, enter or select a value.
6. In the Warehouse field, enter or select a value.
7. Expand the Methods section.
    * The Selected methods pane lists the methods for the selected wave template type. The wave template must include the containerize method.  
8. In the list, find and select the desired record.
9. In the Wave step code field, type a value.
    * Enter a Wave step code for the added method, which can be any code. It’s possible to add the method more than once and assign different wave step codes. To do this, select Repeatable for this method in the Wave process methods page.  
10. Click Save.
11. Close the page.

## Set up a container type
1. Go to Warehouse management > Setup > Containers > Container types.
    * You can define your containers in the Container types page. You can configure the physical dimensions of containers including tare weight, maximum weight, maximum volume, length, width, and height. In this example, we have three different sizes of boxes.  
2. Click New.
3. In the Container type code field, type a value.
4. In the Tare weight field, enter a number.
5. In the Maximum weight field, enter a number.
6. In the Volume field, enter a number.
7. In the Length field, enter a number.
8. In the Width field, enter a number.
9. In the Height field, enter a number.
10. In the Description field, type a value.
11. Click Save.
12. Click New.
13. In the Container type code field, type a value.
14. In the Description field, type a value.
15. In the Tare weight field, enter a number.
16. In the Maximum weight field, enter a number.
17. In the Volume field, enter a number.
18. In the Length field, enter a number.
19. In the Width field, enter a number.
20. In the Height field, enter a number.
21. Click Save.
22. Click New.
23. In the Container type code field, type a value.
24. In the Description field, type a value.
25. In the Tare weight field, enter a number.
26. In the Maximum weight field, enter a number.
27. In the Volume field, enter a number.
28. In the Length field, enter a number.
29. In the Width field, enter a number.
30. In the Height field, enter a number.
31. Click Save.
32. Close the page.

## Set up a container group
1. Go to Warehouse management > Setup > Containers > Container groups.
2. Click New.
    * You can set up logical groups of container types. For each group, you can specify the sequence in which to pack the containers and the percentage of the containers to fill. The size dimensions of the item is used to determine whether it will fit in a container. The container that is closest to the size dimensions of the item is used. If you have multiple container types in a group, we recommend that you arrange the sequence by size, so that the largest container is first, number 1 in the sequence, and the smallest container is last.    
3. In the Container group ID field, type a value.
4. In the Description field, type a value.
5. Click New.
6. In the list, mark the selected row.
7. In the Container type field, enter or select a value.
8. Click New.
9. In the list, mark the selected row.
10. In the Container type field, enter or select a value.
11. Click New.
12. In the list, mark the selected row.
13. In the Container type field, enter or select a value.
14. Click Save.
15. Close the page.

## Set up a container build template
1. Go to Warehouse management > Setup > Containers > Container build templates.
2. Click New.
    * The container build template is based on which of the containerization processes are performed. Each container build template defines one containerization process that will be used by a wave template. The Edit query option allows you to define the conditions on which the selected template will be processed. For example, you may want to only run containerization for specific customers, products, or warehouses or you can add the corresponding query ranges to the template. The Wave step code field is how a container build template is linked to steps in a wave template. When a wave is executed, it determines which container build template(s) are used to initiate containerization. The Base query type field determines what to pack and what to base the filter query on.  
3. In the list, mark the selected row.
4. In the Container template ID field, type a value.
5. In the Container group ID field, enter or select a value.
6. In the Wave step code field, type a value.
7. Select the Allow split picks check box.
8. Click Save.
9. Click Containier mixing constraints.
    * Mixing logic breaks allows you to set up rules for packing allocation lines in containers. For example, if you add the Item number field, when items are assigned to containers, a new container will be created when there is a new item number. This is will prevent workers from packing allocations lines for two different customers in the same container.  
10. Click New.
11. In the Table field, select an option.
12. In the Field Select field, enter or select a value.
13. Click OK.

