---
# required metadata

title: Module configuration presets
description: This topic covers how to preset configuration values that will show up in the site builder tool for each module.
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

This topic covers how to preset default configuration preview values that will show up in the site builder tool for each module configuration field.

## Overview

When a module is placed on a page within site builder, a preset value can be used for the module preview for each configuration field when the field is not set. This is useful to show default values such as images within the site builder preview to show the site author what the module will look like.

Each module configuration field can be configured with a default **preview** value, which will show up in site builder when no value is set.  This module preview data is stored in a special PREVIEW_NAME.preview.json file under the module folder where PREVIEW_NAME can be any name.  Any number of preview files can exist and can be selected in the site builder too.  For example, a custom module named **product-feature** has a preview file stored under the modules directory: **/src/modules/product-feature/previews/defaultValues.preview.json**.

## Preview json file structure

The json file is configured similar to the [module mock file](module-mock-file.md) and below is an example:

```json
{
	"id": "product-feature",
	"config": {
	    "imageAlignment": "left",
	    "productTitle": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses",
	    "productDetails": "High-quality and pioneered with the perfect blend of timeless classic and modern technology with hint of old school glamor.",
	    "productImage": {
		    "src": "https://bit.ly/33cMGxr",
		    "altText": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses"
	    },
	    "buttonText": "Buy Now",
	    "productIds": "68719498121"
	}
} 
```
and contains the following structure
*"Id" - maps to the module Id
*"config" - Array of contains configuration values



## Additional resources

[E-commerce architectural overview](architectural-overview.md)

[Module mock file](module-mock-file.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
