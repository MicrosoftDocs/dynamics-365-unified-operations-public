---
# required metadata

title: Module Definition File
description: The module definition file `MODULE_NAME.definition.json` is used to register the module and provide meta data to the Dynamics 365 Commerce online authoring tools including the module name, description, categories and configurations.
author: SamJarawan
manager: JeffBl
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: SamJar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---
# Module Definition File

The module definition file `MODULE_NAME.definition.json` is used to register the module and provide meta data to the Dynamics 365 Commerce online authoring tools including the module name, description, categories and the module view file.

Below is a sample definition file for a module:

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
            "scope": "module",
            "group": "Layout Properties"
        },
        "productTitle": {
            "type": "string",
            "friendlyName": "Product Title",
            "description": "Product placement title",
            "required" : true
        },
        "productImage": {
            "type": "image",
            "friendlyName": "Product Image",
            "description": "Image representing the featured product"
        },
    }
}
```

The definition file is also used to expose configuration fields, which allow a page author to set module settings. An example may be a layout alignment setting (with left, right and center values to choose from), a module title or heading, description, call to action link, image URLs or Dynamics Retail product data.  

The page author can then choose the specific configurations for the module on a specific page without affecting the setting of the module on other pages. 

## Module Definition Schema
* "$type"
    * A module can be either a “containerModule” if it can render child modules or “contentModule” if it’s a stand-alone module. Container modules will also define “slots” which are used for layout regions.  
* "friendlyName"
    * Friendly name that gets displayed to page authors. Minimum length is 3 characters.
* "name":
    * Name of the module, this must be unique across the application. This is the ID of the module referenced by authoring and should not be changed.
* "description": 
    * The description provides a friendly string which will be shown in the authoring tools when adding modules to pages.
* "categories": 
    * Categories that this module can subscribe to. The values specified here are used by container modules to allow or disallow certain modules in specific slots.
* "tags"
    * Tags used to search modules, all the categories are automatically added as tags.
* "module"
    * The module section contains the file name for the default react view to load.  Only 1 view can be provided here.
* "slots" 
    * Slots are defined only on “containerModules” and exposed in the authoring tool.  Slots can define allow and deny lists to allow or disallow specific modules from being accepted in the slot.
    
## Module Config Schema
The module "config" section contains a list of all the modules exposed configuration fields that will be used in the authoring tool.
* config name:
    * Choose a name that will be used to access the config values from your react source code
* "config.friendlyName":
    * This name will show up in authoring tools as the configuration name
* "config.description":
    * This description will show up in authoring tools as the configuration description
* "config.type":
    * Type of the configuration.  Possible values “string”, “bool”, “number”, “integer”, “resource” , “richText”, “image”, “imageSettings”, “video” or “array”.  Type "resource" will not show up in authoring tool, but will allow the string to be localized.
* "config.enum":
    * For an enumerator type must be set to "string".
* "config.default":
    * Used to set the default value if none is set in the authoring tool.
* "config.scope":
    * Used to scope the config to the a module instance or all modules site on the site.  Possible values "module" or "site".  If set to the site, the module configuration will not show up and be configurable on a page, only at the site level settings. This will allow the value to be set once for your whole site.
* "config.group":
    * Groups are used to organize the configurations into organized groups in the authoring tools.
* "config.required":
    * This marks if a property must be set on the module.  The rendering of the module and tooling will show an error if this is not set.
* "config.resourceKey":
    * Used for localization resources. 
    
Below is an advanced sample that shows the usage of various supported data types:
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
