---
# required metadata

title: Clone a module library module
description: This topic describes how to clone a module library module in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 11/17/2021
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

It is recommended that you avoid cloning if possible because clones will be copies of module library modules and won't receive any automatic service updates that the module library modules get. There are several extensibility alternatives to cloning that should be considered before module cloning, such as module view and definition extensions that enable you to provide alternative layout views, and data action overrides that allow you to modify business logic. For more information, see [Theming overview](theming.md). 

## Clone and update a module

To clone a module and then update it, use the **clone** [command-line interface (CLI)](cli-command-reference.md#clone) command. When you run the following command, you replace **SDK\_MODULE\_NAME** with the name of the module that you want to modify and **NEW\_MODULE\_NAME** with the name of the new module.

**yarn msdyn365 clone SDK\_MODULE\_NAME NEW\_MODULE\_NAME**

This command adds the source code for the module to the /src/modules/ directory and pulls in any required dependencies for the module.

Use the following command to get a list of the modules that can be cloned:

**yarn msdyn365 clone --listmodules**

### Example

The following example shows how to clone the [media gallery](../media-gallery-module.md) module library module so that you can make changes to it.


```Console
yarn msdyn365 clone media-gallery super-media-gallery
```

After the command has finished running, you can find the new module in the \\src\\modules\\ directory.

> [!NOTE]
> Module dependencies aren't automatically pulled down when you clone a module. Before you build the module, you must run Yarn and fix any missing dependencies. If any errors occur when you run the **yarn start** command, you might also have to fix some references inside the module source code.

When building a cloned module, you may see linting errors listed on the cloned module code. To automatically fix linting errors, run the **yarn lint:fix** command.

## Preview a module

There are several ways to preview a cloned module on a development environment using either a [module mock](test-module-mock.md) or a [page mock](test-page-mock.md). Many cloned modules do not come with module mocks, so you may need to create one manually.  

### Preview with a module mock

To create a mock file for the cloned **super-media-gallery** module in the example above, under the module directory create a **mocks** directory, and then create and save a JSON file in that directory with a name that matches the module name (such as "\mocks\super-media-gallery.json" for the example above).

The mock file needs to be in a format similar to that shown in the following example, where the **typeName** value matches the module name:

```json
{
    "id": "R1Module1",
    "config": {

    },
    "typeName": "super-media-gallery"
  }
 ```
 
You can then add specific **config** values as needed. To determine what mock config values to add, a good reference would be to create a page mock as shown in the next section and then copy the **config** values from the live module to the module mock.

To preview the new module in a local web browser, follow these steps.

1. At a command prompt, go to your root SDK folder and run the **yarn start** command as shown in the following example.

    ```Console
    c:\repos\Msdyn365.Commerce.Online\yarn start
    ```

1. In a web browser, open the following URL to view the module: `https://localhost:4000/modules?type=super-media-gallery`. Note the use of the module name in the **type=MODULE\_NAME** query string parameter.

### Preview with a page mock

Alternatively, a page mock can be used to preview the module by following the instructions in [Test modules by using page mocks](test-page-mock.md). Included in the topic are details on creating a dynamic page mock from a live production page using the **?item=nodeserviceproxy:true** query string parameter. Staying with the example above, you would save a product details page into a page mock and then modify the page mock to replace the "buy-box" module with the "super-buy-box" module. The new page mock file would then be save under the **/src/pageMocks/** directory, for example "/src/pageMocks/pdp-page-test.json".

Once you have created the page mock, the module you cloned will then need to be updated to the new cloned module within the mock JSON file. For example, if you created a page mock based off of a product details page, search for the "media-gallery" module and you should find a section similar to that in the following example where you can then change the **typename** and **id** values from **media-gallery** to the new **super-media-gallery**.

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

To preview the new module with a page mock within a local web browser, follow these steps.

1. At a command prompt, go to your root SDK folder, and run the **yarn start** command as shown in the following example.

    ```Console
    c:\repos\Msdyn365.Commerce.Online\yarn start
    ```

1. In a web browser, use the following URL format to view the module, replacing the **PAGE_MOCK** parameter with the page mock filename without the .json extension.

 `https://localhost:4000/page?mock=PAGE_MOCK`
 
 For example, the URL for the page mock file "pdp-page-test.json" would be:
 
 `https://localhost:4000/page?mock=pdp-page-test`

You can now make code changes to the cloned module and see the changes within the page mock.

## Build and deploy the new module

Once your changes have been made, the SDK extension package can be built and deployed to a sandbox and/or production environment following the steps in [Package configurations and deploy them to an online environment](package-deploy.md).

## Load the new module in site builder 

Once the module has been deployed, the original module can then be replaced with the cloned module. For example, to replace the media gallery module with a new cloned super media gallery module, edit the product details page within site builder, remove the media gallery module, and then add the new cloned super media gallery module in its place.

### Module categories

Some modules are designed to only work within specific container modules. For example, the media gallery module (and the cloned super media gallery module from the example) both have module definition files with a **categories** section that includes the **buybox_mediaGallery** category, as shown in the following example code snippet from the super-media-gallery.definition.json file.

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

The parent container module (in this case the buy box module referred to in the example above) has a slot designed to hold the media gallery module as shown in the buybox.definition.json code snippet below (which can be found in the \node_modules\@msdyn365-commerce-modules\buybox\src\modules\buybox directory). 

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

The **allowedTypes** section specifies that the slot allows modules of type **media-gallery** or modules that belong to the **buybox_mediaGallery** category. This metadata is used by site builder to limit the modules shown for a particular slot by only showing the modules allowed for that slot. As long as the cloned module doesn't remove the category, it can replace the original module in its slot.

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
