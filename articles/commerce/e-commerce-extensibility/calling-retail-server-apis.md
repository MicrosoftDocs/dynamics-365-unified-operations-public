---
# required metadata

title: Set up calling Retail Server APIs
description: This topic describes how to set call Microsoft 365 Dynamics Retail Server APIs from a data action.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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
# Calling Retail Server APIs

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to set up calling Microsoft Dynamics 365 Retail Server APIs from either a data action or directly from module code.

## Overview
To call Retail Server APIs, we'll leverage the Retail Server proxy library (also known as the TypeScriptProxy or TSProxy), provided by the Dynamics 365 Retail Server to allow for streamlined communication with Retail Server from JavaScript or TypeScript-based environments.

## Get started with the Retail Server proxy

The Retail Server Proxy is available for download via the Dynamics 365 NPM Feed and can be obtained by adding a reference to the packages.json file. Below are the steps needed to install the Retail Server Proxy into your SDK dev environment.

1. Determine your current active version of Retail Server. This will be the version of the Retail Server NuGet you use for Retail Server backend extensibility. 

2. Add the following entry to the dependencies section of your package.json (it may already be there with up to date version info):

    ```json
        "@msdyn365-commerce/retail-proxy": "{RETAIL_SERVER_VERSION}"
    ```

3. Run `yarn install`

Now you should have access to the correct Retail Server proxy for your project. You may already see a reference included as part of the Store Starter Kit.

## Using the Retail Server Proxy

The Retail Server proxy mainly contains a set of APIs which internally communicate with Retail Server using HTTP. These APIs are all available through a set of Data Action Managers which can be imported in code using the following import paths.

```typescript
// Generic example
import {} from '@msdyn365-commerce/retail-proxy/dist/DataActions/{DATA_ACTION_MANAGER_NAME}.g';

// Specific example
import { getByIdsAsync } from '@msdyn365-commerce/retail-proxy/dist/DataActions/ProductsDataActions.g';
```

The following Data Action Managers are available:

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

For an entire list of all available Retail API's within each Data Action Manager, please refer to the [Retail Server Customer and consumer APIs](https://docs.microsoft.com/en-us/dynamics365/retail/dev-itpro/retail-server-customer-consumer-api) documentation.

The Retail Server proxy is closely tied to the [Data Action Framework](./data-actions), so for every Retail Server API, there are two exposed Retail Server proxy methods:

- The createInput method for the Retail Server API. This method will always be named **create{RETAIL_SERVER_API_NAME}Input**. This method will create an `IActionInput`, which can be used to either run a [Page-load Data Action](./page-load-data-actions) or be used to do direct state updating/fetching via `actionContext.update()**` or `actionContext.get()` methods.

- The action method for the Retail Server API. This method will always be named {RETAIL_SERVER_API_NAME}Async. This method can be invoked on it's own to as a [Event-based Data Action](./event-based-data-actions), or added inside another Action method to create a [Data Action Chain](./chain-data-actions).

We will cover a few common Retail Server proxy usage scenarios below in more depth.

### Create a page load Retail Server proxy data action

When you want to attach a Retail Server Proxy API call to a module so it will run on page load, you need to create a new data action, very similar in practice to just creating a standard [Page-load Data Action](./page-load-data-actions). 

For this example, we will create a module which will use the Retail Server proxy to get all the categories available for the configured channel on page load. To start we need to identify the correct Retail Server proxy API we want to use, which in this case happens to be the `GetCategories` API provided by the CategoriesDataActions manager. We can now construct a [data action](./data-actions) so that it can be used within a module definition. To do so we generally need to do two things:

1. Provide a createInput method which calls the Retail Server proxy provided createInput method for our desired API, and passing along any contextual data we want to the API (such as ChannelId).

2. Have the action method of our new data action be the Retail Server proxy provided `retailAction`. `retailAction` is designed to parse the input that is passed to it and call the corresponding Retail Server proxy API

For example, a new data action can be created under the **src\actions** directory called **getCategoryList.ts** with the following code.

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
        console.log('Creating the unput');
        console.log(context);
        return createGetCategoriesInput({ Paging: { Top: 10 } }, context.requestContext.apiSettings.channelId);
    }
});
```

This above file will now export a data action which can be regsitered on a module to get the first 10 categories from whatever channel has been configure for the project! Because this requires much less custom code to make the HTTP call than communicating with Retail Server manually, it is highly suggested that you only call Retail Server using the Retail Server proxy.

The following example shows how this data action can be registered in the module definition file inside the **"module" -> "dataActions"** node.

```{
    "$type": "contentModule",
    "friendlyName": "Product Feature",
    "name": "productFeature",
    "description": "Feature module used to highlight a product.",
    "categories": ["storytelling"],
    "tags": [""],
    "module": {
        "view": "./productFeature",
        "dataActions": {
            "categories":{
                "path": "../../actions/getCategoryList",
                "runOn": "server"
            }
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

The module data.ts file will also need an entry for the return type of the data action. The following example shows a sample module data.ts file. Once implemented, this property can be accessed from the modules view file using the `this.props.data.` object.

```
import { AsyncResult , Category, SimpleProduct } from '@msdyn365-commerce/retail-proxy';

export interface IProductFeatureData {
    products: AsyncResult<SimpleProduct>[];
    categories: AsyncResult<Category[]>;
}
```
    
### Call a Retail Proxy API directly in module code

The following code snippet shows how to call the getCategories Retail API with the Retail proxy wrapper API **getCategoriesAsync**.  This API call will return a list of all categories.

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
