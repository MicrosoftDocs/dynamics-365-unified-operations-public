---
# required metadata

title: Override a module library component in a theme
description: This topic describes how to override module library components to allow customizations within a theme. 
author: samjarawan
manager: annbe
ms.date: 09/17/2020
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
# Override a module library component in a theme

[!include [banner](../includes/banner.md)]

This topic describes how to override module library components to allow customizations within a theme.

## Overview

The Dynamics 365 Commerce module library contains a set of overridable TypeScript components that are used by various module library modules. These components consist of helper APIs that contain business and other logic to help render module HTML markup, handle events, and make server side calls. If you need to change any logic in a component, the component can be overwritten for a selected theme by using the command-line interface (CLI) [add-component-override](cli-command-reference.md#add-component-override) command. 

For example, if you want to change the logic for strikethrough pricing, you can make changes by overriding the "price" component. Other changes such as [module view overrides](theme-module-extensions.md) can also be used for visual changes. In rare cases, you may need to [clone a module](clone-starter-module.md) to make all the changes you require.

## Component list

To obtain a list of components, you can use the following CLI command. 

```bash
yarn msdyn365 add-component-override --list-components
```

Component source code can be found under **\node_modules\@msdyn365-commerce\components\src&#92;** inside the installed online SDK directory. You may want to browse the source code to see what options are available within each component.

The following is a list of components included as part of the module library. The list may differ based on the version of the module library being used.

| Component                 | Description                                                           |
|---------------------------|-----------------------------------------------------------------------|
| AddToCart     | This component is used to add a product to the cart. It works in combination with the cart state present in the global state package. This component is rendered as a button on a product details page (PDP). When the button is selected, it validates the inventory check for the product and calls the Retail Server addcartline API to add the product to the cart. |
| AddToWishlist | temp description |
| CartIcon      | This component is used to render the HTML to display the cart icon in the header module. The cart-icon component will navigate to the cart page when the cart icon is selected. The module library also has a cart-icon module separate from this component. If the cart-icon module is not configured in a header module, then this component is used as a fallback. |
| CartLineItem  | This component is used to render the HTML to display a single cart line item. It consists of a product image, the product details as selected in the PDP buy box module, the product quantity, and the product price with discounts.  |
| Price         | This component is used to render the HTML to display the product price across the site in the correct formatting. It does not make any API calls. |
| Product       | This component is used to render the HTML to display the products in a card format across the site. It consists of product image, title, description, price, and rating. |
| PromoCode     | This component is used to apply promotional or discount codes to cart. This works in combination with the cart state present in the global state package to apply or remove a promotion in the cart. |
| Rating        | This component is used to render the HTML to display the product rating across the site. It does not make any API calls. This component also handles the click event to update the rating. |
| SocialMedia | This component is used to render the social media icons for sharing a product from the buy box module. Currently it supports Facebook, LinkedIn, Mail, Pinterest, and Twitter.
| WishListIcon  | This component is used to render the HTML to display the wishlist icon in the header module, and handles the click event to navigate to the wishlist page. |

## Override a component in a theme

To override a component in a theme, you can run the CLI command ```yarn msdyn365 add-component-override [themeName] [componentName] [--list-components]```.  Once run, you will find a new TypeScript file under the theme's ```\view\components``` directory, where it can be modified as needed. 

### Example

```yarn msdyn365 add-component-override spring add-to-cart```

## Additional resources

[Theming overview](theming.md)

[Create a new theme](create-theme.md)

[Configure theme settings](configure-theme-settings.md)

[Configure theme style presets](theme-style-presets.md)

[Extend a theme to add module extensions](theme-module-extensions.md)

[Extend a theme from a base theme](extend-theme.md)
