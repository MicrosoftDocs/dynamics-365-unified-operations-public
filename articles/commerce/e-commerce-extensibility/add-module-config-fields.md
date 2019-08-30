---
# required metadata

title: Add module configuration fields
description: This topic describes how to add module configuration fields in Dynamics 365 Commerce. 
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Add module configuration fields

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to add module configuration fields in Dynamics 365 Commerce.

## Overview

Configuration fields can be added to a module to expose them to page authors and give them control of various module features. Examples of these features include different views, alignment properties, boolean switches to turn features on or off, module titles or headings, rich text descriptions, call to action links, image URLs, or Dynamics 365 Retail product data.

The following screenshot shows how these fields appear in the page authoring tools.

![Module config fields in authoring tools](media/module-config-fields.png)

## Add new module configuration fields

Adding configuration fields is done with an entry in the `config` section of the module definition file.

### Example

In the module definition file `MODULE_NAME.definition.json` below, a configuration field **imageAlignment** has been added to enable configuration of the image alignment inside a module. There are two enum options: "Left" (the default option) and "Right."

```
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "productFeature",
    "description": "Feature module used to highlight a product.",
    "categories": ["marketing"],
    "tags": ["feature"],
    "module": {
        "view": "./productFeature"
    },
    "config": {
        "imageAlignment": {
            "friendlyName": "Image Alignment",
            "description": "Sets the desired alignment of the image, either left or right on the text.",
            "type": "string",
            "enum": {
                "left": "Left",
                "right": "Right"
            },
            "default": "left",
            "group": "Layout Properties"
        }
    }
}
```

## Module config schema

The module "config" section contains a list of all the module's exposed configuration fields that will be used in the authoring tool.

* config name:
    * This name that will be used to access the config values from the react source code.
* "friendlyName":
    * This name will show up in authoring tools as the configuration name.
* "description":
    * This description will show up in authoring tools as the configuration description.
* "type":
    * This is is type of the configuration. Possible values are "string," "boolean," "number," "integer," "resource," "link," "productList," "object," "image," "imageSettings," video," or "array."  The "resource" type will not show up in authoring tool, but will allow the string to be localized.
* "enum":
    * For an enumerator type this must be set to "string."
* "default":
    * This is used to set the default value if none is set in the authoring tool.
* "scope":
    * This is used to scope the config to a module instance or all modules on the site. Possible values are "module" or "site." If set to the site, the module configuration will only appear in the site level settings and will not appear or be configurable on a page. This will allow the value to be set once for your whole site.
* "group":
    * Groups are used to organize the configurations into organized groups in the authoring tools.
* "required":
    * This marks if a property must be set on the module. The rendering of the module and tooling will show an error if this is not set.
* "resourceKey":
    * This is used for localization resources. 
    
### Example

The following example shows the usage of various supported data types:
```
{
  "$type": "contentModule",
  "friendlyName": "Sample Config",
  "name": "sample-config",
  "description": "Sample Config",
  "categories": ["sample-config"],
  "tags": ["samples"],
  "module": {
      "view": "./sample-config",
      "dataActions": {}
  },
  "config": {
      "showText": {
          "friendlyName": "showText",
          "description": "example config value",
          "type": "string",
          "default": "Example Config Value",
          "scope": "module",
          "group": "Layout Properties"
      },
      "subTitle": {
        "type": "richText",
        "friendlyName": "SubTitle",
        "description": "Sub title rich text field"
      },
      "bgImage": {
          "type": "image",
          "friendlyName": "Background image",
          "description": "Background image"
      },
      "images": {
          "type": "array",
          "friendlyName": "Images",
          "description": "Image Array",
          "items": {
              "type": "image"
          }
      },
      "backgroundImageSettings": {
          "friendlyName": "Background Image Settings",
          "description": "Image settings for background iamge settings",
          "type": "imageSettings"
      },
      "ambientVideo": {
          "friendlyName": "Ambient Video",
          "description": "Ambient Video",
          "type": "video"
      },
      "headingArray":{
          "type": "array",
          "friendlyName": "Heading Array",
          "description": "Heading Array",
          "items": {
              "$ref": "#/definitions/heading"
          }
      },
      "heading":{
          "$ref": "#/definitions/heading"
      },
      "heading2":{
          "type": "object",
          "friendlyName": "Heading2",
          "description": "Heading2 property with its own enum",
          "properties": {
              "style": {
                  "type": "string",
                  "enum": {
                      "bold": "Bold",
                      "underline": "Underline",
                      "italics": "Italics",
                      "strong": "Strong",
                      "emphasized": "Emphasized",
                      "none": "None"
                  },
                  "friendlyName": "Style",
                  "description": "Heading style"
              }
          }
      }
  },
  "definitions": {
      "heading": {
          "type": "object",
          "friendlyName": "Heading",
          "description": "Heading property",
          "properties": {
              "text": {
                  "type": "string",
                  "friendlyName": "Text",
                  "description": "Heading Text"
              },
              "style": {
                  "type": "string",
                  "enum": {
                      "bold": "Bold",
                      "underline": "Underline",
                      "none": "None"
                  },
                  "friendlyName": "Style",
                  "description": "Heading style"
              },
              "showImage":{
                  "type":"boolean",
                  "friendlyName": "Show Image?",
                  "description": "Should Show Image"
              },
              "bgImage": {
                  "type": "image",
                  "friendlyName": "Background image",
                  "description": "Background image"
              },
              "imageArray":{
                  "type": "array",
                  "friendlyName": "Images",
                  "description": "Image Array",
                  "items": {
                      "type": "image"
                  }
              }
          }
      }
  }
}
```

### Use mock data in configuration fields for local testing 

The following example shows how to set a mock value for a new configuration field in the `mocks/MODULE_NAME.json` file. This will help when rendering the module in a local development environment.

```
{
  "id": "R1Module1",
  "config": {
    "imageAlignment": "left",
    "productTitle": "Men's Grand Wing Tip Shoe",
    "productDetails": "Full genuine leather with a classic design.",
    "buttonText": "Buy Now",
  },
  "typeName": "productFeature"
}
```

### Access configuration fields within the module React component

To access configuration fields in the React component, use the `props.config` API.

The example code below uses an `if` statement to check the new imageAlignment config field and render the appropriate HTML.

```typescript
import * as React from 'react';

import { IProductFeatureData } from './productFeature.data';
import { imageAlignment, IProductFeatureProps } from './productFeature.props.autogenerated';

/**
 *
 * productFeature component
 * @extends {React.PureComponent<IProductFeatureProps<IProductFeatureData>>}
 */
class ProductFeature extends React.PureComponent <IProductFeatureProps<IProductFeatureData>> {

    public render(): JSX.Element {
        const { config } = this.props;

        // set default product info values from config values if available
        const productName = config.productTitle ? config.productTitle : 'No product name defined';
        const productInfo = config.productDetails ? config.productDetails.toString() : 'No product details defined';
        const productImageUrl = config.productImage ? config.productImage.src : '';
        const buttonInfo = config.buttonText ? config.buttonText : 'No button text defined';
        let left;
        let right;

        if (config.imageAlignment === imageAlignment.left) {
            left = this._renderImage(productImageUrl, productName);
            right = this._renderInfo(productName, productInfo, buttonInfo);
        } else {
            right = this._renderImage(productImageUrl, productName);
            left = this._renderInfo(productName, productInfo, buttonInfo);
        }

        return (
            <div className='row align-items-center'>
                <div className='col-sm-6'>
                    {left}
                </div>
                <div className='col-sm-6'>
                    {right}
                </div>
            </div>
        );
    }

    private _renderImage(productImageUrl: string, productName: string): JSX.Element {
        return <img src={productImageUrl} alt={productName} className='img-fluid p-3' />;
    }

    private _renderInfo(productName: string, productInfo: string, buttonInfo: string): JSX.Element {
        return (
            <div className='container'>
                <h2>{productName}</h2>
                <p>{productInfo}</p>
                <button type='button' className='btn btn-primary' onClick={this._buttonClick}>{buttonInfo}</button>
            </div>
        );
    }

    private _buttonClick = (): void => {
        window.location.href = 'https://www.bing.com';
    }
}

export default ProductFeature;
```
