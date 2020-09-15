---
# required metadata

title: This topic provides an overview of how to override a starter kit components to allow customizations within a theme.
description: This topic provides an overview of 
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Override a starter kit component in a theme

[!include [banner](../includes/banner.md)]

This topic provides an overview of how to override a starter kit components to allow customizations within a theme.

## Overview
The Dynamics 365 Commerce store starter kit contains a set of overridable typescript components that are used by various starter kit modules.  These components contain helper APIs called by some starter kit modules that contain business and other logic to help in rendering the appropriate module HTML markup, handle some events and make some server side calls.  If you need to change any logic in a component, the component can be overwritten for a selected theme using the CLI [add-component-override](cli-command-reference.md) command. 

For example if you want to change the logic for strike-through pricing, you can look at overriding the **Price** component and make changes.  Other changes such as [module view overrides](theme-module-extensions.md) can also be used for visual changes.  In rare cases, you may need to [clone a module](clone-starter-module.md) to make all the changes you need.

## Component list
To get a list of components you can use the following CLI command. 

```bash
yarn msdyn365 add-component-override --list-components
```

Component source code can be found under the "\node_modules\@msdyn365-commerce\components\src\" inside the installed Online SDK directory.  You may want to browse the source code to see what options are available within each component.

The following is a list of components includes as part of the store starter kit.  The list may differ based on the version of the store starter kit being used.

| Component                 | Description                                                           |
|---------------------------|-----------------------------------------------------------------------|
| AddToCart     | This component is used to add a product to the cart. It works in combination with the cart state present in global-state package.  On UX, this component is represented as a button. On click of the button, it validates the inventory check for the product and finally calls addcartline API in retail server to add the product to the cart. |
| AddToWishlist | temp description |
| CartIcon      | This component is used to render the HTML to display the cart-icon in the header module. The cart-icon component will navigate to the cart page on click.  The store starter kit also has a cart-icon module apart from this component. If the cart-icon module is not configured in header, then this component is used as a fall back. |
| CartLineItem  | This component is used to render the HTML to display a single cart line item. It consists of product image, product configuration selected in buybox, product quantity, product price with discounts.  |
| Price         | This component is used to render the HTML to display the product price across the site in the correct formatting. It does not make any API call. |
| Product       | This component is used to render the HTML to display the products in a card format across the site. It consists of product image, title, description, price and rating. |
| PromoCode     | This component is used to apply promotion or discount codes to cart. This works in combination with the cart state present in global state package to apply or remove a promotion in the cart. |
| Rating        | This component is used to render the HTML to display the product rating across the site. It does not make any API call. This component also handles the click event to update the rating. |
| SocialMedia | This component is used to render the social media icons for sharing a product on the buybox module. Currently it supports Facebook, LinkedIn, Mail, Pintrest, Twitter.
| WishListIcon  | This component is used to render the HTML to display the wishlist-icon in the header module. This component handles the click event to navigate to the wishlist  page. |

## Override a component in a theme
To override a component in a theme, you can use CLI command ```yarn msdyn365 add-component-override [themeName] [componentName] [--list-components]```.  Once complete you will find a new typescript file under the theme's ```\view\components``` directory.  This file can now be modified as required. 

### Example
```yarn msdyn365 add-component-override spring add-to-cart```





