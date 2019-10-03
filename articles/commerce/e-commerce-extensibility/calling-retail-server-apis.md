---
# required metadata

title: Calling Retail Server APIs
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
# Calling Retail Server APIs

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to set call Microsoft 365 Dynamics Retail Server APIs from ethier a data action or directly from your view code.

## Overview
To call Retail Server APIs, we'll leverage the Retail Server Proxy library (also known as the TypeScriptProxy or TSProxy), provided by the Dynamics 365 Retail Server to allow for streamlined communication with Retail Server from JavaScript or TypeScript based environments.

## Getting Started With the Retail Server Proxy

The Retail Server Proxy is available for download via the Dynamics 365 NPM Feed. It is listed as `@msdyn365-commerce/retail-proxy`. Below are the steps needed to install the Retail Server Proxy into your SDK dev environment.

1. Determine your currently active version of Retail Server. This will be the version of the Retail Server NuGet you use for Retail Server backend extensibility. You can also look up a version chart here to help determine your Retail Server version based off of Retail Server marketing version numbers. {TODO: Vikrant provide link to RS Version Table}

2. Add the following entry to the dependencies section of your package.json (it may already be there with up to date version info):

    ```json
        "@msdyn365-commerce/retail-proxy": "{Your Retail Server Version}"
    ```

3. Run `yarn install`

Now you should have access to the correct Retail Server Proxy for your project.

## Using the Retail Server Proxy

The Retail Server Proxy mainly contains a set of API's which internally communicate with Retail Server via HTTP. These API's are all available via a set of Data Action Managers which can be imported in code using the following import path's:

```typescript
// Generic example
import {} from '@msdyn365-commerce/retail-proxy/dist/DataActions/{Data Action Manager Name}.g';

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

For an entire list of all available API's within each Data Action Manager, please refer to the [Retail Server Customer and consumer APIs](https://docs.microsoft.com/en-us/dynamics365/retail/dev-itpro/retail-server-customer-consumer-api) Documentation.

The Retail Server Proxy is closely tied to the [Data Action Framework](./data-actions), so for every Retail Server API, there are two exposed Retail Server Proxy methods:

1. The createInput method for the Retail Server API. This method will always be named **create{Retail Server API Name}Input**. This method will create an `IActionInput`, which can be used to either run a [Page-load Data Action](./page-load-data-actions), or be used to do direct state updating/fetching via `actionContext.update()` or `actionContext.get()`

2. The action method for the Retail Server API. This method will always be named {Retail Server API Name}Async. This method can be invoked on it's own to as a [Event-based Data Action](./event-based-data-actions), or added inside another Action method to create a [Data Action Chain](./chain-data-actions).

We will cover a few common Retail Server Proxy usage scenarios below in more depth.

### Creating a Page-Load Retail Server Proxy Data Action

When you want to attach a Retail Server Proxy API call to a module so it will run on page load, you need to create a new Data Action, very similar in practice to just creating a standard [Page-load Data Action](./page-load-data-actions). For this example, we will create a module which will use the Retail Server Proxy to get all the categories available for the configured channel on page load. To start we need to identify the correct Retail Server Proxy API we want to use, which in this case happens to be the `GetCategories` API provided by the CategoriesDataActions manager. Now that we know the API we need to use, we can construct a [data action](./data-actions) so that it can be used within a module definition. To do so we generally need to do two things:

1. Provide a createInput method which calls the Retail Server Proxy provided createInput method for our desired API, and passing along any contextual data we want to the API (such as ChannelId).

2. Have the action method of our new data action be the Retail Server Proxy provided `retailAction`. `retailAction` is designed to parse the input that is passed to it and call the corresponding Retail Server Proxy API

For example a new data action can be createe under the ***src\actions\*** directory called **getCagegoryList** with the below code:

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

This above file will now export a data action which can be regsitered on a module to get the first 10 categories from whatever channel has been configure for the project! Because this requires much less custom code to make thie HTTP call than communicating with Retail Server manual, it is highly suggested that you **only call Retail Server useing the Retail Server Proxy**

The below example shows how this data action can be registered in the module definition file inside the **"module" -> "dataActions"** node.

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

The module data.ts file will also need an entry for the return type of the data action.  The below example shows a sample module data.ts file.

```
import { AsyncResult , Category, SimpleProduct } from '@msdyn365-commerce/retail-proxy';

export interface IProductFeatureData {
    products: AsyncResult<SimpleProduct>[];
    categories: AsyncResult<Category[]>;
}
```
