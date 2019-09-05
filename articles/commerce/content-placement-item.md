---
# required metadata

title: Content placement item module
description: This topic describes content placement item module and how it can be used on ecommerce pages.
author: anupamar-ms
manager: Brendan Sullivan
ms.date: 07/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: 
ms.search.industry: 
ms.author: Anupama Raju
ms.search.validFrom: 07/19/2019
ms.dyn365.ops.version: 

---
# Content Placement Item

Content placement item is used for showcasing multiple promotions, policies, product features using both image and text. For example, it can be used on home page to show case store policies, shipping etc. 

Content placement item is driven by CMS data which can authored in the tooling. This allows content placement items to be placed on any page. However, it can only be placed within a content placement module<link> which is the container that will host this module.  .  

## Usage examples in ecommerce:

* Content placement items can be used on home page or any marketing page to showcase informational text such as Store policies, Shipping etc.

* Content placement items can be used on product details page to showcase product features.

## Content Placement Item module properties

| Property name | Values                                                       | Property Description                                         |
| :-----------: | :----------------------------------------------------------- | ------------------------------------------------------------ |
|    Heading    | Heading text<br /><br />Heading tag = H1, H2, H3, H4, H5, H6 | Each content placement item module can have a heading. Heading   supports heading tag which defaults to H2 but can be changed to meet   accessibility requirements. |
|   Paragraph   | Paragraph text                                               | Content placement item supports paragraph in rich text format. Some   basic rich text functionality is supported such a Bold, Underline, Italics,   hyperlinks etc. Some of these capabilities may be overridden by the page   theme applied on the module. |
|     Image     | Image                                                        | An image can be associated to the text                       |
|     Link      | Link Url <br />Link text                                     | A link can be added to the text to redirect the user to a specific   page or content |
|   Tile size   | 1-12                                                         | Tile size on each content placement item defines the number of slots each   item should take within the content placement container. Max size of the   container is 12.    Note: If tile size for first n items in the content placement is over   12, it will reflow to the next row. |

 

## Creating a page with a Content placement item module 

This section explains how to add a Content placement module to a new page and set the required properties. 

1. We need to first create a template. In tooling, create a new template “Content placement template”.

2. In the Main slot the Default Page, add a Content placement module. 

3. Add a Content placement item module to the content placement module

4. Check-in and Publish. 

5. Now create a new page with the “Content placement template” and call it “Content placement page”.

6. Add Default page. In the page outline, add Content placement module to the Main slot of the Default page.

7. To the Content placement module, add a Content Placement item module.

8. In the Content placement item module property panel, choose an Image from the image picker. 

9. In the Content placement item module property panel, set a Heading 

10. In the Content placement item module property panel, add a Paragraph 

11. In the Content placement item module property panel,, add a link and set the link url to some page.

12. Set Tile size =6

13. To the Content placement module, add another content placement item module and repeat steps 10-12

14. Save and Preview. 

15. Preview will show two content placement items placed side by side. You can further alter the Tile size property of each content placement item module or add more modules to achieve the desired layout. 

16. Check-in and Publish the page. 
