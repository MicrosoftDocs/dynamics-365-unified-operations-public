---
title: Change module library static strings
description: This article describes how to change module library strings in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 07/26/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Change module library static strings

[!include [banner](../includes/banner.md)]

This article describes how to change module library strings in Microsoft Dynamics 365 Commerce.

In some cases, modules expose strings that are shown as configurations in a module that can be configured in Commerce site builder. However, other strings, such as the text that is shown for the sign-in button, might be hardcoded as module resource strings. 

Some additional strings are stored as part of a theme. For more information, see [Change theme module strings](change-theme-module-strings.md).

## Find the module library resource string key that you want to change

The first step to change a module library string is to find the module library resource string key for the string that you want to change.

Each module library definition file has an entry for each static resource string that it uses. You can find this entry in the module source code under the **\\Msdyn365.Commerce.Online\\node_modules\\\@msdyn365-commerce-modules** online software development kit (SDK) directory. For example, if you want to change the "Sign in" text in the header module, open the **\\Msdyn365.Commerce.Online\\node_modules\\\@msdyn365-commerce-modules\\header\\src\\modules\\header\\header.definition.json** file, and look in the **resources** section, as shown in the following example.

```json
"resources": {
    "mobileHamburgerAriaLabel": {
        "comment": "The aria label used for mobile view hamburger",
        "value": "Hamburger menu"
    },
    "wishlistTooltipText": {
        "comment": "string to be shown for wishlist tooltip",
        "value": "My Wishlist"
    },
    "cartLabel": {
        "comment": "string to be shown for cart or shopping bag tooltip",
        "value": "Shopping bag, ({0}) items"
    },
    "cartQtyLabel": {
        "comment": "string to be shown for cart item quantity",
        "value": "({0})"
    },
    "signInLinkText": {
        "comment": "Sign-in Link text",
        "value": "Sign in"
    }
}
```

Make a note of the resource key for the string that you want to change. For example, the resource string key for the "Sign in" text in the preceding code sample is **signInLinkText**.

## Override the module library resource string

The next step to change the module library string is to override the module library resource string.

Module library resources are stored in the **global.json** file, which you can find under the **\\Msdyn365.Commerce.Online\\node_modules\\\@msdyn365-commerce-modules\\resources\\src\\resources\\modules** online SDK directory. The localized versions are stored in separate, independent files. To confirm the resource string key that you found in the module source code, open the **global.json** file, and search for the key that you're looking for (**signInLinkText** in this example). For each string, you should see an entry that resembles the following example.

```json
    "signInLinkText": {
        "value": "Sign in",
        "_value.comment": "Sign-in Link text"
    },
```

To override the string, create a new directory under the **\\Msdyn365.Commerce.Online\\src** directory, and name it **resources**. Under that directory, create a subdirectory that is named **modules**. Then, add a new, empty **global.json** file to the **modules** directory (for example,  **...\\Msdyn365.Commerce.Online\\src\\resources\\modules\\global.json**).

Next, add a new string entry to the new **global.json** file, and prepend the **@msdyn365-commerce-modules** namespace to the key name, as shown in the following example (where the resource string key is **signInLinkText**, and the new string is "Log in").

```json
    "@msdyn365-commerce-modules.signInLinkText": { 
        "comment": "Log-in Link text",
        "value": "Log in"
    }
```

After the package has been built and deployed, the new string will override the default module library string.

## Additional resources

[Localize a module](localize-module.md)

[Change theme module strings](change-theme-module-strings.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
