---
# required metadata

title: Override a module library component in a theme
description: This topic describes how to override module library components to allow for customizations in a theme. 
author: samjarawan
ms.date: 10/20/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
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

This topic describes how to override module library components to allow for customizations in a theme.

The Microsoft Dynamics 365 Commerce module library contains a set of TypeScript components that various module library modules use, and that can be overridden. These components consist of helper APIs that contain business logic and other logic to help render the HTML for the module HTML, handle events, and make server-side calls.

If you must change any logic in a component, you can use the command-line interface (CLI) [add-component-override](cli-command-reference.md#add-component-override) command to override the component for a selected theme. For example, if you want to change the logic for strikethrough pricing, you can override the Price component. Other changes, such as [module view overrides](theme-module-extensions.md), can also be used for visual changes. In rare cases, you might have to [clone a module](clone-starter-module.md) to make all the changes that you require.

## Component list

To get a list of components, you can use the following CLI command.

``` bash
yarn msdyn365 add-component-override --list-components
```

Component source code can be found under **\\node\_modules\\\@msdyn365-commerce\\components\\src\\** inside the directory for the online software development kit (SDK) that is installed. You might want to browse the source code to see what options are available in each component.

The following table lists the components that included as part of the module library. The components might vary, depending on the version of the module library that you use.

| Component     | Description |
|---------------|-------------|
| AddToCart     | This component is used to add a product to the cart. It works in combination with the cart state that is present in the global state package. This component is rendered as a button on a product details page (PDP). When the button is selected, it validates the inventory check for the product and calls the Retail Server addcartline API to add the product to the cart. |
| AddToWishlist | This component is used to add a product to, or remove a product from, the wishlist. It works in combination with the wishlist state that is present in the global state package. This component renders the user interface (UI) for the add/remove wishlist button. It also handles the onclick event. The onclick event will ensure that the user is signed in. |
| CartIcon      | This component is used to render the HTML to show the cart icon in the header module. When the cart icon is selected, this component opens the cart page. The module library also has a CartIcon module that is separate from this component. If the CartIcon module isn't configured in a header module, this component is used as a fallback. |
| CartLineItem  | This component is used to render the HTML to show a single line item in the cart. It consists of a product image, the product details that are selected in the buy box module on the PDP, the product quantity, and the product price with discounts. |
| Price         | This component is used to render the HTML to show the product price across the site in the correct format. It doesn't make any API calls. |
| Product       | This component is used to render the HTML to show the products in a card format across the site. It consists of a product image, title, description, price, and rating. |
| PromoCode     | This component is used to apply promotional codes or discount codes to the cart. It works in combination with the cart state that is present in the global state package to apply or remove a promotion in the cart. |
| Rating        | This component is used to render the HTML to show the product rating across the site. It doesn't make any API calls. This component also handles the click event to update the rating. |
| SocialMedia   | This component is used to render the social media icons for sharing a product from the buy box module. It currently supports Facebook, LinkedIn, Mail, Pinterest, and Twitter.
| WishListIcon  | This component is used to render the HTML to show the wishlist icon in the header module. It also handles the click event to open the wishlist page. |

## Override a component in a theme

To override a component in a theme, you can run the following CLI command: **yarn msdyn365 add-component-override \[themeName\] \[componentName\] \[--list-components\]**. After this command is run, you should find a new TypeScript file under the theme's **\\view\\components** directory. You can then modify the file in that directory as you require.

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
