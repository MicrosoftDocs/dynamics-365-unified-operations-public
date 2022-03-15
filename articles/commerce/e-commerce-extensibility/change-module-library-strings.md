---
# required metadata

title: Change module library static strings
description: This topic describes how to change module library strings in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 03/15/2022
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
# Change module library static strings

[!include [banner](../includes/banner.md)]

This topic describes how to change module library strings in Microsoft Dynamics 365 Commerce.

In some cases, modules expose strings that are shown as configurations in a module that can be configured in Commerce site builder. However, other strings, such as the text that is shown for the sign-in button, might be hardcoded as module resource strings. 

Some additional strings are stored as part of a theme, for more information see [Change theme module strings](change-theme-module-strings.md).

## Find the module library resource string key you want to change

The first step to change a module library string is to find the module library resource string key for the string you want to change.

Each module library definition file has an entry for each static resource string it uses, which is found within the module source code found under the  **\Msdyn365.Commerce.Online\node_modules\@msdyn365-commerce-modules** online software development kit (SDK) directory. For example, if you wanted to change the "Sign in" text in the header module, you would open the **\Msdyn365.Commerce.Online\node_modules\@msdyn365-commerce-modules\header\src\modules\header\header.definition.json** file and see a **resources** section as shown in the following example.

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
        "value": "Sign in",
        "comment": "Sign-in Link text"
    }
}
```
Take note of the resource key for the string you want to change. For example, the resource string key for the "Sign in" text in the code sample above is **signInLinkText**.

## Override module library resource strings

The next step to change the module library string is to override the module library resource string.

Module library resources are stored in the global.json file, which is found under the **\Msdyn365.Commerce.Online\node_modules\@msdyn365-commerce-modules\resources\src\resources\modules** online SDK directory, along with the localized versions in separate, independent files. Open the global.json file and search for the key you are looking for, you should see an entry similar to the one in the following example for each string.

```json
    "signInLinkText": {
        "value": "Sign in",
        "_value.comment": "Sign-in Link text"
    },
```

To override the string, create a new directory under the **\src\\** directory named **resources** and then create a subdirectory named **modules** under that. Then add a new file **global.json** to the **modules** directory, for example **...\Msdyn365.Commerce.Online\src\resources\modules\global.json**.

The new string ("Log in" in the following example) can then be added with a prepended **@msdyn365-commerce-modules** namespace on the key name as shown below:

```json
    "@msdyn365-commerce-modules.signInLinkText": { 
        "value": "Log in",
        "comment": "Log-in Link text"
    }
```

Once the package has been built and deployed, the new string will override the default module library string.

## Additional resources

[Localize a module](localize-module.md)

[Change theme module strings](change-theme-module-strings.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
