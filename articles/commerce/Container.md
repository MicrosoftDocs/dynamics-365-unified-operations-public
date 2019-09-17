---
# required metadata

title: Add a container module to a page
description: This topic covers container modules and how to add them to site pages in Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Add a container module to a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers container modules and how to add them to site pages in Dynamics 365 Commerce.

## Overview

A container module is a module that hosts other modules within it, and is the most generic container used in Commerce. The primary purpose of a container module is to define the layout of the modules within it using the properties of the container module. For example, the modules inside a container can be placed side-by-side in a two, three, four, or six-column view. Modules can be set to render within the container width or go full-bleed on a page. A heading can also be added to a container module if needed.

There are three standard types of container modules: container, container with 2-slots, and container with 3-slots. Any module can be placed within these container module types. In addition, there are special container modules such as carousel, content rich block, content placement, cart, checkout, buy box, header, and footer. These containers have a specific application and can only be used to contain certain supported modules. 

It is recommended practice to put modules within a container so they can adhere to the container width.

## Examples of container module uses in e-Commerce

- A site author wants a three-column view with three modules placed side by side. This can be achieved with the container with 3-slots. 
- A site author wants a six-column view with six modules placed side by side. This can be achieved with a container with six columns in it. 
- A site author wants to place a module on the page but does not want it to go full-bleed on the page. This can be achieved by adding the module to a container module and restricting the container's width property. 

## Container module properties 

| Property name     | Values                                            | Property description                                         |
| ----------------- | ------------------------------------------------- | ------------------------------------------------------------ |
| Heading           | Heading text<br/>Heading tag = H1, H2, H3, H4, H5, H6 | The optional container heading text and heading tag. The default heading tag value is H2 but it can be modified to meet accessibility requirements. |
| Width             | Fit container<br/>Fill screen                         | This property defines whether the modules should fit within the width of the container (the default) or fill the screen. |
| Number of columns | 1,2,3,4,6,12                                     | The number of columns allowed in the container, up to 12 columns.         |

## Container with 2-slots 

Container with 2-slots is a container module that is optimized for a two-column view. It has additional properties that allow the layout to be further customized by view port (mobile, tablet, PC, etc.). 

This container has two slots which allow a side-by-side view of the modules within it. The width of each column can be defined for each view port. The column width settings are as follows. 

- **75%/25%:** The first module has a column width of 75% and the second module has a column width of 25%. A **25%/75%** option is also available.

- **50%/50%** Both modules have equal column width.

- **67%/33%:** First module has column width of 67% and the second module has a column width of 33%. A **33%/67%** option is also available.

- **100%** Both modules have a full column width, which makes the modules stack one below the other. In some view ports this may be preferred, even though this goes against the two-column intent of this container module (for example, in extra small view ports such as mobile).


### Container with 2-slots properties  

| Property name                   | Values                               | Property description                                         |
| ------------------------------- | ------------------------------------ | ------------------------------------------------------------ |
| Heading                         | Heading text<br/>Heading tag            | An optional can be provided for the container                |
| X-Small view port configuration | <br>25%/75%</br> <br>75%/25%</br> <br>50%/50%</br> <br>67%/33%</br> <br>33%/67%</br> <br> 100%</br>  | This defines the layout for extra small view ports.              |
| Small view port configuration   | <br>25%/75%</br> <br>75%/25%</br> <br>50%/50%</br> <br>67%/33%</br> <br>33%/67%</br> <br> 100%</br> | This defines the layout for small view ports such as mobile devices.  |
| Medium view port configuration  | <br>25%/75%</br> <br>75%/25%</br> <br>50%/50%</br> <br>67%/33%</br> <br>33%/67%</br> <br> 100%</br> | This defines the layout for medium view ports such as tablets. |
| Large view port configuration   | <br>25%/75%</br> <br>75%/25%</br> <br>50%/50%</br> <br>67%/33%</br> <br>33%/67%</br> <br> 100%</br> | This defines the layout for medium view ports such as PCs.           |


## Container with 3-slots 

Container with 3-slots allows 3 columns inside, its optimized for three column view. It has additional properties that allow the layout to be further optimized by view port 

The width of each column can be defined by view port. Below are the column width settings 

**33%/33%/33%:** All three modules have equal column width.
**50%/25%/25%:** The first module has a column width of 50%, and the remaining two modules have column widths of 25%. Other variations such as **25%/50%/25%** and **25%/25%/50%** are also supported.
**16%/16%/67%:** The first two modules have column widths of 16% and the third module has a column width of 67%. Other variations such as **16%/67%/16%** and **67%/16%/16%** are also supported.


### Container with 3-slots properties  

| Property name                   | Values                    | Property description                                         |
| ------------------------------- | ------------------------- | ------------------------------------------------------------ |
| Heading                         | Heading text  Heading tag | An optional can be provided for the container                |
| X-Small view port configuration |<br>33%/33%/33%</br> <br>50%/25%/25%</br> <br>25%/50%/25%</br> <br>25%/25%/50</br> <br>16%/16%/67%</br> <br> 16%/67%/16%</br> <br> 67%/16%/16% </br>  | This defines the layout for extra small view ports.              |
| Small view port configuration   | <br>33%/33%/33%</br> <br>50%/25%/25%</br> <br>25%/50%/25%</br> <br>25%/25%/50%</br> <br>16%/16%/67%</br> <br> 16%/67%/16%</br> <br> 67%/16%/16% </br>  | This defines the layout for small view ports such as mobile devices.  |
| Medium view port configuration  | <br>33%/33%/33%</br> <br>50%/25%/25%</br> <br>25%/50%/25%</br> <br>25%/25%/50%</br> <br>16% 16% 67%</br> <br> 16%/67%/16%</br> <br> 67%/16%/16% </br>  | This defines the layout for medium view ports such as tablets. |
| Large view port configuration   |<br>33%/33%/33%</br> <br>50%/25%/25%</br> <br>25%/50%/25%</br> <br>25%/25%/50%</br> <br>16%/16%/67%</br> <br> 16%/67%/16%</br> <br> 67%/16%/16% </br>   | This defines the layout for medium view ports such as PCs.           |

 
## Add a container module to a page 

To add a container player module to a new page and set the required properties, do the following.  

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
