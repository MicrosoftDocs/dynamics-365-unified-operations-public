---
title: Page load data actions
description: This article covers page load data actions in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 07/31/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Page load data actions

[!include [banner](../includes/banner.md)]

This article covers page load data actions in Microsoft Dynamics 365 Commerce. 

Every page that is rendered, whether it's a product details page, a department page, or a home page, requires data. Page load data actions are used to obtain that data.

## The createInput method

When a page is loaded, a data action can be called by using the **createInput** method. The following example shows the sample code that is created in the TypeScript file for a data action by using the **yarn msdyn365 add-data-action DATA\_ACTION\_NAME** command-line interface (CLI) command.

```typescript
const createInput = (args: Msdyn365.ICreateActionContext): Msdyn365.IActionInput => {
    return new GetProductReviewsInput();
};
```

The **ICreateActionContext** type represents an object that is passed to every **createInput** method. It contains three pieces of information:

- The request context (**inputData.requestContext**)
- The module's configuration (**inputData.config**)
- The module's data (**inputData.data**)

In the following example, notice that the **createInput** method in the TypeScript template file has been added to the **createObservableDataAction** call. Therefore, the Dynamics 365 Commerce online software development kit (SDK) can determine that this data action can be run on page load.

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

The following example shows a module that uses a data action named "get-product" to get product information so that it can be shown inside the module.

```json
{
    "$type": "moduleDefinition",
    "name": "product-module",
    "friendlyName": "Product module",
    "description": "Product module",
    "categories": ["Product"],
    "dataActions": {
        "product": {
            "path": "../../actions/get-product.action",
            "runOn": "server"
        }
    },
...
}
```

Here, the **dataActions** node indicates the data actions that should be run when a module is loaded on a page. The name of every key in the data actions object refers to the name of the property that the result will be assigned to in the module's data properties (in this case, the **this.props.data.product** property). Additionally, the **path** property of every data action points to a file that exports the data action that should be run. Generally, the data action is the default export of the file it was written in.

To help ensure that you have the correct typing for the module when you develop your module view, you must update the module data file with corresponding types, based on the data actions that you've registered. Here is an example.

```typescript
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';

// product-module.data.ts
export interface IProductModuleData {
    product: AsyncResult<SimpleProduct>;
}
```

Now, when you develop this module, you will have access to the product information via the **this.props.data.product** property.

## Client-side rendering
Dynamics 365 Commerce renders pages server side and [hydrates](https://reactjs.org/docs/react-dom.html#hydrate) the page on the client after the initial load. Data actions defined in a module definition are executed on the server by default, which causes modules to render server side. If a module explicitly needs to render on client, the **runOn** parameter value needs to be set to 'client' in the module definition file as shown below. 

```json
{
    "$type": "moduleDefinition",
    "name": "product-module",
    "friendlyName": "Product module",
    "description": "Product module",
    "categories": ["Product"],
    "dataActions": {
        "product": {
            "path": "../../actions/get-product.action",
            "runOn": "client"
        }
    },
...
}
```
> [!NOTE] 
> If a data action is being used in multiple modules with both server/client "runOn" configurations, the data action will run only on the server side. Therefore, it is important to avoid conflicting the **runOn** configurations if the module needs to be rendered explicitly on the client side.

## Register a core data action

The Dynamics 365 Commerce online SDK contains a set of core data actions that can be used to perform typical Commerce data tasks. Interfaces for core data actions can be found under the \\node\_modules\\@msdyn365-commerce-modules\\retail-actions\\dist\\lib directory. To register a core data action so that you can use it inside your module, use the following format in the **dataActions** node of your MODULE\_definition.json file.

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
        "productIds": {
            "friendlyName": "Product ID",
            "description": "Provide a Product Id that the module will display",
            "type": "string",
            "scope": "module",
            "group": "Content Properties"
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

Notice that this example calls a core data action that is named **get-simple-products**. This data action uses the **productIds** config property to get the list of product IDs and returns an array of **SimpleProduct** results. The following example shows the module data.ts file that defines the return value. The interface for the **SimpleProduct** return type is defined in the \\node\_modules\\@msdyn365-commerce\\commerce-entities\\dist\\types\\commerce-entities directory that is imported at the top of the example.


```typescript
import { AsyncResult, SimpleProduct } from '@msdyn365-commerce/retail-proxy';

export interface IProductFeatureData {
    products: AsyncResult<SimpleProduct>[];
}
```

## Additional resources

[Data actions overview](data-actions.md)

[Data action cache options](data-action-cache.md)

[Test data actions with mocks](test-data-action-mocks.md)

[Event-based data actions](event-based-data-actions.md)

[Core data actions](core-data-actions.md)

[Call Retail Server APIs](call-retail-server-apis.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
