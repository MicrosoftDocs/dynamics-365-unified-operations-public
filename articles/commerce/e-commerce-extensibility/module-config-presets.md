---
title: Module configuration presets
description: This article covers module configuration presets and how to configure them in Microsoft Dynamics 365 Commerce.
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
# Module configuration presets

[!include [banner](../includes/banner.md)]

This article covers module configuration presets and how to configure them in Microsoft Dynamics 365 Commerce.

Module configuration presets are default values that are used in Commerce site builder. These values are needed when configuration values are not set at the template or layout level.

Module configuration presets can be created at the module level or within a theme. That way, different sets of data can be used, depending on the theme that is selected. If no presets exist for a given theme, site builder uses the module-level presets by default if they exist. If both module-level presets and theme presets exist, the theme presets override the module-level presets.

## Module-level configuration presets

The data for module configuration presets is stored in a JavaScript Object Notation (JSON) preview file. This file is stored in a **previews** directory under the module's directory. The file is named **\<MODULE\_NAME\>.preview.json**. For example, the path of the preview file for a custom module that's named "product-feature" is **\\src\\modules\\product-feature\\previews\\product-feature.preview.json**.

## Theme configuration presets

Themes can contain module configuration preset files that are used when a theme is selected. The module configuration preset file must be created under the theme directory. The following structure must be used: **\\src\\themes\\\<THEME\_NAME\>\\previews\\modules\\\<MODULE\_NAME\>\\<MODULE\_NAME\>.preview.json**. For example, for a theme that's named "spring," the path of the configuration preset file for the "product-feature" module is **\\src\\themes\\spring\\previews\\modules\\product-feature\\product-feature.preview.json**.

## JSON preview file structure

The JSON preview file is configured similar to a [module mock file](module-mock-file.md), except for images (see the note later in this article) and the **id** must be set to the module name. Here's an example of a JSON preview file.

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

- **id** – This field is mapped to the module ID.
- **config** – This field contains a list of configuration values that are based on the name of the configuration that is stored in the module's definition file.

> [!NOTE]
> Configuration fields of the **image** type aren't currently supported.

## Additional resources

[E-commerce architectural overview](architectural-overview.md)

[Module mock file](module-mock-file.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
