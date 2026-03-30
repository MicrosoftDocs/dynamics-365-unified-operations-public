---
title: Page load data actions
description: Learn about page load data actions in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/05/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Page load data actions

[!include [banner](../includes/banner.md)]

This article covers page load data actions in Microsoft Dynamics 365 Commerce. 

Every rendered page, whether it's a product details page, a department page, or a home page, requires data. Use page load data actions to get that data.

## The createInput method

When you load a page, use the **createInput** method to call a data action. The following example shows the sample code created in the TypeScript file for a data action by using the **yarn msdyn365 add-data-action DATA\_ACTION\_NAME** command-line interface (CLI) command.

```typescript
const createInput = (args: Msdyn365.ICreateActionContext): Msdyn365.IActionInput => {
    return new GetProductReviewsInput();
};
```

The **ICreateActionContext** type represents an object passed to every **createInput** method. It contains three pieces of information:

- The request context (**inputData.requestContext**)
- The module's configuration (**inputData.config**)
- The module's data (**inputData.data**)

In the following example, the **createInput** method in the TypeScript template file is added to the **createObservableDataAction** call. Therefore, the Dynamics 365 Commerce online software development kit (SDK) can determine that this data action can run on page load.

```typescript
export default Msdyn365.createObservableDataAction({
    action: <Msdyn365.IAction<IGetMyDataData>>action,
    input: createInput
});
```

### Example of the createInput method

In the following example of the **createInput** method, the module that calls the data action has a configuration string property named **productId**. The value of this property is a product ID that the data action uses as input.

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

Before a module can call a data action on page load, register the data action in the module definition file.

The following example shows a module that uses a data action named `get-product` to get product information so that it can be shown inside the module.

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

Here, the **dataActions** node indicates the data actions that should be run when a module is loaded on a page. The name of every key in the data actions object refers to the name of the property that the result is assigned to in the module's data properties (in this case, the **this.props.data.product** property). Additionally, the **path** property of every data action points to a file that exports the data action that should be run. Generally, the data action is the default export of the file it was written in.

To help ensure that you have the correct typing for the module when you develop your module view, you must update the module data file with corresponding types, based on the data actions that you registered. Here's an example.

```typescript
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';

// product-module.data.ts
export interface IProductModuleData {
    product: AsyncResult<SimpleProduct>;
}
```

Now, when you develop this module, you have access to the product information via the **this.props.data.product** property.

## Client-side rendering

Dynamics 365 Commerce renders pages server side and [hydrates](https://reactjs.org/docs/react-dom.html#hydrate) the page on the client after the initial load. Data actions defined in a module definition execute on the server by default, which causes modules to render server side. If a module explicitly needs to render on client, set the **runOn** parameter value to `client` in the module definition file as shown in the following example.

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

Here, the **dataActions** node indicates the data actions that should be run when a module is loaded on a page. The name of every key in the data actions object refers to the name of the property that the result is assigned to in the module's data properties (in this case, the **this.props.data.product** property). Additionally, the **path** property of every data action points to a file that exports the data action that should be run. Generally, the data action is the default export of the file it was written in.

> [!NOTE] 
> If you use a data action in multiple modules with both server and client "runOn" configurations, the data action runs only on the server. Therefore, avoid conflicting **runOn** configurations if the module needs to render explicitly on the client.

## Register a core data action

The Dynamics 365 Commerce online SDK contains a set of core data actions that you can use to perform typical Commerce data tasks. You can find interfaces for core data actions under the `\node_modules\@msdyn365-commerce-modules\retail-actions\dist\lib` directory. To register a core data action so that you can use it inside your module, use the following format in the **dataActions** node of your `MODULE_definition.json` file.

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

Here, the **dataActions** node indicates the data actions that should be run when a module is loaded on a page. The name of every key in the data actions object refers to the name of the property that the result is assigned to in the module's data properties (in this case, the **this.props.data.product** property). Additionally, the **path** property of every data action points to a file that exports the data action that should be run. Generally, the data action is the default export of the file it was written in.

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
