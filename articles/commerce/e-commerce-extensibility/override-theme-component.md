---
title: Override a module library component in a theme
description: Learn how to override module library components to allow for customizations in a theme in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/05/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Override a module library component in a theme

[!include [banner](../includes/banner.md)]

This article describes how to override module library components to customize a theme in Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce module library contains a set of TypeScript components that various module library modules use and that you can override. These components consist of helper APIs that contain business logic and other logic to help render the HTML for the module. The module HTML handles events and makes server-side calls.

If you need to change any logic in a component, use the command-line interface (CLI) [add-component-override](cli-command-reference.md#add-component-override) command to override the component for a selected theme. For example, if you want to change the logic for strikethrough pricing, you can override the Price component. For visual changes, you can also use other changes, such as [module view overrides](theme-module-extensions.md). In rare cases, you might have to [clone a module](clone-starter-module.md) to make all the changes that you require.

## Component list

To get a list of components, use the following CLI command.

``` bash
yarn msdyn365 add-component-override --list-components
```

You can find component source code under **\\node\_modules\\\@msdyn365-commerce\\components\\src\\** inside the directory for the online software development kit (SDK) that you install. You might want to browse the source code to see what options are available in each component.

The following table lists the components that are included as part of the module library. The components might vary, depending on the version of the module library that you use.

| Component     | Description |
|---------------|-------------|
| AddToCart     | Use this component to add a product to the cart. It works in combination with the cart state present in the global state package. Render this component as a button on a product details page (PDP). When you select the button, it validates the inventory check for the product and calls the Retail Server addcartline API to add the product to the cart. |
| AddToWishlist | Use this component to add a product to, or remove a product from, the wishlist. It works in combination with the wishlist state present in the global state package. This component renders the user interface (UI) for the add/remove wishlist button. It also handles the onclick event. The onclick event ensures that the user is signed in. |
| CartIcon      | Use this component to render the HTML that shows the cart icon in the header module. When you select the cart icon, this component opens the cart page. The module library also has a CartIcon module that's separate from this component. If the CartIcon module isn't configured in a header module, this component is used as a fallback. |
| CartLineItem  | Use this component to render the HTML that shows a single line item in the cart. It consists of a product image, the product details that are selected in the buy box module on the PDP, the product quantity, and the product price with discounts. |
| Price         | Use this component to render the HTML that shows the product price across the site in the correct format. It doesn't make any API calls. |
| Product       | Use this component to render the HTML that shows the products in a card format across the site. It consists of a product image, title, description, price, and rating. |
| PromoCode     | Use this component to apply promotional codes or discount codes to the cart. It works in combination with the cart state present in the global state package to apply or remove a promotion in the cart. |
| Rating        | Use this component to render the HTML that shows the product rating across the site. It doesn't make any API calls. This component also handles the click event to update the rating. |
| SocialMedia   | Use this component to render the social media icons for sharing a product from the buy box module. It currently supports Facebook, LinkedIn, Mail, Pinterest, and Twitter. |
| WishListIcon  | Use this component to render the HTML that shows the wishlist icon in the header module. It also handles the click event to open the wishlist page. |

## Override a component in a theme

To override a component in a theme, run the following CLI command: **yarn msdyn365 add-component-override \[themeName\] \[componentName\] \[--list-components\]**. After running this command, find a new TypeScript file under the theme's **\\view\\components** directory. You can then modify the file in that directory as you require.

### Example

``` bash
yarn msdyn365 add-component-override spring add-to-cart
```

## Additional resources

[Theming overview](theming.md)

[Create a new theme](create-theme.md)

[Configure theme settings](configure-theme-settings.md)

[Configure theme style presets](theme-style-presets.md)

[Extend a theme to add module extensions](theme-module-extensions.md)

[Extend a theme from a base theme](extend-theme.md)

[Add custom resources to your customization code](add-custom-resources.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
