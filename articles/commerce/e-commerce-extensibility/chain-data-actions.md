---
# required metadata

title: Chain data actions
description: This topic describes how to chain data actions.
author: samjarawan
ms.date: 07/16/2020
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
# Chain data actions

[!include [banner](../includes/banner.md)]

This topic describes how to chain data actions.

To create a maintainable and compact codebase, you will often need a suite of composable data actions that can easily use each another to create more complex code flows. The Microsoft Dynamics 365 Commerce Online Software Development Kit (SDK) lets you seamlessly chain data actions but still provide all the out-of-box benefits of the data action architecture (caching, batching, and deduplicating).

## Examples

The following examples show data action chaining. First, a product information call is made. This call is followed by an inventory call.

The first example shows a data action that gets product information.

```typescript
// get-product.ts
import { IAction, IActionInput } from '@msdyn365-commerce/action';
import { SimpleProduct } from '@msdyn365-commerce/commerce-entities';
import { CommerceEntityInput, createObservableDataAction, IAny, ICreateActionContext, IActionContext, IGeneric, IHTTPError, IHTTPResponse, sendCommerceRequest } from '@msdyn365-commerce/core';
import { ProductInput } from './inputs/product-input';

/**
 * Product Action Input Class
 * This class is used by our Action Function, so that it has access to a productId
 */
export class ProductInput implements IActionInput {
    public channelId: number;
    public productId: number;
    constructor(productId: number, channelId: number) {
        this.channelId = channelId;
        this.productId = productId;
    }
    public getCacheKey = () => `${this.channelId}-${this.productId}`;
    public getCacheObjectType = () => 'Product';
    public dataCacheType = (): Msdyn365.CacheType => 'application';
}

/**
 * Action Function which calls the Retail API and returns the product based on the passed ProductInputs productId
 */
async function getSimpleProductAction(input: ProductInput, ctx: IActionContext): Promise<SimpleProduct> {
    const { apiSettings } = ctx.requestContext;

    // Construct our HTTP request using information available in actionContext (ctx), and our Action Input (input)
    const requestUrl = `${apiSettings.baseUrl}/Products/${input.productId}`;

    // Make the HTTP Request
    return sendCommerceRequest<SimpleProduct>(requestUrl, 'get'})
        .then((response: IHTTPResponse) => {
            if(response.data) {
                return response.data;
            }
            ctx.trace('[getSimpleProductAction] Invalid response from server');
            return <SimpleProduct>[];
        })
        .catch((error: IHTTPError) => {
            ctx.trace(error.message);
            ctx.trace(error.stack || '');
            ctx.trace(`Unable to Fetch Product.`);
            return <SimpleProduct>{};
        });
}

/**
 * This exports the action Data Action, which the result of passing your action method and createInput method (if used)
 * to the createDataAction method.
 */
export default createObservableDataAction({
    action: <IAction<SimpleProduct>>getSimpleProductAction
});
```

The second example shows a data action that gets inventory information.

```typescript
// check-inventory.ts
import { IAction, IActionInput } from '@msdyn365-commerce/action';
import { ProductAvailableQuantity } from '@msdyn365-commerce/commerce-entities';
import { createObservableDataAction, IAny, IActionContext, IGeneric, IHTTPError, IHTTPResponse, sendCommerceRequest } from '@msdyn365-commerce/core';

// Because this API also only needs a productId, we can re-use the ProductInput we created earlier here.
import { ProductInput } from './get-product.ts';

/**
 * Calls the Retail API and returns the Availability information for the passed Product
 */
async function getProductAvailabilityAction(input: ProductInput, ctx: IActionContext): Promise<ProductAvailableQuantity> {
    const { apiSettings } = ctx.requestContext;

    // Construct our HTTP request using information available in actionContext (ctx), and our Action Input (input)
    const requestUrl = `${apiSettings.baseUrl}/Products/GetProductAvailabilities`;
    const requestBody = {
        productId: input.productId;
    }

    // Make the HTTP Call and handle the response
    return sendCommerceRequest<ProductAvailableQuantity>(requestUrl, 'post', requestBody)
        .then((response: IHTTPResponse) => {
            if(response.data) {
                return response.data;
            }
            ctx.trace('[getProductAvailabilityAction] Invalid response from server');
            return <ProductAvailableQuantity>[];
        })
        .catch((error: IHTTPError) => {
            ctx.trace(error.message);
            ctx.trace(error.stack || '');
            ctx.trace(`Unable to Fetch Product Availability.`);
            return <ProductAvailableQuantity>{};
        });
}

export default createObservableDataAction({
    action: getProductAvailabilityAction
})
```

Now that you have actions for getting the product data and the **ProductAvailableQuantity** value of a product, you can create a new chain data action. Chain data actions are just data actions that invoke other data actions as part of their execution.

The following example shows the **getProductWithAvailability** chain data action, which uses both the preceding actions.

```typescript
import getProduct, { ProductInput } from './get-product';
import getProductAvailability from './check-inventory';

/**
 * This interface will be the return type of our chain data action.
 * This contains both the basic product information in addition to the product's availability information.
 */
export interface SimpleProductWithAvailablility extends SimpleProduct {
    availability: ProductAvailableQuantity
}

/**
 * Calls the Retail API and returns the Availability information for the passed Product
 */
async function getProductWithAvailabilityAction(input: ProductInput, ctx: IActionContext): Promise<SimpleProductWithAvailablility> {
    // First we get the product
    const product: SimpleProductWithAvailablility = await <SimpleProductWithAvailablility>getProduct(input, ctx);

    // If we successfully get the product, then we try to get its availability information.
    if(product) {
        // Get the availability information
        product.availability = await getProductAvailability(input, ctx)
    } else {
        return <SimpleProductWithAvailablility>{};
    }
}

export default createObservableDataAction({
    action: getProductWithAvailabilityAction
})
```

You can now use the new chain data action wherever you need both the basic product information and the product's current inventory status. In addition, the calls that exist in the chain data action are still run through the cache. They are also batched and deduplicated together with other actions that are run on the same page.

## Additional resources

[Batch data actions](batch-data-actions.md)

[Create an observable data action](create-observable-data-action.md)

[Share state across modules](share-state-across-modules.md)

[Data action cache settings](data-action-cache-settings.md)

[Data action overrides](data-action-overrides.md)

[Data action hooks](data-action-hooks.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
