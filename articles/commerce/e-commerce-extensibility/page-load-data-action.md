---
# required metadata

title: Page load data actions
description: Whether rendering a product details page, department page, or a home page, every page needs data and data actions are the way to get it!
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

This topic covers page load data actions in Dynamics 365 Commerce. 

## Overview

Whether rendering a product details page, department page, or home page, every page needs data and page load data actions are used to obtain that data.

## The `createInput` method
A data action supports being called on page load with the `createInput` method. The following example shows the sample code created in a data action TypeScript file using the Command Line Interface (CLI) tool `yarn d365 add-data-action DATA_ACTION_NAME`.

```typescript
const createInput = (args: Msdyn365.ICreateActionContext): Msdyn365.IActionInput => {
    return new GetProductReviewsInput();
};
```
The `ICreateActionContext` type represents an object that is passed to every `createInput` method, and it contains three pieces of information:

- The requestContext (inputData.requestContext)
- The modules configuration (inputData.config)
- The modules data (inputData.data)

In the following example, notice that the `createInput` method in the TypeScript template file has been added to the `createDataAction` call so that the Commerce online software develpoment kit (SDK) understands that this action is capable of running on page load.

```typescript
export default Msdyn365.createObservableDataAction({
    action: <Msdyn365.IAction<IGetMyDataData>>action,
    input: createInput
});
```

### Example of the `createInput` method

In the following `createInput` method example, we assume that the module calling the data action will have a configuration string property called `productId`, which is the ID of a product the data action will use as input.

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

To have a module call a data action on page load, the data action must be registered in the module definition file.

The following example shows a module using the data action above to get product information to display inside the module.  

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
Here the `module.dataActions` property indicates which data actions should be run when a module is loaded on a page. The name of every key in the data actions object refers to the property name the result will be assigned to within the data props of the module (in this case `this.props.data.product`). Also, the path property for every data action points to a file whose default export is the data action that should be run. 

Notice that the config property `productId` defines what is used as the input to the data action. This config property enables a page author to specify a product ID as input to the module when building the page. This same `productId` is also required by the `createInput` method example above. When this module is configured on a page, whichever `productId` is specified in the modules configuration is the one that will be loaded on that page.

To ensure that we have the correct typing for the module when developing our module view, we must update the module data file with corresponding types based on the data actions we have registered, as in the following example.

```typescript
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';

// product-module.data.ts
export interface IProductModuleData {
    product: AsyncResult<SimpleProduct>;
}
```

Now when developing this module, you will have access to the product information via `this.props.data.product`.

## Register a core data action

The Commerce online SDK contains a set of core data actions to perform common retail data tasks. Core data action interfaces can be found under the `\node_modules\@msdyn365-commerce-modules\retail-actions\dist\lib` directory. To register to use a core data action inside your module, use the following format inside your `MODULE_data.ts` file.

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

Notice that the example above is calling a core data action named "get-simple-products" that returns an array of `SimpleProduct` results. The interface for the return type `SimpleProduct` is defined in the `\node_modules\@msdyn365-commerce\commerce-entities\dist\types\commerce-entities` directory, which is imported at the top of the example.
