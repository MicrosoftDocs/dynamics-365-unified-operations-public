---
# required metadata

title: Call Commerce Scale Unit APIs
description: This topic explains how to call application programming interfaces (APIs) for Microsoft Dynamics 365 Commerce Scale Unit from a data action or directly from module code.
author: samjarawan
manager: annbe
ms.date: 10/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
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
# Call Commerce Scale Unit APIs

[!include [banner](../includes/banner.md)]

This topic explains how to call application programming interfaces (APIs) for Microsoft Dynamics 365 Commerce Scale Unit from a data action or directly from module code.

## Overview

To call Commerce Scale Unit APIs, you must use the Commerce Scale Unit proxy library that Commerce Scale Unit provides. This proxy library is also known as TypeScriptProxy or TSProxy. It allows for streamlined communication with Commerce Scale Unit from JavaScript-based or TypeScript-based environments.

## Install the Commerce Scale Unit proxy

The Commerce Scale Unit proxy is available for download via the Dynamics 365 npm feed. You can get it by adding a reference in the packages.json file.

To install the proxy in your software development kit (SDK) development environment, follow these steps.

1. Determine your current active version of Commerce Scale Unit. This version will be the version of the Commerce Scale Unit NuGet package that you use for back-end extensibility.
1. In the **package.json** file, add the following entry in the **dependencies** section. (This entry might already be present and have up-to-date version information.)

    ```json
    "@msdyn365-commerce/retail-proxy": "{RETAIL_SERVER_VERSION}"
    ```

1. Run **yarn install**.

You should now have access to the correct Commerce Scale Unit proxy for your project. You might see that a reference is already included as part of the Store Starter Kit.

## Commerce Scale Unit proxy data action managers

The Commerce Scale Unit proxy contains a set of APIs that communicate internally with Commerce Scale Unit via HTTP. These APIs are all available through a set of data action managers. To import the code for these data action managers, you can use the following import paths.

```typescript
// Generic example
import {} from '@msdyn365-commerce/retail-proxy/dist/DataActions/{DATA_ACTION_MANAGER_NAME}.g';

// Specific example
import { getByIdsAsync } from '@msdyn365-commerce/retail-proxy/dist/DataActions/ProductsDataActions.g';
```

The following data action managers are available:

- CartsDataActions
- CatalogsDataActions
- CategoriesDataActions
- CommerceListsDataActions
- CustomersDataActions
- EmployeesDataActions
- OrgUnitsDataActions
- PickingListsDataActions
- ProductsDataActions
- PurchaseOrdersDataActions
- RecommendationsDataActions
- SalesOrdersDataActions
- ScanResultsDataActions
- ShiftsDataActions
- StockCountJournalsDataActions
- StoreOperationsDataActions
- SuspendedCartsDataActions
- TransferOrdersDataActions
- WarehousesDataActions

For a list of all the available Commerce Scale Unit APIs in each data action manager, see [Retail Server Customer and Consumer APIs](https://docs.microsoft.com/dynamics365/retail/dev-itpro/retail-server-customer-consumer-api).

## Commerce Scale Unit proxy data methods

The Commerce Scale Unit proxy is closely linked to the [Data Action Framework](data-actions.md). Therefore, for every Commerce Scale Unit API, there are two exposed Commerce Scale Unit proxy methods:

- **The createInput method** – This method creates an **IActionInput** class that can be used either to run a [page load data action](page-load-data-action.md), or to do a direct state update or fetch via the **actionContext.update()** or **actionContext.get()** methods. This method is always named **create{RETAIL\_SERVER\_API\_NAME}Input**.
- **The action method** – This method can be invoked on its own as an [event-based data action](event-based-data-actions.md), or it can be added inside another action method to create a [data action chain](chain-data-actions.md). This method is always named **{RETAIL\_SERVER\_API\_NAME}Async**.

## Create a page load Commerce Scale Unit proxy data action

When you want to attach a Commerce Scale Unit proxy API call to a module so that it will run when a page is loaded, you must create a new data action. The process resembles the process for creating a standard page load data action.

In this example, you will create a module that uses the Commerce Scale Unit proxy to get all the categories that are available for the configured channel when a page is loaded. To start, you must identify the correct Retail Server proxy API to use. For this example, this API is the **GetCategories** API that is provided by the **CategoriesDataActions** data action manager. You can then construct a data action that can be used in a module definition. In general, to complete this task, you must do two things:

- Provide a **createInput** method that calls the Commerce Scale Unit proxy **createInput** method for the desired API and passes it any contextual data that you want (for example, the channel ID).
- Have the action method of the new data action be the **retailAction** method that is provided by the Commerce Scale Unit proxy. The **retailAction** method is designed to parse the input that is passed to it and call the corresponding Commerce Scale Unit proxy API.

Under the **src\\actions** directory, create a file for a new data action. For this example, the file is named **getCategoryList.ts**, and it contains the following code.

```typescript
import { IAction, createObservableDataAction, ICreateActionContext, } from '@msdyn365-commerce/core';
import { Category, retailAction } from '@msdyn365-commerce/retail-proxy';
import { createGetCategoriesInput } from '@msdyn365-commerce/retail-proxy/dist/DataActions/CategoriesDataActions.g';

/**
 * Get Org Unit Configuration Data Action
 */
export default createObservableDataAction({
    action: <IAction<Category[]>>retailAction,
    input: (context: ICreateActionContext) => {
        console.log('Creating the input');
        console.log(context);
        return createGetCategoriesInput({ Paging: { Top: 10 } }, context.requestContext.apiSettings.channelId);
    }
});
```

The **getCategoryList.ts** file exports a data action that can be registered on a module to get the first 10 categories from whatever channel has been configured for the project. Because this approach requires much less custom code to make the HTTP call than manual communication with Commerce Scale Unit, we recommend that you call Commerce Scale Unit only by using the Commerce Scale Unit proxy.

The following example shows how the **getCategoryList** data action can be registered in the **module \> dataActions** node in the module definition file.

```
{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "productFeature",
    "description": "Feature module used to highlight a product.",
    "categories": ["storytelling"],
    "tags": [""],
    "dataActions": {
        "categories":{
            "path": "../../actions/getCategoryList",
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
    }
}
```

The module **data.ts** file also requires an entry for the return type of the data action. The following example shows a sample module **data.ts** file. After it's implemented, the property can be accessed from the module's view file by using the **this.props.data.** object.

```
import { AsyncResult , Category, SimpleProduct } from '@msdyn365-commerce/retail-proxy';
export interface IProductFeatureData {
    products: AsyncResult<SimpleProduct>[];
    categories: AsyncResult<Category[]>;
}
```

## Call a Commerce Scale Unit proxy API directly in module code

The following example shows how to call the **getCategories** Commerce API by using the proxy **getCategoriesAsync** wrapper API. This API call returns a list of all categories.

```typescript
import * as React from 'react';
import { IProductFeatureData } from './productFeature.data';
import { imageAlignment, IProductFeatureProps } from './productFeature.props.autogenerated';
import { getCategoriesAsync } from '@msdyn365-commerce/retail-proxy/dist/DataActions/CategoriesDataActions.g';

/**
 *
 * ProductFeature component
 * @extends {React.PureComponent<IProductFeatureProps<IProductFeatureData>>}
 */
class ProductFeature extends React.PureComponent<IProductFeatureProps<IProductFeatureData>> {
    public render(): JSX.Element {
        ...
        getCategoriesAsync({ callerContext: this.props.context.actionContext },this.props.context.request.apiSettings.channelId)
            .then(categoryList => {
                let categories = '';
                for (let i=0; i < categoryList.length; i++) {
                    categories += `${categoryList[i].Name}, `;
                }
                console.log(categories);
            })
...
```
## Additional resources

[Data actions overview](data-actions.md)

[Test data actions with mocks](test-data-action-mocks.md)

[Page load data actions](page-load-data-action.md)

[Event-based data actions](event-based-data-actions.md)

[Core data actions](core-data-actions.md)
