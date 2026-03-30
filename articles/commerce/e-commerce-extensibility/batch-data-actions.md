---
title: Batch data actions
description: Learn how to batch data actions in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/30/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Batch data actions

[!include [banner](../includes/banner.md)]

This article describes how to batch data actions in Microsoft Dynamics 365 Commerce.

Often, an application requires many calls to the same application programming interface (API) during the load of a single page. An example is a product feature page that showcases information about many products instead of just one product. In a typical approach, you make multiple calls to the data action to get products. However, because this approach uses many individual HTTP requests to get the product information, it might not be efficient. To solve this problem, the data action architecture supports batchable data actions.

## Examples

The main difference between a batch data action and a standard data action is the batch data action's support for an array of action inputs. In the following example of a standard data action, the **getSimpleProductAction** action method accepts only one **ProductInput** class.

```typescript
async function getSimpleProductAction(input: ProductInput, ctx: IActionContext): Promise<SimpleProduct>
```

To change this data action to a batch data action, modify the method signature so that the method can accept an array of **ProductInput** classes and return an array of **SimpleProduct** objects. The following example shows how to update the data action method so that it can process an array of inputs and return an array.

```typescript
async function getSimpleProductsAction(inputs: ProductInput[], ctx: IActionContext): Promise<SimpleProduct[]> {
    const { apiSettings } = ctx.requestContext;

    // Construct our HTTP request using information available in actionContext (ctx), and our Action Input (input)
    const requestUrl = `${apiSettings.baseUrl}/Products`;

    // Construct our request context from all the passed inputs
    const requestBody = {
        productIds: inputs.map(input => input.productId);
    }

    // Get the SimpleProducts
    return sendCommerceRequest<SimpleProduct[]>(requestUrl, 'post', requestBody})
        .then((response: IHTTPResponse) => {
            if(response.data) {
                return response.data;
            }
            ctx.trace('[getSimpleProductsAction] Invalid response from server');
            return <SimpleProduct[]>[];
        })
        .catch((error: IHTTPError) => {
            ctx.trace(error.message);
            ctx.trace(error.stack || '');
            ctx.trace(`Unable to Fetch Products.`);
            return <SimpleProduct[]>[];
        });
    }
```

After you update the data action method to handle an array of inputs, set the **isBatched** property in the action creation call to **true**.

```typescript
export default createObservableDataAction({
    action: <IAction<SimpleProduct[]>>getSimpleProductsAction,
    input: createInput,
    isBatched: true
});
```

Because this action now supports batching, if you call the action in multiple places during a page load, the data action framework automatically groups the requests together. This approach helps minimize the number of HTTP requests and helps maximize performance.

> [!NOTE]
> Some APIs might not support batching on their side. When you create a batch data action, confirm that the service you're using can support the action.

## Additional resources

[Chain data actions](chain-data-actions.md)

[Create an observable data action](create-observable-data-action.md)

[Share state across modules](share-state-across-modules.md)

[Data action cache settings](data-action-cache-settings.md)

[Data action overrides](data-action-overrides.md)

[Data action hooks](data-action-hooks.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
