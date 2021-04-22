---
# required metadata

title: Batch data actions
description: This topic describes how to batch data actions.
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
# Batch data actions

[!include [banner](../includes/banner.md)]

This topic describes how to batch data actions.

Often you'll have an application that requires many calls to the same application programming interface (API) during the load of a single page. An example is a product feature page that showcases information about many products instead of just one product. In a typical approach, multiple calls are made to the data action to get products. However, because this approach uses many individual HTTP requests to get the product information, it might not be efficient. To solve this issue, the data action architecture supports batchable data actions.

## Examples

The main difference between a batch data action and a standard data action is the batch data action's support for an array of action inputs. In the following example of a standard data action, notice that the **getSimpleProductAction** action method accepts only one **ProductInput** class.

```typescript
async function getSimpleProductAction(input: ProductInput, ctx: IActionContext): Promise<SimpleProduct>
```

To change this data action to a batch data action, modify the method signature so that the method can accept an array of **ProductInput** classes and return an array of **SimpleProduct** objects. The following example shows how the data action method must be updated so that it can process an array of inputs and return an array.

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

Now that the data action method has been updated so that it can handle an array of inputs, the **isBatched** property in the action creation call must be set to **true**.

```typescript
export default createObservableDataAction({
    action: <IAction<SimpleProduct[]>>getSimpleProductsAction,
    input: createInput,
    isBatched: true
});
```

Because this action now supports batching, if the action is called in multiple places during a page load, the data action framework automatically groups the requests together. That's why this approach helps minimize the number of HTTP requests that are required and helps maximize performance.

> [!NOTE]
> Some APIs might not support batching on their side. So when you create a batch data action, you should confirm that the service that you're using can support the action.

## Additional resources

[Chain data actions](chain-data-actions.md)

[Create an observable data action](create-observable-data-action.md)

[Share state across modules](share-state-across-modules.md)

[Data action cache settings](data-action-cache-settings.md)

[Data action overrides](data-action-overrides.md)

[Data action hooks](data-action-hooks.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
