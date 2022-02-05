---
# required metadata

title: Clone a module library module
description: This topic describes how to clone a module library module in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 11/22/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgriffin
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Clone a module library module

[!include [banner](../includes/banner.md)]

This topic describes how to clone a module library module in Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce online software development kit (SDK) includes a set of [module library](../starter-kit-overview.md) modules that can be used on an e-commerce site. Although these modules can't be modified directly, they can be cloned into new modules and then updated. 

We recommend that you avoid cloning modules, if possible, because the clones will be copies of module library modules and won't receive any automatic service updates that the module library modules get. There are several extensibility alternatives that you should consider before you clone modules. These alternatives include module view and definition extensions that let you provide alternative layout views, and data action overrides that let you modify business logic. For more information, see [Theming overview](theming.md). 

## Clone and update a module

To clone a module and then update it, use the **clone** [command-line interface (CLI)](cli-command-reference.md#clone) command. When you run the following command, you replace **SDK\_MODULE\_NAME** with the name of the module that you want to modify and **NEW\_MODULE\_NAME** with the name of the new module.

**yarn msdyn365 clone SDK\_MODULE\_NAME NEW\_MODULE\_NAME**

This command adds the source code for the module to the /src/modules/ directory and pulls in any required dependencies for the module.

Use the following command to get a list of the modules that can be cloned.

```Console
yarn msdyn365 clone --listmodules
```

### Example

The following example shows how to clone the [media gallery](../media-gallery-module.md) module library module so that you can make changes to it.

```Console
yarn msdyn365 clone media-gallery super-media-gallery
```

After the command has finished running, you can find the new module in the \\src\\modules\\ directory.

> [!NOTE]
> Module dependencies aren't automatically pulled down when you clone a module. Before you build the module, you must run Yarn and fix any missing dependencies. If any errors occur when you run the **yarn start** command, you might also have to fix some references inside the module source code.

When you build a cloned module, you might see that linting errors are listed on the cloned module code. To automatically fix linting errors, run the **yarn lint:fix** command.

## Preview a module

There are several ways to use either a [module mock](test-module-mock.md) or a [page mock](test-page-mock.md) to preview a cloned module in a development environment. Many cloned modules don't have module mocks. Therefore, you might have to create one manually.

### Preview a module by using a module mock

To create a mock file for the cloned **super-media-gallery** module in the preceding example, create a **mocks** directory under the module directory. Then create and save a JavaScript Object Notation (JSON) file in that directory, and give it a name that matches the module name (such as **\\mocks\\super-media-gallery.json** for the preceding example).

The format of the mock file must resemble the following example, where the **typeName** value matches the module name.

```json
{
    "id": "R1Module1",
    "config": {

    },
    "typeName": "super-media-gallery"
}
```
 
You can then add specific **config** values as required. If you want a reference that can help you determine which mock **config** values you should add, you can create a page mock as shown in the next section and then copy the **config** values from the live module to the module mock.

To preview the new module in a local web browser, follow these steps.

1. At a command prompt, go to your root SDK folder, and run the **yarn start** command as shown in the following example.

    ```Console
    c:\repos\Msdyn365.Commerce.Online\yarn start
    ```

1. In a web browser, open the following URL to view the module: `https://localhost:4000/modules?type=super-media-gallery`. Notice that the module name is used in the **type=MODULE\_NAME** query string parameter.

### Preview a module by using a page mock

Alternatively, you can use a page mock to preview the module. For instructions, see [Test modules by using page mocks](test-page-mock.md). That topic includes information about how to use the **?item=nodeserviceproxy:true** query string parameter to create a dynamic page mock from a live production page. For the example earlier in this topic, you will save a product details page into a page mock and then modify the page mock to replace the "buy-box" module with the "super-buy-box" module. Then save the new page mock file under the **/src/pageMocks/** directory (for example, **/src/pageMocks/pdp-page-test.json**).

After you've created the page mock, you must update the module that you cloned to the new cloned module in the mock JSON file. For example, if you created a page mock that is based on a product details page, search for the "media-gallery" module. You should find a section that resembles the following example. You can then change the **typename** and **id** values from **media-gallery** to **super-media-gallery**.

```JSON
"modules": {
    "mediaGallery": [
        {
            "typeName": "media-gallery",
            "id": "media-gallery",
            "friendlyName": "Media gallery",
            "config": {
                "imageZoom": "inline",
                "allowFullScreen": true,
                "dataScale": "2",
            }
        }
    ]
}
```

To preview the new module by using a page mock in a local web browser, follow these steps.

1. At a command prompt, go to your root SDK folder, and run the **yarn start** command as shown in the following example.

    ```Console
    c:\repos\Msdyn365.Commerce.Online\yarn start
    ```

1. In a web browser, use the following URL format to view the module. Replace the **PAGE\_MOCK** parameter with the name of the page mock file, but omit the .json extension.

    `https://localhost:4000/page?mock=PAGE_MOCK`
 
    For example, here is the URL for the pdp-page-test.json page mock file.
 
    `https://localhost:4000/page?mock=pdp-page-test`

You can now make code changes to the cloned module and see the changes in the page mock.

## Build and deploy the new module

After you've made your changes, you can build the SDK extension package and deploy it to a sandbox and/or production environment. For instructions, see [Package configurations and deploy them to an online environment](package-deploy.md).

## Load the new module in site builder 

After you've deployed the module, you can replace the original module with the cloned module. For example, to replace the media gallery module with a new cloned super media gallery module, edit the product details page in site builder, remove the media gallery module, and then add the new cloned super media gallery module in its place.

### Module categories

Some modules are designed to work only in specific container modules. For example, the module definition files for the media gallery module and the cloned super media gallery module from the earlier example have a **categories** section that includes the **buybox\_mediaGallery** category, as shown in the following example from the super-media-gallery.definition.json file.

```JSON
{
	"$type": "contentModule",
	"friendlyName": "Super media gallery",
	"name": "super-media-gallery",
	"description": "Media gallery is used for showcasing images of a product in a product details page",
	"categories": [
		"media-gallery",
		"buybox_mediaGallery"
	],
}	
```

The parent container module (in this case, the buy box module that is referred to in the preceding example) has a slot that is designed to hold the media gallery module, as shown in the following example from the buybox.definition.json file. (You can find this file in the \\node\_modules\\@msdyn365-commerce-modules\\buybox\\src\\modules\\buybox directory.) 

```JSON
"slots": {
    "mediaGallery": {
        "friendlyName": "Media Gallery",
        "description": "This the slot for the media gallery",
        "max": 1,
        "min": 0,
        "allowedTypes": ["media-gallery"],
        "allowedCategories": ["buybox_mediaGallery"]
    },
}
```

The **allowedTypes** section specifies that the slot allows modules of the **media-gallery** type or modules that belong to the **buybox\_mediaGallery** category. Site builder uses this metadata to limit the modules that are shown for a given slot. It shows only the modules that are allowed for that slot. As long as the cloned module doesn't remove the category, it can replace the original module in its slot.

## Additional resources

[Create a new module](create-new-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Test modules by using module mocks](test-module-mock.md)

[Test modules by using page mocks](test-page-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)

[Localize a module](localize-module.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
