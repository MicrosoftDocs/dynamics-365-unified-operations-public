# Hero

Hero is used to market products or promotions using rich images. For example, a new product is launched in the ecommerce site and the retailer wants to promote this product on the homepage to get the shoppers attention. 

Hero module is driven by CMS data which can authored in the tooling. It’s a standalone module and does not have dependency on page context or any other modules on the page. Technically this allows Hero to be placed on any page where a C1 wants to promote content.

Usage examples in ecommerce:

- Hero is used on the ecommerce home page to highlight promotions and new products
- Hero is used in a product details page to showcase product information
- Multiple Hero modules can be placed within a carousel to highlight multiple products or promotions in the store

## Hero module properties

| Property name  | Values                                                       | Property Description                                         |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Image          | Image file                                                   | This is the image that will be used to showcase a product or a   promotion on the Hero. An image can uploaded to the image gallery or an   existing image can be used. |
| Heading        | Heading Text<br /><br />Heading tag = H1, H2, H3, H4, H5, H6 | A hero can have a heading which is embedded on the image. Heading   supports heading tag which defaults to H2 but can be changed to meet accessibility requirements |
| Paragraph      | Paragraph text                                   | Hero has the flexibility to supports additional lines to text as rich   text. Some basic rich text functionality is supported such a Bold, Underline, Italics, hyperlinks etc. Some of these capabilities may be overridden by the page   theme applied on the module. |
| Link           | Link text<br />Link url<br />Aria label<br />Open link in new tab | A Hero can have one or more call to actions. E.g. “Shop Now” which   redirects the shopper to the link. If a link is added, link text, url and aria label must be provided.<br />Aria-label should be descriptive for accessibilty.<br />If user wants to open the link in a new tab, that can be configured. |
| Text placement | Top Left<br />Top Right<br />Top Center<br />Bottom Left<br />Bottom Right<br />Bottom<br />Center Left<br />Center Right<br />Center Center | This property defines the placement of text placement on the image. A total of 9 different placements are supported.|
| Text theme   | Light<br />Dark | A color scheme can be defined for the text based on the image on the  background. If the image has dark background a light theme can be applied on the text to make it visible and to meet color contrast ratios for accessibilty. |
| Gradient |True or false| Applies a gradient to the image. It can be used to meet color contrast ratio for accessiblity |

 

## Creating a page with a Hero module

This section explains how to add a Hero module to a new page and set the required properties for the Hero. Refer to Templates and Pages for more details on these actions.

1. We need to first create a template. In tooling, add a new page template “Hero template”.

2. In the Main slot of the Default Page, add a Hero module. A hero can be placed directly on the page or within a container<link>.  Multiple Hero images can be placed within a Carousel <link>. 

3. Check-in and Publish. 

4. Now create a new page with the “Hero template” and call it “Hero page”

5. In the page outline, add Default Page and then add Hero module to the Main slot.

6. Expand the Hero properties, add Image. From the image picker, choose an existing image or upload a new asset. 

7. Add a Heading to the Hero, change the default text as needed.

8. Add a Paragraph, change the default text as needed.

9. Add a Link, set the link text to “Shop Now” and add a link url to the page you want to redirect. Set the Aria label to be description “Shop now for Surface Laptop sale”

10. Save the page and preview the changes.

11. Other properties of Hero can be changed to achieve a more customized Hero – Text placement, Text theme etc

12. Check-in and Publish
