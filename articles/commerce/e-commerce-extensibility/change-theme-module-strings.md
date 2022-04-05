---
# required metadata

title: Change theme module strings
description: This topic describes how to change module library strings from within a theme in Microsoft Dynamics 365 Commerce.
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
# Change theme module strings

[!include [banner](../includes/banner.md)]

This topic describes how to change module library strings from within a theme in Microsoft Dynamics 365 Commerce.

In some cases, modules expose strings that are shown as configurations in a module that can be configured in Commerce site builder. However, other strings, such as the text that is shown for the sign-in button, might be hardcoded as module resource strings.

## Override resource strings for a theme

To override resource strings for a theme, use the pattern in the following example to modify the global.json resource file that is located in the src/resources/modules directory.

```json
"{ThemeNamespace}.{ThemeName}.{ResourceString}": {
    "value" : "",
    "_value.comment": ""
}
```

To learn more about how resource strings are created and how to create a global.json file if one doesn't exist in your software development kit (SDK), see [Localize a module](localize-module.md).

### Override resource strings for preinstalled themes

To override resource strings for preinstalled themes (for example, fabrikam or starter themes), use **@msdyn365-commerce-modules** as the theme namespace. The following example shows how to change the sign-in link text for the fabrikam theme.

```json
"@msdyn365-commerce-modules.fabrikam.signInLinkText": {
    "value": "Sign in now",
    "_value.comment": "Sign-in Link Text"
}
```

### Override resource strings for custom or local themes

For custom or local themes, use **\_\_local\_\_** as the theme namespace. The following example shows how to change the sign-in link text for a custom theme that is named "adventureworks."

```json
"__local__.adventureworks.signInLinkText": {
    "value": "Log in",
    "_value.comment": "Log in Link Text"
}
```

> [!NOTE]
> For [shared themes](extend-theme.md), child themes inherit all the resources string overrides that are linked to the parent theme.

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
