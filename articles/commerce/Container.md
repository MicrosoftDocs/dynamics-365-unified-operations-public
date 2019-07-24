---
# required metadata

title: Containers
description: This topic reviews setting up a container module in a Dynamics 365 e-Commerce page.
author: anupamar-ms
manager: BrendanSullivanMSFT
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---

# Containers

A container is a module that hosts other modules in it. The properties of the container help define the layout of the modules within. Its primary purpose is to define the layout.  For instance, using a container the modules inside can be placed side by side in a two, three, four or six column view.  

There are three standard containers that we support –Container, Container with 2-slots and Container with 3-slots. Any module can be placed within these containers. In addition, there are some special containers such as Carousel, Content rich block, Content placement, Cart, Checkout, Buy box, Header and Footer. These containers have a specific application and cannot be used for all modules. Please refer to documentation for these containers for more details. In this document we will cover the three standard containers that are available.  

It is recommended practice to put modules within a container so they can adhere to the container width. [Need more on why] 

Usage examples for ecommerce: 

- A site author wants a three-column view with 3 modules placed side by side. This can be achieved with the Container with 3-slots 
- A site author wants a six-column view with 6 modules placed side by side. This can be achieved with a Container with six columns in it. 
- A site author wants to place a module on the page but doesn’t want it to go full-bleed on the page. This can be achieved by adding the module to the Container and restricting the Width property 

## Container 

Container is the most generic container that we support. It allows you to add a heading to the container if needed and set the number of columns for the modules to be rendered. It also allows modules to render within the container width or go full-bleed on the page. 

### Properties for Default Container 

| Property name     | Values                                            | Property Description                                         |
| ----------------- | ------------------------------------------------- | ------------------------------------------------------------ |
| Heading           | Heading text Heading tag = H1, H2, H3, H4, H5, H6 | A container can have a heading. Heading supports heading tag which defaults to H2 but can be changed to meet accessibility requirements |
| Width             | Fit Container Fill screen                         | This defines if the modules should fit the width of the container or go fill the screen. The default setting is fill to width |
| Number of columns | 1,2,3,4,6, 12                                     | The default container allows up-to 12 columns in it.         |

 

## Container with 2-slots 

Container with 2-slots is a container that is optimized for two column view. It has additional properties that allow the layout to be further optimized by view port. 

This container has 2-slots which allows a side-by-side view of modules inside it. In addition, the width of each column can be defined by view port. Below are the column width settings 

3 x 9: In this setting, the first module will have a column width of 3 and the second module will have a column width of 9. 

4 x 4: In this setting, the first module will have a column width of 4 and the second module will have a column width of 4. There will 2-column padding on the left and right margin 

6 x 6:  In this setting, both modules will have equal column width. 

8 x 4: In this setting, the first module will have a column width of8 and the second module will have a column width of 4. 

9 x 3: In this setting, the first module will have a column width of 9 and the second module will have a column width of 3. 

12 x12: In this setting, both modules have full column width. This will make the modules stack one below the other. In some view ports this may be preferred even though this goes against the two-column intent. 

 

### Properties of Container with 2-slots 

| Property name                   | Values                               | Property Description                                         |
| ------------------------------- | ------------------------------------ | ------------------------------------------------------------ |
| Heading                         | Heading text  Heading tag            | An optional can be provided for the container                |
| X-Small view port configuration | 3 x 9 4 x 4 6 x 6 8 x 4 9 x 3 12 x12 | This defines the layout for X-Small view ports.              |
| Small view port configuration   | 3 x 9 4 x 4 6 x 6 8 x 4 9 x 3 12 x12 | This defines the layout for Small view ports such as Mobile  |
| Medium view port configuration  | 3 x 9 4 x 4 6 x 6 8 x 4 9 x 3 12 x12 | This defines the layout for Medium view ports such as Tablets. |
| Large view port configuration   | 3 x 9 4 x 4 6 x 6 8 x 4 9 x 3 12 x12 | This defines the layout of the two columns on PCs.           |

 

## Container with 3-slots 

Container with 3-slots allows 3 columns inside, its optimized for three column view. It has additional properties that allow the layout to be further optimized by view port 

The width of each column can be defined by view port. Below are the column width settings 

<TBD> 

### Properties of Container with 3-slots 

| Property name                   | Values                    | Property Description                                         |
| ------------------------------- | ------------------------- | ------------------------------------------------------------ |
| Heading                         | Heading text  Heading tag | An optional can be provided for the container                |
| X-Small view port configuration |                           | This defines the layout for X-Small view ports.              |
| Small view port configuration   |                           | This defines the layout for Small view ports such as Mobile  |
| Medium view port configuration  |                           | This defines the layout for Medium view ports such as Tablets. |
| Large view port configuration   |                           | This defines the layout of the two columns on PCs.           |

 

## Adding a page with a container 

This section explains how to add a video player module to a new page and set the required properties.  

1. In tooling, create a new page template “Container template”. 

2. In the Main slot of the template, add a Container. 

3. To the default container, add a Feature module 

4. Check-in and Publish.  

1. Now create a new page with the “Container template” and call it “Container page” 

1. In the page outline, add Container. 

1. To the Container, set the number of columns =1 and Width=Fill container width 

1. Add a Feature, set the heading.  

1. Save and Preview. 

1. Preview will show one Feature module that is within container width. 

1. Now change the Number of columns in Container property panel to 3. 

1. Add two more Features modules to the Container 

1. Save and Preview.  

1. Preview will show three Feature modules side by side. 

1. Check-in and Publish the page once the desired layout is achieved. 