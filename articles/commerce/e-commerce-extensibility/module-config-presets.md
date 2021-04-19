---
# required metadata

title: Module configuration presets
description: This topic covers how to create module configuration presets, which are default configuration field values used in the site builder tool  when no value is set.
author: samjarawan
manager: annbe
ms.date: 03/09/2021
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

This topic covers how to create module configuration presets, which are default configuration field values used in the site builder tool when no value is set.

## Overview

When a module is added to any editing surface where defaults are not set at the template or layout level, the module presets will be used as the default configuration field values. 

Module configuration presets can be created at the module level and/or within a theme, allowing different sets of data to be used based on the theme selected.  If no theme module preset exists for a given theme, the site builder will fall back to the module level preset if one exists. If both a module level preset and theme preset exists the theme level preset will override the module level preset.

## Module configuration presets

The module configuration preset data is stored in a JSON file with the name **MODULE_NAME.preview.json** in a **previews** folder under the module folder. For example, a custom module named **product-feature** has a preview file stored under the modules directory: **\src\modules\product-feature\previews\product-feature.preview.json**.

## Theme configuration presets

Themes can also contain module configuration preset files which will be used when a theme is selected.  The module configuration preset file needs to be created under the theme directory using a pattern:  **\src\themes\THEME_NAME\previews\modules\MODULE_NAME\MODULE_NAME.preview.json"**. For example, for a theme called **spring**, the **product-feature** module theme configuration preset file would be **\src\themes\spring\previews\modules\product-feature\product-feature.preview.json"**. 

## Preset file structure

The JSON file is configured similar to a [module mock file](module-mock-file.md) with exception to images (see below more details on images).  Below is a example json file:

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
* "id" - maps to the module Id
* "config" - the config section contains a list of configuration values based on the name of the configuration stored in the modules definition file.

**Note** configuration fields of type "image" are not currently supported.


## Additional resources

[E-commerce architectural overview](architectural-overview.md)

[Module mock file](module-mock-file.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
