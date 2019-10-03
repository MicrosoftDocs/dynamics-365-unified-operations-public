---
# required metadata

title: Page load data actions
description: This topic covers page load data actions in Microsoft Dynamics 365 Commerce.
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

# Page load data actions

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers page load data actions in Microsoft Dynamics 365 Commerce. 

## Overview

Every page that is rendered, whether it's a product details page, a department page, or a home page, requires data. Page load data actions are used to obtain that data.

## The createInput method

When a page is loaded, a data action can be called by using the **createInput** method. The following example shows the sample code that is created in the TypeScript file for a data action by using the **yarn d365 add-data-action DATA\_ACTION\_NAME** command-line interface (CLI) command.

```typescript
const createInput = (args: Msdyn365.ICreateActionContext): Msdyn365.IActionInput => {
    return new GetProductReviewsInput();
};
```

The **ICreateActionContext** type represents an object that is passed to every **createInput** method. It contains three pieces of information:

- The request context (**inputData.requestContext**)
- The module's configuration (**inputData.config**)
- The module's data (**inputData.data**)

In the following example, notice that the **createInput** method in the TypeScript template file has been added to the **createDataAction** call. Therefore, the Dynamics 365 Commerce online software development kit (SDK) can determine that this data action can be run on page load.

```typescript
export default Msdyn365.createObservableDataAction({
    action: <Msdyn365.IAction<IGetMyDataData>>action,
    input: createInput
});
```

### Example of the createInput method

For the following example of the **createInput** method, the module that calls the data action has a configuration string property that is named **productId**. The value of this property is a product ID that the data action will use as input.

```typescript
/**
 * Creates a ProductInput using module configuration data
 */
const createInput = (inputData: ICreateActionContext<IGeneric<IAny>>): IActionInput => {
    // Ensure module has a config property 'productId'
    if(inputData.config && inputData.config.productId) {
        // Create and return an input for the data action using the module configuration data.
        return new ProductInput(inputData.config.productId);
    }
};
```

## Register the data action on a module

Before a module can call a data action on page load, the data action must be registered in the module definition file.

The following example shows a module that uses the data action earlier in this topic to get product information so that it can be shown inside the module.

```json
{
    "$type": "moduleDefinition",
    "name": "product-module",
    "friendlyName": "Product module",
    "description": "Product module",
    "module": {
        "view": "./product-module",
        "dataActions": {
            "product": {
                "path": "../../actions/get-product"
            }
        }
    },
    "categories": ["Product"],
    "config": {
        "productId": {
            "friendlyName": "Id of Product to show",
            "description": "The Id of the Product that will be rendered in this module",
            "type": "string",
            "default": "12345"
        },
    }
}
```

Here, the **module.dataActions** property indicates the data actions that should be run when a module is loaded on a page. The name of every key in the data actions object refers to the name of the property that the result will be assigned to in the module's data properties (in this case, the **this.props.data.product** property). Additionally, the **path** property of every data action points to a file that exports the data action that should be run. Generally the data action is the default export of the file it was written in.

Notice that the **productId** configuration property defines what is used as input for the data action. Page authors can use this configuration property to specify a product ID as input for the module when the page is built. This configuration property is also required by the example of the **createInput** method earlier in this topic. When the module is configured on a page, the **productId** value that is specified in the module's configuration is loaded on that page.

To help guarantee that you have the correct typing for the module when you develop your module view, you must update the module data file with corresponding types, based on the data actions that you've registered. Here is an example.

```typescript
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';

// product-module.data.ts
export interface IProductModuleData {
    product: AsyncResult<SimpleProduct>;
}
```

Now, when you develop this module, you will have access to the product information via the **this.props.data.product** property.

## Register a core data action

The Dynamics 365 Commerce online SDK contains a set of core data actions for performing typical retail data tasks. Interfaces for core data actions can be found under the \\node\_modules\\@msdyn365-commerce-modules\\retail-actions\\dist\\lib directory. To register a core data action so that you can use it inside your module, use the following format in your MODULE\_data.ts file.

```typescript
import { SimpleProduct } from '@msdyn365-commerce/commerce-entities';
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';
export interface IProductFeatureData {
    /**
     * @dataAction @msdyn365-commerce-modules/retail-actions/dist/lib/get-simple-products
     * @runAt server
     */
    products: AsyncResult<SimpleProduct>[];
}
```

Notice that this example calls a core data action that is named **get-simple-products**. This data action returns an array of **SimpleProduct** results. The interface for the **SimpleProduct** return type is defined in the \\node\_modules\\@msdyn365-commerce\\commerce-entities\\dist\\types\\commerce-entities directory that is imported at the top of the example.
