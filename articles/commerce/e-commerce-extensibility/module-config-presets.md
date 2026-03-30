---
title: Module configuration presets
description: Learn about module configuration presets and how to configure them in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/04/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Module configuration presets

[!include [banner](../includes/banner.md)]

This article describes module configuration presets and how to configure them in Microsoft Dynamics 365 Commerce.

Module configuration presets are default values that you use in Commerce site builder. Use these values when you don't set configuration values at the template or layout level.

Create module configuration presets at the module level or within a theme. By using this approach, you can use different sets of data depending on the selected theme. If no presets exist for a given theme, site builder uses the module-level presets by default. If both module-level presets and theme presets exist, the theme presets override the module-level presets.

## Module-level configuration presets

Store the data for module configuration presets in a JavaScript Object Notation (JSON) preview file. Store this file in a **previews** directory under the module's directory. Name the file **\<MODULE\_NAME\>.preview.json**. For example, the path of the preview file for a custom module named "product-feature" is **\\src\\modules\\product-feature\\previews\\product-feature.preview.json**.

## Theme configuration presets

Themes can contain module configuration preset files that the theme uses when selected. Create the module configuration preset file under the theme directory. Use the following structure: **\\src\\themes\\\<THEME\_NAME\>\\previews\\modules\\\<MODULE\_NAME\>\\<MODULE\_NAME\>.preview.json**. For example, for a theme named "spring," the path of the configuration preset file for the "product-feature" module is **\\src\\themes\\spring\\previews\\modules\\product-feature\\product-feature.preview.json**.

## JSON preview file structure

Configure the JSON preview file similar to a [module mock file](module-mock-file.md), except for images (see the note later in this article) and the **id** must be set to the module name. The following example shows a JSON preview file.

```json
{
    "id": "product-feature",
    "config": {
        "imageAlignment": "left",
        "productTitle": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses",
        "productDetails": "High-quality and pioneered with the perfect blend of timeless classic and modern technology with hint of old school glamor.",
        "buttonText": "Buy Now",
        "productIds": "68719498121"
    }
}
```

### JSON preview field definitions

- **id** – Maps to the module ID.
- **config** – Contains a list of configuration values based on the name of the configuration stored in the module's definition file.

> [!NOTE]
> Configuration fields of the **image** type aren't currently supported.

## Additional resources

[E-commerce architectural overview](architectural-overview.md)

[Module mock file](module-mock-file.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
