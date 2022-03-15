---
# required metadata

title: Change module library static strings
description: This topic describes how to change module library strings from within in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 03/08/2022
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

This topic describes how to change module library strings from within Microsoft Dynamics 365 Commerce.

In some cases, modules expose strings that are shown as configurations in a module that can be configured in Commerce site builder. However, other strings, such as the text that is shown for the sign-in button, might be hardcoded as module resource strings.  Some additional strings are stored as part of a theme, see the [Change theme module strings](change-theme-module-strings.md) topic for more information.

## Find the module library resource string key you want to change

Each module library definition file has an entry for each static resource strings it uses which can be found within the module source code found under the  **\Msdyn365.Commerce.Online\node_modules\@msdyn365-commerce-modules** online sdk directory.  For example if you wanted to change the "Sign in" text in the header module, open the **\Msdyn365.Commerce.Online\node_modules\@msdyn365-commerce-modules\header\src\modules\header\header.definition.json** file and you will see a **resources** section as shown below.

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
Take note of the resource key for the string you are interested in changing.  For example **signInLinkText** from the above sample code.


## Override the resource strings

Module library resources are stored in a global.json file and can be found under the online SDK directory **\Msdyn365.Commerce.Online\node_modules\@msdyn365-commerce-modules\resources\src\resources\modules** along with localized version of the strings in independent files.  Open the file and search for the key you are looking for, you should see a similar json as shown below.

```json
    "signInLinkText": {
        "value": "Sign in",
        "_value.comment": "Sign-in Link text"
    },
```

The string can now be overridden by creating a new directory under our src directory called **resources** and then another sub directory called **modules** under that and adding a new file **global.json**.  For example **...\Msdyn365.Commerce.Online\src\resources\modules\global.json**.

The new string can then be added by pre-pending the **@msdyn365-commerce-modules** namespace to the key name as shown below.

```json
    "@msdyn365-commerce-modules.signInLinkText": { 
        "value": "Log in",
        "comment": "Log-in Link text"
    }
```

Once the package has been built and deployed, the new strings will override the default module library string.

## Additional resources

[Localize a module](localize-module.md)

[Change theme module strings](change-theme-module-strings.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
