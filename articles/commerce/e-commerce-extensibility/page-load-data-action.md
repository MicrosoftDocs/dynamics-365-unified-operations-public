---
# required metadata

title: Page load data actions
description: Whether rendering a product details page, department page, or a home page, every page needs data and data actions are the way to get it!
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
# Page load data actions

Whether rendering a product details page, department page, or a home page, every page needs data and data actions are the way to get it!

## The `createInput` method
A data action supports being called on page load with the `createInput` method.  Below shows the sample code created in the data action typescript file that the CLI tool `yarn d365 add-data-action DATA_ACTION_NAME` creates.

```typescript
const createInput = (args: Msdyn365.ICreateActionContext): Msdyn365.IActionInput => {
    return new GetProductReviewsInput();
};
```
The `ICreateActionContext` type, represents an object that is passed to every `createInput` method, containing three pieces of information:

1. The requestContext (inputData.requestContext)
1. The modules configuration (inputData.config)
1. The modules data (inputData.data)

Notice the `createInput` method in the typescript template file has been added to the `createDataAction` call so that the Dynamics 365 Commerce Online SDK understands that this action is capable of running on page load.

```typescript
export default Msdyn365.createObservableDataAction({
    action: <Msdyn365.IAction<IGetMyDataData>>action,
    input: createInput
});
```

### Example createInput method

In the  `createInput` method example below we assume that the module calling this Data Action will have a configuration string property called `productId`, which is the ID of a product the Data Action will use as input.

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

## Registering the Data Action on a module

To have a module call a Data Action on page load, the Data action needs to be registered in the module definition file.

Below is an example of a module using the example Data Action above to get product information to display inside their module.  

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
Here the `module.dataActions` property indicates which data actions should be run when a module is loaded on a page. The name of every key in the data actions object refers to the property name the result will be assigned to within the data props of the module (in this case `this.props.data.prodiuct`), and the path property for every data action points to a file whose default export is the data action that should be run. 

Also notice the config property `productId` defined which is used as the input to the Data Action.  This config property allows a page author to specify a Product Id as input to the module when building the page.  This same productId is also required by the `createInput` method example above. When this module is configured on a page, whatever `productId` is specified in the modules configuration is the one that will be loaded on that page.

Finally to ensure we have the correct typing for our module when developing our module view, we need to update our module data file with corresponding types based on the data actions we have registered:
```typescript
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';

// product-module.data.ts
export interface IProductModuleData {
    product: AsyncResult<SimpleProduct>;
}
```

Now when developing this module, you will have access to the product information via `this.props.data.product`.

## Registering a core Data Action

The Online SDK contains a set of core data actions to perform common retail data tasks. Core data action interfaces can be found under the `\node_modules\@msdyn365-commerce-modules\retail-actions\dist\lib` directory.  To register to use a core Data Action inside your module use the following format inside your `MODULE_data.ts` file where:

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

Notice above example is calling a core Data Action called "get-simple-products" which returns an array of `SimpleProduct`s.  The interface for the return type `SimpleProduct` is defined in the `\node_modules\@msdyn365-commerce\commerce-entities\dist\types\commerce-entities` directory which is imported at the top of the example.
