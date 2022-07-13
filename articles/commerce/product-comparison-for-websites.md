---

# required metadata

title: Product comparison for eCommerce websites
description: This article describes how to allow shoppers on your website to do product comparison.
author: ashishmsft
ms.date: 07/12/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin, josaw
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2022-02-28
---

# Product comparison

> [!NOTE]
> This feature is available starting with the Dynamics 365 Commerce version 10.0.29 release. This feature is available for both B2C and B2B websites.

Enable shoppers to compare products across a wide range of categories in order to make the right purchase decision for themselves. 

![Product Comparison Overview](./media/Product-Comparison-Overview.png)

On product list pages (PLPs) like category results, search results and product collections, through sitebuilder similar to the "Quick view" button, you are now able to add a new button for "Product Comparison" which allows shoppers to add products to the comparison tray. Allowing shoppers to quickly add products for comparison by clicking on it from the product tile. This would bring up preview panel showing the total number of products that shopper may currently have in comparison and the preview of the product. Shoppers are also able to add products from the product details page (PDP) and they can add specific variant of the product if they were to be interested in comparing specific variants versus product masters.

Essentially, 'Comparison tray panel' allows you to add a few products to compare and upon clicking 'Compare' it will redirect you to the product comparison page for the comparison. Product comparison page shows you the product details comparing the images, price, product dimensions (size, style, color), aggregated ratings information as well as various product attributes. 

![Product Comparison Page](./media/Product-Comparison-Page.png)

> [!NOTE]
> Product comparison page shows comparison among default set of properties as shared above as well as all attributes that are viewable on a PDP for a given product. 

## How to limit the number of products in the comparison tray? 
The limit on the number of products in the comparison tray is configurable. By default, there's no limit provided but through **Site settings > Extensions** you can configure the limits for both mobile and desktop view. Allowing you to specify the maximum number of products that can be added to the comparison at the same time. If not defined, no limit will be enforced.

+ Products in the comparison limit - desktop devices
+ Products in the comparison limit - mobile and tablet devices

![Site settings to limit products in comparison tray](./media/Site-settings-to-limit-products-in-comparison-tray.png)


