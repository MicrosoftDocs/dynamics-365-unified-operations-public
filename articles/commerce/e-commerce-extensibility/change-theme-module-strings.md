---
# required metadata

title: Change theme module strings
description: This topic describes how to change module library strings from within a theme in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 03/03/2022
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
# Change theme module strings

[!include [banner](../includes/banner.md)]

This topic describes how to change module library strings from within a theme in Microsoft Dynamics 365 Commerce.

In some cases modules expose strings that are displayed as configurations within a module that can be configured in site builder, but other strings such as the text displayed for the sign-in button may be hardcoded as module resource strings.  

## Override a resource string for a theme

To override resource strings for a theme, modify the global.json resource file located in the src/resources/modules directory using the pattern in the following example. 

```json
"{ThemeNamespace}.{ThemeName}.{ResourceString}": {
    "value" : "",
    "_value.comment": ""
}
```

To learn more about how resource strings are created and how to create a global.json file if one doesn't exist in your software development kit (SDK), see [Localize a module](localize-module.md).

### Override resource strings for preinstalled themes

To override resource strings for preinstalled themes (for example, fabrikam or starter themes), use **@msdyn365-commerce-modules** as the theme namespace. The following example shows how to change the sign-in link text on the fabrikam theme.

```json
"@msdyn365-commerce-modules.fabrikam.signInLinkText": {
    "value": "Sign in now",
    "_value.comment": "Sign-in Link Text"
}
```

### Override resource strings for custom or local themes

For custom or local themes, use **__local__** for the theme namespace. The following example shows how to change the sign-in link text for a custom theme called "adventureworks."

```json
"__local__.adventureworks.signInLinkText": {
    "value": "Log in",
    "_value.comment": "Log in Link Text"
}
```

> [!NOTE]
> For [shared themes](extend-theme.md), child themes inherit all of the resources string overrides tied to the parent theme.

## Additional resources

[Localize a module](localize-module.md)

[Create a new module](create-new-module.md)

[Clone a module library module](clone-starter-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Test modules by using module mocks](test-module-mock.md)

[Test modules by using page mocks](test-page-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
