---
# required metadata

title: Batch data actions
description: This topic describes how to batch data actions.
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
# Batch data actions

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to batch data actions.

## Overview

In many scenarios, you will have an application that requires many calls to the same application programming interface (API) during the load of a single page. An example is a product feature page that showcases information about many products instead of just one product. A typical approach is to make multiple calls to the data action to get products. However, because this approach uses many individual HTTP requests to get the product information, it might not be very efficient. To solve this issue, the data action architecture supports batchable data actions.

## Examples

The main difference between a batch data action and a standard data action is its support for an array of action inputs. In the following example of an action method inside a data action, notice that only one **ProductInput** class is accepted.

```typescript
async function getSimpleProductAction(input: ProductInput, ctx: IActionContext): Promise<SimpleProduct>
```

To change the previous data action into a batch data action, you update the method signature as shown in the following example.

```typescript
async function getSimpleProductsAction(inputs: ProductInput[], ctx: IActionContext): Promise<SimpleProduct[]>
```

Notice that you're expecting the action to receive an array of inputs and return an array of products back from the API. To support this behavior, you must update the action function.

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

Now that the data action method has been updated to handle an array of inputs, you must set **isBatched** in the action creation call to **true**.

```typescript
export default createObservableDataAction({
    action: <IAction<SimpleProduct[]>>getSimpleProductsAction,
    input: createInput,
    isBatched: true
});
```

Because this action now supports batching, if the action is called in multiple places during a page load, the data action framework automatically groups the requests together. Therefore, this approach helps minimize the number of HTTP requests that are required and helps maximize performance.

> [!NOTE]
> Some APIs might not support batching on their side. Therefore, when you create a batch data action, confirm that the service that you're using can support the action.
