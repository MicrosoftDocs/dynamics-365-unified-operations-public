---
# required metadata

title: Configure dimension to be represented as swatch 
description: This topic describes how to configure dimension values  in Commerce headquarters to be represented as a swatch
author: anupamar-ms
ms.date: 01/05/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rapraj
ms.search.validFrom: 2020-09-20
ms.dyn365.ops.version: Retail 10.0.20 update

---

# Configure dimension to be represented as swatch 

[!include [banner](../../includes/banner.md)]

This topic describes how to cconfigure dimensions for a product such that it can be presented as a swatch in the e-commerce experience.

Dynamics 365 Commerce supports dimensions Size, Style and Color for representing product variants. These dimensions are typically displayed as text value E.g Size = Small, Large, Medium or Color = Black, Brown. However, for a product that supports many variations, browsing through these variants requires multiple selections to view each product variant image. This makes the selection process slow and tedious for a shopper.

Displaying dimensions as swatches allow you to browse a large variety of colors, patterns and textures easily. They also allow you to try different combinations of a product quickly. With this feature we are introducing the capability to display dimensions as a swatch using image and hexcode. In addition to displaying dimensions as swatches, we are also providing the capability to group the dimensions in a refiner experience on the product list pages.  For example, if there are 3 products, say A, B and C. A is sold in Dark Blue, Black, B is sold in Navy Blue and White. C is sold in Midnight Blue and Red. On product list page with A, B and C, the refiner shows will show 6 colors - Dark Blue, Black, Navy blue, White, Midnight blue and Red. This makes the product discovery experience difficult for a customer as they have to click on each shade of Blue to find the respective products. With refiner grouping, we can now create a refiner group Blue which maps to colors Dark blue, Navy blue, Midnight blue. This way on a list  page,  a user will see only Blue on the refiner panel which on selection will filter and show products A,B, and C from the above example. It significantly improves the product refinement experience and allows them to find more products with a single refiner click. 

> [!NOTE]
> This feature is now available in Dynamics 365 Commerce 10.0.20 release.

The following is an illustration of displaying Colors as a swatch on e-commerce. 
![Example of displaying color as swatch on e-commerce product details page](../dev-itpro/media/.PNG)

The following is an illustration of refiner experience in e-commerce where the refiner panel shows grouped colors. 
![Example of displaying color as swatch on e-commerce list page](../dev-itpro/media/.PNG)

## Feature flag management
To enable this feature, you must go to Commerce Headquarters, Feature Management and turn on  **Enable image support for product dimension values**.   When this feature flag is enabled, 3 new fields are added for each dimension in the respective tables– **Hexcode**, **Image Url** and **Refiner Group**. 

## Configure dimension values in Commerce Headquarters
Dimension Size, Style and Color dimensions support swatch. Both Hexcode and Image Url configuration must be provided for the respective values in Headquarters. If a value is not provided it will be defaulted to Dimension friendly name for display. Managing Hexcode and Image url follows the same pattern that we use for managing dimension display order. This can be configured in any of the following forms. 
- Dimension: Search for each dimension **Color**, **Size** or **Style**. In each of the respective forms, the dimension values will be shown. Here in addition to managing display order, you can also manage Hexcode and Image Url. The following is an example of the configuration on Color form. 
![Example of dimension configuration on Color form](../dev-itpro/media/.PNG)
- Dimension groups: Dynamics 365 Commerce allows the capability to create dimension groups. If you have dimension groups defined, search for **Color group**, **Size group**, **Style group**. In the respective forms, you can manage the Hexcode or ImageUrl.The following is an example of the configuration on Color group form.  ![Example of dimension configuration on Color group form](../dev-itpro/media/.PNG)

- Product dimension when creating a product. When creating a new product,  **Product Dimensions** form can be used to enter the dimension values. For an existing dimension value, where Hexcode, Url, Refiner Group will be pre-populated. If needed these values can be changed here. In each form, three new fields are included – Hexcode, Image Url and  Refiner Group. In the next few sections, we will discuss how these values should be provided.The following is an example of the configuration on Product dimensions form. ![Example of dimension configuration on product dimensions form](../dev-itpro/media/.PNG)

## Configure dimension values using Hexcode
If a dimension say Color needs to represented using hexcode, the respective hexcode value should be provided in the table as described in the previous section. E.g.  Color=Black should have Hexcode #00000. In Commerce headquarters, for each dimension value, the respective Hexcode value should be provided in the hexcode format. On e-commerce rendering, this hexcode will be represented as a swatch. 
Below is an example of Color configured as Hexcode on Color form in Headquarters. 
 ![Example of dimension configuration using Hexcode](../dev-itpro/media/.PNG)

## Managing dimension values using Image Url
If a dimension say Color needs to represented using image, the respective image url should be provided in the dimension table as described in the previous section.  For example, Color=Leopard, can be best represented only as an image. The Image Url should be defined for Color-Leopard in Commerce Headquarters. The respective image should then be uploaded to Site Builder. On e-commerce rendering, if a dimension is chosen to be displayed as a swatch and a hexcode is not defined, an image look up will be done. If the image look-up also fails, e-commerce rendering will fallback to the dimension friendly name (text). 

Like Products and Category images, a Media template can be used to define the Image Url.  Below is an example of Color using Media template url to define the file path of the images. The name of the file and file path are important as they need to be consistent when uploading the images to Site Builder.

Below is an example of Color configured with Image Urls
![Example of dimension configuration using Image Url](../dev-itpro/media/.PNG)

## Managing dimension values using both Hexcode and Image url
For a dimension say Color, some values can be hexcode while others can be Image url. With the e-commerce rendering fallback logic, it will automatically look for either hexcode or an image url to display the Color.  This simplifies the image management experience when dealing with large numbers of colors.

Below is an example of Color configured with Hexcode and Image Urls
![Example of dimension configuration using Hexcode and Image Url](../dev-itpro/media/.PNG)


## Configure Refiner Group in Commerce Headquarters
While defining Hexcode or Image Url for a dimension value, you can also state the Refiner Group value. The Refiner Group value will be name of the dimension that should be used in the refiner experience. For instance in the below example if a product has Color values Navy Blue, Light blue or Gray Blue, it will show the hexcode mapped for these Colors on the product details page and product cards. On the refiner experience, since these dimension values are mapped to Refiner Group = Blue, refining on Blue will show products that have Color = Navy Blue, Light blue or Gray Blue on the page.

Below is an example of Refiner group management
![Example of refiner group management](../dev-itpro/media/.PNG)



## Image Management in Site Builder
If image Urls are used for any dimension value, the respective image need to be uploaded to Site Builder. They should follow the same folder path and file name as defined in Commerce Headquarters. 
[Folder path]

## Swatch display in e-commerce
On e-commerce, swatches can displayed in experiences that require a dimension selection i.e. Product details page, Product cards on list pages, Quick view module, refiners on list pages. To enable the experience on e-commerce, you need to opt-into the Dimension site settings.

In addition, to display swatches on the list pages, the Search Results module property **Include product attributes** should be enabled on the Search Results module. If there are any enriched category pages, each of these pages should also be updated respectively. 


## Swatch display in POS and other channels
We don’t have an out-of-box implementation to display swatches on POS and other channels. If required it can be achieved as an extension. The channel APIs return the hexcode and image url information needed to render the images.


## Additional resources

[Pickup information module](../pickup-info-module.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
