---
# required metadata


title: Call Commerce Scale Unit APIs
description: This topic explains how to call application programming interfaces (APIs) for Microsoft Dynamics 365 Commerce Scale Unit from a data action or directly from module code.
author: samjarawan
ms.date: 09/21/2021
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
# Call Commerce Scale Unit APIs

[!include [banner](../includes/banner.md)]

This topic explains how to call application programming interfaces (APIs) for Microsoft Dynamics 365 Commerce Scale Unit from a data action or directly from module code.

To call Commerce Scale Unit APIs, you must use the Retail Server proxy library that the Commerce online software development kit (SDK) provides. This proxy library is also known as TypeScriptProxy or TSProxy. It allows for streamlined communication with the Commerce Scale Unit from JavaScript-based or TypeScript-based environments.

## Install the Retail Server proxy


The Retail Server proxy is available for download via the Dynamics 365 NPM feed and should be added by default. If it isn't there, you can get it by adding a reference in the package.json file.


To install the proxy in your software development kit (SDK) development environment, follow these steps.

1. Determine your current active version of Retail Server. This version will be the version of the Retail Server NuGet package that you use for back-end extensibility.
1. In the **package.json** file, add the following entry in the **dependencies** section. (This entry might already be present and have up-to-date version information.)

    ```json
    "@msdyn365-commerce/retail-proxy": "{RETAIL_SERVER_VERSION}"
    ```

1. Run **yarn install**.

You should now have access to the correct Retail Server proxy for your project. You might see that a reference is already included as part of the module library.

## Retail Server proxy data action managers

The Retail Server proxy contains a set of APIs that communicate internally with Commerce Scale Unit via HTTP. These APIs are all available through a set of data action managers. To import the code for these data action managers, you can use the following import paths.

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

For a list of all the available Retail Server APIs in each data action manager, see [Commerce Scale Unit customer and consumer APIs](../dev-itpro/retail-server-customer-consumer-api.md).

## Retail Server proxy data methods

The Retail Server proxy is closely linked to the [Data Action Framework](data-actions.md). Therefore, for every Commerce Scale Unit API, there are two exposed Retail Server proxy methods:

- **The createInput method** – This method creates an **IActionInput** class that can be used either to run a [page load data action](page-load-data-action.md), or to do a direct state update or fetch via the **actionContext.update()** or **actionContext.get()** methods. This method is always named **create{RETAIL\_SERVER\_API\_NAME}Input**.
- **The action method** – This method can be invoked on its own as an [event-based data action](event-based-data-actions.md), or it can be added inside another action method to create a [data action chain](chain-data-actions.md). This method is always named **{RETAIL\_SERVER\_API\_NAME}Async**.

## Create a page load Retail Server proxy data action

When you want to attach a Retail Server proxy API call to a module so that it will run when a page is loaded, you must create a new data action. The process resembles the process for creating a standard page load data action.

In this example, you will create a module that uses the Retail Server proxy to get all the categories that are available for the configured channel when a page is loaded. To start, you must identify the correct Commerce Scale Unit proxy API to use. For this example, this API is the **GetCategories** API that is provided by the **CategoriesDataActions** data action manager. You can then construct a data action that can be used in a module definition. In general, to complete this task, you must do two things:

- Provide a **createInput** method that calls the Retail Server proxy **createInput** method for the desired API and passes it any contextual data that you want (for example, the channel ID).
- Have the action method of the new data action be the **retailAction** method that is provided by the Retail Server proxy. The **retailAction** method is designed to parse the input that is passed to it and call the corresponding Retail Server proxy API.

Under the **src\\actions** directory, create a file for a new data action. For this example, the file is named **get-category-list.ts**, and it contains the following code.

```typescript
import { createObservableDataAction, IAction, ICreateActionContext } from '@msdyn365-commerce/core';
import { Category, retailAction } from '@msdyn365-commerce/retail-proxy';
import { createGetCategoriesInput } from '@msdyn365-commerce/retail-proxy/dist/DataActions/CategoriesDataActions.g';

/**
 * Get Org Unit Configuration Data Action
 */
export default createObservableDataAction({
    action: <IAction<Category[]>>retailAction,
    input: (context: ICreateActionContext) => {
        return createGetCategoriesInput({ Paging: { Top: 0 } }, context.requestContext.apiSettings.channelId);
    }
});
```


The **get-category-list.ts** file exports a data action that can be registered on a module to get the list of all categories from whatever channel has been configured for the project. Because this approach requires much less custom code to make the HTTP call than manual communication with Retail Server, we recommend that you always call Retail Server by using the Retail Server proxy.

The following example shows how the **get-category-list** data action can be registered in the **"module" \> "dataActions"** node in the module definition file.


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
        },
        "productReviews": {
            "path": "../../actions/getproductreviews",
            "runOn": "server"
        },
        "categories": {
            "path": "../../actions/get-category-list",
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
        },
        "productTitle": {
            "type": "string",
            "friendlyName": "Product Title",
            "description": "Product placement title"
        },
        "productDetails": {
            "type": "richText",
            "friendlyName": "Product Details",
            "description": "Rich text representing the featured product details"
        },
        "productImage": {
            "type": "image",
            "friendlyName": "Product Image",
            "description": "Image representing the featured product"
        },
        "buttonText": {
            "type": "string",
            "friendlyName": "Button Text",
            "description": "Text to show on the call to action button"
        },
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

The module **data.ts** file also requires an entry for the return type of the data action. The following example shows a sample module **data.ts** file. After it's implemented, the property can be accessed from the module's view file by using the **this.props.data.** object.

```typescript

import { AsyncResult, Category, SimpleProduct } from '@msdyn365-commerce/retail-proxy';
export interface IProductFeatureData {
    products: AsyncResult<SimpleProduct>[];
    categories: AsyncResult<Category[]>;
}
```

## Call a Retail Server proxy API directly in module code


The following example shows how to call the **getCategories** Commerce API by using the Commerce proxy **getCategoriesAsync** wrapper API. This API call returns a list of all categories, and the sample code logs them to the console.

```typescript
import * as React from 'react';

import { getCategoriesAsync } from '@msdyn365-commerce/retail-proxy/dist/DataActions/CategoriesDataActions.g';
import { IProductFeatureData } from './product-feature.data';
import { imageAlignment, IProductFeatureProps} from './product-feature.props.autogenerated';

export interface IProductFeatureViewProps extends IProductFeatureProps<{}> {
    productName: string;
}

/**
 *
 * ProductFeature component
 * @extends {React.PureComponent<IProductFeatureProps<IProductFeatureData>>}
 */
class ProductFeature extends React.PureComponent<IProductFeatureProps<IProductFeatureData>> {
    public render(): JSX.Element | null {
        const {
            config,
        } = this.props;

        // set default product info values from config values if available
        let ProductName = config.productTitle ? config.productTitle : 'No product name defined';

        getCategoriesAsync({ callerContext: this.props.context.actionContext }, this.props.context.request.apiSettings.channelId)
        .then(categoryList2 => {
            let categories2 = '';
            for (let i = 0; i < categoryList2.length; i++) {
                categories2 += `${categoryList2[i].Name}, `;
            }
            console.log(categories2);
        });

        const ProductFeatureViewProps = {
            ...this.props,
            productName: ProductName,
        };

        return this.props.renderView(ProductFeatureViewProps) as React.ReactElement;
    }
}

export default ProductFeature;
```

## Additional resources

[Data actions overview](data-actions.md)

[Data action cache options](data-action-cache.md)

[Test data actions with mocks](test-data-action-mocks.md)

[Page load data actions](page-load-data-action.md)

[Event-based data actions](event-based-data-actions.md)

[Core data actions](core-data-actions.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
