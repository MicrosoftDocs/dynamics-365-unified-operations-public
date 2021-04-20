---
# required metadata

title: Module configuration presets
description: This topic covers module configuration presets and how to configure them in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 04/23/2021
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
ms.dyn365.ops.version: Release 10.0.18

---
# Module configuration presets

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic covers module configuration presets and how to configure them in Microsoft Dynamics 365 Commerce.

Module configuration presets are default configuration values used in Dynamics 365 Commerce site builder when no configuration values have been set at the template or layout level.

Module configuration presets can be created at the module level or within a theme, allowing different sets of data to be used based on the theme selected. If no theme module preset exists for a given theme, Commerce site builder will default to the module-level presets if they exist. If both a module level preset and a theme preset exist, the theme-level presets will override the module-level presets.

## Module configuration presets

The module configuration preset data is stored in a JSON preview file with the name **\<MODULE_NAME\>.preview.json** in a **previews** directory under the module's directory. For example, a custom module named "product-feature" would have its preview file stored at **\src\modules\product-feature\previews\product-feature.preview.json**.

## Theme configuration presets

Themes can also contain module configuration preset files which are used when a theme is selected. The module configuration preset file must be created under the theme directory using a pattern **\src\themes\THEME_NAME\previews\modules\\<MODULE_NAME\>\\<MODULE_NAME\>.preview.json"**. For example, for a theme called "spring" the "product-feature" module theme configuration preset file would be **\src\themes\spring\previews\modules\product-feature\product-feature.preview.json**. 

## Preset file structure

The JSON file is configured similarly to a [module mock file](module-mock-file.md) except for images (see note below), as in the following example JSON file.

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
### Preset JSON field definitions

- **id** - Maps to the module ID.
- **config** - The config section contains a list of configuration values based on the name of the configuration stored in the module's definition file.

> [!NOTE]
> Configuration fields of type **image** are not currently supported.

## Additional resources

[E-commerce architectural overview](architectural-overview.md)

[Module mock file](module-mock-file.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
