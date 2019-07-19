# Content Rich block

Content rich block is used for textual content on the page. The textual content can be informational or promotional purposes. 

Content rich block is a special container that allows Content Rich Block Items to be placed within it. Multiple content rich block items can be placed in this container in a single or multi-column view. 

Content rich block and content rich block item modules are driven by CMS data which can authored in the tooling. It’s a standalone module and does not have dependency on page context on any other modules in the page. Technically this allows content rich block to be placed on any page for inform.

## Usage examples in ecommerce:

* Content rich block is used to showcase product features on a product details page.
* Content rich block can be used on any page for informational purposes E.g. Benefits of Loyalty program, Shipping and Return policies, Frequently Asked questions, About us etc.
* Content rich block is used to do add custom messages on a product details page E.g. “Free shipping for order over $50”. 
* Content rich block can be used on product details page, cart, checkout etc for disclaimers and contact details E.g. “Shipping and returns are subject to store policies” 

## Content Rich Block module properties

|   Property name   | Values                         | Property Description                                         |
| :---------------: | :----------------------------- | ------------------------------------------------------------ |
| Number of columns | Values 1-4                     | A content rich block supports upto 4 columns inside it.      |
|       Width       | Fit container<br />Fill screen | Fit container restricts the items inside the container to fit within   the container width.   Fill screen does not restrict the items within container, they could   go full-bleed on the screen.<br />The values can be changed per the layout that we want to achieve. |

 

## Content Rich Block Item module properties

| Property name | Values         | Property Description                                         |
| :-----------: | -------------- | ------------------------------------------------------------ |
|   Paragraph   | Paragraph text | This is the text that accompanies each content rich block item. Some basic rich text capabilities such as Bold, Underline, Italics are supported. |

 

## Creating a page with a Content rich block module

This section explains how to add a Content rich block module to a new page and set the required properties. . Refer to Templates and Pages for more details.

1. We need to first create a template. In tooling, create a new page template “Content template”.

2. In the Main slot the Default Page add a Content rich block module. 

3. Check-in and Publish.

4. Now create a new page with the “Content template” and call it “Content page”.

5. In the page outline, add Default Page. To the Main slot, add Content rich block module.

6. Expand the Content rich block properties, set Number of columns to 2.

7. On the page outline, choose Content rich block module and select add a module. Add a Content rich block item, say item1. 

8. To Content rich block item 1, add Paragraph text.

9. On the page outline, choose Content rich block module and select add a module. Add a Content rich block item again, say item2. 

10. To Content rich block item 2, add Paragraph text.

11. Save the page and preview the changes. 

12. You will see two rich text blocks placed in two column view. If a third content rich block item is added, it will stack below the two items.  By changing the number of columns on the container and the number of items inside it, different layouts can be achieved for textual content.

13. Check-in and Publish

