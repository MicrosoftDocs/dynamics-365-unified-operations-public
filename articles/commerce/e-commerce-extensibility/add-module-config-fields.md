---
# required metadata

title: Add module configuration fields
description: This topic describes how to add module configuration fields in Microsoft Dynamics 365 Commerce. 
author: samjarawan
manager: annbe
ms.date: 10/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
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

This topic describes how to add module configuration fields in Microsoft Dynamics 365 Commerce.

## Overview

Configuration fields can be added to a module to expose them to page authors and give them control of various module features. Examples of these features include different views, alignment properties, Boolean switches to turn features on or off, module titles or headings, rich text descriptions, call-to-action links, image URLs, and Microsoft Dynamics 365 Retail product data.

The following illustration shows how these fields appear in the page authoring tools.

![Module configuration fields in the authoring tools](media/module-config-fields.png)

## Add new module configuration fields

To add configuration fields, you add an entry in the **config** section of the module definition file, **MODULE\_NAME.definition.json**.

### Example

In the following example of a module definition file, an **imageAlignment** configuration field has been added so that page authors can configure the alignment of an image inside a module. There are two enumeration (enum) options: **"Left"** (the default option) and **"Right"**.

```json
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "productFeature",
    "description": "Feature module used to highlight a product.",
    "categories": ["marketing"],
    "tags": ["feature"],
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

## Module configuration schema

The **config** section of the module definition file contains a list of all the module's exposed configuration fields that will be used in the authoring tools.

* **configuration name** – The local name that is used to access the configuration values from your react source code.
* **"friendlyName"** – The friendly name that is shown as the configuration name in the authoring tools.
* **"description"** – The description that is shown as the configuration description in the authoring tools.
* **"type"** – The type of the configuration. Possible values are **"string"**, **"bool"**, **"number"**, **"integer"**, **"richText"**, **"image"**, **"imageSettings"**, **"video"**, and **"array"**.
* **"enum"** – For an enumerator type, the value must be set to **"string"**.
* **"default"** – The default value that is set if no value is set in the authoring tools.
* **"scope"** – This field is used to scope the configuration to either a specific module instance or all modules on the site. Possible values are **"module"** and **"site"**. If the value is set to **"site"**, the module configuration doesn't appear on a page and can't be configured there. It appears and can only be configured at the site level. In this way, the value can be set one time for the entire site.
* **"group"** – Groups are used to organize the configurations into organized groups in the authoring tools.
* **"required"** – A boolean flag that specifies whether or not a property must be set on the module. When set to **true**, the authoring tools will show an error if the required property isn't set, and an error will be displayed when the module is rendered.
* **"resources"** – This field is used for localization resources.
* **"definitions"** - This field can contain complex config type definitions, which can be referenced in the config sections as extended types.

The following example shows how the various supported data types are used.

```json
{
    "$type": "contentModule",
    "friendlyName": "Sample Config",
    "name": "sample-config",
    "description": "Sample Config",
    "categories": ["sample-config"],
    "tags": ["samples"],
    "dataActions": {},
    "config": {
        "title": {
            "type": "string",
            "friendlyName": "title",
            "description": "example config value",
            "default": "",
            "scope": "module"
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
            "type": "imageSettings",
            "friendlyName": "Background Image Settings",
            "description": "Image settings for background image settings"
        },
        "ambientVideo": {
            "type": "video"
            "friendlyName": "Ambient Video",
            "description": "Ambient Video",
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

The following example shows how to set a mock value for a new configuration field in the **mocks/MODULE\_NAME.json** file. Mock data is useful when a module is rendered in a local development environment.

```json
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

### Access configuration fields in the module React component

To access configuration fields in the React component, use the **props.config** application programming interface (API).

The following example uses an **if** statement to check the new **imageAlignment** configuration field and render the appropriate HTML.

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

## Additional resources

[Create a new module](create-new-module.md)

[Clone a starter kit module](clone-starter-module.md)

[Preview and debug a module](test-module.md)

[Debug modules](debug-modules.md)

[Test modules by using module mocks](test-module-mock.md)

[Test modules by using page mocks](test-page-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)

[Localize a module](localize-module.md)
