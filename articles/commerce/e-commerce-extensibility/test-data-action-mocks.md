---
# required metadata

title: Test data actions with mocks
description: This topic describes how to test data actions with mock data.
author: samjarawan
ms.date: 07/23/2020
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
ms.dyn365.ops.version: Release 10.0.5

---
# Test data actions with mocks

[!include [banner](../includes/banner.md)]

This topic describes how to test data actions with mock data.

By mocking data actions in Microsoft Dynamics 365 Commerce, you can replace the output of a data action with the data that is specified in the actionmock.json file that has been loaded. An action mock is useful if you want to test your module without invoking the actual action. You will have to use this approach if you haven't configured your Commerce server (**MSDyn365Commerce_BASEURL** property) in the .env file. For more information about .env files, see [Configure a development environment (.env) file](configure-env-file.md).

## Action mock structure

To create a data action mock, create a new file under the **/src/module/&lt;MODULE_NAME&gt;/mocks/** directory for your module. The name of the new file should be in the format **&lt;MODULE\_MOCK\_NAME&gt;.actionmock.json**, as in the following example.

```/src/modules/product-feature/mocks/myModuleMock.actionmock.json```

After the file is created, you can simulate the data action return object inside the file by specifying the **CacheObjectType** and **CacheKey** values that are defined in the data action. The **CacheKey** value can be set to "**&#42;**" to accept any cache key. For more information, see [Data actions](data-actions.md).

The following example shows how the **&lt;MODULE\_MOCK\_NAME&gt;.actionmock.json** file should be structured.

```json
{
    "CacheObjectType": "MyCacheObjectType",
    "CacheKey": "MyCacheKey",
    "Mock": {
        "foo": "bar"      
    }
}
```

If no **CacheKey** value is specified, or if "**&#42;**" is specified, all actions that have the corresponding **CacheObjectType** value will receive the mock output.

## Example

The following example shows a module definition file that uses a data action, and the corresponding data action mock that returns product data.

Example module definition file:

```json
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "product-feature",
    "description": "Feature module used to highlight a product.",
    "categories": [
        "storytelling"
    ],
    "tags": [
        ""
    ],
    "dataActions": {
        "products": {
            "path": "@msdyn365-commerce-modules/retail-actions/dist/lib/get-simple-products",
            "runOn": "server"
        }
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
        }
    },
    "resources": {
        "resourceKey": {
            "comment": "resource description",
            "value": "resource value"
        }
    }
}
```

Example module mock file:

```json
[
    {
        "CacheObjectType": "SimpleProduct",
        "CacheKey": "*",
        "Mock": {
            "RecordId": 22565423455,
            "ItemId": "2101",
            "Name": "Retro Horn-Rimmed Keyhole Sunglasses",
            "Description": "High-quality with the perfect blend of timeless classic and modern technology with hint of old school glamor.",
            "ProductTypeValue": 3,
            "DefaultUnitOfMeasure": "Ea",
            "BasePrice": 15,
            "Price": 15,
            "AdjustedPrice": 14,
            "MasterProductId": null,
            "Components": null,
            "Dimensions": null,
            "Behavior": null,
            "LinkedProducts": null,            
            "PrimaryImageUrl": "https://bit.ly/33cMGxr",
            "ExtensionProperties": null
        }
    }
]
```

> [!NOTE]
> The **CacheObjectType** and **CacheKey** values should match the values in the data action that you're mocking. If no **CacheKey** value is specified, all actions that have the corresponding **CacheObjectType** value receive the mock output.

## Use an action mock in a preview

To use an action mock in your module preview, include the query string parameter for the action mock **actionMock=MODULE_NAME:MOCK_FILE_NAME**, as shown in the following example.

`https://localhost:4000/modules?type=product-feature&actionMock=product-feature:myModuleMock`

Here is the syntax of the query string parameter.

`{module-name}:{action-mock-file-name}`

If no action mock file name is specified, the package name is used to search for the mock.

## Additional resources

[Data actions overview](data-actions.md)

[Data action cache options](data-action-cache.md)

[Page load data actions](page-load-data-action.md)

[Event-based data actions](event-based-data-actions.md)

[Core data actions](core-data-actions.md)

[Call Retail Server APIs](call-retail-server-apis.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
