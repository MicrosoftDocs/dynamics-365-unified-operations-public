---
title: Create a page container module
description: This article describes how to create a page container module in Microsoft Dynamics 365 Commerce.
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
# Create a page container module

[!include [banner](../includes/banner.md)]

This article describes how to create a page container module in Microsoft Dynamics 365 Commerce.

A page container is a module that controls the core structure of a page through specific layout regions that are known as *slots*. For example, a page container might have slots that are defined for the header area, main content area, and footer area. A page container can be embedded only at the root of a page, and each page must have only one page container.

Page authors can configure which modules go into each slot, and the container rendering code then controls the layout of those slots. Configuration settings can also be exposed to page authors so that they can further configure the layout.

## Create a new page container module

The Microsoft Dynamics 365 Commerce online software development kit (SDK) provides an [add-module](cli-command-reference.md#add-module) command-line interface (CLI) command. To create a page container module, use this command to create a new module, and then change the **$type** value to **pageModule** in the module's definition file.

For example, run the following command to create a module that is named **campaign-page-container**.

```Console
yarn msdyn365 add-module campaign-page-container
```

Then open the definition file for the new module, **campaign-page-container.definition.json**, and change the **$type** value to **pageModule**.

In the following example, notice that the **slots** section contains the various named slots that the page container supports. To restrict a slot so that only a specific set of modules can be put into it, use the **"allowedTypes"** array to define the list of allowed modules. Alternatively, use an asterisk (\*) to allow any module to be put into the slot.

```json
{
    "$type": "pageModule",
    "friendlyName": "Campaign Page Container",
    "name": "campaign-page-container",
    "description": "This is a test page container.",
    "categories": ["page"],
    "tags": [""],
    "config": {},
    "slots": {
        "header":
        {
            "friendlyName": "Header Slot",
            "description": "This is the header slot",
            "allowedTypes": ["header"],
            "max": 1,
            "min": 0
        },
        "primary":
        {
            "friendlyName": "Main Slot",
            "description": "This is the Primary slot",
            "allowedTypes": ["campaign-container", "carousel", "content-block", "product-collection"],
            "max": 5,
            "min": 0
        },
        "footer":
        {
            "friendlyName": "Footer Slot",
            "description": "This is the footer slot",
            "allowedTypes": ["footer"],
            "max": 1,
            "min": 0
        }
    }
}
```

In the **MODULE\_NAME.tsx** view file, you can define the HTML structure for the slots on the page.

The following example shows an excerpt from a React view file (campaign-page-container.view.tsx) that takes advantage of the slots for the container.

```React
...
        return (
            <div  {...this.props.renderModuleAttributes(this.props)} id={this.props.id}>
                <div className='row'>
                    {slots.header[0]}
                </div>
                <div className='row'>
                    {slots.primary[0]}
                </div>
                <div className='row'>
                    {slots.footer[0]}
                </div>
            </div>
        );
    }
...
```

## Test a page container module

To test a page container module in a local development environment, you must use a page mock.

The following example shows a page mock that can be used for testing. It's saved in the **/src/pageMocks** directory as **campaignContainerMock.json**.

```json
{
    "exception": null,
    "pageRoot": {
        "id": "core-root_0",
        "typeName": "core-root",
        "modules": {
            "body": [
                {
                    "id": "default-page_0",
                    "typeName": "campaign-page-container",
                    "modules": {
                        "primary": [
                            {
                                "id": "primaryArea__0",
                                "typeName": "myContainer",
                                "modules": {
                                    "slot1": [
                                        { 
                                            "id": "ProductFeature__0",
                                            "typeName": "productFeature",
                                            "config": {
                                                "imageAlignment": "left",
                                                "productTitle": "Men's Grand Wingtip Shoe",
                                                "productDetails": "Genuine leather crafted with perfection.",
                                                "buttonText": "Buy Now"
                                            }
                                        }
                                    ],
                                    "slot2": [
                                        { 
                                            "id": "ProductFeature__1",
                                            "typeName": "productFeature" ,
                                            "config": {
                                                "imageAlignment": "right",
                                                "productTitle": "Men's Grand Wingtip Shoe",
                                                "productDetails": "Genuine leather crafted with perfection.",
                                                "buttonText": "Buy Now"
                                            }
                                        }
                                    ]
                                }
                            }
                        ] 
                    }
                }
            ]
        } 
    },
    "renderingContext": {
        "staticContext": {
            "staticCdnUrl": "/_scnr/"
        },
        "locale": "en-us"
    },
    "statusCode": 200
}
```

Notice that the preceding page mock defines only the **primary** slot in the page container. However, you can also include the **header** and **footer** slots as you require.

## Preview the page

To preview the page in a local web browser, follow these steps.

1. At a command prompt, go to your root SDK folder, and run the **yarn start** command. Here is an example.

    ```Console
    c:\repos\Msdyn365.Commerce.Online\yarn start
    ```

1. In a web browser, open the following URL to view the module: `https://localhost:4000/page?mock=campaign-containerMock`. Note the name of the page mock in the **mock=** query string parameter.

## Additional resources

[Create a new module](create-new-module.md)

[Clone a module library module](clone-starter-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Test modules by using module mocks](test-module-mock.md)

[Test modules by using page mocks](test-page-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Localize a module](localize-module.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
